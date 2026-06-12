---
title: "/proc/pid/status file"
date: 2008-11-27
forum: Programming Talk
---

### Post by DBQ on 2008-11-27
In file /proc/pid/status could somebody please explain the differences between these?  Or is there any place I can find a more detailed discussion of what these entries mean (something more detailed then provided in the man files)?  For example, what is the difference between VmPeak and VmHWM?


* VmPeak: Peak virtual memory size.
* VmSize: Virtual memory size
* VmHWM: Peak resident set size ("high water mark").

Thank you

---

### Post by slavik on 2008-11-27
looking at just the names ...
peak virtual = max memory your program seems to take up (counting loaded shared libraries as part of the program)
virtual memory size = same as above but current
peak resident = how much ram was actually devoted to your program

---

### Post by DBQ on 2008-11-27
So the difference between the VmmPeak and VmHWM is that the the first one is the peak of virtual memory and the other one of physical memory.

---

### Post by slavik on 2008-11-27
AFAIK, yes

---

