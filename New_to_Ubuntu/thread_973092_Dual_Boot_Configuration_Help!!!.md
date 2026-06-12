---
title: "Dual Boot Configuration Help!!!"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by sinned3k on 2008-11-06
Every other thread seems to be specific to a users requirements.

Need some assistance mapping the correct directories!

**My current setup on Install Partition Screen:**

----------Current Prepare Partion Setup----------------------
DEVICE  TYPE  MOUNT-POINT   FORMAT?   SIZE     USED
/dev/sda     -     -     -        -        -           -
/dev/sda1  ntfs                Uncheck   80015MB   400096 MB
free space                                8MB
-------------------------------------------------------------

* As you can see I only have one partition. 
* I am not sure what to mount the partitions too?

Partitions 
Windows - already present
Linux ext3 - /home ?
Linux Swap  - ?
FAT32(Shared) - ?

 * Do not want my home directory on the the shared partition

Any suggestions welcomed!

PS: Although am fairly technical, I'm new to linux

Thanks!!!!

---

### Post by KuroYoma on 2008-11-06
Put this into your terminal and post the display

```
sudo fdisk -lu
```

---

### Post by gn2 on 2008-11-06
The best source of information on setting up a dual-boot is the excellent Hermanzone website, there's a link in my signature.

---

### Post by sinned3k on 2008-11-06
> **KuroYoma said:**
> Put this into your terminal and post the display

```
sudo fdisk -lu
```

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c3558a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

---

### Post by sinned3k on 2008-11-07
Somebody Please assist!

I installed and on boot up got a blank screen. I tried various alternatives but still got no fix.

Now I am currently reinstalling..! And back to my **prepare partition screen**.

To confirm, which devices do I mount to be my **/home** and **/root** directories. 

???

---

### Post by tarps87 on 2008-11-07
If you are installing you will need to create the partitions, the mounting is done at the same time.
During the install mount the partition you want to be:
root as mount point = /
swap partition as mount point = swap
if you want a separate home partition 
home mount point = /home
else you can ignore it and it will be mounted within the root partition
for the share I would suggest mount point /media/share
(You may need to do this after the installation)

If I have misunderstood and you have already installed post back and I can explain how to do it after installation

---

### Post by sinned3k on 2008-11-07
Thats exactly what I wanted to know. And also for the shared partition, Shouldnt that be FAT32 although there are slight restrictions (File size etc). 

And also does the partition type make too much of a difference? 
Logical || Primary

---

### Post by tarps87 on 2008-11-07
Good point, I forgot to say that Ubuntu will now write to a ntfs formatted drive and with third-party software window can write to ext3.
On my desktop I have xp and Ubuntu and use the windows partition for sharing files and music with no real problems.
Really I can't think of a reason to use on other the other so I will leave it up to you.

I don't think it matters, windows will probably be on the first primary partition, you can have four primary partitions in total. Ubuntu can be installed on either a logical or primary partition so either use the partitioner's defaults or go with primary for the root partition and logical for the rest

---

### Post by sinned3k on 2008-11-07
After login the following error is thrown.. And this is after reinstallation including formating drives.

[B]There is a problem with the configuration server
/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)[/B]

I know am being a pain but its one after the next

help!

---

### Post by tarps87 on 2008-11-10
I have read about two causes of this problem, they are bugs in the alpha versions of Ubuntu 8.10 so you may want to check that you are using the official release.
To do the fixes you will need to boot int the root shell, this is an option after booting into recovery mode which is selectable from the grub.
The alternative is press ctrl+alt+f1 at the login screen.
The fixes for the problems are changing the permisoms off gconf.xml.system by doing: ```

sudo chmod 775 /etc/gconf/gconf.xml.system
```
and also changing the ower of your home patition
```
sudo chown *userName*:*userName* /home/*userName*
```
Then reboot and it should work
```
sudo reboot
```

---

