---
title: "Ubuntu 22.04: docker is missing compose command"
date: 2023-09-21
forum: New to Ubuntu
---

### Post by maketopsite on 2023-09-21
Ubuntu:
```
# docker

Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Common Commands:
  run         Create and run a new container from an image
  exec        Execute a command in a running container
  ps          List containers
  build       Build an image from a Dockerfile
  pull        Download an image from a registry
  push        Upload an image to a registry
  images      List images
  login       Log in to a registry
  logout      Log out from a registry
  search      Search Docker Hub for images
  version     Show the Docker version information
  info        Display system-wide information

Management Commands:
  builder     Manage builds
  container   Manage containers
  context     Manage contexts
  image       Manage images
  manifest    Manage Docker image manifests and manifest lists
  network     Manage networks
  plugin      Manage plugins
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes

# docker -v
Docker version **24.0.6**, build ed223bc
```

Devuan Chimaera 4.0:
```
# docker

Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Common Commands:
  run         Create and run a new container from an image
  exec        Execute a command in a running container
  ps          List containers
  build       Build an image from a Dockerfile
  pull        Download an image from a registry
  push        Upload an image to a registry
  images      List images
  login       Log in to a registry
  logout      Log out from a registry
  search      Search Docker Hub for images
  version     Show the Docker version information
  info        Display system-wide information

Management Commands:
  builder     Manage builds
  buildx*     Docker Buildx (Docker Inc., v0.11.2)
  [COLOR=#ff8c00]**compose***    Docker Compose (Docker Inc., v2.21.0)[/COLOR]
  container   Manage containers
  context     Manage contexts
  image       Manage images
  manifest    Manage Docker image manifests and manifest lists
  network     Manage networks
  plugin      Manage plugins
  scan*       Docker Scan (Docker Inc., v0.23.0)
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes


# docker -v
Docker version **24.0.6**, build ed223bc


```
How is it please possible Ubuntu docker is missing some commands (compared to Devuan) although it is same version as in Devuan ?

---

