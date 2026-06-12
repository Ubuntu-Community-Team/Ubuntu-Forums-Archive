---
title: "automant RAIDvolume partition automatically on boot?"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by jimbolad on 2012-11-04
Hi , I have posted before but I think I know know what the problem is. My music folder is stored on RAID0 volume and as I am dual booting Ubuntu with windows 7 this is a windows partition ( am I correct?)...

I need to find a way of automatically mounting this drive in ubuntu on startup so that I dont have to re import my media library into banshee every time I turn my computer on. Another way to manually mount it was to click on the disk drive itself through the folder but this is just hassle and I want it to be automatic. 

I've seen another thread very similair and the guy was told to run these commands

```
cat /etc/fstab
sudo blkid 
sudo fdisk -l

```

So here are the results and I hope you can make more sense than I can?

```

james@james-Ubuntu-pc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdh2 during installation
UUID=883d02d3-97bb-44fe-85ab-06ec38288ac6 /               ext4    errors=remount-ro 0       1
james@james-Ubuntu-pc:~$ sudo blkid
[sudo] password for james: 
/dev/sda1: LABEL="System Reserved" UUID="F68CCCB98CCC7621" TYPE="ntfs" 
/dev/sda2: UUID="7876D11A76D0D9C8" TYPE="ntfs" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/sdd1: UUID="A28EC2CB8EC29767" TYPE="ntfs" 
/dev/sdd2: UUID="883d02d3-97bb-44fe-85ab-06ec38288ac6" TYPE="ext4" 
/dev/mapper/isw_djcebfdaa_RaidVolume1: LABEL="Raid0Volume" UUID="E8C02FCAC02F9E36" TYPE="ntfs" 
james@james-Ubuntu-pc:~$ sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda26eeed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  3907026943  1953410048    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x318b9965

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907035135  1953516544    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2552c7a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   335546367   167772160    7  HPFS/NTFS/exFAT
/dev/sdd2       335546368   500115455    82284544   83  Linux

Disk /dev/mapper/isw_djcebfdaa_RaidVolume: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907039744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x318b9965

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_djcebfdaa_RaidVolume1            2048  3907035135  1953516544    7  HPFS/NTFS/exFAT

Disk /dev/mapper/isw_djcebfdaa_RaidVolume1: 2000.4 GB, 2000400941056 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907033088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                                 Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_djcebfdaa_RaidVolume1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_djcebfdaa_RaidVolume1p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_djcebfdaa_RaidVolume1p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_djcebfdaa_RaidVolume1p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order


```

---

