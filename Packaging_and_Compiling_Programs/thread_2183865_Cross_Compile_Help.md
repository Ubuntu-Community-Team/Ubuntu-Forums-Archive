---
title: "Cross Compile Help"
date: 2013-10-26
forum: Packaging and Compiling Programs
---

### Post by termin on 2013-10-26
I'm new to cross compiling on linux using mingw, and basically all I want to do is get a program to compile for 64 bit windows (on 64 bit linux). The project that I'm trying to compile just has a stand-alone makefile; no configure or autogen, which makes this one slightly difficult. I already had installed mingw, so I just edited the following in the Makefile:
                  CC = x86_64-w64-mingw32-gcc
                  CXX = x86_64-w64-mingw32-g++

and then ran "make". I thought everything would be perfect, until I got this 3/4th's of the way through:
                  error: unrecognized option ‘-pthread'

Can anyone help me with this error?
Thanks.

---

### Post by Bachstelze on 2013-10-26
It means that your program uses the Pthread library, which is a POSIX thing and is not available on Windows. So, unless your program provides a setting to disable multithreading at compile-time, you will not be able to compile, let alone run it on Windows.

---

