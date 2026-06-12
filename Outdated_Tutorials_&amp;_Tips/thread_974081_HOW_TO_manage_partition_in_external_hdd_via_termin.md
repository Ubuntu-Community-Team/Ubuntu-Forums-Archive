---
title: "HOW TO: manage partition in external hdd via terminal"
date: 2008-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Claus7 on 2008-11-07
Hello,

having to repartition my external hard disk drive, I think that a revision to my previous post is required:
[http://ubuntuforums.org/showthread.php?t=435870](http://ubuntuforums.org/showthread.php?t=435870)

what we want to do: we want to repartition an external hard disk drive in such a way so as to keep one partition intact and the other two to merge in one new partition. We become root.

First, while you have mounted the disk you do :
```
df -h
```

in order to see what is going on with all the disks and their partitions you have mounted.

Let's suppose that the disk we want to reformat is sdb.
Then if it has three partitions those should be under :
/dev/sdb1
/dev/sdb2
/dev/sdb3

and also to:
/media/name_of_partition_1
/media/name_of_partition_2
/media/name_of_partition_3

In order to repartition the disk we have to unmount all the partitions:
(we can unmount either using the dev or the media locations, here we will use the dev)
```
umount /dev/sdb1
umount /dev/sdb2
umount /dev/sdb3
```
(watch out that the command umount doesn't have an "n")

Then type :
```
fdisk /dev/sdb
```

that way we will see the total number of cylinders our external hard disk has and now we can start the repartitioning.

press p in order to see the partitions we have created in the disk. If we have three partitions the one will be displayed under the other. For example:

 Device Boot Start   End      Blocks   Id  System
/dev/sdb1     1     27390  220010143+  83  Linux
/dev/sdb2     27391 38913   92558497+  83  Linux
/dev/sdb3     38913 xxxxx        xxx    x   xxx

(here I post my final partition table, and I have added one more partition so as to have 3)

Now I want to delete the second one and the third. I type:
```
d /dev/sdb2
```
and when I'm asked about the partition number, I type 2.
For the third one:
```
d /dev/sdb3
```
and when I'm asked about the partition number, I type 3.

If now I type p, I'll get:
Device Boot Start   End      Blocks   Id  System
/dev/sdb1     1     27390  220010143+  83  Linux

now I want to create a new one in place of the older two and three:
I type n
and I choose the primary partition. For the space of the partition I just typed enter both for the start and the end, because I wanted the beginning of that partition to be the end of the first unaltered partition and the end to be the end of the disk(hope this is clear). The number of that new partition is 2. In the end I type v, and w to write the partition table and exit.

The partitions should be mounted automaticaly. Here it won't be bad to unmount them and replug back the usb cable.

Now it's time to name the new partition:
```
mkfs.ext3 -j /dev/sdb2 -L BACKUP_P2
```

Typing this command you have to wait a little in order for some data to be refreshed.
Doing that I got most of the space of the partition. Before doing that I had lost the 10gb I had in an ntfs partition, so this step is obligatory.

EDIT: Just to say that, based on my recent experience, in the guide I had written:[http://ubuntuforums.org/showthread.php?t=708251](http://ubuntuforums.org/showthread.php?t=708251) 
in order for someone to be able to read and write apart from:
sudo chown (user name) /media/(name of partition)
also the:
sudo chgrp (user name) /media/(name of partition)
was needed.

If you do fstab as root this might not be needed, yet just to be on the safe side.

Regards!

---

### Post by Claus7 on 2009-03-24
Hello,

I would like to post this as in the net there was not an exact answer on how someone can deal with such problem:

error1: Error reading bootsector: Input/output error

error2: **Unable to open /dev/sdb - unrecognised disk label.**

error3: Disk /dev/sdb doesn't contain a valid partition table

error4: mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

error5: Buffer I/O error on device sdb, logical block 0

error6: ... I do not remember really...

So how can someone avoid these errors?

What it was important in my case was error2. That happened because while I was trying to format my disk with:
mkfs.ext3 -j dev/sdb**1** -L name of your partition up to 11 characters

I had forgotten to place 1 after sdb, because with the above command we have to do with partitions. Also, having done that it was almost impossible to mount such a usb drive from a usb1.1 port.

As a result if you see such errors, make sure that you have connected your usb external hdd to a usb2.0 port. In order to verify that you have connected your disk to the right port two simple commands should suffice. The one is:
lsusb
which will give something like:
Bus 005 Device 001: ID 0000:0000  
Bus 00***4*** Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

and the
lshw
which will give:
*-usb:***4***
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd

Note the #4 above which states that usb 4 is a USB2 device.

Now if your disk is not fully corrupted or so you will be able to see it from /dev/sdb (in general /dev/sd...). That way it will be unmounted so you will be able to repartition it and reformat it following the guide from my first post.

One more thing: I was wondering why a usb external hard disk drive from 1 terabyte actually becomes 870GB or so. Reading this:
[http://junocake.blogspot.com/2007/07/debian-software-raid-setup.html](http://junocake.blogspot.com/2007/07/debian-software-raid-setup.html)
some of my doubts disappeared.

Also a very nice tool for disk recovery data is testdisk (via synaptic, a nice discussion here):
[http://ubuntuforums.org/showthread.php?t=525508](http://ubuntuforums.org/showthread.php?t=525508)

From a windows machine I was unable to do anything, except "mounting" the disk without errors. With that I had no icon in mycomputer and I wasn't able to see the disk. Just pop it out and in...  

Hope it helps,
Regards!

---

### Post by Claus7 on 2010-11-06
Hello,

this new instalment covers some new topics found on the way while dealing on the subject. So let's start:

I came across a FAT32 external hdd and I wanted to format it on ubuntu maverick 10.10. I tried to use gparted with no avail (not really knowing why). So the good old method of terminal applied here.

I plugged the disk and it popped up as usual as a FAT32 disk. The:

```
df -h
```

command showed me the disks I had in use. I unmounted the drive:

```
sudo umount /dev/sdb1
```

and then tried to make the partitions:

```
sudo fdisk /dev/sdb
```

while doing so the message:
> WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

appeared and from here:
[http://ubuntuforums.org/showthread.php?t=1443700](http://ubuntuforums.org/showthread.php?t=1443700)

I decided to type c and then u as proposed.

Then I typed: d, n, p, enter enter and finally w.
That way the first righting block would be 2048, which seems to be better than 1. In the end a 1TB drive would be around 870GB.

Then in order to format the disk typed:

*sudo mkfs.ext3 -j /dev/sdb1 -L [I]name_of_my_drive_up_to_11_characters*[/I]

This created an ext3 hdd which I thing for now is the best option since it can be recognised from windows as well with the availability of programs. With ext4, I have not found, till this time or writing, any program that will do the work, except if the journaling is disabled or something similar...

In order to be able to set the right permissions type the commands in my edit above.

Regards!

---

