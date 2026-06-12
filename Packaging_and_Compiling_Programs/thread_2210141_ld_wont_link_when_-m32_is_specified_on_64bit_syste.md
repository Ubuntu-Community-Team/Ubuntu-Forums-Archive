---
title: "ld wont link when -m32 is specified on 64bit system."
date: 2014-03-09
forum: Packaging and Compiling Programs
---

### Post by sam38 on 2014-03-09
Hey,
I'm trying to compile an application which uses the boost libraries and SDL2.
I'm trying to compile it for a 32bit Linux target, but compiling on my 64bit Ubuntu machine.
I'm using g++ to compile and the boost 1.53 libs from the repository aswell as SDL2 from the repository.
I use the -m32 tag for both compiler and linker options. The compile goes fine, but when i reach the linker stage i get the following output:

```
/usr/bin/ld: cannot find -lboost_system/usr/bin/ld: cannot find -lSDL2main
/usr/bin/ld: cannot find -lSDL2
/usr/bin/ld: cannot find -lboost_thread

```

When compiling with -m64 i get no errors and the program compiles and links just fine. Same when specifying no platform.
I have tried to find 32bit versions of the libraries in the repository but to no avail. And I don't really want to compile from source because when i try to compile boost for 32bit i just get compiler errors and nothing compiles.

So my question is how do I compile a 32bit program that uses these libraries on a 64bit system?

Its a pretty frustrating issue because the only 32bit linux machine I have is a small netbook which takes quite a while to compile my program on.

Thanks for reading!

---

### Post by Bachstelze on 2014-03-09
You need to install the 32-bit versions of those libraries. Try appending *:i386* to the package names in *apt-get install*.

---

