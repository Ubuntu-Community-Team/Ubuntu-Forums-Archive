---
title: "[SOLVED] how do I mount external devices?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by slymi2005 on 2008-06-05
I'm trying to mount my mp3 player here is my sudo fdisk -l:

```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001da31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         893     7172991   83  Linux
/dev/sda2             894        2434    12378082+  83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1841 MB, 1841299456 bytes
1 heads, 62 sectors/track, 14501 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.
Note: sector size is 2048 (not 512)

Disk /dev/sdb1: 2199.0 GB, 2199023253504 bytes
1 heads, 62 sectors/track, 17318416 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.
```

I am trying to mount /dev/sdb1, I think, but I don't know the proper way to enter that into the terminal I think it's sudo mount something but I don't know for sure. If anyone can help that would be great.

---

### Post by Raccoon1400 on 2008-06-05
sudo mount -t filesystem type /dev/sdx /path/to/mountpoint

---

### Post by slymi2005 on 2008-06-05
Would you by any chance be able to give me a command that would mount the /dev/sdb1 ?

---

### Post by Raccoon1400 on 2008-06-05
> **slymi2005 said:**
> Would you by any chance be able to give me a command that would mount the /dev/sdb1 ?
What's the file system type?

mount -t filesystemtype /dev/sdb1 /media/disk

you may need to 
mkdir /media/disk first

---

### Post by slymi2005 on 2008-06-06
How do I find out the file system type?

---

### Post by zaviera on 2008-06-06
the filesystem that your mp3 show in system when you run fdisk -l
according to the system information when you run fdisk the filesystem is BBT.

---

### Post by Victormd on 2008-06-06
What is your mp3 player and how is the USB connection on it set up as? MTP or MSC? It might not be as simple as mounting your mp3 player, you might have to change the USB mode before you mount.

---

### Post by slymi2005 on 2008-06-06
I tried bbt but all i get is this

```
sudo mount -t bbt /dev/sdb1 /media/disk
mount: unknown filesystem type 'bbt'

```

any ideas?

---

### Post by slymi2005 on 2008-06-06
Victor it is a sony walkman nwz-s615f, its usb 1.01 but I don't know if it is mtp or msc, how would I go about finding out? The mp3 player no longer shows up in the media section and I don't know how to change the usb mode. Any ideas?

---

### Post by Victormd on 2008-06-06
Generally, you choose the USB mode on the device under settings but I'm not sure how that works with sony mp3 players. What you can try is to mount (manually) using pmount

Connect your mp3 player (does not need to mount) and type:
```
ls /dev/disk/by-label -lah
```
and this will list your usb devices. You should have at least one line like this:
> lrwxrwxrwx 1 root root 10 2008-06-06 10:32 WALKMAN -> ../../sdb1
(In this example, the ID is ***sdb1***
To mount the player, you can try:
```
pmount /dev/<device ID> Walkman
```
and this will create a directory in /media and mount the device there...
To unmount your mp3, use:
```
pumount Walkman
```
Let me know how this works...

---

### Post by slymi2005 on 2008-06-13
Thank you so much! Sorry it's been so long but I finally tried it and I had to install pmount (sudo apt-get install pmount) and then all I did was pmount /dev/sdb1 WALKMAN

---

