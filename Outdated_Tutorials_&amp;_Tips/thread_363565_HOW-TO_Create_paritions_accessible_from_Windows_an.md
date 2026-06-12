---
title: "HOW-TO: Create paritions accessible from Windows and Linux for beginners"
date: 2007-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by jtapper on 2007-02-17
This is one way to create partition that is accessible from both Windows & Linux.

[B]1. Use partition editor to create an OS shared parition
[/B]
Few different ways to do this, for example: 
1. gparted
2. parted
3. fdisk

I will use gparted which can be found from System - Administration
If you don't have it install it with synaptic or any other packet manager of your choice.

Find unallocated disk space or delete some existing partition to make some free space. Remark:  all the data will from that partition will be lost if you decide to delete an existing one.

Select that empty space with mouse and press CTRL+N. Set the size and change Filesystem to fat32.
Be sure to remember /dev/xxxx for the partition you are operating with.
Press the Apply button (not sure what it is in English..)
Confirm that you want to do the changes.

**2. Edit fstab**
from terminal: 
First back up original fstab which can be used if something goes wrong.
```
sudo cp /etc/fstab /etc/fstab.backup
```

Then edit your fstab file
```
sudo pico /etc/fstab
```

add line to end: /dev/xxxx       /your/mntpoint/here vfat iocharset=utf8,rw,users,gid=users,umask=000, 0 0

where xxxx is the partition you created in step 1.

for me this was:
/dev/hdb3       /media/music vfat   iocharset=utf8,rw,users,gid=users,umask=000,       0       0

**3. Try if it works**
from terminal:
```
sudo mount -a
mount | grep /dev/xxxx
```
where xxxx is the partition you created in step 1.

You should now see that the partition you created is mounted.

**4. Done.**

---

### Post by surautomatism on 2007-02-20
I edited fstab to the following, but my mount point was not detected. sda2 is the name of my fat32 drive according to GParted.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6effc5de-3266-4a87-a7d5-9fe8743b7294 /               ext3    defaults,erro$
# /dev/sda1
UUID=64F46444F4641A96 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/sda4
UUID=c80b11ae-2aeb-4854-8524-ba4e866e40cc none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2 /media/shared vfat iocharset=utf8,rw,users,gid=users,umask=000, 0 0

---

### Post by surautomatism on 2007-02-20
Is says that media/shared does not exist. how do I create it?

---

### Post by jtapper on 2007-02-21
You can create directory with mkdir command.
For example:
```
sudo mkdir /media/shared
```

---

### Post by jake3988 on 2007-02-24
gparted is so easy a chimp could learn it, but fdisk is much harder.

So either point that out or actually make an addendum showing how to use fdisk.  That would improve this by 1000%.

But the rest of this is good.

Also, point out that windows really only likes fat32 filesystems (Hence why you choose that, I assume).  I MUCH prefer ext2 but of course I'm fairly certain only linux can access them.

That's awesome that this can be done without even rebooting.  I have 140gb of space on my harddrive just sitting there unallocated, so now I can allocate it!

---

