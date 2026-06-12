---
title: "share memory"
date: 2011-03-13
forum: Programming Talk
---

### Post by petersmith01115 on 2011-03-13
Hi, I need some clarification on:

a.    How we can setup two processes so they share memory.
b.    How we can setup two threads so they share memory.

Thank you.

---

### Post by PaulM1985 on 2011-03-13
I am not sure how you can share memory on different processes.  Perhaps storing information in file, or into a database and then the other process can read that information.  The memory shared would not be in RAM, but some persistent storage.

You can share RAM memory with different threads.  This is going to be specific to the language that you are working with, but take Java as an example, you can have two threads acting on the same object, so they are acting on the same thing in memory.

You question is pretty vague.  What exactly are you trying to do?

Paul

---

### Post by Arndt on 2011-03-13
> **petersmith01115 said:**
> Hi, I need some clarification on:

a.    How we can setup two processes so they share memory.
b.    How we can setup two threads so they share memory.

Thank you.

What have you read so far?

---

### Post by MadCow108 on 2011-03-13
a) [http://beej.us/guide/bgipc/output/html/multipage/shm.html](http://beej.us/guide/bgipc/output/html/multipage/shm.html)
b) threads always share memory as they are in the same process

---

### Post by rnerwein on 2011-03-14
> **MadCow108 said:**
> a) [http://beej.us/guide/bgipc/output/html/multipage/shm.html](http://beej.us/guide/bgipc/output/html/multipage/shm.html)
b) threads always share memory as they are in the same process
high
that the shm.html is right. but be care for touching the "ftok" file because it's made of access time and ....
ciao

---

