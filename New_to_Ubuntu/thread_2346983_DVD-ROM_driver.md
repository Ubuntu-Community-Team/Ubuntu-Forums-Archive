---
title: "DVD-ROM driver?"
date: 2016-12-20
forum: New to Ubuntu
---

### Post by abartomak on 2016-12-20
Hello! I installed Lubuntu few days ago, but now when I play DVD's, the DVD-ROM makes a lot of humming/vibratings sound - it was not like that while I was still using Windows XP. So I was wondering if I could fix this with the new DVD-ROM driver? I didn't find anything with the google search, so if anyone of you have something in mind, please let me know.

Thanks!

---

### Post by kingneutron on 2016-12-20
--Sounds like a hardware issue, make sure you are putting the discs in correctly (centered) and try a few different ones.  A particular DVD may be older and starting to go bad.  I am not aware of any new "DVD-ROM drivers" for Linux unless you want to try upgrading your kernel.

--A new SATA DVD burner drive should run you about $25 or under on Amazon...

---

### Post by DuckHook on 2016-12-20
Please provide relevant HW specs and Lubuntu version. Do:```
sudo lshw -sanitize -C disk
``````
lsb_release -a
```Do you know the native speed of your drive?

In Lubuntu, for practically all DVD drives, the driver is already built into the kernel. I suspect that Lubuntu is trying to run your drive at or beyond its maximum rated speed and this is giving the vibration. XP was notorious for under-spinning CD/DVD drives mainly because they were not very reliable back then, but it used to drive me nuts. In any case, it is pointless trying to compare a 20-year-old OS to a modern one.

There are ways to control drive speed but above info first please.

---

