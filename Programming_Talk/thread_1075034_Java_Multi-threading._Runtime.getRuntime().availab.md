---
title: "Java Multi-threading. Runtime.getRuntime().availableProcessors() = 1?"
date: 2009-02-19
forum: Programming Talk
---

### Post by inktri on 2009-02-19
I've got an i7 with hyperthreading.

Why does Runtime.getRuntime().availableProcessors() return 1 under Ubuntu, but the correct number 8 under Windows?

In addition when I try to run some multi threaded code like matrix multiplication under Ubuntu, the calculation gets slower as more threads are added (1 thread is fastest). Strangely the linux System monitor is indicating that the correct number of processors are under load (eg. if i've got 4 threads, 4 cores are at 100%), but yea it still runs slower. 

Under Windows with the same code, I'm getting the proper speed up as more threads are added (8 threads is about ~6 times faster than 1 thread).

[http://forums.sun.com/thread.jspa?threadID=5367895&tstart=0](http://forums.sun.com/thread.jspa?threadID=5367895&tstart=0)

Is there some setting under Linux or Eclipse I'm missing? 

Thanks

---

### Post by kavon89 on 2009-02-19
> 
**public int availableProcessors()**

Returns the number of *processors available to the Java virtual machine*.

*This value may change during a particular invocation of the virtual machine*. Applications that are sensitive to the number of available processors should therefore occasionally poll this property and adjust their resource usage appropriately.


From the API, should explain it and lead you to some google searches to fix that number.

---

### Post by ajackson on 2009-02-20
> **inktri said:**
> Why does Runtime.getRuntime().availableProcessors() return 1 under Ubuntu, but the correct number 8 under Windows?

In addition when I try to run some multi threaded code like matrix multiplication under Ubuntu, the calculation gets slower as more threads are added (1 thread is fastest). Strangely the linux System monitor is indicating that the correct number of processors are under load (eg. if i've got 4 threads, 4 cores are at 100%), but yea it still runs slower. 

Under Windows with the same code, I'm getting the proper speed up as more threads are added (8 threads is about ~6 times faster than 1 thread).
Which version of Java are you using on Linux? If it is OpenJDK try the Sun one as it could be a bug in the implementation for Linux.

As you say the code does work, so it's not down to the program being in Java but down to something being odd on the Linux implementation.

---

