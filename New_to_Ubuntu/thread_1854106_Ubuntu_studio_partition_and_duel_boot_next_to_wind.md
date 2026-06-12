---
title: "Ubuntu studio partition and duel boot next to windows 7"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-10-03
Hey guys I am currently downloading Ubuntu Studio 11.04 and I have a few questions about it. 

1. Is ubuntu Studio a complete OS on its own or is it an addition to Ubuntu 11.04?

2. While installing Ubuntu 11.04, it is super easy to do the partitioning but from what I have seen its a bit more technical when stetting up ubuntu studio. What is the easiest way to partition it to duel boot with windows 7. (still need windows 7 for school work)

I thank you guys in advance for your tips and help as you guys are always very helpful and respectful.

P.s. I am using an acer aspire 5551-2450 if that matters

---

### Post by Mark Phelps on 2011-10-04
Since you still NEED to use Win7, need to do the following:
1) Check your drive with the Win7 Disk Management utility.  If you already have four partitions on your drive, that is the maximum number allowed and installing to another partition is going to involve a LOT of work.
2) If you don't have four partitions already, use the Win7 Disk Management utility to shrink the Win7 OS partition to make room for Ubuntu.  Do NOT use the Ubuntu installer to do this.  Doing so risks corrupting the Win7 OS partition and rendering it unbootable.
3) Once you have the Win7 OS partition shrunk, boot back into it a couple of times, and then -- use the Backup feature to create and burn a Win7 Repair CD.  This will allow you to repair any damage to the Win7 boot loader from the dual boot setup later.

---

### Post by ajsoulmate on 2011-10-04
> **jiggajoe506 said:**
> 1. Is ubuntu Studio a complete OS on its own or is it an addition to Ubuntu 11.04?


2. While installing Ubuntu 11.04, it is super easy to do the partitioning but from what I have seen its a bit more technical when stetting up ubuntu studio. What is the easiest way to partition it to duel boot with windows 7. (still need windows 7 for school work)



1) [http://ubuntustudio.org/](http://ubuntustudio.org/)

2) Use GParted - boot from Live CD and run GParted.

---

### Post by Mark Phelps on 2011-10-04
As far as I know, both the Ubuntu installer and GParted use the same app -- parted -- to do partitioning.  So, NO, do NOT use GParted to shrink the Win7 OS partition.  Use the Win7 Disk Management utility instead.

---

### Post by audiomick on 2011-10-04
> **jiggajoe506 said:**
> 
1. Is ubuntu Studio a complete OS on its own or is it an addition to Ubuntu 11.04?


in short, the "studio" edition is Ubuntu with a swag of additional specialist programs added. That is putting it just a bit simply, but yes, Ubuntu Studio is a complete OS.

---

