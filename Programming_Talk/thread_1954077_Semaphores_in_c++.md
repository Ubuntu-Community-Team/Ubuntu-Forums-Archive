---
title: "Semaphores in c++"
date: 2012-04-07
forum: Programming Talk
---

### Post by josephellengar on 2012-04-07
Hello, I am currently working on a programming assignment using multiple threads. I completely understand what I'm doing and how to do it, with one exception. It has to use semaphores, and I can't for the life of me figure out what #include statements I have to use to get semaphores to work. All of the sample code that I find online is for c, rather than c++. So far, I am only using #include<pthread> for the multithreading part. Anyway, do you have any suggestions?
 
Thanks!

---

### Post by muteXe on 2012-04-08
Hiya. 
You could have a look at the boost library:
[http://www.boost.org/doc/libs/1_35_0/doc/html/interprocess/some_basic_explanations.html](http://www.boost.org/doc/libs/1_35_0/doc/html/interprocess/some_basic_explanations.html)

---

### Post by josephellengar on 2012-04-08
> **muteXe said:**
> Hiya. 
You could have a look at the boost library:
[http://www.boost.org/doc/libs/1_35_0/doc/html/interprocess/some_basic_explanations.html](http://www.boost.org/doc/libs/1_35_0/doc/html/interprocess/some_basic_explanations.html)

It's an assignment. I'm required to use POSIX.

---

### Post by gardnan on 2012-04-08
Can you use librt and Posix semaphore.h?

[http://linux.die.net/man/7/sem_overview](http://linux.die.net/man/7/sem_overview)

---

### Post by josephellengar on 2012-04-08
> **gardnan said:**
> Can you use librt and Posix semaphore.h?

[http://linux.die.net/man/7/sem_overview](http://linux.die.net/man/7/sem_overview)

Sorry, thought this was a different thread. Yeah, I had already figured this out. I'm using semaphore.h and I found a site that gave the syntax I need. [http://www.csc.villanova.edu/~mdamian/threads/posixsem.html](http://www.csc.villanova.edu/~mdamian/threads/posixsem.html)

---

