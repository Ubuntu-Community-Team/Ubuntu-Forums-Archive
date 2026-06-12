---
title: "control number of cpu's used in a multithreadprogram"
date: 2007-05-07
forum: Programming Talk
---

### Post by monkeyking on 2007-05-07
I'm doing a multithread program, on a system with 4 dual core cpu's.

And I want to check how well it scales.

Is there a way to control the number of cpu's used by a program?

thanks in advance

---

### Post by Quikee on 2007-05-07
> **monkeyking said:**
> I'm doing a multithread program, on a system with 4 dual core cpu's.

And I want to check how well it scales.

Is there a way to control the number of cpu's used by a program?

thanks in advance

Look for package "schedutils" in synaptic - one of the tools is "taskset" for setting CPU affinity for a process.

---

### Post by amo-ej1 on 2007-05-08
You might wish to examine man 2 sched_setaffinity:

```

DESCRIPTION
       A process’s CPU affinity mask determines the set of CPUs on which it is
       eligible  to run.  On a multiprocessor system, setting the CPU affinity
       mask can be used to obtain performance benefits.  For example, by dedi&#8208;
       cating one CPU to a particular process (i.e., setting the affinity mask
       of that process to specify a single CPU, and setting the affinity  mask
       of  all  other processes to exclude that CPU), it is possible to ensure
       maximum execution speed for that process.  Restricting a process to run
       on  a single CPU also prevents the performance cost caused by the cache
       invalidation that occurs when a process ceases to execute  on  one  CPU
       and then recommences execution on a different CPU.

```

---

### Post by monkeyking on 2007-05-08
Thanks I went for the schedutils,
it was excatly want I wanted.

I get the following with the other

```

man 2 sched_setaffinity
No manual entry for sched_setaffinity in section 2

```

---

