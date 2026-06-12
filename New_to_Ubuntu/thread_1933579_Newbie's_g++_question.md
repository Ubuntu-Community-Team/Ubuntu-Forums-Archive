---
title: "Newbie's g++ question"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by chenxinghao on 2012-02-29
I used to write .c and .h files for C programming. Now I am learning C++ in Ubuntu (installed its 11.10 version in Jan, 2012). The default installation of Ubuntu 11.10 came with a GNU C compiler on my Ubuntu box. Advised by the Ubuntu community I just installed a C++ compiler with the following command in a Terminal window:

sudo apt-get install g++ build-essential

Now, my question is what file name conventions should I use?

(1) Do I use .C or .cpp for C++ source files? 

(2) Do I continue to use .h or .H (or something else) for C++ header files?

(3) An online tutorial on C++ programming used the following line

#include <iostream>

while my old Microsoft C++ Tutorial says to use:

#include <iostream.h>

(for which the g++ compiler on my Ubuntu box says could not find iostream.h)

(4) Do I use the gcc command for both C and C++ compilations or use gcc for C and g++ for C++? 

Too much stuff out there online and many are inconsistent and confusing to me.

A pointer to a good C++ tutorial specifically valid for the Ubuntu 11.10 platform is very much appreciated.

These are my questions for now.

Thank you very much.

---

### Post by silverglade00 on 2012-02-29
1) A .c file is for straight C. A .cpp file is for C++. Please note that case is important. A .c file is different from a .C file. 

2) Use .h

3) This has nothing to do with Microsoft. Ignore that include. use iostream instead of iostream.h.

4) gcc - GNU project C and C++ compiler. g++ is the actual C++ compiler. It comes as a part of gcc (GNU Compiler Collection).

---

### Post by chenxinghao on 2012-02-29
(1) Do I use .C or .cpp for C++ source code files?

(4) I am confused: what is the difference between gcc and g++? Does gcc compile C++ programs too?

I copied the "Hello World!" example - it compiled with g++ but didn't with gcc.

Thanks.

---

### Post by Porcini M. on 2012-02-29
> **chenxinghao said:**
> 
(4) I am confused: what is the difference between gcc and g++? Does gcc compile C++ programs too?


gcc compiles strictly C files - g++ compiles both C++ and C.

---

### Post by MG&amp;TL on 2012-02-29
> **chenxinghao said:**
> (1) Do I use .C or .cpp for C++ source code files?

(4) I am confused: what is the difference between gcc and g++? Does gcc compile C++ programs too?

I copied the "Hello World!" example - it compiled with g++ but didn't with gcc.

Thanks.

.C, .cpp, .cc, .cxx are all used, but convention is for .cpp, and I recommend convention.

gcc-for compiling C
g++-for compiling C++

There's lots of other g<language> compilers, have a look at the gnu website. :)

---

### Post by Dubslow on 2012-02-29
If you're ever in doubt, try 'man g++'. It has the following:

```
For any given input file, the file name suffix determines what kind
       of compilation is done:

       file.c
           C source code which must be preprocessed.

       file.i
           C source code which should not be preprocessed.

       file.ii
           C++ source code which should not be preprocessed.

       file.m
           Objective-C source code.  Note that you must link with the
           libobjc library to make an Objective-C program work.

       file.mi
           Objective-C source code which should not be preprocessed.

       file.mm
       file.M
           Objective-C++ source code.  Note that you must link with the
           libobjc library to make an Objective-C++ program work.  Note that
           .M refers to a literal capital M.

       file.mii
           Objective-C++ source code which should not be preprocessed.

       file.h
           C, C++, Objective-C or Objective-C++ header file to be turned
           into a precompiled header.

       file.cc
       file.cp
       file.cxx
       file.cpp
       file.CPP
       file.c++
       file.C
           C++ source code which must be preprocessed.  Note that in .cxx,
           the last two letters must both be literally x.  Likewise, .C
           refers to a literal capital C.

       file.mm
       file.M
           Objective-C++ source code which must be preprocessed.

       file.mii
           Objective-C++ source code which should not be preprocessed.

       file.hh
       file.H
       file.hp
       file.hxx
       file.hpp
       file.HPP
       file.h++
       file.tcc
           C++ header file to be turned into a precompiled header.

       file.f
       file.for
       file.ftn
           Fixed form Fortran source code which should not be preprocessed.

       file.F
       file.FOR
       file.fpp
       file.FPP
       file.FTN
           Fixed form Fortran source code which must be preprocessed (with
           the traditional preprocessor).

       file.f90
       file.f95
       file.f03
       file.f08
           Free form Fortran source code which should not be preprocessed.

       file.F90
       file.F95
       file.F03
       file.F08
           Free form Fortran source code which must be preprocessed (with
           the traditional preprocessor).

       file.ads
           Ada source code file which contains a library unit declaration (a
           declaration of a package, subprogram, or generic, or a generic
           instantiation), or a library unit renaming declaration (a
           package, generic, or subprogram renaming declaration).  Such
           files are also called specs.

       file.adb
           Ada source code file containing a library unit body (a subprogram
           or package body).  Such files are also called bodies.

       file.s
           Assembler code.

       file.S
       file.sx
           Assembler code which must be preprocessed.
```It is a lot, but informative.

---

### Post by chenxinghao on 2012-02-29
Thanks for all the replies.

Are there any differences between the .C and the .cpp? The man g++ page seems to list them in the same group without mentioning any difference. If no, I will use .C for simplicity.

---

### Post by Dubslow on 2012-02-29
I don't think there's a difference, but keep in mind this will confuse others like you were an hour ago who don't know that the file extension is case sensitive. It really is safer to go with .cpp .

---

### Post by chenxinghao on 2012-02-29
Good point and thank you very much.

---

