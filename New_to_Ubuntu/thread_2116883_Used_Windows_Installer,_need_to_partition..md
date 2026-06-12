---
title: "Used Windows Installer, need to partition."
date: 2013-02-17
forum: New to Ubuntu
---

### Post by floattube on 2013-02-17
I need more space for Ubuntu on my hard drive. This is my secondary hard drive, so it doesn't have OS on it.

I don't see a Linux partition anywhere, Big Daddy is my main partition for my Windows 7 OS. I really need more space for my Ubuntu, but I don't know what to change. Sorry if this is a stupid question, I just can't figure it out.

I am using Ubuntu 12.04LT

[IMG]http://i.imgur.com/07SAEEo.png[/IMG]

---

### Post by majorburt on 2013-02-17
> **floattube said:**
> I need more space for Ubuntu on my hard drive. This is my secondary hard drive, so it doesn't have OS on it.

I don't see a Linux partition anywhere, Big Daddy is my main partition for my Windows 7 OS. I really need more space for my Ubuntu, but I don't know what to change. Sorry if this is a stupid question, I just can't figure it out.

I am using Ubuntu 12.04LT

[IMG]http://i.imgur.com/07SAEEo.png[/IMG]

just got done with this exact thing.

the top one (/dev/sata1) is for the company (dell) software. 
the second one appears to be a system recovery partition. could be wrong on that one tho. 

you're going to want to use the third one "big daddy" (/dev/sata3). 

while your at it, you should merge the unallocated 2.02 Mib with "big daddy" just to be better organized unless it has a reason for being there.

hope this helps.

---

### Post by floattube on 2013-02-17
Okay, will do! I'll edit this with the results after I am finished. Thank you!

---

### Post by 3rdalbum on 2013-02-17
The Windows installer (Wubi) does not partition, it merely creates a file on your Windows disk that contains Ubuntu. This file is limited to 16 gb or so, which is why you've run out of space so quickly.

If you want more space, you should install Ubuntu for real. First, remove Ubuntu using Windows' Add/Remove Programs. Then, boot Ubuntu from the CD and choose "Install Ubuntu". Follow the prompts to resize a partition (to make room for Ubuntu) or format an existing partition and install Ubuntu onto it.

If you get asked for the mount point, it's "/". If you get asked for a filesystem type, use "ext4".

---

### Post by Mark Phelps on 2013-02-17
> **floattube said:**
> Okay, will do! I'll edit this with the results after I am finished. Thank you!

Hope I'm not too late! NO, NO, do NOT do that!

Messing around with the Win7 OS partition using GParted is asking for trouble.  You might be OK and have Win7 survive, but more likely, that will corrupt Win7 and render it unbootable.

The "/host" indicates that Ubuntu is installed INSIDE Windows -- NOT in its own partition.  Shrinking the Win7 OS partition will do nothing to increase or decrease the filespace allocated to Ubuntu.

---

### Post by majorburt on 2013-02-18
> **Mark Phelps said:**
> Hope I'm not too late! NO, NO, do NOT do that!

Messing around with the Win7 OS partition using GParted is asking for trouble.  You might be OK and have Win7 survive, but more likely, that will corrupt Win7 and render it unbootable.

The "/host" indicates that Ubuntu is installed INSIDE Windows -- NOT in its own partition.  Shrinking the Win7 OS partition will do nothing to increase or decrease the filespace allocated to Ubuntu.

i thought that resizing partitions only shrank the free space. it seemed to work on mine but i could have gotten lucky.


sorry floattube, hope everything still works. my bad.

---

### Post by Mark Phelps on 2013-02-18
> **majorburt said:**
> i thought that resizing partitions only shrank the free space. it seemed to work on mine but i could have gotten lucky.
That is what it is supposed to do .. but with Vista, Win7, and Win8, MS did something to NTFS filesystem making it fragile to changes from "outside" Windows. Seems to happen most when folks go into Win7 Disk Management, find out it won't shrink the amount they want, then go into GParted, shrink it the full amount -- and then try to boot back into Windows.

---

