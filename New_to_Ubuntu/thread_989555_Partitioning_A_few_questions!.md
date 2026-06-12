---
title: "Partitioning: A few questions!"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by strN00B on 2008-11-21
Here is my scenario:

I have an old machine with a 60ish Gig hard drive that i wish
to install 1 single OS: Ubuntu.  I wish to partition the hard disk
into 2? partitions basically. One partition (ext3)to house the
ubuntu OS and another partition (NTSF) as network storage.

My questions are... How should I set this up using Ubuntu's
installation partitioning feature. It gives me options I do not
understand such as Type (Primary, Logical) and Mount Point.

Also do you recommend any other partitions such as a swap? Is a
swap necessary if there is only 1 bootable OS? 

Thank you!

---

### Post by beno1990 on 2008-11-21
The partition you are installing your operating system on should be the primary partition (with an ext3 filesystem), the NTFS partition should be logical.

The mount point is basically where the partition is placed in your filesystem hierarchy, such as / (root) or /home or any of the other standard mount points, or a custom one. For your ext3 partition (OS partition) you should mount it to /. For your NTFS partition, you can mount it to wherever you'll remember it as your NTFS partition, eg: /network.

---

### Post by taurus on 2008-11-21
Yes, swap partition is necessary especially if you install it on an old machine (unless you have a bunch of RAM).  Therefore, you can use gparted from the LiveCD (System -> Administration) and divide your harddrive into three primary partitions:  first one for / (ext3), second for swap (~1GB), and whatever left over for storage (ntfs).  Then when you install Ubuntu, just pick Manual at the partition screen and tell the installer to use the first partition and mount that as /.  You don't have to do anything with the swap partition since the installer should pick it up automatically for you.  Then, you can have the installer to mount the third partition but don't format it since it's already in ntfs.

---

### Post by doas777 on 2008-11-21
just a peice of advice, stick to primary's unless you need more than 4 per physical disk.

good luck,
franklin

---

### Post by adult swim on 2008-11-21
also before you do all of this in gparted, go ahead and delete all of the existing partitions first and click apply.  then go through and change them how you want.  i had to wait on gparted 20 hours once when i moved some partitions around.

---

### Post by bodhi.zazen on 2008-11-21
Start with this :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

Then this (you can probably get the information you need quickly)

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Then , fire up teh live CD, use gparted to make your partitions, then install

[Gparted Documentation]("http://gparted.sourceforge.net/documentation.php")


One small piece of advice, if I may. If you are going to install Ubuntu only I would use a linux native filesystem for your data partition (ext3). You can share the partition with samba (or other protocols) and there are no maintenance tools for nfts partitions in Ubuntu.

EDIT: WOW, you all are FAST today :)

---

### Post by strN00B on 2008-11-21
> **bodhi.zazen said:**
> I would use a linux native filesystem for your data partition (ext3)

You would use ext3 even if this partition is mostly gonna be
used as network storage for windows XP/Vista systems?

---

### Post by bodhi.zazen on 2008-11-21
> **strN00B said:**
> You would use ext3 even if this partition is mostly gonna be
used as network storage for windows XP/Vista systems?
 
Yes. You will share the drive via samba (I presume) and the network protocols do not depend on the underlying file system (you can share ext3 on a network share with windows just as easily as NTFS).

Ubuntu does not have any way of maintaining a NTFS partition (defragmentation, file system corruption, etc) so if you have issues (with ntfs) you could easily be stuck (as your installation does not inculde windows to fix the problem). There are some maintenance tools "in development" but I personally would stay with ext3.

---

### Post by strN00B on 2008-11-21
Those links are excellent! Thank you!~

---

