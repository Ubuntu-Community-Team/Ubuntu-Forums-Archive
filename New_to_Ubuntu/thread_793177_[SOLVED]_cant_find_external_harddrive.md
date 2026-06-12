---
title: "[SOLVED] cant find external harddrive??"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by lover_of_sc on 2008-05-13
I just bought a IOMEGA 500gb external harddrive, but nothing happends when I plug it in... Do I need to mount it maybe? 

Would be thankful if anyone could help me.

Cheers

---

### Post by mlentink on 2008-05-13
> **lover_of_sc said:**
> I just bought a IOMEGA 500gb external harddrive, but nothing happends when I plug it in... Do I need to mount it maybe? 

Would be thankful if anyone could help me.

Cheers

please post the output of

```
sudo lsusb
```
and 
```
sudo fdisk -l
```
Take careL that's a lowercase L at the end, not a 1!

---

### Post by kellemes on 2008-05-13
> **lover_of_sc said:**
> I just bought a IOMEGA 500gb external harddrive, but nothing happends when I plug it in... Do I need to mount it maybe? 

Would be thankful if anyone could help me.

Cheers

Can you see it in the BIOS?
Did you format it?
Does it show up when issuing the following from a terminal window?
```
fdisk -l
```

---

### Post by cyberbill on 2008-05-13
You might just have to. What are you running?

post the output of

sudo fdisk -l

-cb

---

### Post by mgranet on 2008-05-13
If there's an icon for the drive, you may just need to mount it. IIRC, some of the external drives are formatted in FAT32, and don't mount automatically, but my memory is hazy on this one. What is the output of ```
 sudo fdisk -l
```

---

### Post by django0909 on 2008-05-13
This might work.

With the drive plugged in, type into a terminal

```
sudo fdisk -l
```

That will show your drive information. 

To mount a drive, type

```
mount /dev/hda1
```

replacing hda1 for whatever the USB drive comes under.

I know that isn't completely helpful but should point you the right way.

---

### Post by kellemes on 2008-05-13
> **django0909 said:**
> 
To mount a drive, type

```
mount /dev/hda1
```

replacing hda1 for whatever the USB drive comes under.


It should be..
```

mkdir /mnt/myextharddrive
mount -t ext3 /dev/hda1 /mnt/myextharddrive
```
hda1 depends on output of **fdisk -l**, ext3 should be replaced with the filesystem it's formatted with and myextharddrive can be any user defined directory you want to use to mount the harddrive at.

---

### Post by mlentink on 2008-05-13
> **kellemes said:**
> It should be..
```

mkdir /mnt/myextharddrive
mount -t ext3 /dev/hda1 /mnt/myextharddrive
```


Sorry, no.
First of all, /mnt is a system directory, so creating a subdirectory would need for this command to be preceded with 'sudo'.
Secondly, I would mount a removable drive (as a usb-drive) in /media
So that would mean:
```
sudo mkdir /media/myusbdrive
sudo mount /dev/hda1 /media/myusbdrive
```

But that's usually unnecessary. 
First, I like to see the output of:
```
sudo lsusb
```
and
```
sudo fdisk -l
```
And we'll take it from there

---

### Post by lover_of_sc on 2008-05-13
Below are the outputs as requested,I tried to plug it into my windows cpu and format it but my dog run over the cable half way finished. So the format never finished. :-/

anders@anders-laptop:~$ sudo lsusb
[sudo] password for anders: 
Bus 007 Device 007: ID 059b:0277 Iomega Corp. 
Bus 007 Device 004: ID 04f2:b023 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
anders@anders-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fcdf9c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    6  FAT16
anders@anders-laptop:~$

---

### Post by lover_of_sc on 2008-05-13
maybe this will help?

anders@anders-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8ece2c8-1bfb-4f2d-8261-e418284af78d /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1   /media/disc   ext3   defaults   0   1
# /dev/sda5
UUID=f3692d2a-63a0-4f91-befe-1a8406428a35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

anders@anders-laptop:~$ 

I am a ubuntu noob btw...

---

### Post by mlentink on 2008-05-13
> **lover_of_sc said:**
> Below are the outputs as requested,I tried to plug it into my windows cpu and format it but my dog run over the cable half way finished. So the format never finished. :-/ 
Oops... unfortunate, but since there wasn't anything on it..
> **lover_of_sc said:**
>  
Bus 007 Device 007: ID 059b:0277 Iomega Corp.
Hello buddy. that's our external drive, recoginzed as it should by ubuntu
> **lover_of_sc said:**
> Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fcdf9c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    6  FAT16

Fat16? You wouldn't want that. I'd format it as fat32 or rather as ext3.
My best guess is if you do partition and format it, it'll be recognized immediately...

---

### Post by lover_of_sc on 2008-05-13
Thank you for a quick reply, I think FAT32 would be better as I would like to use it for both cpu:s. Can I maybe ask a extremely stupid question then, how do I format it then? Tole you, I am a noob... hehe

---

### Post by OldTimeTech on 2008-05-13
Use gparted that on the live cd

---

### Post by mlentink on 2008-05-13
> **OldTimeTech said:**
> Use gparted that on the live cd

I agree.

Fire up the Ubuntu Live CD, [PITCH]just so you experience how incredibly useful it is[/PITCH],
and go to GParted. You'll find it under 'System' and 'Administration'. Be sure not to format the wrong drive.

You're looking for /dev/sdc

---

### Post by sunstriker on 2008-05-13
Gparted is indeed a nice graphical tool for partitioning disks. I wouldn't recommend FAT32 because it had a file size limit of 4 gb or so. So you can't put big iso's on it. 
NTFS is readable and writable by Linux/MacOSx (ntfs-3G, thank you) and ofcourse by Windows. And it's very reliable

---

### Post by lover_of_sc on 2008-05-13
Thanks that worked perfectly, altough how do I get default read and write access to the drive?

---

### Post by django0909 on 2008-05-14
Keep the dog in the yard :)

Sorry if I'm hijacking someone elses thread here but why is this necessary?

```
sudo mount /dev/hda1 /media/myusbdrive
```

As in, why do you have to mount hda1, then myusbdrive?

Or is the above line mounting myusbdrive *onto* hda1?

---

### Post by mlentink on 2008-05-14
To mount something, you need to mount it some*where*, i.e. you need to tell the OS where to find it in its file system. That is called the *mount point*

Hope that clarifies it a bit.

---

