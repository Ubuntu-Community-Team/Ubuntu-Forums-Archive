---
title: "installing C header file with makefile.gcc"
date: 2009-11-17
forum: Programming Talk
---

### Post by Ajat on 2009-11-17
Hi, i'm newbie in programming using linux.. i dont even know how to use the C/C++ header files i got from [http://sourceforge.net/projects/cpp-bigint/](http://sourceforge.net/projects/cpp-bigint/) 

there is a makefile and a cpp files.. it's look like a windows base.. if yes it is, can someone point me to the linux big integer C header file? 

thanks.

---

### Post by Zugzwang on 2009-11-17
First of all, it looks like a C++ library, not a C library. Keep that in mind.

Second, the library doesn't come with anything like an installation procedure or something like that. Just copy the bigint.cpp and bigint.h files into the directory of the project you are trying to use it with, #include the .h file in the source files in which you want to use the classes and make sure that the .cpp file is also compiled and linked against in your project. How to do the latter step depends on the building system of your choice.

The "Makefile.gcc" seems to be for Windows only. 

Note that the library is GPL!

---

### Post by Ajat on 2009-11-17
thanks for the reply..  i'm using eclipse-cdt for my project..
it detects the *.h files, but seems not to working..

can i use this library in a simple C hello-world-like program?

---

