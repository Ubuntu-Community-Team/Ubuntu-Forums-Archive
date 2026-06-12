---
title: "job scheduling with java threads"
date: 2011-11-10
forum: Programming Talk
---

### Post by jmwalloh on 2011-11-10
Hi everyone, i have this scheduling problem to deal with. I have three threads each doing a certain task.**T1,T2 and T3**. T1 does its task **after every 5 sec looping 10 times**. T2 and T3 are **high priority task thread which run only once**. T2 runs after 2 sec and T3 after 11 sec. After 2 sec, **T1 is supposed to pause** for T2 to run and resume when it has finished and the pause when T3 is ready to run and resume later. How do i do this in java ??. Any help is highly appreciated.

---

### Post by ofnuts on 2011-11-10
> **jmwalloh said:**
> Hi everyone, i have this scheduling problem to deal with. I have three threads each doing a certain task.**T1,T2 and T3**. T1 does its task **after every 5 sec looping 10 times**. T2 and T3 are **high priority task thread which run only once**. T2 runs after 2 sec and T3 after 11 sec. After 2 sec, **T1 is supposed to pause** for T2 to run and resume when it has finished and the pause when T3 is ready to run and resume later. How do i do this in java ??. Any help is highly appreciated.Use semaphores? [http://download.oracle.com/javase/1,5,0/docs/api/java/util/concurrent/Semaphore.html](http://download.oracle.com/javase/1,5,0/docs/api/java/util/concurrent/Semaphore.html)

---

### Post by 11jmb on 2011-11-10
I don't think you can stop T1 "in its tracks" they way you want unless you lock and release after every statement.

Will T2 and T3 ever have to run concurrently?

---

### Post by ofnuts on 2011-11-10
> **11jmb said:**
> I don't think you can stop T1 "in its tracks" they way you want unless you lock and release after every statement.

Will T2 and T3 ever have to run concurrently?One can wonder why T1 should stop doing whatever it does to let T2 & T3 run...  is it to solve a concurrent access problem?

---

