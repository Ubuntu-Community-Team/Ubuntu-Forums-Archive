---
title: "boost::thread set stack size"
date: 2007-01-27
forum: Programming Talk
---

### Post by angustia on 2007-01-27
hi

this a question rised after reading this [post]("http://www.ubuntuforums.org/showthread.php?t=336948&highlight=pthread_create")

and after playing a bit with boost::thread and boost::threadpool

there's some way to define the thread stack size of a boost::thread?

thanks in advance.

---

### Post by LordHunter317 on 2007-01-27
Not that I'm aware of.  Boost::threads is kind of a poor interface, do you really need cross-platform threading?

---

### Post by angustia on 2007-01-27
well, yes, with a thread pool implementation

---

