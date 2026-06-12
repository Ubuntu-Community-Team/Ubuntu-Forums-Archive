---
title: "swap"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by ub9876 on 2013-07-03
if your laptop had an SSD only and was running Xubuntu 13 ......would you still do the swap adjustment where you change it from 60 to 10???
or is this just for regular HD laptops...??

---

### Post by vasa1 on 2013-07-03
How much RAM?

---

### Post by deadflowr on 2013-07-03
Here from the archlinux wiki
[https://wiki.archlinux.org/index.php/Solid_State_Drives#Swap_Space_on_SSDs](https://wiki.archlinux.org/index.php/Solid_State_Drives#Swap_Space_on_SSDs)

---

### Post by ub9876 on 2013-07-03
how do I see how much ram???

---

### Post by papibe on 2013-07-03
Hi ub9876.

To see how much RAM your system has available (and how much is being used):
```
free -m
```
Regards.

---

### Post by ub9876 on 2013-07-04
what does this say????

             total       used       free     shared    buffers     cached
Mem:           993        669        324          0         27        424
-/+ buffers/cache:        216        776
Swap:         1012          0       1012

---

### Post by moltenicee on 2013-07-04
Your computer only has 1GB of RAM (993 MB total ~ 1GB).

I would leave swappiness as it is because it does not matter whether you have an SSD or a conventional HDD; it is purely dependent on the amount of available RAM in your system.

Since you only have 1GB, your computer will most likely require heavy use of swap space regardless of the settings.

---

### Post by Impavidus on 2013-07-04
It means you have 993MiB of RAM, 669MiB of which is in use, but most of that is cache, which can be dropped from RAM whenever it's needed for something else. You have 1GiB of swap, but don't use it right now. In fact, with Xubuntu you won't use swap very often with 1GiB of RAM. I only use more than 1GiB when rendering pdfs at high resolution. Right now, my Xubuntu uses 290 MiB of 3000MiB available, excluding cache.

---

### Post by vasa1 on 2013-07-04
> **moltenicee said:**
> Your computer only has 1GB of RAM (993 MB total ~ 1GB).

I would leave swappiness as it is because it does not matter whether you have an SSD or a conventional HDD; it is purely dependent on the amount of available RAM in your system.

Since you only have 1GB, your computer will most likely require heavy use of swap space regardless of the settings.
OP hasn't described the intended usage.

---

### Post by moltenicee on 2013-07-04
> **vasa1 said:**
> OP hasn't described the intended usage.

OP is asking if he should change swappiness from 60 to 10 because he has an SSD.
10 swappiness, which I am using currently, means that ubuntu will try to wait as long as possible until it swaps which is good for computers >4GB RAM.

However, he only has 1GB, and whether he changes swappiness or not will not drastically affect the frequency of swapping and therefore will not have a profound impact on the life of his SSD.

If anything, setting such a low swappiness on a low memory system would result in more lag because at around only 300MB free, ubuntu would wait as long as possible before swapping and this might cause some larger programs to be less responsive as the system only swaps when the RAM is on the verge of being completely filled instead of leaving some leeway.

---

### Post by ub9876 on 2013-07-04
thanks for info...   I hope this SSD ,Samsung 840 pro,  lasts for awhile so I can install it in a future ultrabook,when prices are cheap..

---

### Post by moltenicee on 2013-07-04
You shouldn't have to worry about the life span of modern SSDs because by the time it dies from intensive usage, the technology within would have already been rendered obsolete in terms of speed, size, and security by newer, cheaper models.

---

### Post by mardybear on 2013-07-05
Hello.

I would definitely change your swappiness down to 10. Try it and see, can always change it back. FYI: I have <1GB ram, keep my systems at swappiness 10 and never have a problem as they rarely access swap (not even a little bit). Guess it depends how you utilize your system.

Have fun tweaking,

mardybear

---

