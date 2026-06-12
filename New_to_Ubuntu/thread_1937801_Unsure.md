---
title: "Unsure"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by andycarp on 2012-03-08
I am currently a windows 7 user. I have been recently sent a Ubuntu Linux 11.10 disc to try. Recently I have been reading reviews recently about Linux and all seems good but I am worried about changing over and what if any effect it will have on my desktop pc. Any advice or reassurance would be appreciated.

---

### Post by jerome1232 on 2012-03-08
Dual boot, that way you have Ubuntu to play with and learn, and Windows to fall back to, the Ubuntu installer can set it up fairly easy, just choose to install along side windows (it's worded something like that)

---

### Post by Matt__ on 2012-03-08
why is it an issue?
try ubuntu from the cd without making any changes to your system.

If and when you decide you like it, install it alongside windows so you can access both.

If you play any pc games or use CaD programs you will be at a disadvantage, for everything else ubuntu will win over windows by being faster and doing exactly as you want it to.


//out-typed again!

---

### Post by jerome1232 on 2012-03-08
> **Matt__ said:**
> 
//out-typed again!

I hate that!

---

### Post by Mark Phelps on 2012-03-09
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

