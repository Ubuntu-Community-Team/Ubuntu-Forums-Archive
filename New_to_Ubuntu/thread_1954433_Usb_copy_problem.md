---
title: "Usb copy problem"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by pqku on 2012-04-08
Hello all,

I try to copy one movie to my usb, but it always stop and say " error splicing file input,output"
Maybe i can cut this movie in several small parts and merge them together after.

How can i do ?

Thank you

---

### Post by papibe on 2012-04-08
Hi pqku.

By any chance the file size is > 4Gb, and the USB has a FAT32?

If not, what size? what filesystem?

Regards.

---

### Post by pqku on 2012-04-08
The movie is 4.5GB.

My usb is in NFTS.

So i was thinking to cut in several part ? is it possible ?

---

### Post by papibe on 2012-04-08
FAT32 has a file size limit of 4Gb, but NTFS does not.

Is there enough space on the USB?
Have you run a check disk from Windows lately?

Regards.

---

### Post by jeznadel on 2012-04-08
Try to zip it first and save it again.

---

### Post by oklokl on 2012-04-08
ntfs Partition bug?
gvf error?
u-disk error..?

gparted 

usb-> new mbr created
 
usb partition -> ext4 make
(Error is less.)


mount /media/a789
(The click of a mouse)

sudo fdisk -l
sudo chown -Rh username:root /media/a789



# /media/a789 -> usb
# /media/test/123 ->  File Folder


cp -rf /media/test/123/* /media/a789

#!/bin/bash
umount -l /media/a789
sync

or
find ' /media/test/123' -name "*.mp3" -exec cp -rf {} /media/a789 \;
find ' /media/test/123' -name "*.zip" -exec cp -rf {} /media/a789 \;


ext3 -> windows access
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
A little bug exist

---

### Post by pqku on 2012-04-08
> **papibe said:**
> FAT32 has a file size limit of 4Gb, but NTFS does not.

Is there enough space on the USB?
Have you run a check disk from Windows lately?

Regards.

Yes my USB is 8GB

---

### Post by pqku on 2012-04-08
> **jeznadel said:**
> Try to zip it first and save it again.


Can i use winrrar to zip it ?

---

### Post by pqku on 2012-04-08
> **oklokl said:**
> ntfs Partition bug?
gvf error?
u-disk error..?

gparted 

usb-> new mbr created
 
usb partition -> ext4 make
(Error is less.)


mount /media/a789
(The click of a mouse)

sudo fdisk -l
sudo chown -Rh username:root /media/a789



# /media/a789 -> usb
# /media/test/123 ->  File Folder


cp -rf /media/test/123/* /media/a789

#!/bin/bash
umount -l /media/a789
sync

or
find ' /media/test/123' -name "*.mp3" -exec cp -rf {} /media/a789 \;
find ' /media/test/123' -name "*.zip" -exec cp -rf {} /media/a789 \;


ext3 -> windows access
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
A little bug exist


I need to transfert the file to a windows 7 after. So what should i do ?

---

### Post by oklokl on 2012-04-08
usb chipset patch.(How to patch the...I do not know .. sorry.. )
or..
ext4 red
[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

---

### Post by 3rdalbum on 2012-04-08
Input/Output Error usually means "Your disk is failing". Either the source file is on a damaged part of your hard disk, or the flash drive has a bad spot that is being written to.

No solution except to work out which of those drives is at fault, then bin it.

---

### Post by oklokl on 2012-04-08
man badblocks

sudo fdsk -l

umount -l /dev/sdb1

sudo badblocks -vw /dev/sdb  ## testing.. Required long time
Is accurate


 mount >
sudo badblocks -v /dev/sdb1 
Is not accurate.

---

