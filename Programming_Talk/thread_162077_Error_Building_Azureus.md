---
title: "Error Building Azureus"
date: 2006-04-18
forum: Programming Talk
---

### Post by Kimm on 2006-04-18
I'm experimenting with Azureus and the Mono Framework.

Azureus seems to be using the "ant" build system, but when I run ant in the directory where I extracted the sources, this is what I get...

> 
kim@ubuntu:~/Azureus$ ant
Buildfile: build.xml

init:
     [echo] Building Azureus2.jar...
    [mkdir] Created dir: /home/kim/Azureus/dist

compile:
    [javac] Compiling 2055 source files to /home/kim/Azureus

BUILD FAILED
/home/kim/Azureus/build.xml:32: /home/kim/Azureus/build/libs not found.


Can anyone help me with this one... build/libs is indeed not there and I tried downloading the source twice.

---

