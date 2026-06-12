---
title: "access windows files w/ gparted"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by stum22 on 2012-07-22
Hi,

I was following this manual [http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu) but cant seem to mount the windows files.

```
stum@stum:~$ sudo -s
[sudo] password for stum: 
root@stum:~# mkdir /mnt/windows
root@stum:~# mount -t ntfs /dev/sda2 /mnt/windows -o "unmask=022"
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

I have /sda2 extended, sda5 ext4 and sda6 linux swap.

Thanks, Stu

---

### Post by richpri on 2012-07-22
Try 

mount -t ntfs /dev/sda2 /mnt/windows -o "umask=022"

that's umask not unmask

---

### Post by stum22 on 2012-07-22
Doesn't seem to have changed:

```
 root@stum:~# mount -t ntfs /dev/sda2 /mnt/windows -o "umask=022"
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

---

### Post by NikTh on 2012-07-23
Hi ,
open a terminal and post the results of these commands 

```
sudo fdisk -l
sudo parted -l 
``` 

And if  you want (_with Risk to lose your data_) you can try to repair Ntfs partition with fsck tool. 

Thanks

---

### Post by stum22 on 2012-07-23
```
stum@stum:~$ sudo fdisk -l
[sudo] password for stum: 

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x814a3d33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   171069401    85534669+   7  HPFS/NTFS/exFAT
/dev/sda2       171069438   250068991    39499777    5  Extended
/dev/sda5       171069440   241963007    35446784   83  Linux
/dev/sda6       241965056   250068991     4051968   82  Linux swap / Solaris
stum@stum:~$ sudo parted -l
Model: ATA SAMSUNG SSD PM81 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  87.6GB  87.6GB  primary   ntfs            boot
 2      87.6GB  128GB   40.4GB  extended
 5      87.6GB  124GB   36.3GB  logical   ext4
 6      124GB   128GB   4149MB  logical   linux-swap(v1)

```

Thanks

---

### Post by NikTh on 2012-07-23
Hi  , 
as you can see  /dev/sda2 its an Extended partition. So you cannot mount an extended partition.
An Extended partition has no file-system , its just contains logical partitions. 

[B]Your windows partition is /dev/sda1 
[/B]
Thanks

---

### Post by stum22 on 2012-07-23
Great, fixed! And I've even mounted it on my desktop. 

Thanks!

---

