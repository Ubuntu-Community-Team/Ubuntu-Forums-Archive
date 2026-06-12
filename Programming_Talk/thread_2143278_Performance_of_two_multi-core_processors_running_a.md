---
title: "Performance of two multi-core processors running a serial process."
date: 2013-05-08
forum: Programming Talk
---

### Post by eotakos on 2013-05-08
Hello everyone,

The discussion I want to start involves two computers, one with an 
Intel(R) Core(TM) i3 CPU         550  @ 3.20GHz
the other with an
Intel(R) Xeon(R) CPU           E5606  @ 2.13GHz
and one program of mine, serial, meaning it has no parallelization features, that is, makes no use of the multi-threading capabilities of the two processors.

First of, I don't understand why running lscpu will not give me always the same number for cpu MHz, and why if I do 
"cat /proc/cpuinfo" I get info for all the threads, some of them reading the right cpu clock speed, others giving a reduced (by much) value.

For example, for the Xeon, I get this output (one part of it)
> 
model name	: Intel(R) Xeon(R) CPU           E5606  @ 2.13GHz
stepping	: 2
cpu MHz		: 1200.000
cache size	: 8192 KB
physical id	: 1
siblings	: 4

And for the i3 I get
> model name	: Intel(R) Core(TM) i3 CPU         550  @ 3.20GHz
stepping	: 5
cpu MHz		: 1197.000
cache size	: 4096 KB
physical id	: 0


The main question is:
Which one is the processor that theoretically will execute my program faster? The i3 because of the better clock speed? Or the cache size and stepping of the Xeon should make it the best choice???

The second question is:
Running multiple versions of my program at the same time will reduce the speed of execution for every individual version of the program? Let's assume that the number of the programs that I'm running in parallel is smaller than the number of threads residing with the processor. Is the cache memory shared in between threads? or it's dedicated so the execution in one thread is not affected at all from what the others do?


Thank you for any input.

---

### Post by Zugzwang on 2013-05-08
> **eotakos said:**
> First of, I don't understand why running lscpu will not give me always the same number for cpu MHz, and why if I do 
"cat /proc/cpuinfo" I get info for all the threads, some of them reading the right cpu clock speed, others giving a reduced (by much) value.

To save energy, modern processors have the capabilities to reduce the speed of their processor cores when not in use. As you probably don't utilize your CPU by 100% when doing the measurement, they will often not be running at full speed at that point in time. Note that "/proc/cpuinfo" will show the cycle rates for processor cores, not for threads. You might want to look up these terms.

> **eotakos said:**
> 
Which one is the processor that theoretically will execute my program faster? The i3 because of the better clock speed? Or the cache size and stepping of the Xeon should make it the best choice???


There is no general answer - it depends on the program. The processors are close enough in terms of year of build that one is likely to be able to write one program that runs faster on processor A than on processor B, and one program that runs faster on processor B than on A.

> **eotakos said:**
> 
Running multiple versions of my program at the same time will reduce the speed of execution for every individual version of the program? Let's assume that the number of the programs that I'm running in parallel is smaller than the number of threads residing with the processor. Is the cache memory shared in between threads? or it's dedicated so the execution in one thread is not affected at all from what the others do?


Most processors have a shared 2nd-level cache, but a separate 1st-level cache for each core. Programs with lots of random I/O will interfere, programs with very little I/O access less so. You can't fully avoid the fact that running two programs in parallel will be slower than running only one in parallel, as I/O bus capacity is limited and the operating system has more to do when multiple programs run in parallel.

---

### Post by oldfred on 2013-05-08
I found this comparison interesting.

 Is This Even Fair? Budget Ivy Bridge Takes On Core 2 Duo And Quad

[http://www.tomshardware.com/reviews/ivy-bridge-wolfdale-yorkfield-comparison,3487.html](http://www.tomshardware.com/reviews/ivy-bridge-wolfdale-yorkfield-comparison,3487.html)

---

### Post by eotakos on 2013-05-09
@ Zugzwang :
Thank you for your thorough response... What happened was that doing some runs I found that the cheaper, more down to earth i3 was running faster my code. So I thought 'it can't be it, I must be doing something wrong".  I guess I need to do some dedicated test-runs to find out for sure. At least now I know it's not necessary that I'm doing something wrong, even if the i3 turns out to be the best choice of the two.

Thanks again

---

