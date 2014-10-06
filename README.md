Docker Client [![Circle CI](https://circleci.com/gh/spotify/docker-client.png?style=badge)](https://circleci.com/gh/spotify/docker-client)
=============

This is a simple [docker](https://github.com/dotcloud/docker) client written in Java.

```java
final DockerClient docker = new DefaultDockerClient("http://localhost:2375");

// Pull image
docker.pull("busybox");

// Create container
final ContainerConfig config = ContainerConfig.builder()
    .image("busybox")
    .cmd("sh", "-c", "while :; do sleep 1; done")
    .build();
final ContainerCreation creation = docker.createContainer(config);
final String id = creation.id();

// Inspect container
final ContainerInfo info = docker.inspectContainer(id);

// Start container
docker.startContainer(id);

// Kill container
docker.killContainer(id);

// Remove container
docker.removeContainer(id);
```

Maven
-----

```xml
<dependency>
  <groupId>com.spotify</groupId>
  <artifactId>docker-client</artifactId>
  <version>2.4.2</version>
</dependency>
```


Releasing
---------

```sh
mvn release:clean
mvn release:prepare
mvn release:perform
```
