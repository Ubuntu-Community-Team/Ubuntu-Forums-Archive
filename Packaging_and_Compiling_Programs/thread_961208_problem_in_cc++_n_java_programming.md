---
title: "problem in c/c++ n java programming"
date: 2008-10-28
forum: Packaging and Compiling Programs
---

### Post by rahullao on 2008-10-28
hey hi!
well iam  new to ubuntu and iam basically into programming.
I want to know what packages and from where i ve to install for c/c++ and java programming...so that i could build my programs and execute them successfully. also what is Emacs?
reply soon!
thanx

---

### Post by tarps87 on 2008-10-28
Emacs is a text editor for Unix systems. Emacs is command line base but there are several GUI front ends for it.
For C you I suggest using the gcc compiler and C++ g++
```
sudo apt-get install g++
```
This should install both as g++ depends on gcc
For Java I suggest using the sun java compiler
```
sudo apt-get install sun-java6-jdk
```
Should install it.

If you want to use an IDE I suggest using netbeens or eclipse, I am currently using eclipse. Both can be found in synaptic

---

