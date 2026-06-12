---
title: "SystemC library"
date: 2007-02-02
forum: Programming Talk
---

### Post by aijazbaig1 on 2007-02-02
Hello freinds.
A linux newbie here.
Just installed the gcc compiler from ubuntu using the following script:

```

sudo apt-get install build-essential

```

Now I would extend the library by adding systemC library files, Im lookin to know more abt where and how should I go about adding systemC library files and other such 3rd party libraries.

Pls do let me know if u know something abt it.

Best Reg.
Aijaz.

---

### Post by po0f on 2007-02-02
aijazbaig1,

Looks like the library you are looking for isn't in the repos.  You're going to have to compile it from source.

---

### Post by mentat5kyu on 2007-04-16
[http://www.jonas-diemer.de/english/articles/systemc.html](http://www.jonas-diemer.de/english/articles/systemc.html)

Follow the road of yellow brick.

---

### Post by moogyd on 2007-04-27
On a similar subject, has anyone managed to build the systemC verification library (SCV) on Ubuntu?

Thanks,

Steven

---

### Post by michael_f909 on 2008-03-23
I am also having trouble installing the systemC libraries. I am able to run the configure script, however when I run make or make install, I get the following error:

```
Error: can't open qtmds.s for reading: no such file or directory
```

qtmds.s should be found within system-2.2.0/objdir/src/sysc/qt, however the only files in that directory after running configure are Makefile, qt.o and qtmdc.o

If anyone could give me a hand in fixing this that would be a great help

---

### Post by laertemr on 2010-08-31
> **michael_f909 said:**
> I am also having trouble installing the systemC libraries. I am able to run the configure script, however when I run make or make install, I get the following error:

```
Error: can't open qtmds.s for reading: no such file or directory
```qtmds.s should be found within system-2.2.0/objdir/src/sysc/qt, however the only files in that directory after running configure are Makefile, qt.o and qtmdc.o

If anyone could give me a hand in fixing this that would be a great help

Hi michael, to fix this problem you need move the file qtmds.s from the folder systemc-2.2.0/src/sysc/qt to destination folder ( systemc-2.2.0/objdir/src/sysc/qt )

---

