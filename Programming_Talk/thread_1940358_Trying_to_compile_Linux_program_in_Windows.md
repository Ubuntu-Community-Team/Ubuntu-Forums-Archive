---
title: "Trying to compile Linux program in Windows"
date: 2012-03-13
forum: Programming Talk
---

### Post by xytron on 2012-03-13
I'm trying to compile a C program that expects a POSIX environment (it's a Unix/Linux program) in Windows with Visual Studio, using Cygwin. I finally got it to compile without error messages, but now the problem is running the executable.

The problem is the original program needs to open and read a certain file on startup.

The path to this file is defined in a #define statement like this;

#define LIB "C:/usr/local/share/prog/lib"

Of course in a Windows environment this will be different so I'm trying something such as;

#define LIB "C:\\Users\\markos\\Programming\\lib"


I've tried all sort of ways to specify the path to the lib directory but nothing is working it simply can't find it.

Any clues?

Thank you.

---

### Post by Zugzwang on 2012-03-14
Looking at the documentation, it seems as if a path like "/cygdrive/c/Users/markos/Programming/lib" should work. There should also be special Cygwin functions available for doing this path translation.

Note that your thread subject is a bit misleading - you are trying to compile a program that was originally written on and for Windows rather than cross-compiling for Linux on Windows.

---

