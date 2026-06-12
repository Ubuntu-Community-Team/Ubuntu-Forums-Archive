---
title: "How do I access a newly formatted HDD partition with GUI?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Ethereal PanMan on 2008-10-06
I followed these directions to create and mount a partition of my HDD that was previously used for windows:

[http://www.techotopia.com/index.php/Allocating_a_Windows_Partition_to_Ubuntu_Linux](http://www.techotopia.com/index.php/Allocating_a_Windows_Partition_to_Ubuntu_Linux)

But I would like to have access to it on the desktop.  What do I need to do?  I feel a bit lost right now.

Cheers!

---

### Post by jerome1232 on 2008-10-06
Well if you followed that guide to the letter, it's mounted at /vol1

so to browse to that using nautilus, just click places->computer->filesystem->vol1 and your in it.

btw the 'normal' place to mount drives at is under /mnt/namehere, if you want an icon on your desktop then put it at /media/namehere

---

### Post by Ethereal PanMan on 2008-10-06
So is there no way I can move my partition (named Xerxes, in honor of the 2nd greatest game of all time)?  

Can I unmount and then remount to the location specified?

Cheers!

---

### Post by jerome1232 on 2008-10-06
you certainly can!

You will have to adjust these commands to suite your circumstance
(if you were dealing with /dev/sda2 before then subsitute /dev/sdx# for /dev/sda2, and of course change /newplace/tomount to the location you want to mount at
to unmount from the command line:

```
sudo umount /dev/sdx#
## then to remount it
sudo mkdir /newplace/tomount
sudo mount /dev/sdx# /newplace/tomount
## now if you want it to do this everytime you boot for you redo the fstab section of that guide and change /vol1 to /newplace/tomount
```

---

### Post by Ethereal PanMan on 2008-10-06
Cheers!  It's on the desktop, but it simply tells me the size of the partition.  Is there any way to rename?

Thanks for your help!

---

### Post by jerome1232 on 2008-10-06
It does the name based on the partitions label if there is no label it bases it on partition size. With the version of gparted installed on Ubuntu I haven't bothered to figure out how to change the label.

Hopefully some else knows how to do that. Knowing the file system would help. I'm assuming it's an ntfs partition correct?

---

### Post by jerome1232 on 2008-10-06
Actually I figured it out (command line of course, oh well I like it better than gui's)

this is where I got my info from [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

I'm going to assume ntfs you can consult that link if it's another type

First we need to install the necessary packages:
note it may be possible to do all of this using gparted after installing these programs
```
sudo apt-get install ntfsprogs
```
```
sudo umount /dev/sdx#
sudo ntfslabel /dev/sdax# newlabel
sudo mount -a
```

You may have to do a full reboot for the change to take affect so if the label doesn't change (according to the guide the label is cached) just reboot it should change.


edit: It is possible to do this in gparted once the appropriate programs are installed; (sudo apt-get install gparted; to get it, it's a gui partition editor) You just select the device right click the partition unmount it, then right click the partition again and select label, type in the new label

---

