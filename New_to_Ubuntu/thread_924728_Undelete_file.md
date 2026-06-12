---
title: "Undelete file"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by ChanTico on 2008-09-19
Hey, I hope I'm putting this post in the right place, apologies if not.

I've recently swapped laptops and I gave my old one to my father. I installed windows vista for him and to do so formatted the entire Hardrive to NTFS.

I backed up and transfered all my crucial data but I managed to miss a save file for one of my games. (It was on an ext2 partition, now part of the big NTFS one).

Is there any software or any way that I will be able to undelete the file?

Thanks for any help in advance.

---

### Post by madsmeg on 2008-09-19
You need to look for a data recovery tool, there are plenty out there but many of them you need to pay for.

The list is too long, its best to search for yourself and choose which best suits you.

EDIT:depending on the size of the drive, you will be sifting through ALOT of stuff

---

### Post by iaculallad on 2008-09-19
Use [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover your deleted files.

From Photorec's site:
> Photorec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (thus, its 'Photo Recovery' name) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted.

---

### Post by madsmeg on 2008-09-19
Adding that to my toolkit, thanks.

---

### Post by iaculallad on 2008-09-19
> **madsmeg said:**
> Adding that to my toolkit, thanks.

You can also add the [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") utility. Testdisk and Photorec had saved me not more than once on my Server maintenance problem.

From Testdisk site:

> Testdisk is OpenSource software and is licensed under the terms of the GNU Public License (GPL).

TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.

TestDisk can

    * Fix partition table, recover deleted partition
    * Recover FAT32 boot sector from its backup
    * Rebuild FAT12/FAT16/FAT32 boot sector
    * Fix FAT tables
    * Rebuild NTFS boot sector
    * Recover NTFS boot sector from its backup
    * Fix MFT using MFT mirror
    * Locate ext2/ext3 Backup SuperBlock
    * Undelete files from FAT filesystem
    * Copy files from deleted FAT, NTFS and ext2/ext3 partitions. 

TestDisk has features for both novices and experts. For those who know little or nothing about data recovery techniques, TestDisk can be used to collect detailed information about a non-booting drive which can then be sent to a tech for further analysis. Those more familiar with such procedures should find TestDisk a handy tool in performing onsite recovery. 



---

### Post by k33bz on 2008-09-19
> **iaculallad said:**
> Use [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover your deleted files.

From Photorec's site:

im adding this one as well

---

### Post by ChanTico on 2008-09-19
Thanks for that, I'm sure that it'll work.

At the moment I'm getting "error, could not search disk".

I think that it's because there is only one partition and it doesn't like saving the files on the partition that it's searching, for obvious reasons! :P

The Hardrive used to be 30Gb of NTFS, followed by the swap space, then the ext2 bit last. The Current Vista system and files have only taken up the first 25GB, so I'm pretty confident that the file still exsists.

I've tried to resize the vista partition, but it won't let me make it smaller than 60GB :S

Are there any good disk resizing tools, out there?

Or am I wrong and could there be another reason why I get the error and only having one partition has nothing to do with it.



EDIT: Also, if I do resize the partition, I've never seen a partition expansion tool, only a shrinking one, it'd be nice to only have one partition and not have to dick about, do they exsist or not?

Thanks for any help in advance.

---

