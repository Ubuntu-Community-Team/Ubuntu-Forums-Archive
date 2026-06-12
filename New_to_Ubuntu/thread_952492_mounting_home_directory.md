---
title: "mounting /home directory"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by jamaas on 2008-10-19
I've been playing around with a new eeepc, attempting to install another os on a sdhc disk and when I reistalled ubuntu on the first hd, got grub installed but now does not recognize /home on /dev/sdb1 ... What is the easiest/best way to go in and change this?  It is assigned in fstab as 

UUID= .....      /home   ext3 relatime  0  2

Is there a logical reason why this wouldn't work?

Thanks a bunch,

Jim

---

### Post by jamaas on 2008-10-19
please ?

---

### Post by Kellemora on 2008-10-19
Hi J

There IS a nice long number behind that UUID I hope?

sudo blkid

will show the UUID of all partitions
then doublecheck to make sure the correct number is where it should be.

TTUL
Gary

---

### Post by jamaas on 2008-10-20
Hi Gary,

Yes, thanks it is a big long number and I've done blkid and it is the correct number.  Something wrong during boot process does not setup /home onto /dev/sdb1 correctly.  The cause of this problem is that I made an image of /dev/sda1 containing ubuntu, while I loaded/installed xp to put it on a sdhc disk ...and upon putting the image back onto the actual disk, it all went pear-shaped.  

Suggestions?  Thanks

Jim

---

### Post by jerome1232 on 2008-10-20
Sounds like a mistake may have been made when putting the image back on and the partition table got borked? 

Do you still have the image? 
Can you mount the image as a loop device? If not what is the error?

What's the error if you try and mount the partition from the command line?

---

### Post by jamaas on 2008-10-20
thanks Jerome, one step at a time!  :-)  I have the image, how can I mount it as a loop device?


thanks

J

---

### Post by jerome1232 on 2008-10-20
You can of course adjust the mount point to whatever. This is just to verify your image file is in good working order.

```
sudo mkdir /mnt/homeimg
sudo mount /path/to/img/file /mnt/homeimg -o loop
```

---

### Post by jamaas on 2008-10-20
Done that and it works fine, has mounted the image, and I did some looking around, it all looks fine, nothing in /home as I would expect.  That is a great feature, now what should I try?  Thanks a bunch.

J

---

### Post by jerome1232 on 2008-10-20
Ok so at least we know your image is in good shape so try and mount the partition. I'll pretend for my example it's /dev/sdc3 adjust your command according to what it really is, let me know if you need help pin-pointing what device it actually is.

first unmount that img, then we'll mount your partition to the same place where we mounted the img.

```
sudo umount /path/to/img/file
sudo mount /dev/sdc3 /mnt/homeimg
```

---

### Post by jamaas on 2008-10-20
Done, that directory contains a root owned lost+found directory.  Next?  :-)

thanks J

---

### Post by jerome1232 on 2008-10-20
So it was exactly the same as your image file was?

Sounds like the problem lies in fstab then. Can you post the output of a couple commands and let me know what partition is the one that you want mounted at /home. Oh and go ahead and unmount that partition since we know it's in good working order.

```
cat /etc/fstab
sudo blkid
sudo fdisk -l
```

edit: I thought this partition was an old /home that you had imaged, is it just an image that had no files in it? Are you working from a live cd right now or are you booted into your install.

---

### Post by jamaas on 2008-10-20
Is an eee 901 pc, small 4 GB ss hard disk to contain / which is in the image, currently on a connected external usb hard disk, /home is still on the eee on the larger 16GB ss hard disk.  It is also fine, just need to get / installed and pointed to /home!  Yes, currently running eee on live disk.

---

### Post by jamaas on 2008-10-20
fstab  (in the image file)
-----------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71604fcb-12ca-4585-ae18-64228098d4af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=04e289a8-b975-4878-a6eb-e3eae6a5669e /home           ext3    relatime        0       2
#/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


--------------------
blkid
--------------------

/dev/sda1: UUID="320a7885-4a08-4668-9c97-54d4e9772741" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="04e289a8-b975-4878-a6eb-e3eae6a5669e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="71604fcb-12ca-4585-ae18-64228098d4af" TYPE="ext3" 
/dev/sdc1: UUID="3418259F1825615A" LABEL="XPNTFSDrive" TYPE="ntfs" 
/dev/sdc2: LABEL="XPFAT32DISK" UUID="8C33-22C0" TYPE="vfat" 
/dev/sdc5: UUID="adb02719-53b6-45cb-9537-a7aba1c5a4b0" TYPE="ext3" 


---------------
fdisk -l
---------------

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bb227

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         490     3935893+  83  Linux

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux

Disk /dev/sdc: 122.9 GB, 122942324224 bytes
1 heads, 1 sectors/track, 240121727 cylinders, total 240121727 sectors
Units = cylinders of 1 * 512 = 512 bytes
Disk identifier: 0x2e7fdd15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2    61440001    30720000    7  HPFS/NTFS
/dev/sdc2        61440002   128455803    33507901    b  W95 FAT32
/dev/sdc3   *   128455803   240121729    55832963+   f  W95 Ext'd (LBA)
/dev/sdc5       128455804   240106619    55825408   83  Linux
/dev/sdc6       240106621   240121729        7554+  83  Linux

---

### Post by jerome1232 on 2008-10-20
Well I don't know. I'm out of reasons for it to not mount :( The filesystem is intact, there doesn't appear to be anything wrong with that fstab to me.

---

### Post by jamaas on 2008-10-20
Thanks Jerome,

That helps, nothing explicitly blown up.  I think I may have got myself into trouble by making image of /dev/sda1 instead of /dev/sda  as I should have ...now getting it back correctly if there was a small /dev/sda2 swap or something might be the problem.

Thanks a bunch.

Jim

---

