---
title: "Ubuntu upgrade to 14.04.1 thru full install, can't access RAID 1 partitions"
date: 2014-11-10
forum: New to Ubuntu
---

### Post by Scott_Hamilton on 2014-11-10
Help!  Here's the deal.  I was on 12.10 and had a RAID1 software raid (created via mdadm) working fine.  The 2 drives are 1TB drives.

On install of 14.04.1, it detected that I had a raid and "activated" it.  But what I'm left with is an inaccessible couple of drives.  Basically the drives show in the /dev/sd* list but there are no usable partitions to mount, and no mountable /dev/dm0 that used to be there.  I'd really, REALLY like to recover what is on the drive, whether or not it involves reassembling the RAID array or just "breaking" the RAID and treating the disks as individual disks (in which case I'll back up the data and recreate the raid).

The two drives show up as /dev/sdc and /dev/sdd, as you'll see below.  The filesystem on the drives should be ext4 but parted will show it as ext2 for some reason.  Running testdisk finds partitions that appear to be NTFS.  (However, I can't navigate into them to see files - says it is corrupted, and if I navigate into the Linux RAID partition it says it wasn't compiled with support for that.)

In my many attempts to salvage the situation, I did end up pulling an image onto another disk (so I could experiment) and was able to mount using an offset switch using both ext2 and ext4 but the file set this exposes is a bunch of *-generic files that look like linux system files.  (I'm guessing that is from a different partition than I was hoping to restore?)

Here are some important bits of data:
```

scott@uberserver:~$ cat /proc/mdstat Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

scott@uberserver:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/uberserver--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=a61da7a6-40f8-439e-9ddb-2021a034fed2 /boot           ext2    defaults        0       2
/dev/mapper/uberserver--vg-swap_1 none            swap    sw              0       0
/dev/sdb1    /media/wd300gb    ext3    0    0


scott@uberserver:~$ lsblk
NAME                             MAJ:MIN RM   SIZE RO TYPE   MOUNTPOINT
sda                                8:0    0 139.8G  0 disk   
&#9500;&#9472;sda1                             8:1    0   243M  0 part   /boot
&#9500;&#9472;sda2                             8:2    0     1K  0 part   
&#9492;&#9472;sda5                             8:5    0 139.5G  0 part   
  &#9500;&#9472;uberserver--vg-root (dm-1)   252:1    0   132G  0 lvm    /
  &#9492;&#9472;uberserver--vg-swap_1 (dm-2) 252:2    0   7.5G  0 lvm    [SWAP]
sdb                                8:16   0 279.5G  0 disk   
&#9492;&#9472;sdb1                             8:17   0 279.5G  0 part   /media/wd300gb
sdc                                8:32   0 931.5G  0 disk   
&#9492;&#9472;nvidia_cgcdfabe (dm-0)         252:0    0 931.5G  0 dmraid 
sdd                                8:48   0 931.5G  0 disk   
&#9492;&#9472;nvidia_cgcdfabe (dm-0)         252:0    0 931.5G  0 dmraid 
sde                                8:64   0   2.7T  0 disk   
&#9492;&#9472;sde1                             8:65   0   2.7T  0 part   /media/wd3tb
sdf                                8:80   1  28.9G  0 disk   
&#9492;&#9472;sdf1                             8:81   1  28.9G  0 part   
sr0                               11:0    1  1024M  0 rom    


scott@uberserver:~$ sudo fdisk -l
[sudo] password for scott: 


Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b185


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      499711      248832   83  Linux
/dev/sda2          501758   293046271   146272257    5  Extended
/dev/sda5          501760   293046271   146272256   8e  Linux LVM


Disk /dev/sdb: 300.1 GB, 300069052416 bytes
81 heads, 63 sectors/track, 114848 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026759


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   586072367   293035160   83  Linux


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
81 heads, 63 sectors/track, 382818 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063b6b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953525167   976761560   fd  Linux raid autodetect


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
81 heads, 63 sectors/track, 382818 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56378eba


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953525167   976761560   fd  Linux raid autodetect


WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Note: sector size is 4096 (not 512)


Disk /dev/sde: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1   732566644  2930266576   ee  GPT


Disk /dev/sdf: 31.0 GB, 30967529472 bytes
255 heads, 63 sectors/track, 3764 cylinders, total 60483456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061a34


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          63    60483455    30241696+   c  W95 FAT32 (LBA)


Disk /dev/mapper/nvidia_cgcdfabe: 1000.2 GB, 1000204884992 bytes
81 heads, 63 sectors/track, 382818 cylinders, total 1953525166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063b6b


                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_cgcdfabe1            2048  1953525167   976761560   fd  Linux raid autodetect


Disk /dev/mapper/uberserver--vg-root: 141.8 GB, 141775863808 bytes
255 heads, 63 sectors/track, 17236 cylinders, total 276905984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/uberserver--vg-root doesn't contain a valid partition table


Disk /dev/mapper/uberserver--vg-swap_1: 8002 MB, 8002732032 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/uberserver--vg-swap_1 doesn't contain a valid partition table



```

What can be done?

---

### Post by TheFu on 2014-11-10
Did you use fakeRAID, softwareRAID or a real RAID controller, like an LSI?

BTW - it is always smarter to make a backup **before** doing system updates/upgrades.  "**before**" being the keyword here.

---

### Post by Scott_Hamilton on 2014-11-10
Heh, ya... I thought I had been backing it up, but... turns out my little script wasn't doing what I thought it was.

I've never used fakeRAID, however... long while back I had used the drives in a box with an nvidia raid controller.  For some reason Ubuntu 12 did not seem to care, but the upgrade to 14 somehow took note.

After reading more pages on linux raid restoration than I ever thought I would have to, I found the solution (at least that helped me): force the drives to forget about the nvidia raid:

dmraid -r -E /dev/sdX
See [http://ubuntuforums.org/showthread.php?t=1600014](http://ubuntuforums.org/showthread.php?t=1600014) for the thread that helped me out.

Once I did this, suddenly my RAID drive partitions were back and after a reboot, so was my /dev/md0.  All data on the RAID was there and my wife (whose pictures I was danger of losing) stopped giving me threatening looks.

And yes... I'm fixing that backup problem!

---

