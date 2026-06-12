---
title: "Multi-Boot Partitioning"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by OneRingShort on 2008-08-05
Hey everyone, I was wondering if you could help me out with some partition planning?  I've read the Psychocats linux resource, and that significantly helped me, but I still have some questions regarding the setup.

So, I picked up an Asus Eee PC, and replaced the Xandros distro with Ubuntu, and I absolutely love it.  I have had zero problems with it so far, and I've decided I want Ubuntu on my primary computer as well now.

Right now, I am running Windows Vista Home Premium x86, have two 320 gb hard drives, divided into four partitions (OS, Program Files, Media, and Data).  What I'm aiming for is to be multi-booting Windows Vista Home Premium x86, Windows XP Home x86, and Ubuntu 8.04 x86.  My current knowledge on partitioning says I need a partition for each Windows OS, one for Ubuntu, a swap, and preferably a home partition.

Now here is where I'm getting stuck, and could use some suggestions/help.  I'm trying to find a way for shared files between all three OS's.  I've considered a FAT32 partition, but after I learned about the 4gb file size limit, I decided that method wasn't good for me.  I've heard Ubuntu now has a decent/effective NTFS read/writer, that would allow me to keep the files in an NTFS partition.  I also discovered Ext2 IFS 1.11 from the Psychocats resource, which just let me read the linux files on Windows.  Are there any other methods, or ones that you prefer (and why)?

Additionally, I could use some help on sizing the partitions.  My Vista partition right now is 45 gb, and that seems to be working fine and still has some extra space (11 gb).  I haven't used XP in a while (nor paid attention to partitions when I did), so I'm not quite sure how large of a partition to make for that one, but I'm thinking 20-25.  How large should I make the main Ubuntu partition?  I've read it only uses 1.5 gb, and more would be required if I installed more programs.  I think 6-8 gb for the swap should be fine (just going by the Psychocats recommendation here...I have 4 gb of RAM).

One last question.  I know this is a linux forum, but I was thinking maybe you guys knew and could save me some time researching.  If I create a program files partition for Windows, am I correct in saying that I would need to install each program twice (once for each version of Windows), or would both Windows OS's be able to read the same program files?

I know the post was long, but I'm trying to get as much information to you about what I need help with, so you do not have to ask questions that I should have predicted in the first place.  If you need more information, feel free to ask!Thanks for any and all help in advance!

OneRingShort

Note: for sizing purposes, I have about 100-110 gb of media currently, and 160-170 gb of data/other files.  I would prefer to have growing room in those partitions.

---

### Post by hyper_ch on 2008-08-05
> **OneRingShort said:**
> Now here is where I'm getting stuck, and could use some suggestions/help.  I'm trying to find a way for shared files between all three OS's.  I've considered a FAT32 partition, but after I learned about the 4gb file size limit, I decided that method wasn't good for me.  I've heard Ubuntu now has a decent/effective NTFS read/writer, that would allow me to keep the files in an NTFS partition.  I also discovered Ext2 IFS 1.11 from the Psychocats resource, which just let me read the linux files on Windows.  Are there any other methods, or ones that you prefer (and why)?
With NTFS-3G you can read/write ntfs partitions. No problem.
With Ext2/3 drivers you can read/write access your linux ext3 partitions.

> **OneRingShort said:**
> How large should I make the main Ubuntu partition?  I've read it only uses 1.5 gb, and more would be required if I installed more programs.  I think 6-8 gb for the swap should be fine (just going by the Psychocats recommendation here...I have 4 gb of RAM).
Get rid of windows altogether and give it all to linux ;)
6.8 gb are fine but I think it's small. Especially if you have no seperate home folder. with 4 gb ram you shouldn't need swap only if you want to hibernate/sleep your computer.


> **OneRingShort said:**
> One last question.  I know this is a linux forum, but I was thinking maybe you guys knew and could save me some time researching.  If I create a program files partition for Windows, am I correct in saying that I would need to install each program twice (once for each version of Windows), or would both Windows OS's be able to read the same program files?
I think you'll have to install it twice because some stuff is put into the windows folder and windows registry. However you can install it twice into the sama data partition and save space.

---

### Post by OneRingShort on 2008-08-05
> **hyper_ch said:**
> With NTFS-3G you can read/write ntfs partitions. No problem.
With Ext2/3 drivers you can read/write access your linux ext3 partitions.
So NTFS-3G is for linux to read NTFS partitions, and the Ext2/3 drivers are for Windows to read the linux partitions. Gotcha.

> **hyper_ch said:**
> Get rid of windows altogether and give it all to linux
I certainly would if I could get my gaming fix with linux :|

> **hyper_ch said:**
> I think you'll have to install it twice because some stuff is put into the windows folder and windows registry. However you can install it twice into the same data partition and save space.
Excellent.  I was thinking something along the same lines.

---

### Post by indytim on 2008-08-05
The other thing I would add is while you are partitioning, consider creating 2 more ext3 partitions.  Size them to accomodate another version / distro with the associated /home.  This will give you the option of exploring another Lx ops. without compromising your production ops.

IndyTim

---

