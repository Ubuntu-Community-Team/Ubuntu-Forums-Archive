---
title: "Cross Compile vs Canadian Cross"
date: 2009-03-05
forum: Programming Talk
---

### Post by pocketchange on 2009-03-05
I've been reading the configure.pdf ("The GNU configure and build system") from the gnuarm.com support section.  It describes the difference of Cross-Compiling vs a Canadian Cross.  I'm really confused because it says a Canadian Cross compile has the build, target, and host all different, but the example only says

> While running on a GNU/Linux, you can build a program which will run on a Solaris system. You would use a GNU/Linux cross Solaris compiler to build the program.
Of course, you could not run the resulting program on your GNU/Linux system. You would have to copy it over to a Solaris system before you would run it.


If I'm on an ubuntu system, trying to build a program for an ARM-based board, am I using cross-compiling or canadian cross?

---

### Post by dwhitney67 on 2009-03-05
A cross-compiler.

---

### Post by mmix on 2009-03-07
The Canadian Cross is a method to make first-cross-compiler.

Using metaphor: compiler-compiler. 

Here,

> **"[wikipedia](http://en.wikipedia.org/wiki/Cross-compiler)"]
Canadian Cross

The Canadian Cross is a technique for building cross compilers for other machines. Given three machines A, B, and C, one uses machine A to build a cross compiler that runs on machine B to create executables for machine C. When using the Canadian Cross with GCC, there may be four compilers involved:

    * The proprietary native Compiler for machine A (1) is used to build the gcc native compiler for machine A (2).
    * The gcc native compiler for machine A (2) is used to build the gcc cross compiler from machine A to machine B (3)
    * The gcc cross compiler from machine A to machine B (3) is used to build the gcc cross compiler from machine B to machine C (4)

The end-result cross compiler (4) will not be able to run on your build machine A said:**
> 

---

