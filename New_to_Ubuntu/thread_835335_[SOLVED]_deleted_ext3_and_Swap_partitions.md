---
title: "[SOLVED] deleted ext3 and Swap partitions"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by rockerphil on 2008-06-20
ok, i don't know why or even how it happened, but when i got on my PC today it was slower than molasis, which is nothing new for a 500 MHz Intel Pentium processor and 128 MB of SD RAM, but it was slower than normal, so i did some poking around, and sure enough somehow my ext3 and Swap partitions got deleted. here is my partition table:



Disk /dev/sda: 7510 MB, 7510164480 bytes
255 heads, 63 sectors/track, 913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000269b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         913     7333641   83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe26ae26a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            3846        4865     8193150   83  Linux
/dev/sdb2               1        3845    30884931    7  HPFS/NTFS

Partition table entries are not in disk order
phil@phil:~$ 


so basically what i'm wanting to know is how can i restore these partitions and what size do i need them to be for my computer to run effeciently? thanx in advance,


Phil

---

### Post by Cypher on 2008-06-20
You have 2 EXT3 partitions, namely /dev/sda1 and /dev/sdb1. You don't have a SWAP partition, that's true..

Please show us the contents of your /etc/fstab file.
```

cat /etc/fstab

```

---

### Post by rockerphil on 2008-06-20
here ya go


phil@phil:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=931371f6-70f4-4d8f-9b4b-d2e44d1d3ec4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=754a70ac-712b-44c9-ba08-bafa7a32b995 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

phil@phil:~$

---

### Post by Miljet on 2008-06-20
I'm not sure what you mean that your EXT3 partition has been deleted. It looks like you have two Linux partitions, both of which are probably EXT3.
One is on sda1 and the other is on sdb1. Are you running two Linux distros?

But you do need a swap partition. It needs to be around 1GB. You can make it either with GParted live or with your live CD. Just as long as the disk you are modifying is not mounted.

---

### Post by rockerphil on 2008-06-20
at one point i did have an install of Damn Small Linux on my second hard drive, but god it was ugly, so i deleted the install and havn't reformatted the partition yet, so that's where the second Linux partition is coming from

---

### Post by Gannon8 on 2008-06-20
> Just as long as the disk you are modifying is not mounted.
Or the partitions you are doing stuff to.

You defiantly need swap if you have that much memory. I recommend puppy linux, but that may leave you with 28mb of ram, so make sure that it doesn't load into ram (or that you have swap)

I got a usb drive with a small swap partition, so when it is plugged in, I can have more memory :)

---

### Post by Cypher on 2008-06-20
OK..now do the following
```

sudo vol_id /dev/sda1
sudo vol_id /dev/sdb1

```
In the output of those two commands look at the ID_FS_UUID field, that should equate to one of the entries in the /etc/fstab file. That is going to tell you what filesystem is getting mounted where.

Looking at your /etc/fstab file, you only have one EXT3 (Linux) partition listed but you show 2 Linux partitions and no SWAP partition. So perhaps the partition /dev/sdb1 should actually be a SWAP partition..

---

### Post by rockerphil on 2008-06-20
ok, come to find out it wasn't my ext3 partition that got deleted, it was my ext2 partition along with my Swap, so i created a new ext2 and Swap partition using the Gparted Live CD, and it's doing a bit better, but i'm still running slow compared to prior to the partitions getting deleted. this is what my partition table looks like now:




phil@phil:~$ sudo fdisk -l
[sudo] password for phil:

Disk /dev/sda: 7510 MB, 7510164480 bytes
255 heads, 63 sectors/track, 913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000269b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         765     6144831   83  Linux
/dev/sda2             766         913     1188810    5  Extended
/dev/sda5             766         913     1188778+  82  Linux swap / Solaris

any ideas? oh, and the both the ext2 and Swap partitions are a little over a GB

---

### Post by louieb on 2008-06-20
use the** free **command to see of swap is being use.
to turn swap on
 ```
sudo swapon /dev/sda5
```try the free command again to see if  swap is on now.

to make it permanent add a swap line to /etc/fstab it should look something like this.

```
/dev/sda5      none            swap    sw                0       0
```

---

### Post by rockerphil on 2008-06-20
> **louieb said:**
> use the** free **command to see of swap is being use.
to turn swap on
 ```
sudo swapon /dev/sda5
```try the free command again to see if  swap is on now.

to make it permanent add a swap line to /etc/fstab it should look something like this.

```
/dev/sda5      none            swap    sw                0       0
```

thanx man, this did it. much appreciated

---

