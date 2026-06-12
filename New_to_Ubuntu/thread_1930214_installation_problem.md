---
title: "installation problem"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by totocompany on 2012-02-23
hi 

when i want to install H drive my laptop's but there is problem .
how i will solve this? mainly i want to dual boot my c drive i use  windows 7 and h drive i want to use ubuntu.[img]http://www.freeimagehosting.net/t/nc14r.jpg[/img]

---

### Post by cortman on 2012-02-23
Hi and welcome to the forums!

Are you saying you have two partitions on your hard drive, and you want to keep Windows in one and install Ubuntu in the other? Or do you have two physical drives?

---

### Post by sadaruwan12 on 2012-02-23
Welcome to the forum !

I would love to help you but my dear friend can you give us a clear view of the screen shot it's too small can't see it very clearly.

---

### Post by Mark Phelps on 2012-02-24
Can't read the screen shots -- too small.  But guessing at the first one, it looks like Ubuntu is not allowing you to choose any side-by-side options because the drive is already fully allocated.

Read through the materal below BEFORE you continue:

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

