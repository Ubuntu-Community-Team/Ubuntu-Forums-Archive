---
title: "What is ext2 for?"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by Homeground on 2012-03-23
I've just shrunk my Ubuntu 10.04 partition down to 20Gb, and I intend later to install a couple of other OS's in the freed up space (200Gb). But for the moment I will use it as a dumping area for video files. But I formatted it as ext2, and now I find I can't use copy/paste to move data into it. When I right-click the mouse the "paste" command is greyed out. Is this due to it being the wrong file system? Which one should I have used?

---

### Post by Perfect Storm on 2012-03-23
ext2 is the previous version of ext3 (and now ext4).

The problem regarding copy and paste, you need to set the permission up for the new partition.

---

### Post by jerome1232 on 2012-03-23
+1, ext2, like fat32 is mostly a relic of days gone by, but your issue isn't that, it's the permissions.

To change permissions:

[http://ubuntuforums.org/showpost.php?p=7164073&postcount=2](http://ubuntuforums.org/showpost.php?p=7164073&postcount=2)

---

### Post by 1clue on 2012-03-23
> **jerome1232 said:**
> +1, ext2, like fat32 is mostly a relic of days gone by....


I hate to say it but fat32 is alive and well.  It&#347; the only format I've found that is supported by default installations of Linux, Windows and Mac.  If you have a drive you share between all 3 operating systems, you're going to use fat32 or you're going to install drivers on at least one operating system.

---

### Post by jerome1232 on 2012-03-23
> **1clue said:**
> I hate to say it but fat32 is alive and well.  It&#347; the only format I've found that is supported by default installations of Linux, Windows and Mac.  If you have a drive you share between all 3 operating systems, you're going to use fat32 or you're going to install drivers on at least one operating system.

True, a lot of small flash devices use fat, but bigger ones tend to use ntfs, ntfs r/w is supported out of the box on every Linux distro I have ever used, it has been that way for years. ntfs is supported out of the box by all modern Windows OS's. OS X takes a minor tweak to enable ntfs r/w support, read support is enabled by default.

I mostly used that as comparison, sorry if the comparison was inadequate, ext2, as fat32, has it uses, but rarely would a regular user have a use for a file system with no journal.

---

### Post by mastablasta on 2012-03-23
> **1clue said:**
> I hate to say it but fat32 is alive and well. It&#347; the only format I've found that is supported by default installations of Linux, Windows and Mac. If you have a drive you share between all 3 operating systems, you're going to use fat32 or you're going to install drivers on at least one operating system.
 
 
good luck sharing a 5 GB file like that ;-)

---

### Post by Homeground on 2012-03-23
So, if you're just going to use an area as a data dump, you'd format as Fat32 or NTFS? And if you wanted to install Ubuntu in a partition, you format as ext4?

---

### Post by evilsoup on 2012-03-23
You only need FAT32 if you need to share data with windows computers. On a hard drive being used by Ubuntu, just go with EXT4.

EXT4 (and 3) uses a thing called 'journalling', which makes your data safer in the event of a power cut/other catastrophic or sudden failure. For a computer HDD this is what you should use.

However, journalling means that the storage is written to more often. On a hard drive that isn't a problem, but flash memory (USB sticks, SD cards, maybe SSDs?) degrades at a relatively small number of writes, so using a journalling filesystem like EXT4 might not  be the best choice - for USB sticks, I use EXT2.

Unless you need to transfer files to windows computers, in which case you should use FAT32. HOWEVER, FAT32 has a maximum filesize of around 4GB, so if you need to transfer large files to windows, go for NTFS (which does have read/write support, but it is very slow).

In conclusion:

For Hard Disc Drives: **EXT4**
For USB memory sticks (linux/BSD only, I think OSX also has support): **EXT2**
For USB memory sticks (linux+windows, with no really large files): **FAT32**
For USB memory sticks (linux+windows, files >4GB): **NTFS**

---

### Post by Homeground on 2012-03-23
> **evilsoup said:**
> You only need FAT32 if you need to share data with windows computers. On a hard drive being used by Ubuntu, just go with EXT4.

EXT4 (and 3) uses a thing called 'journalling', which makes your data safer in the event of a power cut/other catastrophic or sudden failure. For a computer HDD this is what you should use.

However, journalling means that the storage is written to more often. On a hard drive that isn't a problem, but flash memory (USB sticks, SD cards, maybe SSDs?) degrades at a relatively small number of writes, so using a journalling filesystem like EXT4 might not  be the best choice - for USB sticks, I use EXT2.

Unless you need to transfer files to windows computers, in which case you should use FAT32. HOWEVER, FAT32 has a maximum filesize of around 4GB, so if you need to transfer large files to windows, go for NTFS (which does have read/write support, but it is very slow).

In conclusion:

For Hard Disc Drives: **EXT4**
For USB memory sticks (linux/BSD only, I think OSX also has support): **EXT2**
For USB memory sticks (linux+windows, with no really large files): **FAT32**
For USB memory sticks (linux+windows, files >4GB): **NTFS**

Thanks. There's a lot of useful info there.

"...flash memory (USB sticks, SD cards, maybe SSDs?) degrades at a relatively small number of writes". 

I was beginning to suspect that myself. There are enough 1-star ratings against flash drives on Amazon to make you think that too many 5-star ratings had been given too soon. If everyone had to wait 6 months before writing a review, those flash drives might not score so high. However, I went ahead and bought an 8Gb Sandisk about a week ago. It was fine until last night, when Ubuntu failed to recognize it. And Windows on my other machine recognized it but said it was unformatted. I wasn't sure if it was my fault, if I'd done something fatal. But I took it back for a replacement today. I should have got a refund instead. After what you've said, I don't think I'll put much trust in it.

---

### Post by jerome1232 on 2012-03-23
The limitation is actually the number of times the device can zero out a block, after so many times it can't zero the block out anymore. Most are certified to last at least 100,000. That's a lot of zeroing out.

So it's not simply writing data that wears flash memory, it's replacing data. I think most of them fail from being jostled around, coke being spilled into them, dropping them, sitting on them etc.. than due to heavy use.

---

