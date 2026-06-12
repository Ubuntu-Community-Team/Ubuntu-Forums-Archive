---
title: "Install Kali Linux (Dual Boot) on a pre-installed Ubuntu system"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by DXXPublic on 2014-02-12
Hi all, 

I apologize if im asking on the wrong place of if this was already asked before.

Im a absolute beginner on Linux OS and im on the process of learning it.  I have a system (Inspiron 14) with Ubuntu 12.04 pre-installed and i want to install Kali Linux as well for learning purposes for the security path im taking.  I would like to have a dual boot between those two because running Kali from a CD is very slow.

These are the current partitions i have

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      718847      358400   de  Dell Utility
/dev/sda2          718848     7010303     3145728    c  W95 FAT32 (LBA)
/dev/sda3   *     7010304  1448923135   720956416   83  Linux
/dev/sda4      1448925182  1465147391     8111105    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1448925184  1465147391     8111104   82  Linux swap / Solaris

All the guides ive seen get me to the point where i need a free partition space, and since i have none i was wondering if you could guide me tru the process of resizing the sd3 partition (boot) to free up some space to install Kali.   Or if there is another easier way i will appreciate that very much

Thank you in advance

---

### Post by oldfred on 2014-02-12
You have used all 4 primary partitions as the extended counts as a primary.
So you have to shrink sda3 with gparted and then moved extended left into unallocated to in effect move unallocated inside the extended partition. Then you can create new logical partition(s). 

You have to run gparted from liveCD/DVD/Flash as you cannot use working system as it is mounted. And even with live system, you may have to click on swap and swap off to unmount it as many live installer automount swap. I think the gparted liveCD does not automount swap.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


 gparted also is on Ubuntu live installer.
[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

