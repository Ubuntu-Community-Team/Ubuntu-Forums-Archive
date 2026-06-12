---
title: "Which partition is / and which is /home?"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by RayArdia on 2013-12-31
After much advice from various expert contributors I have finally got a dual boot Ubuntu 13.04 and Win7. The Win7 OS on /dev/sda1 works OK, and as it's only purpose in life is to allow me to run Sketchup, all is well.
When it comes to the other 3 partitions I' a bit confuse as to which Ubuntu is using as / and which as /home.
Output s follow:-

ray@ray-Aspire-5735:~$ df -h 
Filesystem      Size  Used Avail Use% Mounted on 
/dev/sda3        25G  3,1G   21G  14% / 
none            4,0K     0  4,0K   0% /sys/fs/cgroup 
udev            1,5G  4,0K  1,5G   1% /dev 
tmpfs           297M  868K  296M   1% /run 
none            5,0M     0  5,0M   0% /run/lock 
none            1,5G  140K  1,5G   1% /run/shm 
none            100M   36K  100M   1% /run/user 
/dev/sda4       181G   38G  134G  23% /home 
/dev/sr0        794M  794M     0 100% /media/ray/Ubuntu 13.04 i386  - *What is this? Does Ubuntu really have only 794MB? What is /dev/sr0?*
/dev/sdc1       294G  167G  112G  60% /media/ray/Phillips 

from sudo parted -l 
ray@ray-Aspire-5735:~$ sudo parted -l 
[sudo] password for ray: 
Model: ATA WDC WD2500BEVT-2 (scsi) 
Disk /dev/sda: 250GB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 

Number  Start   End     Size    Type     File system     Flags 
 1      1049kB  21,5GB  21,5GB  primary  ntfs            boot 
 2      21,5GB  26,1GB  4565MB  primary  linux-swap(v1) 
 4      26,1GB  223GB   197GB   primary  ext4 
 3      223GB   250GB   26,8GB  primary  ext4 


Model: Hitachi HDT725032VLAT80 (scsi) 
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 

I thought I had Ubuntu in the smaller sda3 and that sda4 was being used for /home but when I try to reload backup copies of files from sdc into my Home directory Iget an error that 'nautilus hsn't got enough room for the operation'  or something similar.

---

### Post by ian-weisser on 2013-12-31
> **RayArdia said:**
> ray@ray-Aspire-5735:~$ df -h 
Filesystem      Size  Used Avail Use% Mounted on 
[COLOR=#ff0000]/dev/sda3[/COLOR]        25G  3,1G   21G  14% [COLOR=#ff0000]/ [/COLOR]
[COLOR=#ee82ee]/dev/sda4[/COLOR]       181G   38G  134G  23% [COLOR=#ee82ee]/home [/COLOR]

I thought I had Ubuntu in the smaller [COLOR=#ff0000]sda3 [/COLOR]and that [COLOR=#ee82ee]sda4 [/COLOR]was being used for[COLOR=#ee82ee] /home[/COLOR] 

Yes, that's what you did.

> **RayArdia said:**
> when I try to reload backup copies of files from sdc into my Home directory Iget an error that 'nautilus hsn't got enough room for the operation'  or something similar.

The exact error message would be more helpful. Nautilus is an application, not a partition.

---

### Post by deadflowr on 2013-12-31
Are you trying to copy all the files from the sdc partition to the home partition?
If so, then the error makes sense. The sdc partition has a larger used space than the home partition's available space.

---

### Post by grahammechanical on 2013-12-31
> [COLOR=#000000]/dev/sr0 794M 794M 0 100% /media/ray/Ubuntu 13.04 i386 - [/COLOR]*What is this? Does Ubuntu really have only 794MB? What is /dev/sr0?*

Are you running a Ubuntu live session? or perhaps have the live session disk in the drive and mounted?

Regards.

---

### Post by Jonathan Precise on 2013-12-31
> **grahammechanical said:**
> Are you running a Ubuntu live session? or perhaps have the live session disk in the drive and mounted?

The OP has the "Ubuntu 13.04 Live DVD" mounted, as /dev/sda3 is the / (root) directory in this case.

---

### Post by RayArdia on 2013-12-31
> **grahammechanical said:**
> Are you running a Ubuntu live session? or perhaps have the live session disk in the drive and mounted?

Regards.
I wasn't running a live session but had left the disk in the drive! How stupid of me; apologies for the silly question.

---

### Post by RayArdia on 2013-12-31
> **ian-weisser said:**
> Yes, that's what you did.



The exact error message would be more helpful. Nautilus is an application, not a partition.
Thanks to you and to deadflowr  for your help will look out for the error message next time. Incidentally, what tells you that the one is / and the other is  /home?
Yes I know that the total size of the used space in /sdc1 is greater than that of /sda3 but I was only trying to move a folder of about 4GB.

---

### Post by deadflowr on 2013-12-31
> **RayArdia said:**
> Incidentally, what tells you that the one is / and the other is  /home?
From your output,
```
[COLOR=#000000]Filesystem Size Used Avail Use% Mounted on [/COLOR]
[COLOR=#000000]**/dev/sda3** 25G 3,1G 21G 14%** /** [/COLOR]
[COLOR=#000000]none 4,0K 0 4,0K 0% /sys/fs/cgroup [/COLOR]
[COLOR=#000000]udev 1,5G 4,0K 1,5G 1% /dev [/COLOR]
[COLOR=#000000]tmpfs 297M 868K 296M 1% /run [/COLOR]
[COLOR=#000000]none 5,0M 0 5,0M 0% /run/lock [/COLOR]
[COLOR=#000000]none 1,5G 140K 1,5G 1% /run/shm [/COLOR]
[COLOR=#000000]none 100M 36K 100M 1% /run/user [/COLOR]
[COLOR=#000000]**/dev/sda4 **181G 38G 134G 23%** /home **[/COLOR]
[COLOR=#000000]/dev/sr0 794M 794M 0 100% /media/ray/Ubuntu 13.04 i386 - [/COLOR][I]What is this? Does Ubuntu really have only 794MB? What is /dev/sr0?
/dev/sdc1 294G 167G 112G 60% /media/ray/Phillips [/I]
```

---

### Post by Jonathan Precise on 2014-01-01
> **RayArdia said:**
> After much advice from various expert contributors I have finally got a dual boot Ubuntu 13.04 and Win7. The Win7 OS on /dev/sda1 works OK, and as it's only purpose in life is to allow me to run Sketchup, all is well.
When it comes to the other 3 partitions I' a bit confuse as to which Ubuntu is using as / and which as /home.
Output s follow:-

```
ray@ray-Aspire-5735:~$ df -h 
Filesystem      Size  Used Avail Use% Mounted on 
/dev/sda3        25G  3,1G   21G  14% / 
none            4,0K     0  4,0K   0% /sys/fs/cgroup 
udev            1,5G  4,0K  1,5G   1% /dev 
tmpfs           297M  868K  296M   1% /run 
none            5,0M     0  5,0M   0% /run/lock 
none            1,5G  140K  1,5G   1% /run/shm 
none            100M   36K  100M   1% /run/user 
/dev/sda4       181G   38G  134G  23% /home 
**/dev/sr0        794M  794M     0 100% /media/ray/Ubuntu 13.04 i386  - *[B]What is this? Does Ubuntu really have only 794MB? What is /dev/sr0?***[/B]
/dev/sdc1       294G  167G  112G  60% /media/ray/Phillips 
```

from sudo parted -l 
```
ray@ray-Aspire-5735:~$ sudo parted -l 
[sudo] password for ray: 
Model: ATA WDC WD2500BEVT-2 (scsi) 
Disk /dev/sda: 250GB 
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 

Number  Start   End     Size    Type     File system     Flags 
 1      1049kB  21,5GB  21,5GB  primary  ntfs            boot 
 2      21,5GB  26,1GB  4565MB  primary  linux-swap(v1) 
 4      26,1GB  223GB   197GB   primary  ext4 
 3      223GB   250GB   26,8GB  primary  ext4 


Model: Hitachi HDT725032VLAT80 (scsi) 
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B 
Partition Table: msdos 
```

I thought I had Ubuntu in the smaller sda3 and that sda4 was being used for /home but when I try to reload backup copies of files from sdc into my Home directory I get an error that 'nautilus hasn't got enough room for the operation'  or something similar.

No, ubuntu doesn't have only 794 MB. That's the size of the DVD installer.

/dev/sr0 is usually the CD and/or DVD and/or BluRay drive.

---

