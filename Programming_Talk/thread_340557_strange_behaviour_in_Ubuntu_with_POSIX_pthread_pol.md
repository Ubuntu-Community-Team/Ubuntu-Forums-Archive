---
title: "strange behaviour in Ubuntu with POSIX pthread policy"
date: 2007-01-17
forum: Programming Talk
---

### Post by gcote on 2007-01-17
I'm new at programming on Linux and I am trying to learn more about POSIX pthread.

My machine contains 2 dual-core Opterons = 4 processors. System Monitor reports 4 CPUs and so does /proc/cpuinfo.

I wrote a small test app that creates 5 threads that do something intensive numerical computations. One of my objectives is to understand how to configure the threads (set the priority, set the affinity, etc).

If I try to change the policy of the threads either at creation time
iReturn = pthread_attr_setinheritsched(&attr, PTHREAD_EXPLICIT_SCHED);
iReturn = pthread_attr_setschedpolicy(&attr, SCHED_RR);
param.sched_priority = 1; // for the time being
iReturn = pthread_attr_setschedparam(&attr, &param);
and finally
pthread_create (&(thread[i]), &attr, &compute_prime, pData[i]);
or
threadPolicy = SCHED_RR;
param.sched_priority = 1;
iReturn = pthread_setschedparam(pthread_self(), threadPolicy, &param);
iReturn = pthread_getschedparam(pthread_self(), &threadPolicy, &param);
fprintf(stdout, "Within thread #%ld policy=%s priority=%d\n", pData->lIndex,
(threadPolicy == SCHED_FIFO ? "FIFO" : (threadPolicy == SCHED_RR ? "RR" :
(threadPolicy == SCHED_OTHER ? "OTHER" : "?"))),
param.sched_priority);

What happens is that I have a 4 threads taking 100% of the CPUs, not being pre-empted until they complete their work. My mouse stops moving, Amarok stops streaming.

They all call a function to report the progress of their work. I added a global mutex in there to make sure that collisions between threads happen.

I also added a semaphore to make sure that they start at the same time when I signal the semaphore.

If I leave the policy to SCHED_OTHER, it works fine but I can't set the priority for each thread.

I have Ubuntu 6.10 and uname -r returns 2.6.17-10-generic.

My first reaction was that I forgot something or that I misconfigured the thread attribute.

Then I tried my program on 2 Fedora 6 machines and it seemed to work properly. uname -r returned 2.6.18-1.2849.fc6 on 1 machine and it returned 2.6.18-1.27something on the other one. I also tried on 2 other Ubuntu computers and I also got the freeze. I am going to try on a SUSE machine. *(Update: the system call to set the policy on Fedora and OpenSUSE fails unless I'm a superuser. In that case (superuser), I get the same behaviour).*

I am going to run menu config to compare the 2 kernels to see if there are obvious differences that could explain the strange behaviour on Ubuntu.

Any clues?

Thanks!

---

