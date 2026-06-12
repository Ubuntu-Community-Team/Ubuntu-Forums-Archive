---
title: "[SOLVED] Can not mount eSata Drive"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by VTT Alps on 2008-11-30
My 500Gb eSata drive was working ok,  now it will not mount.   I mostly use this drive for my Music and Pictures.   It would mount automatically every time I booted.    Normally,  I use Rhythm Box, but today, I went to AmRock,  after a few minutes, the disk unmounted by itself,  and has been off line ever since.  

This is what I get when I try to mount the Drive

sudo mount /dev/sda
mount: mount point /media/disk does not exist


 sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table


This is the line from my Fstab File

/dev/sda /media/disk ext2 rw,nosuid,nodev,uhelper=hal 0 0


I used mkfs to reformat the disk,  and check for bad blocks.  It looked like it worked, but,  I still can not mount it.  

I don't know what else to do.  Does anyone have an Idea.  

Thanks.

---

### Post by taurus on 2008-11-30
You need to create a partition, **/dev/sda1**, and format it to ext3 before you can use it.  You can do that from a terminal or use gparted in System -> Administration.  Install it if you don't already have it on your machine.

---

### Post by VTT Alps on 2008-11-30
gparted worked.  I can now mount the drive by hand with sudo mount.  However,  it doesn't start automatically at boot up.   How can I make that happen.  Do I need to put another line in the fstab file.   If yes,  should it look like like  

/dev/sda1 /media/disk ext2 rw,nosuid,nodev,uhelper=hal 0 0

or something different.   

Thanks

---

### Post by taurus on 2008-11-30
Personally, I would add an entry in /etc/fstab for /dev/sda1 as

```
/dev/sda1   /media/sda1   ext2   defaults   0   2
```
Save it and then create a new mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
```
Now, if you want to be able to write to it without using sudo or gksudo, then you need to change the ownership of /media/sda1 from root to your login name, assuming it's alps.

```
sudo chown -R alps:alps /media/sda1
ls -la /media
```

---

### Post by VTT Alps on 2008-11-30
That worked,  The Drive now mounts during boot.   Thanks A Lot.

---

