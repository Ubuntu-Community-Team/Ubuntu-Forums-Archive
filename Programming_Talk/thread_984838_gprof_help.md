---
title: "gprof help"
date: 2008-11-17
forum: Programming Talk
---

### Post by nitro_n2o on 2008-11-17
Hi all

I'm trying to use gprof to profile a piece of code, but it never produces the gmon.out file. 

The problem is that I can run code like this ./helloworld I have to run it from another directory like ./bin/hellworld 

is there a way that gprof could work like this? I can't find any info in the net. 

Any help is really appreciated!

---

### Post by nitro_n2o on 2008-11-17
does gprof have support for multi-threaded code, anyways?

---

### Post by hod139 on 2008-11-17
I can't answer your question, but I can offer an alternative to  gprof, valgrind.  I've never had much luck with gprof, but valgrind has always worked well for me.

---

