---
title: "C++ - compiling a program on different platforms with library support"
date: 2010-03-29
forum: Packaging and Compiling Programs
---

### Post by marshmallow1304 on 2010-03-29
For a mathematics course, I've written a program that performs Cauchy's method of minimization.  The program uses the GiNaC library and one separate source (for finding roots of polynomials).  I can compile these fine on Linux by including the source of the root-finder and ginac/ginac.h and using pkg-config to link to the local install of GiNaC.  Eventually, I wish to compile the program on both Mac and Windows (or Mac at the very least).  The question is, how do I compile support from GiNaC into the program on those platforms?


I'm still very much a beginner in linking and compilers.  I know how to code decently after a little more than half a semester of c++, but I'm just now starting to learn how to compile straight from g++ rather than using an IDE, so any help is greatly appreciated.

---

### Post by Bachstelze on 2010-03-30
You should be able to compile your program on OSX the same way you do on Linux. Have you tried that? On Windows, MinGW can probably compile your program in an UNIX-y way too.

---

### Post by marshmallow1304 on 2010-03-31
Thanks for the reply.  I started messing around on a Mac.  The problem is that I don't have super-user access on the Macs I want to use to compile, so I can't install GiNaC and CLN (which GiNaC requires).

Also, I looked into mingw32, but trying to compile with my usual command but substituting i586-mingw32-c++ doesn't work.

This is my normal command, which works fine:
```
g++ -o gmo `pkg-config --cflags --libs ginac` gmo.cc
```

For mingw32, I tried
```
i586-mingw32-g++ -o gmo `pkg-config --cflags --libs ginac` gmo.cc
```
but it didn't work.  I get a bunch of errors starting with
```
gmo.cc:4:25: error: ginac/ginac.h: No such file or directory
```

So, I change to an absolute path in my include statement (/usr/include/ginac/ginac.h).  Then I get errors that the ginac files can't link to CLN ones.


Now I'm going to try installing CLN, GiNaC and Mingw32 on Windows.

---

### Post by SevenMachines on 2010-03-31
for windows, you might want to look at the [ginac windows port for gcc]("http://theor.jinr.ru/%7Evarg/web/proj/ginac/woe32/") guide and see if thats any help

---

### Post by marshmallow1304 on 2010-04-01
> **SevenMachines said:**
> for windows, you might want to look at the [ginac windows port for gcc]("http://theor.jinr.ru/%7Evarg/web/proj/ginac/woe32/") guide and see if thats any help

Gah!  That **almost** worked.  It seems that the provided Windows port of of GiNaC is too old and doesn't support some of the stuff I'm trying to do.


Another question:
If I manage to get these compiled on Windows/Mac, does GiNaC/any generic library have to be installed on a machine for it to run the binary?

---

