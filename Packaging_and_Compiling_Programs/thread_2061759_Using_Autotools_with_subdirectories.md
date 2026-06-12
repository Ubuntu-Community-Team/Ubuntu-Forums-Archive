---
title: "Using Autotools with subdirectories"
date: 2012-09-23
forum: Packaging and Compiling Programs
---

### Post by PrideRage on 2012-09-23
Hello.

(First off I'm sorry if it's in the wrong category but I think it's the most appropriate category)

A couple of days ago, I figured I should try learning how to make a makefile and stuff that's related to it. As of yet, I have a very basic knowledge of makefiles, but I've already made a working one based off a tutorial.
However, bigger projects use subdirectories (like /include, /bin, /src etc.)
so now I've put my project into one root directory (with the makefile, readme, install instructions etc.) with 3 subdirectories (/bin, /obj and /src)
Should be obvious what they're used for.

Now I've made a little makefile for this project, and it works perfectly fine.
Here's my makefile:
```
all: main

main: main.o mathex.o
    g++ obj/main.o obj/mathex.o -o bin/main
    
main.o: src/main.cpp
    g++ -c src/main.cpp -o obj/main.o

mathex.o: src/mathex.cpp
    g++ -c src/mathex.cpp -o obj/mathex.o
    
clean:
    rm -f bin/*
    rm -f obj/*
```running the make command creates a working executable file in the /bin directory, executing the command ./bin/main runs that program and no errors occur.

Now I've stumbled upon the autotools, and they're really useful. So I learned how to apply the autotools to a project, and now I'm super proud that my project is not a simple stupid (and totally platform dependent) makefile, BUT there's a problem:
building the program like this:
```
./configure
make

```creates all the .o files and the main executable file in the root directory,
but I want the .o files to be in the /obj directory, and the executable file should be in /bin

Before I forget, here's the makefile.am I use (according to the tutorial I've read it's necessary to write it yourself):
```
bin_PROGRAMS=main
main_SOURCES=main.cpp mathex.cpp
```I don't know what to do anymore :(

I am grateful for any advice :)

Greets, PrideRage

---

### Post by SevenMachines on 2012-09-25
Certainly I'm no expert on autotools but I don't think they work that way, in the sense of having objects and binaries sent to separate directories. Think of it more in terms of having a source tree and some build trees, you could have any number of these shadowing the main source tree, often good for having a range of different builds in this sort of manner.

Maybe you need a debug build, keeping it separate from your source
```
$ mkdir debug_build
$ cd debug_build
$ ../configure --some-debug-options
$ make
```
The you could also have an optimised release build tree like
```
$ mkdir release_build
$ cd release_build
$ ../configure --some-optimisation-options
$ make
```

---

### Post by SevenMachines on 2012-09-25
Ah, this is what I was thinking of
[http://www.gnu.org/savannah-checkouts/gnu/automake/manual/html_node/VPATH-Builds.html](http://www.gnu.org/savannah-checkouts/gnu/automake/manual/html_node/VPATH-Builds.html)

---

