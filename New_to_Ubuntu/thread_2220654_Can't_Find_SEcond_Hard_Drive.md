---
title: "Can't Find SEcond Hard Drive"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-04-28
I have a desktop system runing ubuntu 12/04-64 desktop edition. It has two hard drives one is 160GB solid state that uses SATA wiring. The other is a tradional hard drive which uses IDE wiring. Both of the hard drives show up in BIOS, but the traditional hard drive is not showing in the file manager.

---

### Post by oldfred on 2014-04-29
Post this:
sudo parted -l

How is it physically configured? Cable select?
       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Paper Pusher on 2014-04-29
```
axel@axel-GA-78LMT-USB3:~$ sudo parted -l
[sudo] password for axel: 
Model: ATA M4-CT128M4SSD2 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  93.7GB  93.7GB  primary   ext4            boot
 2      93.7GB  128GB   34.3GB  extended
 5      93.7GB  128GB   34.3GB  logical   linux-swap(v1)


Model: ATA Maxtor 6Y160P0 (scsi)
Disk /dev/sdb: 164GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  156GB  156GB   primary   ext4            boot
 2      156GB   164GB  8032MB  extended
 5      156GB   164GB  8032MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label 
```

Oldfred, 

       Thank you for looking at my problem, I have posted the output that your requested. Like you, I am also old and I remember IDE. 

My motherboard is a combination of IDE and SATA. The SSD is connected by a SATA and the second hard disk is connected by IDE.

---

### Post by deadflowr on 2014-04-29
I see two hard drives listed.
Is the second not listed in the left side pane/panel of the Home Folder, file manager?

Another thing is you have a gigantic swap partition on /dev/sda.
You could probably do some resizing of that.
My opinion, tough.

---

### Post by Paper Pusher on 2014-04-29
When we start the file manager, it shows under drives a 156GB Hard Drive and the DVD drive. So yes, the second is not listed in the home folder, file manager.

---

### Post by oldfred on 2014-04-29
The 156GB drive is the second drive sdb.
And if your install is on the first drive sda, then you do not see it as a partition but as your install with home, system etc.

---

### Post by deadflowr on 2014-04-29
> **Paper Pusher said:**
> When we start the file manager, it shows under drives a 156GB Hard Drive and the DVD drive. So yes, the second is not listed in the home folder, file manager.

The one listed under devices is the second drive.
The one your are currently on doesn't get listed in that, instead it is the listing called File System(on 12.04) or Computer.

---

