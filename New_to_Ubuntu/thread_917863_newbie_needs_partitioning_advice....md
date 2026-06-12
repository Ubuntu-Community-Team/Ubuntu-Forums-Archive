---
title: "newbie needs partitioning advice..."
date: 2008-09-12
forum: New to Ubuntu
---

### Post by zizzerboy on 2008-09-12
Hi there, I am hoping to dual-boot ubuntu on:
Dell Studio 15, Intel Core Duo T8100, 2.1 Ghz, 800 Mhz, 3M L2 Cache, 3 GB Ram, 250 GB Hard Drive, running vista home edition.

This is kind of a dumb question, but should I download the ‘64bit AMD and Intel Computers’ at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) , even though I have a 32 bit processor?

My next question is about partitioning. I’m really new to this, so I need help. I have read the documentation, but I’m not sure how to apply it to my system, since I have a recovery partition:

[IMG]http://farm4.static.flickr.com/3043/2849345081_56c0d2fba8_o.jpg[/IMG]

I know the documentation says that you can only have 4 partitions. Do I need the recovery partition, or could I just delete it?  (I don’t really need it, as I have other ways of backing it up)

About the swap partition, is it true that the biggest that it should be is 1GB? I know you’re supposed to have it be twice the size of your memory…

So basically, I would like your advice on how to set up my partitions, I.e., how would you set up your partitions if you were me?

---

### Post by halitech on 2008-09-12
if you have a 32bit machine then you need the 32bit version

far as partitions, you can only have 4 primary partitions, you can have more logical ones though. Are you planning on keeping Windows and dual booting or just going with Ubuntu?

---

### Post by neurostu on 2008-09-12
You should have 4 partitions (assuming you want to dual boot):
1 - 1 formatted NTFS for windows (50 - 150 Gb)
2 - 1 formatted EXT3 for Ubuntu / (15-25 Gb)
3 - 1 formatted EXT3 for Ubuntu /home/ (50 - 150 Gb)
4 - 1 formatted linuxswap (512mb - 2gb)

If you don't want to dual boot drop the windows partition.
Also don't worry about deleting the recovery partition, its a waste of space anyway, and once you install ubuntu it will be broken anyway...

---

### Post by zizzerboy on 2008-09-12
> **halitech said:**
> if you have a 32bit machine then you need the 32bit version

far as partitions, you can only have 4 primary partitions, you can have more logical ones though. Are you planning on keeping Windows and dual booting or just going with Ubuntu?

Thanks for the fast response! So should I download the 'Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)' Version instead? I wasn't sure, since it's an Intel 32 bit processor...

I am planning on dual booting.

---

### Post by neurostu on 2008-09-12
Yes just download the i386 live cd.

---

### Post by halitech on 2008-09-12
yes, go with the standard i386 version

---

### Post by waspbr on 2008-09-12
provided you want some practice before trying the real thing, you could try installing ubuntu in windows through wubi

---

### Post by zizzerboy on 2008-09-12
thanks everyone for all your help! :KS

---

### Post by halitech on 2008-09-12
before  you start installing Ubuntu, run a defrag in windows a few times, rebooting between each one then use the builtin partition tool in Windows to shrink the windows partition and leave the empty partition for Ubuntu to find

---

### Post by prshah on 2008-09-12
> **zizzerboy said:**
> Hi there, I am hoping to dual-boot ubuntu on:
Dell Studio 15, Intel Core Duo T8100,

 but should I download the ‘64bit AMD and Intel Computers’ 

even though I have a 32 bit processor?

My next question is about partitioning. I’m really new to this, so I need help. 

 the documentation says that you can only have 4 partitions. Do I need the recovery partition, or could I just delete it?

About the swap partition, is it true that the biggest that it should be is 1GB? I know you’re supposed to have it be twice the size of your memory…

I.e., how would you set up your partitions if you were me?

Are you sure you have a Core and not a Core 2? The T8100 spec is for Core 2 CPUs, which have EM64T support (64 bit). In this case, you can use either version, but 32bit is better for newbies.

As for partition setup:

a) Don't disturb your recovery partition

b) While you can have only 4 "primary" partitions, _one_ of those 4 can be an "extended" partition which contains any number of "logical" partitions.

c) I don't know what the first partition is for (EISA configuration!!?!?!)

d) Suggestion: Resize your Vista to 30-odd Gb, then create an Extended Partition which contains:

[INDENT]i) 10 Gb "/" (root) partition
ii) 3.3Gb "swap" partition
iii) 50% of the balance for "/home" partition
iv) The leftover as an additional NTFS partition for Vista spillover.
[/INDENT]

e) I suggest 3.3Gb for swap because you need 1.1 times your RAM (allowing for future bad sectors) if you want to use the hibernate feature. If you don't plan to use hibernate, you can do away with swap altogether, or just stick in a 512-Mb swap (which will be _very_ rarely used).

f) You can also install the Ext2/3 IFS drivers, which will allow you access to your ubuntu partitions; but when installing, choose "Read-only" access.

Post back if you need more help in the partitioning phase.

---

