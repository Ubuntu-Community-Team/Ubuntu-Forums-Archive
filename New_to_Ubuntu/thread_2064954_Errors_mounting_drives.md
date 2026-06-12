---
title: "Errors mounting drives"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by gilestelnarbe on 2012-09-30
Hi guys
I'm dual booting Win7-64b with Ubuntu 11.10 . my win7 crushed and I made a fresh installation but by mistake I forgot that my boot loader data are saved in Win7's drive so I deleted them. then I fixed it using Boot Repair. Now I have an error when I boot ubuntu that the drive Win7 has problem mounting. wait ?or skip blah blah blah.
I guess during this fresh installation and boot repairing some data of Grub is changed. 
how can I fix this problem.
btw I have encountered the same error before on a netbook about its Linux Swap drive.
any chance I can fix this errors?

---

### Post by NikTh on 2012-09-30
Hi , 
Open a terminal [Ctrl]+[Alt]+[t] and post the output of these 2 commands 

```
sudo blkid 
cat /etc/fstab
``` 

Thanks

---

### Post by gilestelnarbe on 2012-09-30
sudo blkid
[sudo] password for gilestel: 
/dev/sda1: LABEL="System Reserved" UUID="F0DC1907DC18C9AC" TYPE="ntfs" 
/dev/sda2: UUID="82DC227CDC226B1D" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="20447BE6447BBD5A" TYPE="ntfs" 
/dev/sda6: UUID="d4f97545-2f1a-42d6-be4c-5984d3d8cf67" TYPE="swap" 
/dev/sda7: UUID="3e7a91ef-f46d-4769-a885-a69515987d10" TYPE="ext4" 
/dev/sda8: UUID="c16e76a1-f4e5-47ab-a233-6f5b70fe7f37" TYPE="swap"



cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda7 :
UUID=3e7a91ef-f46d-4769-a885-a69515987d10	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=20447BE6447BBD5A	/media/Data	ntfs-3g	defaults,locale=en_US.UTF-8	00
#Entry for /dev/sda1 :
UUID=F0DC1907DC18C9AC	/media/System_Reserved	ntfs-3g	defaults,noauto,locale=en_US.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=6CCE27A6CE276792	/media/Win7_64b	ntfs-3g	defaults,locale=en_US.UTF-8	00
#Entry for /dev/sda8 :
UUID=c16e76a1-f4e5-47ab-a233-6f5b70fe7f37	none	swap	sw	0	0
#Entry for /dev/sda6 :
UUID=d4f97545-2f1a-42d6-be4c-5984d3d8cf67	none	swap	sw	0	0

#/dev/sda5	/media/Data	ntfs-3g	users,noauto	0	0
#/dev/sda5	/media/sda5	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sdXn /mnt/usb auto rw,user,noauto 0 0

---

### Post by ajgreeny on 2012-09-30
I think the problem is that the UUID for the win7 partition in fstab is now incorrect and the current
```
#Entry for /dev/sda2 :
UUID=6CCE27A6CE276792	/media/Win7_64b	ntfs-3g	defaults,locale=en_US.UTF-8	00
```
needs to be edited and changed to 
```
#Entry for /dev/sda2 :
UUID=82DC227CDC226B1D	/media/Win7_64b	ntfs-3g	defaults,locale=en_US.UTF-8	00
```

---

### Post by Bashing-om on 2012-09-30
gilestelnarbe; Hi !

While awaiting NikTh's return ...there are two points to be addressed in your fstab.
1. sda2: the uuid does not agree with blkid's identification.
2. The final line entry "/dev/sdXn/ : in this context is nonsense. X is to represent a drive, the "n" is to represent a partition. (ie sdb3).

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Verify the uuid by comparing both outputs of:
```
sudo blkid
ls -l /dev/disk/by-uuid/

```now make a backup copy of fstab (murphie's law always applies)
```
cp /etc/fstab /etc/fstab.bak
```edit fstab to correct it for mounting as you want it.
```
gksudo gedit /etc/fstab
```insert the correct uuid for sda2 and delete the invalid last line(/dev/sdXn)

now save the edited file, exit gedit and reboot ...see what grub does at this time.[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by gilestelnarbe on 2012-10-01
thanks
I will mark this as solved but still I feel that my fstab is not normal.
btw why I dont have a sda4 ?
there is a warning in Disk Utility. the logical drive containing sda 5-8 (an ntfs for data, Linux Swaps and ext).
"The partition is misaligned by 1024 bytes. This may result in very poor performance. Repartitioning is suggested."
any idea what it means?

---

### Post by NikTh on 2012-10-01
> **gilestelnarbe said:**
> 
"The partition is misaligned by 1024 bytes. This may result in very poor performance. Repartitioning is suggested."
any idea what it means?

Hi , 

this is probably a tool mistake - bug. Ignore it. 

I assume you have an extended partition . Give the results of these commands 

```
sudo fdisk -l 
sudo parted -l
```

Also I can see that you have 2 swaps . Why ? 

and this entry ```
 /dev/sdXn /mnt/usb auto rw,user,noauto 0 0
``` 
what is this ?
Thanks

---

### Post by gilestelnarbe on 2012-10-01
FDISK:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe3ce42bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   209111039   104452096    7  HPFS/NTFS/exFAT
/dev/sda3       209113086  1953521663   872204289    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5       516313088  1953521663   718604288    7  HPFS/NTFS/exFAT
/dev/sda6       508137472   516313087     4087808   82  Linux swap / Solaris
/dev/sda7       209113088   499957759   145422336   83  Linux
/dev/sda8       499959808   508135423     4087808   82  Linux swap / Solaris

Partition table entries are not in disk order
```


PARTED

```
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   107GB   107GB   primary   ntfs
 3      107GB   1000GB  893GB   extended                  lba
 7      107GB   256GB   149GB   logical   ext4
 8      256GB   260GB   4186MB  logical   linux-swap(v1)
 6      260GB   264GB   4186MB  logical   linux-swap(v1)
 5      264GB   1000GB  736GB   logical   ntfs
```
 
the last line I deleted. I dont know what it is.
I actually dont know what swap drives are let alone why there are 2 of them!

---

### Post by NikTh on 2012-10-01
> **gilestelnarbe said:**
> FDISK:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe3ce42bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   209111039   104452096    7  HPFS/NTFS/exFAT
/dev/sda3       209113086  1953521663   872204289    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5       516313088  1953521663   718604288    7  HPFS/NTFS/exFAT
/dev/sda6       508137472   516313087     4087808   82  Linux swap / Solaris
/dev/sda7       209113088   499957759   145422336   83  Linux
/dev/sda8       499959808   508135423     4087808   82  Linux swap / Solaris

Partition table entries are not in disk order
```PARTED

```
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   107GB   107GB   primary   ntfs
 3      107GB   1000GB  893GB   extended                  lba
 7      107GB   256GB   149GB   logical   ext4
 8      256GB   260GB   4186MB  logical   linux-swap(v1)
 6      260GB   264GB   4186MB  logical   linux-swap(v1)
 5      264GB   1000GB  736GB   logical   ntfs
```the last line I deleted. I dont know what it is.
I actually dont know what swap drives are let alone why there are 2 of them!

Is not necessary  to repartition the drive. This is my opinion. 
Swap drive is the drive that Ubuntu (or you manually) creates for swap memory. 
Swap memory : [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Ignore /dev/sda3 warning of Fdisk. 
You miss a partition so the order is not correct. If you want to correct this , you can do it with fdisk , but I don't know if will has side effects (DATA LOSS). 

If you want to try it 
```
sudo fdisk /dev/sda
```press [x]  (for expert mode) and the press [f] for "fix partition order". 

Nothing will happen if at the end not press the [w] for "write partition table" 

If you decide to repartition the drive , you must backup all of your data first. 

Thanks

---

