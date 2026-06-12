---
title: "An unusual dual-boot situation, and related problems"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by Mykas0 on 2012-03-10
Hey there, everyone.

I was hoping you could give me a hand around here, since this kind of procedure just isn't my cup of tea...

Basically, I have an old computer with two hard drives, let's call them "A" (120 GB) and "B" (20 GB). Right now I have Ubuntu currently installed on "B", but I wanted to install Windows XP on "A", and I'm afraid this will break my current Ubuntu installation. So, I have a few questions:

1- Is there any sort of simple tutorial you can point me to, that will help me across this procedure? I'm particularly worried by the fact that installing XP now will obviously break my previous Ubuntu system.

2- Is is possible for me to join "A" and "B" in two partitions, so I can have two 60GB partitions, one for Ubuntu and another for my other OS? If so, how?

Thanks in advance!

---

### Post by acimi66 on 2012-03-10
This might have some info for you

[http://pressf1.pcworld.co.nz/archive/index.php/t-30.html](http://pressf1.pcworld.co.nz/archive/index.php/t-30.html)

Good Luck

---

### Post by Mykas0 on 2012-03-11
Unfortunately, that didn't help me that much.... any more ideas?

---

### Post by acc61287 on 2012-03-11
> **Mykas0 said:**
> Hey there, everyone.

I was hoping you could give me a hand around here, since this kind of procedure just isn't my cup of tea...

Basically, I have an old computer with two hard drives, let's call them "A" (120 GB) and "B" (20 GB). Right now I have Ubuntu currently installed on "B", but I wanted to install Windows XP on "A", and I'm afraid this will break my current Ubuntu installation. So, I have a few questions:

1- Is there any sort of simple tutorial you can point me to, that will help me across this procedure? I'm particularly worried by the fact that installing XP now will obviously break my previous Ubuntu system.

2- Is is possible for me to join "A" and "B" in two partitions, so I can have two 60GB partitions, one for Ubuntu and another for my other OS? If so, how?

Thanks in advance!

Dual boot?:confused: your hard disk A and B has separated MBR, if you install WinXP in A its fine, but in booting you must choose what disk is master and slave.

In question 2, try LVM I'm not sure about this:P

---

### Post by Mykas0 on 2012-03-11
acc61287, that's exactly my main problem... having two disks, opposed to two partitions, will cause me a lot more trouble in the long run... that's why I wanted to join them together, but I'm not even sure if this is possible...

---

### Post by acc61287 on 2012-03-11
> **Mykas0 said:**
> acc61287, that's exactly my main problem... having two disks, opposed to two partitions, will cause me a lot more trouble in the long run... that's why I wanted to join them together, but I'm not even sure if this is possible...

Try to read this tutorial:
[http://workaround.org/ispmail/lenny/basic-debian-installation](http://workaround.org/ispmail/lenny/basic-debian-installation)

Read only the installation process maybe It will help you :)

---

### Post by oldfred on 2012-03-11
Is this an older IDE system that can only boot from the primary master? Or can you select boot drive in BIOS?

With two drives I prefer to keep systems separate, especially if you can boot separately from BIOS. If grub is in sda, you can reinstall to sdb. But if you only can boot from sda, you will have to reinstall grub2's boot loader to the MBR of sda as Windows will put its boot loader in the MBR of sda.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

I do not understand why you think you need to combine drives into one. Not easy, LVM is about the only way to do that and it is an extral level of complexity. While it gives that flexibility any failure of one drive destroys all data on both, so backups are even more important.

---

### Post by presence1960 on 2012-03-11
I agree with oldfred's suggestions. If you are a noob (nothing wrong with that BTW) or not so versed in partitioning or OS installations what oldfred suggested is the best way for you to go, provided you can choose either hard disk for boot in BIOS. Let us know if your disks are IDE or an IDE and SATA disks, also as oldfred asked can you choose either disk to boot from BIOS?

---

### Post by Mykas0 on 2012-03-11
Guys, thanks for your help, but I already managed to fix this problem a few hours ago, with some help from the Ubuntu IRC channel. However, for future reference, I thought I should mention here what I did...

Basically, I reinstalled Ubuntu on "A". Then, swapping the disk order by using the BIOS, I installed Windows XP on "B". Then, I edited the boot.ini to be able to boot to the Windows XP (the disc swap lead to a "hal.dll missing" problem), but this also lead to a problem - depending on the disk I put first in the BIOS, that system would start, which was sort of nagging and complicated since I wouldn't be the primary user of the whole system.
So, I went to Ubuntu and updated it to a newer version, knowing it would force an update of GRUB (yes, there are certainly easier ways to do this, but I knew of none)... soon after, the GRUB system started to show both systems, and this was all working the way I wanted it to...


Oh, and about the discs, I had an IDE and a SATA one in that system!

---

