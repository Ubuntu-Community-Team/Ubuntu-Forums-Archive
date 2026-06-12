---
title: "CMake"
date: 2009-06-18
forum: Programming Talk
---

### Post by jacensolo on 2009-06-18
My laptop runs Linux and my Desktop runs windows, so naturally developing a project on both is difficult because of libs/dlls/etc. I started searching for a way and I found Cmake. It is a godsend. I don't have to write makefiles, cmake does it for me, and on Windows it can make VS solutions. (It can generate many others too, such as netbeans or code::blocks.) I really like that it writes makefiles because I never learned/wanted to write them, but I didn't want to use an ide all the time on Linux either. I know about autotools and was heading towards that direction before cmake.

If anyone is interested [http://www.cmake.org](http://www.cmake.org) is the site. 

Anyway, here come the questions. There are a lot of "byproduct" files created such as CMakeFiles folder (with many things inside), cmake_install.cmake, and CMakeCache.txt. Even in the MakeFile there are cmake things. I thought Cmake just generated the makefile does it do something when make is ran too? What are all of these files?

Also, I ran it under windows to test a hello world and it created 3 projects under the solution for one project. I forgot what they were and I'm not at my desktop right now, but I can post it later if needed. Why would it create 3? It was a simple hello world if that helps.

---

### Post by jacensolo on 2009-06-18
Bump

---

### Post by leblancmeneses on 2009-06-19
here ya go...

script compiles all c files in the given directory.  
puts the executables in bin folder.
```

TESTS = $(subst .c,.o,$(shell ls *.c))

%.o: %.c
    @mkdir -p bin
    $(CC) $(CFLAGS) $< ${STATIC_LIBRARIES} -o bin/$@


all: ${TESTS} 

```


learn make.  expand as you need to don't over complicate a simple project.

---

### Post by jacensolo on 2009-06-19
> **leblancmeneses said:**
> here ya go...

script compiles all c files in the given directory.  
puts the executables in bin folder.
```

TESTS = $(subst .c,.o,$(shell ls *.c))

%.o: %.c
    @mkdir -p bin
    $(CC) $(CFLAGS) $< ${STATIC_LIBRARIES} -o bin/$@


all: ${TESTS} 

```


learn make.  expand as you need to don't over complicate a simple project.

Did you read my questions? I was asking what cmake does and why it has those extra files and why my makefiles still rely on cmake. I'm not interested in writing my own makefiles because this project will get very large and make is not (very) windows compatible.

---

### Post by leblancmeneses on 2009-06-20
it's a fancy to believe that one tool can accomplish it all.

use what works great in a specific environment.  

I've worked on large projects managed with make without a problem.
it also ran on windows with cygwin.


I would use make when on linux and use msbuild proj when on windows.
I do this now..  a shell script starts my "make" build and runs my regression harness.  I also have mono develop msbuild project so i can have an ide and debug.  I keep the build processes separate.


you eventually need to understand the build process.  msbuild has targets, and dependencies so does make.  one is xml the other is not.  

Since your a windows guy start with msbulid create a project that runs a configuration called deploy.

you can look at codeplex for user contributed tasks.  This will give you the footing you need to understand make quite quickly.

---

