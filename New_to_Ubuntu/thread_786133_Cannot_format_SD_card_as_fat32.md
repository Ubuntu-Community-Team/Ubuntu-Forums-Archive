---
title: "Cannot format SD card as fat32"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by palosanto on 2008-05-07
Hello,
Totally newbie in any kind of Linux. Im a windows user starting to really like Linux...
I have a 8gb SD card which worked fine in my HTC phone until one morning it was't seen.  It wasn't detected by windows either.  So I had no chance to reformat it. Someone advised me to try in Linux. I downloaded Slax and ran it. Sure enough the card was there !. Although my data was gone (no biggie), I could read and write files.
I wanted to reformat it as Fat32 so,
I then partitioned it with Fdisk of but when I try to format it with: mkdosfs -F 32 /device/mydevice it seems to format ok, but if I list the devices with fdisk -l  it shows up as Linux formatted... not Fat32
After that I've tried to read it in windows but it is not detected yet.   
What am I doing wrong?

---

### Post by leonidas25 on 2010-05-22
My suggestion is to use "gparted" it should be in the repositories. It's nice because of the GUI and you can visualize your hard drive, or in this case your SD.

What I've notices is that SD cards are usually formatted as FAT16 instead of FAT32. You might try it. I would need support from the experts. Hope this can be the solution

---

### Post by John Bean on 2010-05-22
> **leonidas25 said:**
> What I've notices is that SD cards are usually formatted as FAT16 instead of FAT32

Not if they're 8GB they're not ;-)

---

### Post by smileyacid on 2010-05-22
ive had this exact same problem + many other similar especially with my 16GB SD card I just tried a myriad of tools on both win + Ubuntu but yes defiantly G parted a good + easy use one 

I suppose if your running a live CD (I assuming) you should have G parted but no more real choice of Linux tools or I would recommend Gnome format if Slax has it (should do or something similar)

---

### Post by srs5694 on 2010-05-22
> **palosanto said:**
> I wanted to reformat it as Fat32 so,
I then partitioned it with Fdisk of but when I try to format it with: mkdosfs -F 32 /device/mydevice it seems to format ok, but if I list the devices with fdisk -l  it shows up as Linux formatted... not Fat32

First, be aware that the word "format" is hopelessly ambiguous in this context. People can and do use it to refer to low-level formatting (possible on floppies, but done at the factory and not do-able by users for hard disks), partitioning, creating a filesystem, a combination of the last two things, and perhaps some other things. The mkdosfs creates a filesystem, while fdisk creates or modifies partition tables.

Second, the partition table includes a partition type code, but this code, as part of the partition table, does not tell you anything about what's actually in the partition; it can be inaccurate. The filesystem itself is stored entirely within the partition and does not affect the partition table. It's sort of like a filing cabinet, where each drawer is a partition and its contents are the filesystem and the files it contains. The partition table's type code is like a label on a drawer that reads "A-D," but the files within the filing cabinet (that is, the filesystem) might or might not match that description.

Your specific issue is probably a matter of a mis-matched label. If you used fdisk to create the partitions, the default type code is 0x83 (Linux data). You should explicitly change that type code (using 't' in fdisk) if you want to store something other than a Linux-native filesystem on the partition. For FAT, you should change the type code to 0x01, 0x04, 0x06, 0x0b, 0x0c, or 0x0e, depending on the FAT variety in use. (Type 'L' at an fdisk prompt to see a list of type codes.) For FAT-32, the usual type code is 0x0c.

Linux doesn't actually use the type codes for much, but Windows does, so when Windows sees a 0x83 type code, it doesn't look inside the partition and it won't show a FAT filesystem even if the partition contains one.

The suggestion to use GParted is a reasonable one, particularly for new users. Although fdisk gives a more accurate view of what's actually on the partition table, GParted is much easier to use. In particular, it automatically synchronizes the partition type code with the filesystem type when you create a partition or create a new filesystem on an existing partition.

---

