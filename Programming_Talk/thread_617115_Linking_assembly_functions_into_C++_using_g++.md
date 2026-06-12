---
title: "Linking assembly functions into C++ using g++"
date: 2007-11-19
forum: Programming Talk
---

### Post by NevilleS on 2007-11-19
Hey guys.  I'm working on a medium-sized C++ program that requires a bit of an assembly back-end to tinker with the stack. I've got a bunch of .cpp files that reference an assembly function defined in a .s file elsewhere. I can use gcc to compile the .s into a .o without any problems, but am not sure exactly how I can link the assembly function it defines so my other files can use it... I've tried the obvious:
```
g++ -lassemblyCode.o cppCode.cpp
```
but the compiler complains about missing functions. For regular C++ functions, I'd avoid this by using header files, but unfortunately in this case I can't. If it matters, this is to be compiled on a SPARC system so the inline __asm__ directives are kind of out the door, to be replaced with code like this:
```
.seg "text"
.proc 4
.global _assembly_function:
_assembly_function:
//do work
retl
nop

```

How can I get this assembly code from a .s file as a working function in C++?

Thanks for any help.

---

### Post by Lux Perpetua on 2007-11-19
You need to declare your assembly language functions in your C++ code as ```
extern "C"
```Then you can link the object file normally with your C++ file. By the way, you don't need "-lassemblyCode.o". ```
g++ assemblyCode.o cppCode.o
```

---

### Post by NevilleS on 2007-11-19
Awesome, this worked nicely. Thanks for the help!

---

