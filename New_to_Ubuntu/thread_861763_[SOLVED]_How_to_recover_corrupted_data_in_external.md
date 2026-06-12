---
title: "[SOLVED] How to recover corrupted data in external hard drive"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-16
I think the data were corrupted when I use VirtualBox. Anyway, I still can see all the folders in XP (my wife's laptop) even though I just can open only a few because most of them are corrupted, therefore prevent me to open. However in Hardy Heron, I do not see any folder (this USB external hard drive was successfully mounted) as if it was empty. I think Ubuntu refuse to show the folders (in the external HD) because it was corrupt. How to recover all my precious data (thousand of personal photos from 2 years ago till now, important documents etc). I already run dosfsck -a (the whole night) but it yield nothing. Hope something can be done because no one in their sane mind want to be parted with these kind of files (photo especially:(

---

### Post by iaculallad on 2008-07-16
Try to download [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") for data recovery.
And:
[Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") for image file recovery.

---

### Post by bumanie on 2008-07-16
Photorec is good. It will in fact try to save things other than photos eg. documents as well, whereas testdisk is more to retrieve a deleted partition or rewrite a clobbered partition table. By the way, unless installed incorrectly or without enough space, I find it hard to understand how virtualbox did this. I have 3 different vm's running with no issue.

---

### Post by wariskampar on 2008-07-16
Thanks for assistance. Just one question before I try testDisk. How do I run it if I can not see either folders or anything in the drive. Do I just run it on the blank drive and this program will help me recover the lost data?

---

### Post by iaculallad on 2008-07-16
> **wariskampar said:**
> Thanks for assistance. Just one question before I try testDisk. How do I run it if I can not see either folders or anything in the drive. Do I just run it on the blank drive and this program will help me recover the lost data?

Refer to this [page]("http://www.users.bigpond.net.au/hermanzone/p21.html") on how you could use the Testdisk utility.

---

### Post by wariskampar on 2008-07-16
I tried to install the program from it source package. However, I get this error message. What is the problem?

aznan@aznan-laptop:~$ sudo apt-get install build-essential e2fslibs-dev libncurses5-dev libncursesw5-dev libntfs-dev libjpeg62-dev libreiserfs0.3-dev uuid-dev zlib1g-dev
[sudo] password for aznan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libreiserfs0.3-dev
aznan@aznan-laptop:~$ cd ~/Desktop 
aznan@aznan-laptop:~/Desktop$ ./configure 
bash: ./configure: No such file or directory
aznan@aznan-laptop:~/Desktop$

---

### Post by iaculallad on 2008-07-16
> **wariskampar said:**
> I tried to install the program from it source package. However, I get this error message. What is the problem?

aznan@aznan-laptop:~$ sudo apt-get install build-essential e2fslibs-dev libncurses5-dev libncursesw5-dev libntfs-dev libjpeg62-dev libreiserfs0.3-dev uuid-dev zlib1g-dev
[sudo] password for aznan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libreiserfs0.3-dev
aznan@aznan-laptop:~$ cd ~/Desktop 
aznan@aznan-laptop:~/Desktop$ ./configure 
bash: ./configure: No such file or directory
aznan@aznan-laptop:~/Desktop$

What not just install it from the repo?

```
sudo apt-get install testdisk
```

---

### Post by wariskampar on 2008-07-17
In my understanding, first we need to copy the data from corrupted drive to secondary location. In my case my HD is much more bigger (320GB) than my hard disk (80GB with only 20GB empty space). Can I recover the data in their original location (external HD)

[sudo] password for aznan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+  83  Linux
/dev/sda2            9536        9729     1558305    5  Extended
/dev/sda3            1947        7137    41696707+  83  Linux
/dev/sda4            7138        9535    19261935   83  Linux
/dev/sda5            9536        9729     1558273+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

---

### Post by bumanie on 2008-07-17
For what it's worth, I still think that photorec is more appropriate. I have used testdisk and its a great program, but it is more efficient at repairing partition tables and recovering lost partitions etc. as per test disks page > "TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again" In your case you have not lost a partition, thus as photorec's page says > "Photorec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (thus, its 'Photo Recovery' name) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted." That sounds more like your problem to me. True, your hdd partition table may well be compromised, but if your data is corrupted, a functioning partition table won't help. Before doing anything else, read both the testdisk and the photorec documentation.

---

### Post by wariskampar on 2008-07-17
What are you saying (i'm not english native speaker). Can I use photorec or can i not?

---

### Post by expatCM on 2008-07-17
Perhaps things have changed .....  I used PhotoRec on an external hard drive about 18 months ago.

I was utterly and totally amazed.  And horrified.

The program is clearly excellent.  If a file once breathed on the hard drive it will be recovered.  This means that the list of recovered files is huge.  Like really huge.  It even recovers temp files.

When I used the program there was one significant problem though.  The file is recovered with perfect content but the original file name is not.  So in my case I ended up with a list of files like file0001, file0002 ....  and then had to first sort them by file size and zap the zero byte files and small file and then work on what remained.  That was a huge task.

But at the end of the day I had to use the program ....  I could find no alternative.  As I imply ...  perhaps the program has since been updated and will recover the file name as well ...

---

### Post by phantomjoker on 2008-07-17
heres some useful *and free* recovery tools - I think they are all windows based so back to your wifes laptop - but saves you anymore trouble.

[http://www.snapfiles.com/Freeware/system/fwdatarecovery.html]("recovery software")

hope i helped

---

### Post by Yannick Le Saint kyncani on 2008-07-17
I'd suggest you make all those test on a disk image instead of on the real one.

So dd if=/dev/baddospartition of=/some/where/to/an/image.file

---

### Post by wariskampar on 2008-07-17
expatCM, do you need to prepare extra space of exactly the size of the folder that you wanted to recover in other partition or, the files was recovered within the same corrupted drive. Now I'm running chkdsk in XP and hopefully can achieve something at the end. Anyway, I'm sure to sure photorec later on.

---

### Post by wariskampar on 2008-07-18
Problem solved!:) The XP saves me with chkdsk. Even though it spent the whole night to complete, it was worth it. Now, my external HD even pop up automatically once I plug it in Hardy. How nice! Just for reference, these are the steps:
1) Plug in ex. HD in XP
2) type chkdsk /f <DRIVE> in Start>Run
3) Wait until finish (may take several minutes to hour depend on size) 
4) Safely disconnect from XP

Thanks all!

---

### Post by no_angst on 2010-06-14
Thanks guys, PhotoRec installs with testdisk and worked great for me.

```
sudo apt-get install testdisk
```
Then,
```
photorec
```

It auto-detected my DVD drive and pulled the home movie file I needed (and a couple others) off the damaged camcorder rewritable DVD disk in just a few minutes.  (Something checkdisk would not be able to do).  It wasn't too terribly important, just a video of my son loosing his first tooth, but I still wouldn't have wanted to loose it.

Again, thanks!

---

