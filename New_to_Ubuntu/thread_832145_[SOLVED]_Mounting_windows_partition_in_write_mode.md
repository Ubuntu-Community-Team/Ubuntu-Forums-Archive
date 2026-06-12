---
title: "[SOLVED] Mounting windows partition in write mode"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by ajinkya_naik on 2008-06-17
I am new to Ubuntu. I have installed Ubuntu 7.04 on my system as a dual-boot with Windows XP SP2 on the other partition. I want to have load the Windows partition in the write mode. Currently, when I open my Places>Computer, it shows the disk and when I select to mount it, it mounts only in the Read mode. 

I searched for this and found that I needed to install the ntfs-3g driver for this to work correctly, and so I did. When I run the driver, the option called Enable Write Support for Internal Device is not available.  

So I tried this : I mounted the partition normally, and then ran sudo nautilus and tried to give root the permission to write. Then there was this error that said :
Couldn't change the permissions of "disk" because it is on a read-only disk

What should I do?

---

### Post by cdtech on 2008-06-17
Try to mount it manually with:
sudo mount /dev/yourdev -o remount,rw

See if that gives you the read/write.

---

### Post by bodhi.zazen on 2008-06-17
Permissions are set at the time of mounting and can be specified in fstab.

See :

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: 
[list=number]
[*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent]
[/list]

---

### Post by Victormd on 2008-06-17
Check my signature... there's a post on the user permissions...

---

