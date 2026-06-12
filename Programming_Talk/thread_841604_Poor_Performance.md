---
title: "Poor Performance"
date: 2008-06-26
forum: Programming Talk
---

### Post by Ubangi on 2008-06-26
My plain C programs run just fine. However, any benchmarks involving more intensive use of the stack, in particular the "recursive" benchmark from: [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/) is twice as slow as expected. This happens when using interpreted languages, in comparison against similar machines running it under SUZY Linux, for instance. The benchmark runs typically 60 times slower than compiled C, instead of just 30 times slower under Suzy.

I realise that the 64bit machine is going to be a bit slower perhaps than the 32bit version but this is out of proportion and must be caused by something else? 

Did anyone else notice similar slowdown?

Is this possibly connected with the busybox issue I, amonst many others, suffered from during installation? I had only managed to install with manual boot parameter:

all_generic_ide=1

Could this be subsequently affecting the performance?

---

### Post by finer recliner on 2008-06-26
> **Ubangi said:**
> My plain C programs run just fine. However, any benchmarks involving more intensive use of the stack, in particular the "recursive" benchmark from: [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/) is twice as slow as expected. This happens when using interpreted languages, in comparison against similar machines running it under SUZY Linux, for instance. The benchmark runs typically 60 times slower than compiled C, instead of just 30 times slower under Suzy.

I realise that the 64bit machine is going to be a bit slower perhaps than the 32bit version but this is out of proportion and must be caused by something else? 

Did anyone else notice similar slowdown?

Is this possibly connected with the busybox issue I, amonst many others, suffered from during installation? I had only managed to install with manual boot parameter:

all_generic_ide=1

Could this be subsequently affecting the performance?

you can only change one thing at a time when comparing benchmarks. it sounds like you are trying to compare a benchmark on different hardware, a different OS, and different language! this benchmark test was designed only to be run on the same computer but in a different language.  software tests are of no value to compare with each other when you change other factors. *EVERYTHING* in a computer will change its speed -- the CPU clock, the CPU architecture, cache, bus speed, memory size, memory speed, the list goes on and on.

---

### Post by Ubangi on 2008-06-27
Fair point. I did compare it for the same language against two friends using machines with slower processors and theirs run significantly faster. I agree that there will be other factors, such as the memory (I have 2Gigs which ought to be enough) but it is still rather surprising. The only significant difference I can think of was that they run other versions of Linux.

---

