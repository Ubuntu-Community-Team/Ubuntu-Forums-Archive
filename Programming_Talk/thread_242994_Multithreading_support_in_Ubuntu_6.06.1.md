---
title: "Multithreading support in Ubuntu 6.06.1"
date: 2006-08-24
forum: Programming Talk
---

### Post by Lalithkx on 2006-08-24
Hi All,

what is the standard multi-threading api supported on vesion 6.06.1. where can I find some documentation and examples?

I shall be greatfull to anybody who can give some direction

thanks in advance

Lalith

---

### Post by jordilin on 2006-08-24
I'm not sure if you are talking about the cpu. If you are, then you must use the smp kernel version.

---

### Post by Lalithkx on 2006-08-24
Sorry for the confusion,

I am talking about writing an application in c/C++ which uses multi threading  to acheive parallel tasks. let me know if I have to provide any more info.

thanks

Lalithkx

---

### Post by thumper on 2006-08-24
Look up posix threads.  Also called pthreads.

You could always start [here](http://en.wikipedia.org/wiki/POSIX).

---

