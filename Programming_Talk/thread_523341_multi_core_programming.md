---
title: "multi core programming"
date: 2007-08-11
forum: Programming Talk
---

### Post by Elisei on 2007-08-11
Hi:

if i have a dual core processor, is there a way to optimize my code, lets say C, to specifically share tasks between the cores;  is there a special syntax or library or compiler options that can be used?

thanks;

---

### Post by aks44 on 2007-08-11
You need to make your program multi-threaded (eg. using pthreads).

However I would advise you to be extremely careful. Concurrent programming has many non-obvious pitfalls. You gotta read & practice a lot before being able to write anything stable.

Synchronization primitives (mutexes, semaphores, critical sections...) and the related issues must be mastered if you want to share data across threads.

Good luck, you'll need it.

---

### Post by slavik on 2007-08-12
but it's fun playing whackamole this way ... except the moles fork() instead of going away ;) (locked up my system too many times)

---

### Post by ssam on 2007-08-12
have a look at openmp. it is in GCC 4.2

---

