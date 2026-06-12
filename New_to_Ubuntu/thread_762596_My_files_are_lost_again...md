---
title: "My files are lost again.."
date: 2008-04-22
forum: New to Ubuntu
---

### Post by sayakb on 2008-04-22
Hello all
I use Gutsy amd64 on a Laptop (Core2Duo T7700, 3GB DDR2, nVidia 8600 M GTS, 320GB + 540GB SATA HDD)
Ok, I have a 540GB external USB HDD that contains everything on the go.. believe me, everything. . . my documents, important data, music, movies. So it's naturally in NTFS since I can't change my college PCs to Ubuntu. But earlier this morning when I was copying a chunk of about 1200 files to it, at about 250, the copy paused and it showed "You do not have permissions to access the folder". I pressed the back button and got the same message. So I unmounted and remounted just to get this : "The volume cannot be mounted. The NTFS filesystem may be broken..." Damn, I lost about 450GB of critical data. This is the 5th or 6th time Ubuntu is screwing up my NTFS external HDD. I am not complaining or anything and I can literally bear anything than going back to Windows. But this is really bad. Last time it was some 100 MP3s that screwed the drive. What should I do? Should I convert it to FAT32? Or just wait for Hardy final version which might have a solution to this.??
Please advise.

---

### Post by philinux on 2008-04-22
If memory serves you'll need to get windows to repair the file system like chkdsk etc.

---

### Post by Joeb454 on 2008-04-22
You could try mounting it in Windows (using the college PC's or something) and then mounting it in Linux again.

I'm not 100% sure if this would work, but it's worth a try :)

---

### Post by frodon on 2008-04-22
You shouldn't use NTFS if you mainly use linux, FAT32 is way more appropriate and stable although it is less performant and has a 4Gb max file size limitation.

Anyway please give us the exact error message as i can't believe partition to be screwed so easily on a sane drive.

The above advices are the way to go as linux don't have NTFS check tools, in all the cases you data are not lost, there's many ways to get back datas from a damaged drive as long as the disk itself is not physically damaged.

---

### Post by sayakb on 2008-04-22
> **frodon said:**
> You shouldn't use NTFS if you mainly use linux, FAT32 is way more appropriate and stable although it is less performant and has a 4Gb max file size limitation.

Anyway please give us the exact error message as i can't believe partition to be screwed so easily on a sane drive.

The above advices are the way to go as linux don't have NTFS check tools, in all the cases you data are not lost, there's many ways to get back datas from a damaged drive as long as the disk itself is not physically damaged.

I cannot post the error message since I already formatted the volume. Plus, OMG, mounting it on Windows would have solved it.. I didn't try it, maybe it could save my data :( :( :(
Yes, I use Gutsy only (No, I don't dual boot it with Windows), so I would be formatting it again to FAT32 I think.

---

### Post by Joeb454 on 2008-04-22
:lolflag: Never mind, at least you'll know for next time.

I only dual boot to do very few things with Windows, and to remind myself how it works *family IT Guy* :( You could have a small (i.e. minimal) Windows partition to let you mount the drive? Just an option you might want to look into.

Note I'm not trying to get you to go back to windows ;)

---

### Post by frodon on 2008-04-22
Next time you will know that you can always recover datas from a sane disk even with a partition table screwed up.
If you have a 540Gb drive i advice you one big FAT32 partition and one smaller NTFS one in case you need to store big file as FAT32 does not support files bigger than 4Gb.

---

### Post by philinux on 2008-04-22
> **LinuxIsInnovation said:**
> I cannot post the error message since I already formatted the volume. Plus, OMG, mounting it on Windows would have solved it.. I didn't try it, maybe it could save my data :( :( :(
Yes, I use Gutsy only (No, I don't dual boot it with Windows), so I would be formatting it again to FAT32 I think.

Yep chkdsk would have recovered the files.

---

### Post by Joeb454 on 2008-04-22
> **frodon said:**
> Next time you will know that you can always recover datas from a sane disk even with a partition table screwed up.
If you have a 540Gb drive i advice you one big FAT32 partition and one smaller NTFS one in case you need to store big file as FAT32 does not support files bigger than 4Gb.

500Gb Fat32
40Gb NTFS

That sort of size?

---

### Post by sayakb on 2008-04-22
Okay.. would do that. Thanks to all for replying.

---

### Post by sayakb on 2008-04-22
Plus, I think I would make one 400GB FAT32 and one 127GB NTFS partition (Since I get only 527GB on the drive)

---

### Post by someonestolemyname on 2008-04-22
Definitely not NTFS. Fat32 sucks, but is universal, so anything can read it...

Pity you didn't try to save your data =/

---

### Post by Joeb454 on 2008-04-22
Personally I would go with ext2 or ext3, and add the drivers to Windows to read ext partitions (it allows write too, but I don't trust it).

However as your Windows PC's are college owned, I doubt you'll be able to do this :(

---

### Post by brennydoogles on 2008-04-22
You can also use testDisk and photoRec (all in the repos as one package, TestDisk) to repair the drive or recover files from a dead drive (I have used this to recover files from drives that are physically damaged even). The only thing about Photorec is that it renames all of the files it recovers, which is a pain in the butt.

---

### Post by slick_nick on 2008-04-25
Before trying Windows/chkdisk, try "ntfsfix".  It's worked for me in the past. From the manual:
"ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.

You may run ntfsfix on an NTFS volume if you think it was damaged by Windows or some other way and it cannot be mounted. "

---

### Post by sayakb on 2008-04-26
ntfsfix sounds good. :)
@Joeb454: I think EXT2IFS driver screws up ext3 more often than Ubuntu screws up NTFS. :(

---

