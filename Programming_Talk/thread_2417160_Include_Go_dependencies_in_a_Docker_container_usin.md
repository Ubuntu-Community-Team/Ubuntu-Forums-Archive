---
title: "Include Go dependencies in a Docker container using mono repo"
date: 2019-04-21
forum: Programming Talk
---

### Post by Crafty Kisses on 2019-04-21
Hey guys, so I have a mono repo with the following structure: 

```
mono-repo
- serviceA
 - main.go
 - Dockerfile
-serviceB
 - main.go
 - Dockerfile
go.mod
go.sum
```

I'm calling the service "serviceA" and the contents of the Dockerfile are as follows: 

```
FROM golang

ENV GO111MODULE=on

WORKDIR /app

COPY . .

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build

ENTRYPOINT ["/app/serviceA"]
```

I want to build the Docker image and include the dependencies from the root of my mono-repo inside the container, I am currently receiving an error saying it can't find any of the dependency packages when I run: 

```
docker build -t serviceA .
```

Unless I place a go.mod inside serviceA I can't see a nice way of achieving what I want. By placing a go.mod inside the service it feels like I'm losing the advantage of services sharing dependencies within the repo. I've also added this line, just to be sure in the Dockerfile:

```
RUN go mod download
```

Still no luck, I'm obviously using mono-repo for the ease of simplified dependencies, so it's a bit discouraging and I'm thinking about going about this the more traditional way.

---

