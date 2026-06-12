---
title: "files just gone from my pictures folder or pictures folder"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by Val87 on 2014-07-31
I backed everything up before installation of ubuntu...
When the install was done i copied my music and docs and the whole lot back to folders.

And all photographs where there for the entire day... now i look and they are gone... all photos are gone...  
Can't find this stuff and folders neither through search or anywhere.
All i know i was playing with themes and had to press Ctrl+H to creat a .themes folder. 

Are they gone? Does anyone know what happened, because backed up paperwork, and music is still there in docs and music folders.

---

### Post by papibe on 2014-07-31
Hi Valeri_Tarassov.

Sorry to hear that.

Here's a few ideas:

In the case they were accidentally moved, try using the command find to go through all your directory:
```
find ~/ -type f -iname '*photo_name*'
```
Where 'photo_name' is part of the name of one of the pictures you had. For instance, 'holiday', or 'girlfriend'. You can also used that common camera naming standard like 'IMG_', or 'DSC'.

It may be possible that the pictures were in another partition and that partition is not being mounted for some reason.

Check current mounted partition:
```
mount -l
```
or
```
df -h
```
versus the partitions available on the system:
```
sudo fdisk -l
```
Hope these ideas help. Let us know how it goes.
Regards.

---

### Post by Val87 on 2014-07-31
df -h

[ATTACH=CONFIG]255179[/ATTACH]

sudo fdisk -l

[ATTACH=CONFIG]255180[/ATTACH]

The section Private... as the drive is encrypted i would assume, i have to enter the encryption key before i even get to login. 
But i don't understand any of this ... :( 

As to look for a file name:

[ATTACH=CONFIG]255181[/ATTACH]

Its not like it is lifethreatening ... but if this happened, the work can go, college work... and the music ...

---

### Post by tgalati4 on 2014-08-01
Perhaps it is a permissions problem?  Log into a root terminal and look around.

```
sudo su
```

Otherwise install *testdisk* and run a check for a busted file table.

Is the entire drive encrypted or just a few folders?

Were you root user when you copied the files back into your new distro?

---

### Post by mastablasta on 2014-08-01
seems like partition table is messed up or somehow locked. not sure what encryption does as I do not use it. it seems mostly it causes problem. :) at least when using it one should have some propper backups elsewhere.

[http://askubuntu.com/questions/366749/enable-disk-encryption-after-installation](http://askubuntu.com/questions/366749/enable-disk-encryption-after-installation)
in case you did some parittions resizing: [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

the control+h command only shows hidden files (those with the dot in front) and in home folders these are mostly configuration files.

---

### Post by Val87 on 2014-08-01
Well, its the entire drive i think... as i replaced Win 7 with Ubuntu. Then it asked if i wanted to encrypt the drive, i said yes so now i must enter a password before i get to login. :) 
I was logged in, i mean i entered a password on a login...then i just connected an external hard drive copied my folder with stuff on desktop and from ther with Cut option to relevant folders. 
Pictures, Music, Documents and etc... the only thing that went away is Pictures.

Actually, i realised last night that from using Ubuntu 13.04 previously i had a Ubuntu One account where most of the pictures are just lying there, so i got the U1 Downloader and it is downloading as we speak. Ill get most of it back, at least. 

But still it did happen... for some reason.

---

### Post by tgalati4 on 2014-08-01
If you disconnected the external drive before the copy was finished, then that could cause a problem.  The dialog notification of copying files does not always match reality.  I presume you copied the pictures last.  Using the cut operation is risky because you want to make sure your data is safely copied over before it is removed.  You want to properly "eject" or "unmount" any external drive before removing it in Linux--otherwise bad things can happen.

---

