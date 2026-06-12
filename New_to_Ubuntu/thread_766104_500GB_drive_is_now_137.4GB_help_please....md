---
title: "500GB drive is now 137.4GB?? help please..."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2008-04-25
(I started a thread a while ago but things have changed so i thought a new one would make things easier)

So i have a 500GB drive that had heaps of important data on it. One day suddenly the drive mounted and said it was 137.4GB :O Anyway, i wanted to save the data but now i have given up and formatted it. It was ext2 but i made it ext3...Anyway it still comes up as a 128GB drive and i wanna know if the other partition is still there somewhere and if i can recover it?? 

```
root@ben-desktop:/home/ben# fdisk -l

Disk /dev/sda: 137.4 GB, 137437871104 bytes
255 heads, 63 sectors/track, 16709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8c36

```

```
e2fsck /dev/sda
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```


[IMG]http://i74.photobucket.com/albums/i247/dales618/Screenshot--dev-sda-GParted.png[/IMG]



[IMG]http://i74.photobucket.com/albums/i247/dales618/Screenshot-diskProperties.png[/IMG]
[IMG]http://i74.photobucket.com/albums/i247/dales618/Screenshot-1374GBMediaProperties.png[/IMG]

---

### Post by diablo75 on 2008-04-25
This sounds like the ATA 128/137 GB barrier.  You can read more here:

[http://www.pcguide.com/ref/hdd/bios/sizeGB128-c.html](http://www.pcguide.com/ref/hdd/bios/sizeGB128-c.html)

You should check your motherboard's BIOS and see if it is up to date.

---

### Post by aquavitae on 2008-04-25
Check out testdisk, photorec and ddrescue. Search in google and you'll get a plethora of guides, hopefully help you recover your old data. Btw, make sure you don't use the disk at all. Every read-write operation will wipe part of it.

---

### Post by e1ektrob0y on 2008-04-25
hmmm ok, so it looks like when moving the drive from one computer to another, the bios in the older computer has changed the size of the disk to 137.4GB. When i try to change the mode to CHS, LARGE or whatever in my bios it has no effect. Also, when i auto detect the disk in bios, it shows up as 137GB. The weird thing is i have another disk, exactly the same in the computer that comes up as 500GB just fine...Seriously, the disks are the same brand, model number and everything...

---

