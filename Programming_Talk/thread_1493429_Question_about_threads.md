---
title: "Question about threads"
date: 2010-05-25
forum: Programming Talk
---

### Post by KdotJ on 2010-05-25
This may seem like a silly question, but I just want to know..

Does using more threads when possible make a program more efficient? or does it have the opposite effect?

Apologies for the n00b question

---

### Post by tookyourtime on 2010-05-25
If theres more than one core then it will.

But with only one core it could have the opposite effect. But that depends on a hundred things.

---

### Post by s3a on 2010-05-25
The reason for this is because having multiple threads allows multiple parts of a program to run simultaneously.

---

### Post by lostinxlation on 2010-05-25
there are different scenarios depending on the design of CPU.
 
CPU may support SMT with one core, where multiple threads share the same resources such as execution unit, cache and such except register files, there might be conflects of resource.. For example, thread A and B are both floating point intensive and B sometimes may have to wait for execution units occupied by A to free up or vice versa. Another example is thread A's cache access got missed, and refilled the cache line with new data.. Later on. thread B accessed a cache line which happens to be the same location as the one A just accessed, and purged that line to refill it with the requested data.. Now when A tries to access the same memory location again, it gets cache missed, because B just purged it. In such a scenario, having multiple threads doesn't get you much performance gain, but it PROBABLY still gets better performance than just running one thread all the time unless the resource confliect is seriously bad(which I believe does not happen very often).
 
If CPU has totally separated resources such as multi core, you are most certainly to get performance gain with multiple threads.

---

### Post by Some Penguin on 2010-05-25
It's quite possible for a multithreaded program to be less performant than a single-threaded program, even on a multi-core system.  It depends rather much on what the bottlenecks are and the overhead of concurrency control and context switching.

---

### Post by KdotJ on 2010-05-26
Thanks guys for the replies. Ive also been looking at the CPU usage with two programs that do the same thing but one uses threads... The one using more threads actually returned a higher usage

---

### Post by tbastian on 2010-05-26
> **KdotJ said:**
> Thanks guys for the replies. Ive also been looking at the CPU usage with two programs that do the same thing but one uses threads... The one using more threads actually returned a higher usage

These things usually depend on how you use threads. You can't blindly spawn new threads every time you get an event (for example). There is a considerable thread spawning overhead, so if you have a task that needs to run once in a while, and for a long time, you might want to spawn a new thread for this, or even spawn it once, and make it wait between calls.

As already mentioned it also depends on if you have multiple cores/CPUs.

---

### Post by Some Penguin on 2010-05-26
> **KdotJ said:**
> Thanks guys for the replies. Ive also been looking at the CPU usage with two programs that do the same thing but one uses threads... The one using more threads actually returned a higher usage

That would be the most common intent.  If you have a workload composed of (irregular) amounts of computation followed by I/O, and the tasks are sufficiently independent of each other, you may be able to increase CPU utilization and decrease total real time requirements by having one thread perform computation while another thread is blocked waiting for I/O.   Likewise, if you have multiple computational workloads with manageable interdependencies, you may be able take advantage of multiprocessors.  Attempting to brute-force search for cryptographic keys is easily parallelizable, for instance.

Something like LZW decompression is inherently serial, IIRC, because you build up the dictionary as you process the stream.  You could decompress multiple streams in serial, but breaking a single stream into chunks and simultaneously decompressing them in multiple threads wouldn't work very well.  You *might* gain a bit by using a secondary thread for I/O buffering, but LZW is lightweight enough that you might well be completely I/O bound.

---

### Post by uOpt on 2010-05-26
> **KdotJ said:**
> This may seem like a silly question, but I just want to know..

Does using more threads when possible make a program more efficient? or does it have the opposite effect?

Apologies for the n00b question

Efficient? I assume you mean faster. Multithreading is never more efficient in total CPU cycles taken because of the reschduling and the locking.

Speed-wise, depends on many things.

First of all some languages such as Python don't do threads across CPUs. So you'll just get the overhead from whatever locking you have for no benefit.

Even if you have CPU-scheduled threads you can sometimes run into e.g. trashing some CPU cache or other when running more threads. This should be rare. More common could be a situation where you built locking that clashes way too often and slows everything down with more threads. This can end up slower than the original.

---

