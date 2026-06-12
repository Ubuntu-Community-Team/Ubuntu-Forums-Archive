---
title: "Programming in c and c++ in the CLI"
date: 2010-11-30
forum: Programming Talk
---

### Post by nir2000 on 2010-11-30
Hi everybody!
How can I compile programs written in c in the CLI?
Second question. How can I compile programs written in c++ in the CLI?
Answers will be greatly appreciated.
Thank you in advance.
Nir

---

### Post by fct on 2010-11-30
Install the build-essentials package.

Then you can compile C programs with the gcc command and C++ with the g++ command.

Tutorial:
[http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html)

---

### Post by PaulM1985 on 2010-11-30
I don't think you need to compile your C code in CLI.  You should just be able to interop onto it from you .NET code by defining the method you want to call and making sure that the method is exported from your C library.
To use your C++ code, I would consider writing an object oriented wrapper for it, but I don't know how to compile it.

Maybe this link will help.

[http://www.mono-project.com/Interop_with_Native_Libraries](http://www.mono-project.com/Interop_with_Native_Libraries)

Paul

---

### Post by fct on 2010-11-30
Ouch, I thought he meant the Command Line Interface, not the Common Language Infrastructure.
*facepalms*

---

### Post by PaulM1985 on 2010-11-30
It looks like compiling for C++ may not be supported yet.

[http://www.mono-project.com/CPlusPlus](http://www.mono-project.com/CPlusPlus)

Maybe you could make some sort of system where you have a static map of objects in C++ with an integer key and an object.  In the interop you pass in the key to specify which object you want to perform the action on.

Paul

---

### Post by PaulM1985 on 2010-11-30
> **fct said:**
> Ouch, I thought he meant the Command Line Interface, not the Common Language Infrastructure.
*facepalms*

Oh, maybe I mis-interpreted it...
:oops:

(I have been doing quite a bit of work using CLI recently)

I guess we will find out when the original poster responds.

Paul

---

### Post by muteXe on 2010-11-30
I was thinking command line interface as well.  Not sure at all now.
Incidentally, you can use gcc to compile c++ programs, you just need to add -lstdc++ at the end of the compile line to pull in the c++ runtime libs.

---

