---
title: "Defragmentation"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by chitragurung on 2012-05-19
My dell inspiron machine with ubuntu 10.04 OS is getting slower to load. Still have over 100 gb free space. How can I check error ? How to fix this issue.

---

### Post by Pilot6 on 2012-05-19
Run this command and post the result here.

sudo fsck -fnv | grep non-contiguous

---

### Post by Silent Warrior on 2012-05-19
[SNIP] (Why does everyone have to be faster than I am?)

Hm, now I actually had a clever thought: Is Ubuntu installed on an SSD? I understand they could slow down over time, but I admit I have no experience at all with that technology, first-hand.
Also: Why are you still using 10.04? I'm just curious, myself, but the reason might be important for your solution.

---

### Post by bodhi.zazen on 2012-05-19
> **chitragurung said:**
> My dell inspiron machine with ubuntu 10.04 OS is getting slower to load. Still have over 100 gb free space. How can I check error ? How to fix this issue.

Fragmentation is extremely unlikely to be causing the problem. There is always a small amount of fragmentation, but typically not enough to cause performance issues.

Typically fragmentation only becomes an issue with the disk is almost full.

Can you give a better description of the problem. What is slow ? booting ? log in ? what.

---

### Post by jtarin on 2012-05-19
Over time you add software and some of this software can cause services to run at boot time which can slow the boot process 
and then if they run in the background that's another hit. 
Consider what your running.....and your hardware.

---

### Post by chitragurung on 2012-05-24
here is the result

chitra@chitralaptop:~$ sudo fsck -fnv | grep non-contiguous
[sudo] password for chitra: 
e2fsck 1.41.11 (14-Mar-2010)
chitra@chitralaptop:~$ 


> **Pilot6 said:**
> Run this command and post the result here.

sudo fsck -fnv | grep non-contiguous

---

