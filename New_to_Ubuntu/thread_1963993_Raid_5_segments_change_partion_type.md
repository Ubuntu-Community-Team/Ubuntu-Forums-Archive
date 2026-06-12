---
title: "Raid 5 segments change partion type"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by Bruce0 on 2012-04-23
I am not booting off raid, I am not running windows or any other operating system.  Just ubuntu server 11.10. With gnome desktop installed on top.

For my server application , I built a raid 5 array using mdadm with 4 2TB disks.
Prior to doing that I created one large partition on each disk
I wanted to have the partions raw ( no file structure) because i figured the raid software would take care of the space, so I used Linux-swap, because unallocated seemed wrong, and seemed to cause me problems on my first try.

So now I am happy, it all works except that even though mdadm had made a nice array all over the disks, the disks still show as linux-swap, and I am worried that somehow some utility (gparted) and some fat finger will someday turn the partions actually INTO swap space and I will lose my data.

I would start all over, but it is so hard to destroy these mdadm arrays (I did it once), and I have about 1.8TB of data loaded now (8TB of disk, a 5.4TB array, everything takes a while at these sizes).

I was wondering, is there some way to say the space is "unallocated" or really anything but swap, or is this really no problem.  

Or maybe you could tell me what parted/gparted are looking at to decide this is swap space, because mdadm has stomped all over the physical storage by now.

Note:

I of course don;t have the devices marked as swap in /etc/fstab ...  But I am worried to even type the word swap for fear of accidentally getting these array segments marked as swap in fstab or somehow written on by linux as swap space.

You will note I set the "raid" flags on the partitions, but I am not sure that really helps much.

 

Below is a parted -l of the bott disk file systems, and the relevant devices that make up the array file system, and a cat of fstab and /proc/mdstat

Thanks for your help.  I have searched pretty thoroughly, but I can't seem to find anything on these partitions as part of mdadm that don't really matter. 

Bruce


bhb@ub:~$ sudo parted -l
Model: ATA WDC WD2500KS-00M (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  246GB  246GB   primary   ext4            boot
 2      246GB   250GB  4292MB  extended
 5      246GB   250GB  4292MB  logical   linux-swap(v1)


Model: ATA ST32000542AS (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2000GB  2000GB  linux-swap(v1)        raid
 2      2000GB  2000GB  54.5MB  ext2


Model: ATA ST32000542AS (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2000GB  2000GB  linux-swap(v1)        raid
 2      2000GB  2000GB  54.5MB  ext2


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2000GB  2000GB  linux-swap(v1)        raid
 2      2000GB  2000GB  54.5MB  ext2


Model: ATA ST32000542AS (scsi)
Disk /dev/sde: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2000GB  2000GB  linux-swap(v1)        raid
 2      2000GB  2000GB  54.5MB  ext2


Model: Linux Software RAID Array (md)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  6001GB  6001GB  ext4


bhb@ub:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ca35689e-1fba-431d-a483-1d05ce0f1db1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=528e3128-765d-4c29-9f91-d42922ef642a none            swap    sw              0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=f9055785-5ede-4768-98aa-c2a053edbb7c       /r5a    ext4    defaults        0       2
#

bhb@ub:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd1[2] sde1[4] sdc1[1] sdb1[0]
      5860376064 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
bhb@ub:~$

---

