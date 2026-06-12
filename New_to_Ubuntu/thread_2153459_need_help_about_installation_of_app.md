---
title: "need help about installation of app"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by protoss96 on 2013-06-11
when i type 'make' it prints out
```
make: *** No targets specified and no makefile found.  Stop.
```

But there is about 3 makefile files (Makefile.in, Makefile.check and makefile.ms)... I am stuck here, i really need this emulator.
I also tried 'make -f Makefile' but same problem.

Thanks in advance. :D

---

### Post by slickymaster on 2013-06-11
**make** takes a make file as input. Make file usually is named makefile or Makefile. The configue command should generate a make file, so that make could be in turn executed.
The make command looks for a file called "Makefile", no extension, not "Makefile.in". Since the file is not found, make does not know what to do, and stops. (The error message is cryptic because in some rare cases, make can guess what to do without an actual Makefile.)
Read the instructions on how to compile your program. It's likely that you are required to run ./configure, first. This script will create "Makefile" based on your setup and "Makefile.in".

---

