---
title: "Partition 5 does not start on physical sector boundary."
date: 2015-01-30
forum: New to Ubuntu
---

### Post by danne33 on 2015-01-30
```
sudo fdisk -l

Disk /dev/sda: 596,2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xa93a8f9c

Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1  *         2048     409599    407552   199M  7 HPFS/NTFS/exFAT
/dev/sda2          409600  794552319 794142720 378,7G  7 HPFS/NTFS/exFAT
/dev/sda4       806273022 1157832703 351559682 167,7G  5 Extended
/dev/sda5       806273024  845332479  39059456  18,6G 83 Linux
/dev/sda6       845334528 1157832703 312498176   149G 83 Linux

Partition 5 does not start on physical sector boundary.
```
I can't understand why I get the problem. Isn't 806273024 dividable with 512 and 4096?
Is it a problem and what do I need to do to fix it?

---

### Post by oldfred on 2015-01-30
What does this show?
sudo parted -l

Not sure fdisk is totally up to date. Or if you can divide by 8 it should be ok.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by danne33 on 2015-02-02
> **oldfred said:**
> What does this show?
sudo parted -l

Not sure fdisk is totally up to date. Or if you can divide by 8 it should be ok.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

I am not so technical so I don't understand what is written in the threads. 
Here is an output from sudo parted -l
```
Model: ATA Hitachi HTS54756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  210MB  209MB   primary   ntfs         boot
 2      210MB   407GB  407GB   primary   ntfs
 4      413GB   593GB  180GB   extended
 5      413GB   433GB  20,0GB  logical   ext4
 6      433GB   593GB  160GB   logical   ext4


```

---

### Post by oldfred on 2015-02-02
I do not see anything wrong. Not sure why fdisk is complaining.
The start is divisible by 8 show according to all the links it is correct.

---

