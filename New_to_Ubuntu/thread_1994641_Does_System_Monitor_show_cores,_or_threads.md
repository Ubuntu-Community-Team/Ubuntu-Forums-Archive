---
title: "Does System Monitor show cores, or threads?"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by KingNeil on 2012-06-03
If I want to know how many threads are available on my CPU, how do I find it?

System Monitor shows CPU 1 and CPU 2, but I've heard that the number of threads can be 2x the number of CPUs, so, 4.

So, the question is... how, in Ubuntu, do I find the number of threads on my CPU?

---

### Post by jtarin on 2012-06-03
In a terminal ```
lscpu
```

---

### Post by 3rdalbum on 2012-06-03
Cool, I'd never heard of the lscpu command; I'll tuck that away in my memory for next time someone wants to know that information :-)

---

### Post by mcduck on 2012-06-03
> **KingNeil said:**
> If I want to know how many threads are available on my CPU, how do I find it?

System Monitor shows CPU 1 and CPU 2, but I've heard that the number of threads can be 2x the number of CPUs, so, 4.

So, the question is... how, in Ubuntu, do I find the number of threads on my CPU?

It shows cores, both physical and virtual ones. (So if by "threads" you mean features like HyperThreading, that will show as double the amount of physical cores the CPU has.) The actual nubler of threads a CPU can run can of course be much higher than the count of cores it has, regardless of if the CPU supports Hyperthreading or not. That simply means less of the threads Are processed at the samee.

---

### Post by KingNeil on 2012-06-03
lscpu

Cheers. That's exactly what I was looking for.

---

