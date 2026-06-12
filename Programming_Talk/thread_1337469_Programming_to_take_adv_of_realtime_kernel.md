---
title: "Programming to take adv of realtime kernel?"
date: 2009-11-25
forum: Programming Talk
---

### Post by kachofool on 2009-11-25
Hi all,

I'm developing an interface for several sets of coupled sensors and motors which are all 'handled' via several RS232 ports.

I'd like to improve the performance of the system by using a realtime kernel. The interface has been built in C++, but the 'real-time' related operation such as I/O and threading is all done using C libraries.

I had a few generic questions, including

* Will using an RT kernel help at all? 

* Is there a good way to measure the difference in performance (valgrind?)

* Has anyone used Xenomai with Ubuntu? If so would anyone be willing to share any insight on it? I'm a little fuzzy as to how it works beyond patching the kernel. Do I need to rewrite my code to take advantage of Xenomai, etc.

Regards,

KF

---

### Post by jabl on 2009-11-27
> **kachofool said:**
> Hi all,

I'm developing an interface for several sets of coupled sensors and motors which are all 'handled' via several RS232 ports.

I'd like to improve the performance of the system by using a realtime kernel. The interface has been built in C++, but the 'real-time' related operation such as I/O and threading is all done using C libraries.

I had a few generic questions, including

* Will using an RT kernel help at all? 
  Depends on what you mean by improving performance. RT is, generally, not about making things go faster, but rather about providing deterministic worst-case latency. In order to do this, RT must sacrifice some of the throughput performance.  >  * Is there a good way to measure the difference in performance (valgrind?)
  valgrind contains a tool for doing cache profiling, but for profiling you generally want a profiler. See e.g. oprofile, or the new &quot;perf&quot; tool in the 2.6.31 kernel. Unfortunately the perf tool was left out of Ubuntu 9.10 even though it has 2.6.31. But you can compile it yourself from the kernel source, or maybe some enterprising person has made a PPA.

---

