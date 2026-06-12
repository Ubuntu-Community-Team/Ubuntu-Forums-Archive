---
title: "[SOLVED] Is Linux using both my HD's?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Kenza on 2008-06-24
I was trying to mount an IPod, but did something to get my HD on my Desktop and now i'm afraid to delete it...only option i really see is to "unmount" it now, but here is what i got with sudo fdisk -l:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d7d7d7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10010    80405293+   7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f770f76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9636    77401138+  83  Linux
/dev/sdb2            9637       10011     3012187+   5  Extended
/dev/sdb5            9637       10011     3012156   82  Linux swap / Solaris

One of my Harddrives should be blank, was debating on installing windows on the other one (trying to get away from M$ Windows, don't know much about Linux though), but when i go to look at both drives it seems that the Linux File System is on both (one is a Swap File?) I'm really confused and don't wanna' mess up anything like i usually do

---

### Post by Jabz.biz on 2008-06-24
good question...looks similar to my system. Waiting for an answer as well.  :)

---

### Post by alphane on 2008-06-24
No expert, but looks to me like you've one 82gig (SDA) disk formatted to NTFS (windows file system), and another 82gig (SDB) disk split into 3 partitions using the linux file system.

Is that not what you expected?

---

### Post by gtdaqua on 2008-06-24
You are definitely using two physical devices. 

One is /dev/sda and the other is /dev/sdb.

your /dev/sda has one partition which is an NTFS partition.


Your second /dev/sdb has linux partitions. 

If you had a third hard-disk it would be "/dev/sdc"....so on and so forth.

Wat you wanna do now?

---

### Post by mcduck on 2008-06-24
That seems like you have 2 hard drives.

First one (sda) only has one partition (sda1), formatted to NTFS, might contain Windows..

The second one (sdb) has 2 actual partitions; your Ubuntu install (sdb1) and swap partition (sdb5).

(sdb2 is and extended partition that contains the sda5.)

---

### Post by Nepherte on 2008-06-24
All the entries with /dev/sdb<number> are on the same disk. Each number denotes a partition. Each character: /dev/sd<character><number> denotes another disk. Here linux is installed on sdb, sda is formatted in ntfs so I presume you have a windows installed on that disk.

A swap partition is automatically created upon installing ubuntu or any other linux for that matter. You can consider it a sort of cache. When you run a program, a part of the program is loaded in your ram memory, the rest is loaded in the swap. If the program needs another part, it will swap the part that is loaded into the memory with your swap partition.

When you want to use a disk in an operating system (linux or windows for that matter), you have to mount it. The operating system will attach the disk onto your system so you can use the disk. When you unmount the disk, you detach it so you can't use it. The data on the disk will remain though.

---

### Post by Kenza on 2008-06-24
Ty for the replies and yes, i did have Windows on the other disk at one point, guess it kept the Windows file system even though i thought the disk was formatted (Blank), what confused me was the fact that i had 2 Linux "File Systems" (and one of them appeared to be on the extra HD).

Going to try to install windows now again on the first drive, hope it don't mess up Grub like last time, i had a heck of a time...since i'm a Linux n00b i had to reinstall after i tried that.

---

### Post by mcduck on 2008-06-24
> **Kenza said:**
> Ty for the replies and yes, i did have Windows on the other disk at one point, guess it kept the Windows file system even though i thought the disk was formatted (Blank), what confused me was the fact that i had 2 Linux "File Systems" (and one of them appeared to be on the extra HD).

Going to try to install windows now again on the first drive, hope it don't mess up Grub like last time, i had a heck of a time...since i'm a Linux n00b i had to reinstall after i tried that.

Installing Windows _will_ overwrite Grub.

But re-installing Grub is fairly simple thing to do and only takes couple of minutes to do..

---

