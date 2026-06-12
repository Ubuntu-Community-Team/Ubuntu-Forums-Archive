---
title: "Disk ID clarification - different in FDISK vs Clonezilla ..."
date: 2013-02-05
forum: New to Ubuntu
---

### Post by cwmoser on 2013-02-05
Clarify something for me.
The Disk ID that I get from sudo fdisk -l /dev/sda is 
different that that in Clonzilla.

For example, fdisk displays the Disk ID as 0x29fd29fc
But, Clonzilla shows it like ...4315757.

I did not write down the full number when I ran Clonezilla.
Still, if you convert the hex number to decimal, its not even close.

So, what are these identifiers used by fdisk anc Clonezilla????

Carl

---

### Post by TheFu on 2013-02-05
First, fdisk has been replaced by parted and gparted due to GPT format, 4K sector and large disk support.  fdisk is only safe to use on MBR formated drives less than 2TB in size and performance will usually suck if the partitions are not aligned on 4K boundaries for 4K sector HDDs.

It is best just to end all use of fdisk.

If you want to see UUIDs, the best way that I know is to look at the uuids and links in /dev/disk/by-uuid/* .  I'm sure there is a command that will do it too, but 
$ **ls -al /dev/disk/by-uuid/* **
works perfectly.  There are other disk identifiers too in other **/dev/disk/by-*** folders.

---

### Post by Mark Phelps on 2013-02-05
For reasons I can't explain, even in the case of MBR disks, fdisk and clonezilla can have different identifiers for the same drives.

I noticed this when I started to use Clonezilla (booted from the hard drive) to do image backups.

I would use Gparted and fdisk inside Ubuntu to write down the drive and partition designations (e.d., sda, sda1, etc) but when I then booted into clonezilla, the same items would be sdc, or sde, or something else.

---

### Post by sudodus on 2013-02-05
```
sudo blkid
```
will show for each partition: label, uuid, type (file system)

I recommend that you use ***labels*** to make it easier to identify partitions, e.g. ubuntu, data, multimedia, windows. Labels are used when external drives are identified and mounted via file browsers.

Labels can be added to partitions with ***gparted*** (all file systems) or with ***tune2fs*** (ext[234])

---

