---
title: "GCC and G++"
date: 2007-10-20
forum: Programming Talk
---

### Post by shoaibnawaz on 2007-10-20
I have installed GCC in my system. When I tried to compile a C++ program using eclipse. See the console output:

> 
[INDENT][FONT="Courier New"]**** Build of configuration Debug for project TestProject ****

make all 
Building file: ../src/TestProject.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/TestProject.d" -MT"src/TestProject.d" -o"src/TestProject.o" "../src/TestProject.cpp"
/bin/sh: g++: not found
make: *** [src/TestProject.o] Error 127[/FONT][/INDENT]

Is G++ is different then GCC?
I have to tell that I tried Hello World C++ program in the above test.

---

### Post by FredB on 2007-10-20
> **shoaibnawaz said:**
> I have installed GCC in my system. When I tried to compile a C++ program using eclipse. See the console output:



Is G++ is different then GCC?
I have to tell that I tried Hello World C++ program in the above test.


sudo apt-get install build-essential and you'll get g++ too.

gcc is a bundle of compiler : C, C++, ada, fortran, and a lot more. Not only C ;)

---

### Post by Tuna-Fish on 2007-10-20
This is just a part of the TLA insanity the gnu project is so fondly known for.

GCC = Gnu Compiler Collection (gcc, g++...)

gcc = gnu c compiler.

---

