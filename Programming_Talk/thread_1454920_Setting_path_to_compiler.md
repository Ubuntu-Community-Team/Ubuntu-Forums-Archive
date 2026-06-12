---
title: "Setting path to compiler"
date: 2010-04-15
forum: Programming Talk
---

### Post by StefanSeo on 2010-04-15
I just installed SDL on my ubuntu. I wrote simple program and saved it as num1.c.
Now when i want to compile it with * g++ -o -L/usr/include/SDL/ num1.c*  it says that it cant read the SDL.h file.

So how to set the path to /usr/include/SDL/ and compile the program?

---

### Post by MadCow108 on 2010-04-15
include paths are set with -I
-L is for library paths
also your -o flag is missing a output filename

sdl has a config program which makes this easier
sdl-config --libs --cflags
prints all flags and libraries

g++ `sdl-config --libs --cflags` file.cpp

---

