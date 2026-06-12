---
title: "Change read-only for usb stick"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Djalmahal on 2008-10-31
Hi,

I have this old laptop and I want to install Ibex on it, the CD-Drive is broken and a friend has Ibex and there is this tool to make a usb boot startup disk tool which should work for my old laptop. Now, I also have an old usb stick but it says its read-only file system. I looked things up but preferences>permissions, sudo nautilus, gparted and chown didn;t do anything. All I need to do now is format the stick or change the read-only.

How do I do it?

Andreas

---

### Post by talsemgeest on 2008-11-01
Try installing mount manager. That should let you change permissions.

---

### Post by stephanvaningen on 2008-11-01
First check from which device it gets mounted. Let's suppose sd*[COLOR="Blue"]x[/COLOR]*.
Now unmount the device(s) first (in case it has more than one partition, you'll see sdx1, sdx2, .. unmount them all:
 ```
sudo umount /dev/sd[COLOR="Blue"]x[/COLOR]1
```
Then startup a partionner:
 ```
sudo fdisk /dev/sd[COLOR="Blue"]x[/COLOR]
```
In that program:
[LIST]
[*]Use **d** to delete partitions
[*]When all partitions are deleted, use **n** to create a new partition
[*]Enter **p** for primary partition
[*]Enter **1** for partition number
[*]Press **Enter** (First-cylinder)
[*]Press **Enter** (Last cylinder)
[*]Type **t** to enter a partition type
[*]Enter **b** as partition type (W95 FAT32)
[*]Enter **a** to activate a partition
[*]Now exit the tool using **w** (this writes the new partition table to the device)
[/LIST]
Unmount the device to make sure it is not mounted:
 ```
umount /dev/sd[COLOR="Blue"]x[/COLOR]1
```
Now create a blank file system on it:
 ```
sudo mkfs.vfat /dev/sd[COLOR="Blue"]x[/COLOR]1
```
Now remove the USB memory stick and re-insert it again.

Now your USB stick is guaranteed to be 'clean' so the USB startup-disk creator can easilly use it...

---

