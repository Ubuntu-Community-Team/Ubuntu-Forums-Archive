---
title: "Harddrive partitions"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by EricFalbe on 2012-12-10
I have a problem with partitioning my harddrive.
I installed Windows 7 on one of the four partitions of my harddisk before and now I want to install ubuntu on a different partition, but the installer for ubuntu looks like it wants to reformat my whole harddisk. :(  What can I do, to make sure ubuntu is installed on the secound partition without my Windows 7 installation beeing damaged or deleted?

---

### Post by Bucky Ball on 2012-12-10
Welcome to the forums.

When you get to the partitioning section choose 'Something Else' and create partitions manually.

Leave Win partitions alone (you will clearly see them as NTFS partitions) and create an extended partition with the rest of the disk. Inside that create the logical drives /, /home and swap.

/ = where the OS is, 15Gb plenty;
/home = where your personal data is, big as you like;
/swap = last partition at end of disk, 2Gb fine.

There are defaults in there for all three. You just need to select those mount points and allocate sizes. Format them as EXT4. 

Take note that Linux must be on a EXT* partition but Win can not read them. If you want to share data you are going to need an NTFS data partition which both OSs can read/write to. ;)

---

### Post by Impavidus on 2012-12-10
Did you say you already have four partitions? Drives can only have four primary partitions (with MBR formatting, but I think that's what win7 wants), so if your four partitions are all primary partitions this explains why you can't install ubuntu without formatting at least one of the partitions to turn it into an extended partition. That's why the ubuntu installer may not give the option to install alongside.

Make your win7 installation use at most three primary partitions and leave part of your disk unallocated, and then use the ubuntu install dvd, with manual partitioning (choose "something else") to make the ubuntu partitions as described in the previous post.

PS: Swap should be slightly larger than your RAM if you want to hibernate. Else, it doesn't really matter. If you've got plenty of memory and never hibernate you don't really need swap, but as it's only a small fraction of your disk there's no problem in making a swap partition anyway.

---

### Post by Bucky Ball on 2012-12-10
> **Impavidus said:**
> Drives can only have four primary partitions ... That's why the ubuntu installer may not give the option to install alongside.

+1. Could be the case.

> **Impavidus said:**
> Make your win7 installation use at most three primary partitions and leave part of your disk unallocated, and then use the ubuntu install dvd, with manual partitioning (choose "something else") to make the ubuntu partitions as described in the previous post.

+1. But, create an extended partition with the free (unallocated) space, then make the partitions described in my previous post, as suggested. ;)

---

### Post by EricFalbe on 2012-12-11
I have one primary and an extended partition with three logical ones. I have Windows 7 on a logical and my system boots fine, although the primary is marked as boot. 
I could select the secound partition as ext4-filesystem, but I wasn't sure, what to select as mountpoint. I thought it maybe "/" the root, but I didn't know for sure. :-(

Furthermore, the installer asked for a file called 'rtl_nic/rtl8168d-1.fw'.

---

### Post by Bucky Ball on 2012-12-11
Your setup is fine and yes, / is where Ubuntu lives:

/ = where the OS is, 15Gb plenty;
/home = where your personal data is, big as you like;
/swap = last partition at end of disk, 2Gb fine.

Bypass the file the installer is asking for. That is for your wireless card and you can deal with that once installed. (As it looks like a Realtek card that should be taken care of during install, part of the kernel, and you shouldn't need to install any driver manual ... shouldn't need to ...)

---

