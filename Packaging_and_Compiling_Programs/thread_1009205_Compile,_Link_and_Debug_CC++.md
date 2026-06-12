---
title: "Compile, Link and Debug C/C++"
date: 2008-12-12
forum: Packaging and Compiling Programs
---

### Post by ScEngMan on 2008-12-12
Hello,

I'm kind of new to C/C++ development in Linux, but I have experience with C/C++ development using Visual Studio.

I want to do software engineering in an application that uses the typical configure and make build system, but I also want to debug the code to learn how it works and probably contribute by fixing some bugs.

But I don't know how to setup the project to use an IDE or a debugger.

My first question is... If I have a project that uses configure and make, how can I load it into an IDE?

The project I'm talking about it GIMP 2.6.3.

I've installed quite a few IDEs (Anjuta, NetBeans, and right now I'm installing KDevelop). Does anybody knows what IDE would work best to develop code for GIMP in Ubuntu?

Thank you,
Diego

---

### Post by gmclachl on 2008-12-13
I don't think Gimp is a good starting point to learn this, I would pick a smaller project to start looking at. 

As for IDE's I like Anjuta but it's custom Makefile support is poor, I think Code::Blocks is about the best one I have found so far. 

In order to debug you need to use a flag (-g) when you compile, if you have an existing Makefile the chances are there is a target which will include this flag. 

Once you have done this you can use gdb to debug, either from the command like or through the IDE, it's your personal preference really. 

George

---

