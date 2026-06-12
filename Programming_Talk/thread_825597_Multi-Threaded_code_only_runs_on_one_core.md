---
title: "Multi-Threaded code only runs on one core?"
date: 2008-06-11
forum: Programming Talk
---

### Post by jimgaffney001 on 2008-06-11
Hi All

I am developing a threaded version of an existing F77 code to run on my core 2 duo machine with Ubuntu 8.04 LTS.

The code now compiles and runs giving the same result as the serial version, however it will not use both cores. openMP confirms that it is running on two threads but the process never uses more than 50% of my total processor power.

Can ubuntu support multi-threaded codes like this or will it limit processes to a single core? Im no expert in the way this works; id be interested if there was a way of modifying the way ubuntu manages this job!

Cheers!

Jim

---

### Post by Lster on 2008-06-11
What library are you using to manages threads? I have used PThreads before and found it used both of my CPUs.

Also, if you open System Monitor and click on the System tab, how many processors does it report? I have:

> Processor 0: Intel(R) Core(TM)2 Duo CPU
Processor 1: Intel(R) Core(TM)2 Duo CPU

That's with my Core 2 T7300.

---

### Post by kknd on 2008-06-11
Strange.

I have an Core2 duo too, an my test applications with OpenMP runs in both cores.
OpenMP is influenced by specific environment variables, maybe this is the problem (just guessing)?

---

### Post by public_void on 2008-06-11
Correct me I'm wrong, but isn't the scheduling of threads up to the OS, and therefore the OS could decide to run a multi-threaded process on a single core. The OS could also decide to split the execution of the same process between multiple cores.

---

### Post by jdrodrig on 2009-04-15
"OpenMP confirms ..."

what do you mean by that?

I have made once to many stupid mistakes trying to get parellelized fortran codes running. Make sure you have PARALLE=x and OMP_NUM_THEADS=x variables in your environment set to number of cores or threads.

Ubuntu as most Linux OS can support parallel codes out of the box.

---

### Post by slavik on 2009-04-15
parallel threads, OS, scheduling, pthreads ... etc.

Here's the lowdown: pthreads is short for POSIX threads, meaning that it is a spec (most likely). There are three implementations of pthreads. There is a way to find out what version you have, but I don't know the command off the top of my head but in GNU/Linux it is LPNM or something like that (I remember it being 4 letters).

In Linux, there is no real concept of a thread or a process. There is a concept of a "task" ... a task is a thread or a process. Hence in Linux, any threads is in the kernel space, meaning that the kernel knows about it and the scheduler schedules them separately. In Solaris, for example, threads are userspace, so the kernel sees your process and schedules that.

What you are describing sounds like userspace threads, although it should not be so unless there is some configuration you are doing or if the F77 compiler uses something else for pthreads, but the problem is definately not in the kernel. Maybe it is something with how you coded the threads/openmp pragmas which has some kind of dependcy between the threads (we're not the devs of this code, so we cannot know).

---

