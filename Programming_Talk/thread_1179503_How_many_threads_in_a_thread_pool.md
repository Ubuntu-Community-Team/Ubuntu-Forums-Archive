---
title: "How many threads in a thread pool?"
date: 2009-06-05
forum: Programming Talk
---

### Post by night_fox on 2009-06-05
If you use a thread pool, lets say the glib one, how many threads should you set as the maximum? Do you choose some arbitrary value? Is there a default? Would it be worth somehow measuring the performance, memory usage and and number of cores and continuously adapting to them? Are there any examples of this?

---

### Post by stroyan on 2009-06-05
The optimum number of threads can be extremely complicated to determine.
It will depend on not only the number of available processors, but also
the structure of memory and the way that the threads interact and use resources.  Threads that are CPU-bound will usually get best performance when there are as many threads as processors.  But that will vary if threads actually block on I/O, or if threads need more memory/cache than the system has available, or if threads need to frequently access shared memory.
You can do the most basic tuning by looking at the number of available CPUs.
You can get that from sysconf(_SC_NPROCESSORS_CONF) on linux, (as well as many other ways).
But to get really interesting information have a look at libnuma and the numactl command.  Many linux kernels include support for awareness and reporting of Non-Uniform Memory Access.  (But the default ubuntu kernels do not support NUMA features.)  Numa APIs recognize that different CPUs can get at different memory locations faster on some big systems, (or even fairly small systems using AMD processors.)

---

### Post by night_fox on 2009-06-06
Ah thanks for replying! It seems as though its impossible to exactly determine the optimum number of threads except by measuring the performance of the program and adapting to it (except in the special case with 1 cpu where theres no point in multithreading, and thanks for telling me how to find that out).

I understand that with too many threads, the kernel spends too much time switching between them. I read somewhere that it took on the order of 1 to 2 microseconds to switch threads, but the performance hit from this is impossible to determine unless you know what makes the kernel decide to switch threads. Surely this effect is only likely to be significant at a very large number of threads

With too few threads, you might lose out because if a thread has locked a mutex, there is a lower chance that another thread is still using the cpu rather than waiting to lock the same mutex. This effect depends on the number of mutexes and the percentage of cpu time spent with each one locked per thread. My threads are going to spend most of their time using the cpu/memory, so this is likely to be insignificant.

So the gut feeling is that on the graph of useful cpu usage vs number of threads, there is a long plateau of nearly 100%, and I might as well fix the max number of threads at, say 5 times the number of processors. I would like to generate and then post back with this graph. How can I measure the amount of time the kernel spends switching my threads?

---

### Post by Reiger on 2009-06-06
> **night_fox said:**
> (except in the special case with 1 cpu where theres no point in multithreading, and thanks for telling me how to find that out).

Actually the benefit of multi threading lies not solely in the ability to use multiple CPU cores for the same process at the same time. So even on a single core it may be beneficial to `do multi threading' especially in situations where one thread is strongly IO bound and another one is strongly CPU bound: in those cases you may find that the system at large (the entirety of all running processes and their threads) performs better because the kernel task switcher is able to make better decisions (it gives different priorities to different types of tasks) or just because of the fact that you can split CPU intensive from IO intensive work that way.

---

### Post by night_fox on 2009-06-06
Okay, so how can I measure the amount of time the kernel spends task-switching?

---

