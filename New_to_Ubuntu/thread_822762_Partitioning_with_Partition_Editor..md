---
title: "Partitioning with Partition Editor."
date: 2008-06-08
forum: New to Ubuntu
---

### Post by LoadedBum on 2008-06-08
I'm running the CD of Ubuntu Hardy Heron 8.04 that has the option "Try without any change to your computer" or something like that. I want to install Ubuntu on my hard drive, but I don't know how much to resize the partition to put it on my hard drive. I don't want it to take over my whole C drive, so I need it partitioned.

plztobeaskingforhelp

---

### Post by logos34 on 2008-06-08
> **LoadedBum said:**
> I'm running the CD of Ubuntu Hardy Heron 8.04 that has the option "Try without any change to your computer" or something like that. I want to install Ubuntu on my hard drive, but I don't know how much to resize the partition to put it on my hard drive. I don't want it to take over my whole C drive, so I need it partitioned.

Choose Install.  After the desktoploads click on the Install icon, then when you come to partitioning section, select 'Guided--Resize' option.  It will shrink windows for you by the appropriate amount.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Paqman on 2008-06-08
One good option is to skip the whole partitioning issue all together. Just boot into Windows and put your Ubuntu CD in. An installer called Wubi will start up. Make sure you give Ubuntu 20GB or so when it asks, and a couple of clicks later you'll have Ubuntu installed.

---

### Post by housam on 2008-06-08
+ you can rezise C: partition manually and create 2 new partitions for ubuntu using the partition editor on ubuntu live cd: 
10-15 GB for the root ext3 format with the sign ( / )
1-2 GB for the swap
then commence the installation and when it comes to the partitioning , choose the manual way and assign the root partition.

---

### Post by LoadedBum on 2008-06-08
Well, this is freaking great.

I did the guided resize, and it was installing, but it says something's wrong with the disk. Even though I've installed Linux with it before.

>=(

---

### Post by logos34 on 2008-06-08
reboot and do the 'cd integrity' test.  

Maybe you burned it too fast and just got lucky the first time?  could be any number of things

---

### Post by Sef on 2008-06-08
Are you XP or Vista?  If Vista, then you need to use the Vista partitioner to shrink the partition for Vista.

---

### Post by logos34 on 2008-06-08
> **Sef said:**
> Are you XP or Vista?  If Vista, then you need to use the Vista partitioner to shrink the partition for Vista.

oh, I thought he was referring to the cd 'disk' 

> says something's wrong with the disk. Even though I've installed Linux with it before.

yeah, if he meant hard disk and vista is there, then it needs to be shrunk using its own utility

---

