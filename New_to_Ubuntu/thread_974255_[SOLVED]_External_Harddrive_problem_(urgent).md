---
title: "[SOLVED] External Harddrive problem (urgent)"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Periswell on 2008-11-07
hello

this week i got told by my teacher that i was going to have another ict corsework but there is one problem, my computer has run out of space. so i have bought a external hard drive (Desktop harddrive) and plugged it in. ubuntu recognized it but it wont let me write to it in user or root. it wont let me change the permission to read and write, its just stuck on read only. any clues? it is a iomega 500gb desktop hard drive and i am running ubuntu 8.04 (hardy). please help.

-joshua

---

### Post by cariboo on 2008-11-07
Once you have the drive mounted, in a terminal type:

```
sudo chmod -R 777 /media/mountpoint
```

where /media/mountpoint is where you have your ecternal drive mounted

Jim

---

### Post by logos34 on 2008-11-07
run this in a terminal:
> 
sudo chmod -R 755 /media/disk

sudo chown -R username:username /media/disk

(replace 'username' with yours and '/media/disk/' with actual mount point)

See:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(bottom)

---

### Post by halitech on 2008-11-07
if its only going to be used on your linux machine, consider changing it to ext3 so you don't have to worry about ntfs corruption

---

### Post by cmnorton on 2008-11-07
I agree with Halitech. Unless this drive is going back and forth between a Windows and Linux system, and given that at the time of purchase there was no data on it, I would format the drive and put an ext3 file system on it, if you are only going to use it to offload storage. 

If you are going to format the drive with ext3, then you'll need to run fdisk, fsck, and mount the drive. If you need to keep ntfs, you probably should recover the volume on a Windows system.

Here are some interesting links regarding mounting external drives in Linux. There are tons more in these forums.

[http://ubuntuforums.org/showthread.php?t=955015&highlight=mounting+external+hard+drive](http://ubuntuforums.org/showthread.php?t=955015&highlight=mounting+external+hard+drive)

[http://ubuntuforums.org/showthread.php?t=956042&highlight=mount+usb+drive](http://ubuntuforums.org/showthread.php?t=956042&highlight=mount+usb+drive)

[http://ubuntuforums.org/showthread.php?t=955264&highlight=mount+usb+drive](http://ubuntuforums.org/showthread.php?t=955264&highlight=mount+usb+drive)

---

### Post by logos34 on 2008-11-07
I assumed you meant you already formatted it ext3, but rereading your post a little closer it appears the drive is still factory formatted fat32 or ntfs.  Like the guys above said, format ext3 is preferable.  You can do it easily with gparted:

> sudo apt-get install gparted

gksudo gparted(it must be UNMOUNTED to format, btw)

To read/access the partition from windows get [fs-driver]("http://www.fs-driver.org/")

---

### Post by Periswell on 2008-11-08
> **logos34 said:**
> I assumed you meant you already formatted it ext3, but rereading your post a little closer it appears the drive is still factory formatted fat32 or ntfs.  Like the guys above said, format ext3 is preferable.  You can do it easily with gparted:

(it must be UNMOUNTED to format, btw)

To read/access the partition from windows get [fs-driver]("http://www.fs-driver.org/")

thanks logos34, i did not unmount before i formatted, my problem. well now it works. thanks everyone.

-joshua

---

