---
title: "Compile C programs for windows on Linux"
date: 2006-12-14
forum: Programming Talk
---

### Post by hatchek on 2006-12-14
Hi everyone, I've been writing some OpenGL programs in C under Ubuntu, and it works great, apart from the slow graphics performance. I wanted to try some of my programs on a windows platform to show to some friends and see what they're really capable of. Well anyway, I was able to dump my code into MS Visual Studio C++ compiler and EVENTUALLY get it to compile and run. ](*,)  Except that compiler is not ISO C and is way too picky. 

So instead of sifting through my code to make it work for the Windows compiler, is there a way I can compile exes on Linux for Windows? I did some research before and found some people using Cygwin to do it, but I'm not sure if Cygwin dumps exes. Thanks!

---

### Post by jpeddicord on 2006-12-14
Cygwin is a Windows program that dumps .exe's, but that is the problem: it (the compiler) only runs on Windows. Cygwin is essentially a Linux emulator for Windows when used correctly.

To compile Windows programs from Linux (aka cross-compiling) just install the **mingw32** package. Now, instead of using **gcc** (or **g++**) to compile, you use **i586-mingw32msvc-gcc** (or **i586-mingw32msvc-g++** if you use C++ code).

So, to compile main.c into program.exe, run this:
```
i586-mingw32msvc-gcc -o program.exe main.c
```

Hope I wasn't too confusing with that description. :) 

Jacob

---

### Post by kaamos on 2006-12-14
Can be done. I just compiled a c++ game project for school (multiplayer tetris with network play ;)) for windows in ubuntu using mingw. The package that you need is "mingw32".

[This]("http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux") page has some info to get you started.

---

### Post by hatchek on 2006-12-15
Well this seems to be exactly what I was looking for, except I don't know how to link to the required GL libraries. 

I tried i586-mingw32msvc-gcc tetris.c -o tetris.exe -lglu32 
and I get a shiat loat of errors. (mostly undeclareds or previous definitions..) The first one points to my #include <GL/glut.h> statement. :confused: I tried changing that to just #include <glut.h> and the same thing happens. 

I don't know much about how compiling actually works, other than it works for a linux binary, nor the CVS stuff talked about on that Wiki page. I didn't use SDL or widgets or anything special when programming the thing, just glut, and I have no idea what the heck ./configure is.

So yeah, I just need one makefile or a statement that will do the trick. Nothing special.

---

### Post by Game_Ender on 2006-12-17
You can't link the Linux GL library to the executable.  You need to have the windows GL libraries to link against.  You will have to some googling on how this works.

---

