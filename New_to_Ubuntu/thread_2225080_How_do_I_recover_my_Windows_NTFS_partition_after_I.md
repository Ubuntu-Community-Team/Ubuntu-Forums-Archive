---
title: "How do I recover my Windows NTFS partition after I accidentally used it as a &quot;swap&quot;"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by a08tchar on 2014-05-19
So, long story short, while I was installing Ubuntu I selected my windows partition for the Linux "swap" and now the hard drive is inaccessable. From what I've read, I know it's pretty much reformatted and the only way I can restore it is to use testdisk.

Anyway, I've analyzed my disks on testdisk and I'm not entirely sure where to go from here. I just want to remove the swap and change it restore it back to windows and try to recover what files I can. Any advice would be appreciated. Thanks.

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
   HPFS - NTFS              0  32 33    12 223 19     204800 [System Reserved]
   HPFS - NTFS             12 223 19    25 159  5     204800
>  Linux Swap              12 223 20 95492 162 30 1533882368
   HPFS - NTFS             12 223 20 95492 162 30 1533882368
   HPFS - NTFS             12 223 20 121601  25 24 1953314816
   Linux                95492 162 31 121600 247 55  419430400






Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, pagesize=4096, 785 GB / 731 GiB

---

### Post by oldfred on 2014-05-19
Similar thread.
[http://ubuntuforums.org/showthread.php?t=2224729](http://ubuntuforums.org/showthread.php?t=2224729)

If in your system immediately swap off so it will not be used.
man swapoff
sudo swapoff -a

Restore the NTFS partition that has the same start & end as your swap.
>  Linux Swap              12 223 20 95492 162 30 1533882368
   HPFS - NTFS             12 223 20 95492 162 30 1533882368

---

### Post by a08tchar on 2014-05-20
How do I restore it with testdisk?

---

### Post by oldfred on 2014-05-20
I never have used testdisk but many have reported it works well.

Partitions do have to follow the correct partition rules. You can only have 4 primary partitions. One and only one primary can be the extended partition. And all logical partitions must be in the one extended (or next to each other on drive).

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Mark Phelps on 2014-05-20
IF Testdisk doesn't work, you can try downloading and burning a CD of the Minitool Partition Wizard Boot CD.  Boot from it and use the option to recover the partition.

---

### Post by a08tchar on 2014-05-20
I tried viewing the files in the partition by pressing 'p' but I just end up getting the message "*Can't open filesystem*. *Filesystem seems damaged"*

---

### Post by oldfred on 2014-05-20
Did you immediately swap-off if in your install?

Or are you using gparted or parted magic liveCD as they do not mount swap. 

Ubuntu live installer mounts swap and copies data into it to speed up access. So that damages the old NTFS data.

If you have overwritten major parts of the NTFS partition it becomes difficult to recover much.

You can try just changing partition to NTFS from swap as I posted in thread in my first post.

You need to confirm which partition it is, it looks like it may be sda2, but I cannot be sure. It looks like a typical Windows 7 with a 100MB boot partition as sda1.
sudo parted -l

Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

If Windows 7 is/was sda2, note space after sda, see man sfdisk for details type 07 is NTFS.
   change sda2 to type 07
sudo sfdisk --change-id /dev/sda 2 07

---

### Post by a08tchar on 2014-05-21
Do I select "Write partition structure to disk"?

---

### Post by oldfred on 2014-05-21
If you have removed swap and restored NTFS you do have to save it or else it reverts.

---

