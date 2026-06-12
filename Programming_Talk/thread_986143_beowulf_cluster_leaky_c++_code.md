---
title: "beowulf cluster/ leaky c++ code"
date: 2008-11-18
forum: Programming Talk
---

### Post by abraxas334 on 2008-11-18
If you ran a c++ code, which leaks, i.e. none of the new assignments are freed, could that result in crashing a node on a cluster if it doesn't ever get restarted?

Thanks

---

### Post by Tony Flury on 2008-11-18
I think you will find that the process would get killed first automatically, by the kernel.

The Linux kernel has built in watchdogs which look for excessingly resource hungry process, and should kill leakers before they manage to kill the machine. However the machine will run very very slowly before the watchdogs kicks in.

---

