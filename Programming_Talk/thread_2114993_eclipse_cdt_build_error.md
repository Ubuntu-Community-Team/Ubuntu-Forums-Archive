---
title: "eclipse cdt build error"
date: 2013-02-11
forum: Programming Talk
---

### Post by linux spartan on 2013-02-11
help...i am a newbie and trying to build and compile c projects in  eclipse indigo using the cdt plugin.i first make a new c project aloisi  then make a new source file lol.c and on the console i get the following  output 
**** Build of configuration Debug for project aloisi ****

make all 
Building target: aloisi
Invoking: GCC C Linker
gcc  -o "aloisi"  ./lol.o   
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [aloisi] Error 1

**** Build Finished ****

the errors specified are:
Description                                   Resource      Type
make: *** [aloisi] Error 1            aloisi             C/C++ Problem
undefined reference to `main'    aloisi             C/C++ Problem

in the project explorer no binaries are getting displayed from which i can run
and only displayes includes lol.c and debug which contains lol.o,lol.d,makefile,objects.mk,sources.mk,subdir.mk

---

### Post by spjackson on 2013-02-11
The error message means that you are trying to build an executable from a single source file and that source does not contain a [main function]("http://en.wikipedia.org/wiki/Main_function_(programming)"). One of your sources needs a main(), and if lol.c is your only source, it needs to be in there.

---

### Post by linux spartan on 2013-02-12
apparently i did that...i geuss it has to do with path names or something because this happened only after i decided to change my workspace from the default workspace set.any ideas how to go about this when switching to a new workspace?

---

### Post by spjackson on 2013-02-12
> **linux spartan said:**
> apparently i did that...i geuss it has to do with path names or something because this happened only after i decided to change my workspace from the default workspace set.any ideas how to go about this when switching to a new workspace?
So lol.c contains a main function, but
> 
```

gcc -o "aloisi" ./lol.o 
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/crt1.o: In function 
`_start':
(.text+0x18): undefined reference to `main'

```

says that it isn't in lol.o .

I can't imagine what sort of voodoo causes that. Sorry I can't help.

---

### Post by leonmaxx on 2013-02-12
Can we see your lol.c?

P.S. try to Clean and then Build again.

---

### Post by Warren Hill on 2013-02-12
try 


```
gcc -o "aloisi" ./lol.c
```
To build  lol.o again.  If that does not work can we see lol.c?
 It may be something obvious.

---

