---
title: "Does C support parallel programming?"
date: 2010-12-28
forum: Programming Talk
---

### Post by TheHimself on 2010-12-28
I've written a program which reads data from a file and analyse it and does this for several thousand times. It would run much faster if it could read the next dataset from the hard disk while analyzing the current dataset. Is there any way of doing this in C or C++?

---

### Post by Barrucadu on 2010-12-28
Yes, look up threading.

---

### Post by MadCow108 on 2010-12-28
not directly, but there are libraries which provide means of doing it.

e.g. you can use the linux implementation of posix threads, enabled by -pthread in gcc
[https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/)

---

### Post by TheHimself on 2010-12-28
Thank you, I found some info.

---

