---
title: "Partition issue with WinXP"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by iluvoats on 2008-07-28
Hi there everyone, Im a novice linux user and I just installed Ubuntu 8.04 this morning.   My problem is I'm trying to access the files on the windows portion of my pc, but i can't seem to.  

From what I understand, I should just have to mount the windows partition, but I can't find it!  When I run  
$ sudo fdisk -l
it returns only two partitions:

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+  42  SFS
/dev/sda2           30401       30401        8032+  42  SFS

When I mount the first it tells me its already in use, so I assumed then that i had mistakenly overwritten the whole XP OS drive with ubuntu, but XP still boots fine.  Any help would be really appreciated.

Oh, and if it makes any difference when I installed ubuntu I did it from within windows by mounting the disk to a virtual drive using Daemon Tools Pro.

BTW, this is the code I input

$ sudo mkdir /mnt/winxp
$ sudo mount -t ntfs /dev/sda1 /mnt/winxp


Thanks in advance!

---

### Post by Fire_Chief on 2008-07-28
Did you install Ubuntu using Wubi? You mentioned that you mounted the ISO from within Windows and performed the install from there. Unless you used Wubi or installed into a Virtual Machine, I don't know how you did that. Is the system dual booting or do you always load Windows first and then run Ubuntu from within it?

Cheers!

---

