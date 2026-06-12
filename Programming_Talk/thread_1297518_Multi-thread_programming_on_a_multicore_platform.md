---
title: "Multi-thread programming on a multicore platform"
date: 2009-10-21
forum: Programming Talk
---

### Post by mustang on 2009-10-21
Hi all,

I have a question regarding using pthreads on a multicore platform: If I launch n threads, can I be guaranteed that the kernel will schedule them to n different cores? If it helps, the system that I will be using has NPTL 2.5 installed.

I am working on a stream processing application and I want some of the cores of my platform to be the workers (and stay the workers). I do not want to kill and re-launch these worker threads because their work will continue to be the same throughout the duration of the program (the data that they operate over however, will change). 

I understand that with NPTL, you can configure CPU affinities---does this mean it is possible to statically assign a thread to a particular core?

Thank you all for your help. The resources on multithread programming over multiple cores appear to be very scant. It feels like I'm going into the wild west with some of these questions.

Manish

---

### Post by shadylookin on 2009-10-22
I believe the scheduler just runs each thread wherever it thinks is best for overall performance. From the programmers stand point it shouldn't really matter which core is running which thread.

---

### Post by mustang on 2009-10-23
Hi shadylookin:

thank you for the reply. I realize that what you said is true for the general case but it is not for mine. The application that I'm working on depends, atleast for performance reasons (not functional correctness), that the threads stay active on the core. I realize that those threads can be get preempted by the kernel for daily OS activity but I'd like atleast some measure on control on atleast some threads staying in place.

---

### Post by dwhitney67 on 2009-10-23
Bear in mind that although some of us have multi-threading experience, we do not share the abundant sunshine you have in SoCal, much less have the privilege to have a multi-core system.

What was stated by shadylookin is spot-on based on the limited information you have provided for your project's requirement(s).

I do not have any experience with [OpenMP]("https://computing.llnl.gov/tutorials/openMP/"), but perhaps this is something you may consider.  I'm old-school, thus I use POSIX threads, and derivatives of such to accomplish my multi-threading tasks.  Of course, I am not serving tens-of-thousands threads at any given moment.

---

### Post by slavik on 2009-10-24
with NTPL, threads are scheduled by the kernel.

In Linux, the scheduler does not distinguish between thread and process. The scheduler only knows of tasks. Tasks can be scheduled on different cores. Two concurrent threads (if not locking on each other's resources) will be scheduled to run on separate cores.

Can I presume that you are using C for this?

---

