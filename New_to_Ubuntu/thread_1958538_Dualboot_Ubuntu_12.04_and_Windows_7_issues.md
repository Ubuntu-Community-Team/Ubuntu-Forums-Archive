---
title: "Dualboot Ubuntu 12.04 and Windows 7 issues"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by vasiauvi on 2012-04-14
Hello all,
I want to install Ubuntu 12.04 on a DELL Inspiron which has Windows 7 installed allready. It's not my first time installing Ubuntu on a laptop but this time it's a little bit tricky for me.

I have a 640GB Hard disk and Windows is on 100GB NTFS and I have an other NTFS partition for 100GB. So, **should** remain arround 440GB which is "unallocated".

When I want to resize/format that partition from my 640 GB hard disk something is wrong. I don't see a NTFS partition of 100GB and the unallocated partition is 500GB instead of around 440G.

Please see the image from [here]("http://dl.dropbox.com/u/1518616/Share/ubuntu_live.png").

I am stuck here because i don't know why doesn't show me both NTFS partitions and the unallocated space is to large compared whith how should have been. Also I really don't want to loose my data from Windows 7.

Can anyone give me an idea how to continue?

Thanks!

[EDIT]
```
ubuntu@ubuntu:~$ sudo fdisk -l -u

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0c7a859b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2           80325       81919         797+  42  SFS
Partition 2 does not start on physical sector boundary.
/dev/sda3   *       81920      286719      102400   42  SFS
/dev/sda4          286720   204881919   102297600   42  SFS
```

---

### Post by PhantomTurtle on 2012-04-14
Can you run 
```
diskmgmt.msc
```
in Windows. Can you please take a screenshot and show me that you have 440GB unallocated and that that you have another 100GB NTFS partiton. It's not that I don't believe you, it's just that, I have never seen something like that.

---

### Post by oldfred on 2012-04-14
Your SFS partitions means you have dynamic partitions which do not work with Linux (and some Windows tools).

Whatever you do be sure to have good backups. Microsoft's official instructions are to backup all data, erase drive and create new basic partitions and restore data. Best if you have not actually resized dynamic to cross physical partition boundaries and if you can delete any empty dynamic before converting.  You can only have 4 primary partitions with MBR(msdos) partitioning.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.

You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.

Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

---

### Post by vasiauvi on 2012-04-14
Thank you for your help.

Indeed the partitions are dynamic (see [picture]("http://dl.dropbox.com/u/1518616/Share/partitions.png")).

@oldfred
I will try to follow the tutorials for changing the partition from dynamic to basic. I will come back with a response here after finishing.

---

### Post by vasiauvi on 2012-04-14
I've changed from dynamic to basic with EASUS and after booting Windos7 workes like before.In Win7 showes me that are really "basic" drives/partitions. Trying to install Ubuntu shows me now that I have all my drive as "unallocated"([see image]("http://dl.dropbox.com/u/1518616/Share/unallocated_drive.png")).


```

ubuntu@ubuntu:~$ sudo fdisk -l -u

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0c7a859b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       81920      286719      102400    7  HPFS/NTFS/exFAT
/dev/sda2          286720   204881919   102297600    7  HPFS/NTFS/exFAT
/dev/sda3              63   409681919   204840928+   f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5             126       80387       40131    1  FAT12
Partition 5 does not start on physical sector boundary.
/dev/sda6       204881984   409681919   102399968    7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

Disk /dev/sdb: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77b08b86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15646719     7823328+   c  W95 FAT32 (LBA)


```

---

### Post by oldfred on 2012-04-14
It looks like the conversion where it had to create some logicals did not work exactly right. 

You can have only 4 primary partitions and only one can be converted to an extended partition holding many logical partitions. All primary partitions are numbered sda1 thru sda4 and logicals are sda5 & up. 

Your configuration seems to violate several of the rules, so gparted does not know what to do. It looks like sda1 & sda2 are inside the extended partition.

Again before any fixes be sure to have good backups.

Also backup current partition table to a text file, so you can go back if necessary.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by vasiauvi on 2012-04-15
Thank you for your help.
I've managed to install Ubuntu 12.04 LTS and it's working great.

So, if someone has dynamic partitions should use [EASEUS partition manager]("http://www.partition-tool.com/easeus-partition-manager/comparison.html") to make the partition basic. Be careful not to have more than 4 NTFS partions.

Good luck!

---

