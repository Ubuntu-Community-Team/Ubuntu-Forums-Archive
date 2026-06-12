---
title: "reformat,, non used storage drive for EXT3"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by hvac3901 on 2008-07-01
OOPPSSS well, i am really pissed, but its my fault, i installed Hardy on the wrong drive to my desktop. 

So i lost a ton of files, but anyway, what do i do to reformat that other drive with 7.10 Gutsy on it for EXT3 under Heron??? or at least to ditch all the old OS from the drive.

---

### Post by Inxsible on 2008-07-01
I am not sure if I understand correctly..but if you already have Gutsy on that drive..all you have to do is start update-manager and hit upgrade OS. That will get you Hardy.

---

### Post by sayakb on 2008-07-01
Please provide the output of:
```
sudo fdisk -l
```

Also, to reformat a drive, you can use gparted:
```
sudo apt-get install gparted
```
Then goto System->Administration->Partition Editor
Click on the appropriate partition and select Format option.

---

### Post by kuja on 2008-07-01
Well, what I would do is first determine the name of the drive (ie: /dev/sdb if the drive has no partition table, /dev/sdb1 if it is partitioned and has a partition table... we'll use that for the rest of the example)

Then, ```
sudo mkfs.ext3 /dev/sdb
``` assuming there is no partition table on the disk, if there is  partition tablee you'll use /dev/sdb1 instead.

Then, to set up automounting.

```
sudo mkdir /media/otherdrive
```
Then open the file /etc/fstab in an editor as root (ie: kdesudo kate /etc/fstab OR gksudo gedit /etc/fstab) and add the following line:

```
/dev/sdb /media/otherdrive ext3 relatime 0 2
``` (again, substituting the /dev/sdb part as necessary)

From there you ```
sudo mount /media/otherdrive
``` and you should be good to go.

---

### Post by bumanie on 2008-07-01
> **hvac3901 said:**
> OOPPSSS well, i am really pissed, but its my fault, i installed Hardy on the wrong drive to my desktop. 

So i lost a ton of files, but anyway, what do i do to reformat that other drive with 7.10 Gutsy on it for EXT3 under Heron??? or at least to ditch all the old OS from the drive.

Unfortunate. You could try to recover things with testdisk, photorec, foremost or use sleuthkit (and its gui autopsy). If you haven't written anything else to the drive, you may be lucky and get most, if not all your stuff back and then you can try the hardy reinstall again to the correct drive/partition.

---

### Post by hvac3901 on 2008-07-01
damn see there i go again, maybe i should tie a ribbon around my finger to remind me not to do this. Poor information given to helpful folks. 

Two drives;
oroiginal 40 Gb had 7.1
other 80 Gb had my files carried over from Windows,

when i upgraded desktop to heron, i put it on the 80 Gb, The forty Gb has th Gutsy install on it. would like to wipe it clean and use the 40 Gb for storage of stuff.

---

### Post by Inxsible on 2008-07-01
```
sudo apt-get install gparted
``` Start GParted and then simply format the 40GB drive to whatever filesystem you want eg. EXT3 or NTFS

and you can then create one or more partitions on it and then mount them.

---

