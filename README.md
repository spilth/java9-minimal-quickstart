# Java Minimal Quickstart

This is a Maven Archetype for starting a minimal Java project.

It adds the following to what was defined in [java9-minimal-quickstart](https://github.com/spilth/java9-minimal-quickstart):

- `java.version` command line setting via the property `javaVersion`
- Add default `Application.java` and test file `ApplicationTest.java`
- Add Junit 5 dependency
- Add `jacoco-maven-plugin` plugin for code coverage
- Add `maven-enforcer-plugin` and `versions-maven-plugin` plugins for obsolete dependencies handling

## Usage

To create a new Java project using this archetype:

### Build the archetype locally

```console
git clone git@github.com:grumpyf0x48/java-minimal-quickstart.git
cd java-minimal-quickstart
./mvnw install
```

### Generate a project using the archetype

For example, to create a Java **11** project with the following coordinates: `com.example`, `java11-project`, `0.0.1-SNAPSHOT`:

```console
mvn --batch-mode \
    -DarchetypeGroupId=org.grumpyf0x48 \
    -DarchetypeArtifactId=java-minimal-quickstart \
    -DarchetypeVersion=0.1-SNAPSHOT \
    -DgroupId=com.example \
    -DartifactId=java11-project \
    -Dversion=0.0.1-SNAPSHOT \
    -Dname="Project Name" \
    -Ddescription="Project Description" \
    -DjavaVersion=11 \
     archetype:generate
```

Property `javaVersion` will set `java.version` in `pom.xml` of the generated project.

Its default value is: **17**.

Properties `version`, `name` and `description` are optional and will be set with default values if not set in the previous command.

Then, the generated project will look like:

```console
tree java11-project
java11-project
├── pom.xml
└── src
    ├── main
    │        └── java
    │            └── com
    │                └── example
    │                    └── Application.java
    └── test
        └── java
            └── com
                └── example
                    └── ApplicationTest.java

9 directories, 3 files
```

#### Run the tests

Once `ApplicationTest.java` has no more failing tests:

```console
mvn test
```

#### Check the code coverage

```console
firefox target/site/jacoco/index.html &
```

#### Check obsolete plugins

```console
mvn versions:display-plugin-updates
```

#### Check obsolete dependencies

```console
mvn versions:display-dependency-updates
```
