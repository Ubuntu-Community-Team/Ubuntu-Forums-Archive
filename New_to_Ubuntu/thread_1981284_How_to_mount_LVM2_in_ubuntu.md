---
title: "How to mount LVM2 in ubuntu"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by sbyrdsell on 2012-05-16
I have tried to mount using step
1) apt-get install lvm2
2) fdisk -lu
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c273d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   487894049   243946993+  8e  Linux LVM
/dev/sda2       487894050   488392064      249007+   f  W95 Ext'd (LBA)
/dev/sda5       487894113   488392064      248976   83  Linux

3) pvscan
 PV /dev/sda1   VG ds-national   lvm2 [232.64 GiB / 4.00 MiB free]
  Total: 1 [232.64 GiB] / in use: 1 [232.64 GiB] / in no VG: 0 [0   ]

4) vgscan
Reading all physical volumes.  This may take a while...
  Found volume group "ds-national" using metadata type lvm2

5) vgchange -a y
 2 logical volume(s) in volume group "ds-national" now active

6) lvscan
ACTIVE            '/dev/ds-national/root' [223.18 GiB] inherit
  ACTIVE            '/dev/ds-national/swap_1' [9.46 GiB] inherit

7) mount  /dev/ds-national/root /mnt/root
mount: you must specify the filesystem type

I have tried and tried tips over the net and nothing works can you help me please

---

### Post by cmont899 on 2012-05-16
You can specify type with -t, maybe:

```
mount -t ext4  /dev/ds-national/root /mnt/root
```

or

```
mount -t ext3  /dev/ds-national/root /mnt/root
```

---

### Post by sbyrdsell on 2012-05-22
mount -t ext3  /dev/ds-national/root /mnt/root
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ds--national-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

&

mount -t ext4  /dev/ds-national/root /mnt/root
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ds--national-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I don't why it want mount!!!!! :(

---

### Post by steeldriver on 2012-05-22
the way it worked for me is to grab the aliases from /dev/mapper:

```
$ ls /dev/mapper
control  raid--lvm-lvm0  raid--lvm-lvm1
``````
$ mount |grep mapper
/dev/mapper/raid--lvm-lvm1 on /storage/mythtv type xfs (rw)
/dev/mapper/raid--lvm-lvm0 on /home type ext4 (rw,errors=remount-ro,commit=0)

```

DISCLAIMER: I don't know if that is the 'correct' way to do it

---

### Post by zeukiki on 2012-05-23
Hi,
Why I read the commands you made, I don't see the format command ?
Do you format your partitions ?
When I 've made my lvm partitions (over RAID5), I installed a usefull GUI lvm soft, that may help you ...
```
sudo apt-get install system-config-lvm
```
Maybe If you still can't find your problem, you can take screenshot of this soft information...

---

### Post by sbyrdsell on 2012-05-23
Here are the screen shots I hope this help you help me..

Thanks
Stan

---

### Post by zeukiki on 2012-05-23
Hi,
Just one question, have you some datas on your /dev/ds-national/root ?
If not, just format your "/dev/ds-national/root" with :
```
mkfs.ext4 /dev/ds-national/root
```
And then you can mount your partition with 
```
mount  /dev/ds-national/root /mnt/root
```
or force filesystem with 
```
mount  -t ext4 /dev/ds-national/root /mnt/root
```

In your fouth picture you can see that there is "no Filesystem" in front of "File System".

Once you'll make the mfks command above, you will have a "ext4" in "File System" info.

---

### Post by sbyrdsell on 2012-05-23
I have data on this drive what should I try?

---

### Post by zeukiki on 2012-05-23
:confused:
I don't understand ???
You have never mount this partition and you have Data on it ?
How is it possible ?

---

### Post by zeukiki on 2012-05-23
Ah Ok, 
Looking your pics, I think I understand what you mean.
You have 3 partitions on /dev/sda
/dev/sda1 support yourn lvm partitions.
When you're saying that you have datas on your drive, you mean that you have data on /dev/sda2 and /dev/sda3 ? Am I right ?
If this is it, you can do the command that I told you, you will keep your data on the others partitions.

---

### Post by sbyrdsell on 2012-05-23
I have 2 drives in this server the one I'm trying to mont had Ubuntu 10.1 with a software Raid on it. I could not upgrade to Ubuntu 11 so I installed Ubuntu 11 on the 2 drive.  And when I tried to munt the 1 drive with LVM2 on it, it would not mount.

---

### Post by steeldriver on 2012-05-23
you should be able to find the existing LVM fs type using

```
sudo file -s /dev/dm-*

```or 
```
sudo file -Ls /dev/mapper/*

```if you want to go via the mapper symlinks

then modify your mount command accordingly

---

### Post by sbyrdsell on 2012-05-23
Hi, 
I changed the file type to ext2 in the GUI Tool and it mounted but I think I lost my data because all I see one folder that say Lost&Found :-( is there any thing I can do now?

file -s /dev/dm-*
/dev/dm-0: Linux rev 1.0 ext2 filesystem data (mounted or unclean), UUID=f07c914e-1226-4e26-be0c-96e5cfc21767 (large files)
/dev/dm-1: Linux/i386 swap file (new style), version 1 (4K pages), size 2481151 pages, no label, UUID=00000000-0000-0000-0000-000000000000

file -Ls /dev/mapper/*
/dev/mapper/control:             ERROR: cannot read `/dev/mapper/control' (Invalid argument)
/dev/mapper/ds--national-root:   Linux rev 1.0 ext2 filesystem data (mounted or unclean), UUID=f07c914e-1226-4e26-be0c-96e5cfc21767 (large files)
/dev/mapper/ds--national-swap_1: Linux/i386 swap file (new style), version 1 (4K pages), size 2481151 pages, no label, UUID=00000000-0000-0000-0000-000000000000

---

### Post by sbyrdsell on 2012-05-30
Can any one Help ME?

---

