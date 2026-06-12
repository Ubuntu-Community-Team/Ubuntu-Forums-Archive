---
title: "Cannot set hidden partition from gparted"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by NikTh on 2012-06-04
Hi , 
Maybe i miss something  , but why can't set hidden partition from gparted ? 
My installations are triple boot with Ubuntu 12.04 , Lubuntu 12.04 , Bohdi linux 2.0.0(alpha) . 
Gparted hidden function does not work , with all OS's I've tested. 
I know the trick with fstab that i can mount a partition to another place (except /media ) to hide it from nautilus , but gparted way is easier . 
What did i miss ? maybe a package ? or something else ? 
I can set any other flags (eg boot) . 

Here a little info about my partitions 

**sudo fdisk -l **
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001f627

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4094   287031295   143513601    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sda2       613308416   625141759     5916672   82  Linux swap / Solaris
/dev/sda3       287031296   489975807   101472256   83  Linux
/dev/sda4       489975808   613308415    61666304   83  Linux
/dev/sda5            4096   206665727   103330816   83  Linux
/dev/sda6       206667776   210929663     2130944   83  Linux
/dev/sda7       210931712   287031295    38049792   83  Linux

Partition table entries are not in disk order
```**sudo parted -l **
```
Model: ATA WDC WD3200BPVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      2096kB  147GB  147GB   extended
 5      2097kB  106GB  106GB   logical   ext4
 6      106GB   108GB  2182MB  logical   ext4
 7      108GB   147GB  39.0GB  logical   ext4
 3      147GB   251GB  104GB   primary   ext4
 4      251GB   314GB  63.1GB  primary   ext4
 2      314GB   320GB  6059MB  primary   linux-swap(v1)
```**Extra info :  **In another pc with ntfs partitions i can hide ntfs but still i cannot hide linux filesystems. 

Thanks

---

### Post by NikTh on 2012-06-05
Someone ? 
an idea , something ? 
Can you set hidden flag with gparted and hide (from nautilus)  a specific partition(linux filesystem) ? 
Here is my fstab(if that helps) , i think its clean 

**cat /etc/fstab**
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
#/ was on /dev/sda3 during installation
UUID=5004f11e-3752-4015-b392-9b9905ae4828 /               ext4    noatime,errors=remount-ro     0       1
# swap was on /dev/sda2 during installation
UUID=4d729f83-b4b3-4e8c-a334-370d563173a1 none            swap    sw                            0       0

```

---

### Post by wilee-nilee on 2012-06-05
Does not work here from 12.10, I wonder if a older version or booting from a live gparted cd might work.

I tried a live gparted 10 no different there.

---

### Post by NikTh on 2012-06-05
I don't know if something conflicts with gparted . In my Lubuntu and Bodhi linux(Ubuntu 12.04 - based) installations i didn't have gparted. I install it and the same thing happened. Unable to set hidden flag. 
I also tried from an Ubuntu 11.10 , same thing. 
I cannot configure what is wrong cause no error messages appeared . It just don't mark the flag. 

I will test it with two other live usb's i have. Linux mint 13 and Ubuntu 10.04 .

**Edit:** Nop , nothing . Neither Ubuntu 10.04 or Linux Mint 13 , neither Arch Linux (on another desktop). 

Is this option available only for ntfs partitions or maybe the reason is that i have not separate /home ? 
Haha , i don't know what to think about this...

---

### Post by NikTh on 2012-06-06
Is anyone able to set correctly the hidden flag ?

---

### Post by NikTh on 2012-06-08
Again : Is anyone able to set the hidden flag ? (correctly) 
Just try it and give an answer please. 
Thanks

---

### Post by NikTh on 2012-06-12
Ok , found it . 
Here is the answer in Launchpad (same question there). --> [https://answers.launchpad.net/ubuntu/+source/gparted/+question/199563](https://answers.launchpad.net/ubuntu/+source/gparted/+question/199563)
Gredits goes to [Filippos Kolyvas (fkol-k4)]("https://launchpad.net/%7Efkol-k4") 
Thanks.

---

