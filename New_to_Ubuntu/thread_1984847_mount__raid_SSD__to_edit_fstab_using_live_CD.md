---
title: "mount  raid SSD  to edit fstab using live CD"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by tvor on 2012-05-22
Hi, I've made a mistake in fstab file on my ubuntu  and now it's giving me an error message upon restart(failed to load (isw_igbgbjgff_Volume0p6).This error is blocking me from starting ubuntu. I can fix the fstab, but I'm so far unable to mount it using live CD. How do I mount /dev/mapper/isw_igbgbjgff_Volume0p5 (this is where ubuntu and /fstab is) from live CD? 

The HD is 2x 128Gb RAID SSD with dual boot Windows. I have also attached sceenshot from Gparted - shows the partitions (first three are windows) then linux and shared data on ntfs.  Any help in this issue will be very helpful:P

Output of sudo fdisk -l in live CD is
> Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc072c294

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24393727    12195840   27  Hidden NTFS WinRE
/dev/sda2   *    24393728    24598527      102400    7  HPFS/NTFS/exFAT
/dev/sda3        24598528   142769654    59085563+   7  HPFS/NTFS/exFAT
/dev/sda4       142769662   490361343   173795841    f  W95 Ext'd (LBA)

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34e434e4

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/isw_igbgbjgff_Volume0: 256.1 GB, 256066715648 bytes
255 heads, 63 sectors/track, 31131 cylinders, total 500130304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0xc072c294

                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_igbgbjgff_Volume0p1            2048    24393727    12195840   27  Hidden NTFS WinRE
/dev/mapper/isw_igbgbjgff_Volume0p2   *    24393728    24598527      102400    7  HPFS/NTFS/exFAT
/dev/mapper/isw_igbgbjgff_Volume0p3        24598528   142769654    59085563+   7  HPFS/NTFS/exFAT
/dev/mapper/isw_igbgbjgff_Volume0p4       142769662   490361343   173795841    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p5       142769664   161853439     9541888   83  Linux
/dev/mapper/isw_igbgbjgff_Volume0p6       161854938   483524369   160834716    7  HPFS/NTFS/exFAT
Partition 6 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p7       483526656   490360831     3417088   82  Linux swap / Solaris

Disk /dev/mapper/isw_igbgbjgff_Volume0p1: 12.5 GB, 12488540160 bytes
255 heads, 63 sectors/track, 1518 cylinders, total 24391680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_igbgbjgff_Volume0p1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p1p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p1p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p1p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_igbgbjgff_Volume0p2: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_igbgbjgff_Volume0p2p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p2p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p2p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p2p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_igbgbjgff_Volume0p3: 60.5 GB, 60503617024 bytes
255 heads, 63 sectors/track, 7355 cylinders, total 118171127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_igbgbjgff_Volume0p3p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p3p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p3p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_igbgbjgff_Volume0p3p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order
fdisk: unable to seek on /dev/mapper/isw_igbgbjgff_Volume0p4: Invalid argument
ubuntu@ubuntu:~$ 



---

### Post by tvor on 2012-05-22
I was able to access fstab from windows (unable to write to ext4 there to fix it) Ubuntu is not loading as it's fails load isw_igbgbjgff_Volume0p6 

This is what was working and loading as DATA partition before > /dev/mapper/isw_igbgbjgff_Volume0p6 /media/DATA ntfs-3g user,nosuid,exec,nodev  0  0
and then I tried to "improve" the ability to mount with the recycling bin option etc. this :
> UUID 44A29E6C083ACF12 /media/DATA ntfs-3g defaults,auto,uid=1000,windows_names,umask=000 0 0
that failed the boot. Any I idea why it the UUID mount does not work and mainly how do I write to fstab now ? Thank you

---

### Post by tvor on 2012-05-22
This is a code which comes when booting into ubuntu now :
> mount: unknown filesystem type /media/data
montall: mount 44XXXXXXXXX12[673] terminated with status 32
mountall: filesystem counld not be mounted : 44XXXXXXXXX12
fsck from util-linux 2.20.1
swapon: /dev/mapper/isw_igbgbjgff_Volume0p6 [803] terminated with status 255
mountall: Problem activatin swap: /dev/mapper/isw_igbgbjgff_Volume0p6

---

### Post by steeldriver on 2012-05-22
shouldn't that be 

```
UUID**=**44A29E6C083ACF12 /media/data ... 
```(with the space after UUID it is parsing UUID as the block device, 44A29E6C083ACF12 as the mount point, and /media/data as the fstype - the clue is in the error message...)

---

### Post by tvor on 2012-05-22
thank you > You are right my fstab DOES have a space between UUID and the number! This could work and i'll try to modify it, however still not sure how to mount the partition using live CD to modify the fstab ...

---

### Post by tvor on 2012-05-23
live CD gives me this:
> sudo mount /dev/mapper/isw_igbgbjgff_Volume0p5 
mount: can't find /dev/mapper/isw_igbgbjgff_Volume0p5 in /etc/fstab or /etc/mtab

same goes for /dev/mapper/isw_igbgbjgff_Volume0p4 how do I mount from live CD to modify fstab?

---

### Post by tvor on 2012-05-23
Ok, solved! :-)Inspiration [from here ]("http://ubuntuforums.org/showthread.php?t=1967683&highlight=unable+mount")
The way to go was:
[LIST]to boot live CD
[/LIST][LIST]
[*]edit the fstab (yes the live CD fstab!) and save
[/LIST][LIST]
[*]then sudo mount partition (this time it worked)
[/LIST]
[LIST]
[*]find the partition where it was mounted
[/LIST]
[LIST]
[*]run sudo gedit > in this editor find /etc/fstab on the mounted partition > modify(fix) and save
[/LIST]
[LIST]
[*]reboot to normal ubuntu
[/LIST]
I'm sure there are more efficient ways to get there, the key which i did know know to modify virtual (live CD fstab) before mounting partition. Now we know :-D thanks all for help

---

