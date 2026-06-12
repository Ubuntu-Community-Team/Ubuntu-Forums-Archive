---
title: "Dual boot"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by davorin104 on 2013-10-25
I have installed win 7 on my PC and i used rufus to make an bootable usb with ubuntu 13.10 (i have used many tools: yumi, sardu) and when i boot ubuntu from the usb and install it (selectiong along side win 7 or other) then restart it to chose winodws 7 or ubuntu to boot i get thise eror error: no such partition. entering rescue mode. grub rescue>_ i tried to use boot repair 100 times on ubuntu but it didnt work so what is the problem hire the bootloader gnu grub 2.0 or how it is called wont show to chose what os i wuld like to run.{removed email}

---

### Post by davorin104 on 2013-10-25
[img]http://shrani.si/f/2i/DO/43090Y7J/brez-naslova.png[/img]

The picture is showing a litle 2 mb space is thise the problem ? And yes i deleted the shrinked partitions for ubuntu.

---

### Post by davorin104 on 2013-10-25
[h=3]ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
16 heads, 63 sectors/track, 1938018 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2d5d2d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953517567   976757760    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500103634432 bytes
16 heads, 63 sectors/track, 969012 cylinders, total 976764911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37cb5ec8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   976760831   488379392    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5bafba07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   625139711   312568832    7  HPFS/NTFS/exFAT

Disk /dev/sdi: 16.1 GB, 16052643840 bytes
255 heads, 63 sectors/track, 1951 cylinders, total 31352820 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a534

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *        2048    31352819    15675386    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 





ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ntfs         boot


Model: JetFlash Transcend 16GB (scsi)
Disk /dev/sdi: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  16.1GB  16.1GB  primary  fat32        boot, lba


ubuntu@ubuntu:~$[/h]

---

### Post by sudodus on 2013-10-25
@davorin

As it is now, there is only one partition in each drive, and it should work well to install Ubuntu. Do you want a dual boot in drive /dev/sda?

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot

```

In that case, use ***gparted*** to shrink the partition /dev/sda1 (and create unallocated space). Remember ***backup*** before editing partitions.

Are the other drives internal or external (USB or eSATA)? Would it be an option to install Ubuntu into one of those?

*Edit*: Sorry, I did not observe that you were two people. I will ask a moderator to make it into two separate threads.

---

### Post by davorin104 on 2013-10-25
I wont sory for typing my problem in your thread but i think your problem is that you must repair mbr. Just run ubuntu from usb try it dont install then go to firefox type in boot repair and open the first or second side where you can se how to use the boot repair go advanced and select repair mbr. Link :[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by davorin104 on 2013-10-25
i already shrinked the 1TB drive 30 gb 1 gb for swap and 29 gb ext4 for ubuntu and when ubuntu install i restart my computer trying to boot but cant i get the error: no such partition. entering rescue mode. grub rescue>_

---

### Post by sudodus on 2013-10-25
@davorin

As it is now, there is only one partition in each drive, and it should  work well to install Ubuntu. Do you want a dual boot in drive /dev/sda?

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot

```

In that case, use ***gparted*** to shrink the partition /dev/sda1 (and create unallocated space). Remember ***backup*** before editing partitions.

Are the other drives internal or external (USB or eSATA)? Would it be an option to install Ubuntu into one of those?

---

### Post by sudodus on 2013-10-25
> **davorin104 said:**
> i already shrinked the 1TB drive 30 gb 1 gb  for swap and 29 gb ext4 for ubuntu and when ubuntu install i restart my  computer trying to boot but cant i get the error: no such partition.  entering rescue mode. grub rescue>_
You need to explain more about your system to make it possible to help in an efficient way:

- computer specs: brand name, model, cpu, ram (size), graphics card/chip, wifi card/chip

- operating system version and flavour of Ubuntu (for example Ubuntu 12.04 LTS 64-bits or Lubuntu 13.10 32-bits

and how you installed it.

---

### Post by fantab on 2013-10-25
Where is Windows installed?
Where do you want to install ubuntu?

You just seem confused. RELAX!

Gives us the info we need and we can walk you through it.

---

### Post by davorin104 on 2013-10-25
Windows and ubuntu are on the same 1TB but difrend locald drives ... instaled ubuntu using usb stick

---

### Post by sudodus on 2013-10-25
Please run ```
**sudo parted -l**
``` again (from the live drive). That will show us the present partitions.

Please also give information about your system (as I asked in post #6)

---

### Post by winters2687 on 2013-10-25
I have put ubuntu with windows xp but now my windows xp only shows admin account and when you click it it just brings me right back to admin account. I like ubuntu but I like windows better and need to know why when I try to reinstall windows my installer doesn't show up at the beginning even when i hit esc and hit my disk drive to start up first. I would really like some help plz.

---

### Post by oldfred on 2013-10-25
Removed email address. Forums will be scanned and then you may get spammed. Also we are a forum where user help users.

Since you have multiple hard drives I might suggest keeping Windows on a Windows drive, but then have Ubuntu on a Ubuntu drive. It also has an advantage of each can boot with its boot loader if you have hard drive issues with the other system. I prefer to have an operating system on every drive as drives will need repairs or may fail and it is a bit more convenient to be able to just boot another drive.

---

