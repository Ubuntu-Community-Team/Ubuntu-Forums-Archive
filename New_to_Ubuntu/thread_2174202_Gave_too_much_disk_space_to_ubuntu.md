---
title: "Gave too much disk space to ubuntu"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by sofian2 on 2013-09-13
Hello

I've just donwloaded ubunto 13.04 dual booth on windows 8.
But Ubuntu has 500 gb (from 1TB), but this is too much. 
How can I fix this? 

Kind regards

---

### Post by bkline on 2013-09-13
There are lots of tutorials online showing you how to do this.  For example:

[http://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/](http://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/)

Googling will find others for you, but when you search don't use the term "memory," which refers to the volatile storage whose contents are gone when the machine is no longer running.  What you're dealing with is the persistent storage provided by the "file systems" which occupy the "partitions" into which the storage disks are divided.  It's these "partitions" which you need to manipulate.  Read the instructions carefully.

Good luck!

---

### Post by grahammechanical on 2013-09-13
Basically, you need to shrink the Ubuntu Partition using a tool that comes with the Live Session - gparted. That will create unallocated space that you can expand the Windows partition into but you must do this using Windows utilities and I have seen recommendations to defrag Windows more than once before resizing a Windows partition.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by oldos2er on 2013-09-13
Changed thread title.

---

### Post by Pako Pako on 2013-09-13
> **grahammechanical said:**
> I have seen recommendations to defrag Windows more than once before resizing a Windows partition.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
I thought defragging was for shrinking a Windows partition, not expanding it?

Also, in regards to sofian2's install -- was it a full install or a WUBI install?

---

### Post by Impavidus on 2013-09-13
With 500GB it must be a full install. Wubi has maximum 30GB.

Boot from a live disk, use gparted to shrink your Linux partition. Pay attention to the side from which you shrink, as you can only expand your Windows partition into unallocated space when adjacent, or just make an extra partition for data storage. Expand the Windows partition only from Windows. Make sure you have backups. The whole operation takes a while and if you lose power you can lose data. If you just installed and hadn't done anything yet, the alternative is to delete the Linux partition, create a smaller new one and reinstall. This may be quicker.

---

### Post by sofian2 on 2013-09-15
Thanks everyone!

---

### Post by WacoJohn on 2013-09-15
> **Pako Pako said:**
> I thought defragging was for shrinking a Windows partition, not expanding it?

I don't believe it is either.  Certain file systems can create fragmented files on a hard drive.  Example:

Write file #1 to 'empty' drive.  It is written contiguously.  Write file #2, then #3.  Delete #2.  Write #4 .. which, if larger than #2 will write PART of itself where #2 was and the rest of itself after #3.  #4 is now a fragmented file.  Defragging corrects this fragmentation and creates contiguity across the hard drive.  It has nothing to do with changing partition SIZE or creating empty space on a hard drive (the same amount of space is used whether files are fragmented or not).

The Linux file system is not subject to fragmentation ... as I understand it.

that will be 2 cents, please :p

---

### Post by CeejRab on 2013-09-15
Hello again Wacojohn,

So its a pretty easy fix, as mentioned above, your easiest fix is to load a ubuntu live cd and use gparted to select the partition you wish to shrink, then make it the size you desire. Then choose the partition you wish to enlarge, and make it however large you want (probably to use all the remaining free space rather than leaving Gigs of free space unpartitioned).

Not much too it, happy ubuntu-ing!

PS: Defragmenting a HD has nothing to do with partitions or  filesystems... Also, defragmenting is pretty much only used by windows  users because the windows operating system leaves little crummy chunks  of information all over the place >:P

---

