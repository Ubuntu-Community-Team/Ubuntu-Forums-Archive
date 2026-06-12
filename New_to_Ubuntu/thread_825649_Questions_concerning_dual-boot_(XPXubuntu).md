---
title: "Questions concerning dual-boot (XP/Xubuntu)"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by MachFront on 2008-06-11
Hello all! While I've known of Linux for many years, it was only until a month or so ago I became curious/excited enough to give it a go.

Being a Linux newb, there are some things I'm curious about and need to know.

Specifically about dual-booting.

I'd like to know if it is necessary for me to even create a shared partition. I don't forsee needing files to be both read and written between XP and Xubuntu, but...one thing. I listen to my music collection non-stop while browsing the internet. Since Linux can read NTFS, will it and the media player be able to read the mp3s on the XP partition? Or, is booting into one OS on a partition make the other OS's partition "invisible" during that time, thus making a shared partition necessary?

Is it true that running a shared partition make things slower and will it cause the hard drive to work hard enough to cause more than usual 'wear and tear'?

I've a 320GB HD, so I've plenty of space. I was thinking of a small partition for Xubuntu. Perhaps 60GB or so.

What is sufficiant for the swap partition? I've read no more than 512MB, and I've read that 'so and so' over your total RAM is good, so I just don't know. I've 2 Gigs of RAM.

Last question (for now):
Do I need to format the Linux partition in FAT32 first, or does the installer take care of this? (By the way, what's ext3?)
I have my drive partitioned already, 128GB XP and the other 128 is unallocated. (It was a mistake, and I've never bothered to change it, knowing that I'd make use of the other partition someday, someway.) I was going to resize to make my XP partition larger, but should I just do that with the installer or before? (I have Partition Commander 10.)

Sorry to absolutely deluge you folks with newbie questions.
Thanks in advance for the help! :)

---

### Post by MegaJim on 2008-06-11
You can access files on a XP partition (as long as its NTFS/FAT) under linux quite safely; the only situation where you would lose access is if windows was hibernated - this would mark the partition as "active" and it would then be inaccessible under linux, just make sure you do a proper shutdown before booting up linux.

There is no extra "wear and tear" on the drive using a shared partition, however linux performs significantly better using linux file systems, I would not recommend trying to run any games or significant apps from an NTFS partition, but listening to music / general files should be fine.

As for partitioning, Xubuntu would be happy with 10GB for the root (/) partition.  A swap partition is generally recommended to be twice the amount of physical memory available on the system or a maximum of 1GB - depending on what kind of applications you are going to run, its always possible to shift the partitions slightly later on if you feel you need more (using something like partedmagic live cd) but for general use 1GB is plenty.  You can then create a home partition of however much you feel appropriate, anything from 2GB and up, this is where your user settings and files will be stored, safely protected between distribution upgrades.

Xubuntu uses ext3 or reiserfs depending on user choice, ext3 is a well established and reliable file system, reiserfs provides journaling for linux.  There are many good guides about how to partition up your drives on the net but I would recommend a small /boot partition (150mb, ext3), a decent sized / partition (10GB, ext3), and a moderate /home partition (5GB, reiserfs).  The rest you can leave unallocated for now, and make a decision later on as to what it will be used for (either expand the XP partition, or expand your /home partition).

Any other questions, feel free to ask, I'm here all day.

---

### Post by Najand on 2008-06-11
Ok, first of all, having a shared partition is not necessary. You still can mount your Windows Partition and listen to your favorite music there.
If you just want to give Linux a try, probably 60GB is even more than enough. About SWAP Partition, since old days, we had a kind of rule like SWAP=2xRAM. Nowadays, computers have a lot of RAM Memory. In your case you probably need 1GB. 
About FAT32, the answer is no, you won't need it. However you need to format the partition you want to install linux to "ext3" or "ReiserFS" filesystem to be able to use linux. 
I think Ubuntu Distributions come with Gparted (The GNU Partitioner) which can resize your NTFS partition too.

---

### Post by signseeker on 2008-06-11
Something to consider re: playing music files from your windows partition - if it's encrypted like with itunes music - you will not be able to play it easily. If it's just simple old fashioned mp3 - there should be no problem whatsoever. 

Good luck.

---

### Post by MachFront on 2008-06-11
Thanks so much to all of you that have thus far answered. I truly appreciate it.

I've got plenty to think about now, and can make a better informed decision.

I do believe that 60Gigs is probably overkill all things considered. I'm not sure yet, but maybe I'll be aiming more towards the area of 20-25 total(swap and / and /home)


MegaJim, why would you recommend the /home partition to be in reiserfs as opposed to ext3? Is there something else I'm missing here? (as if there wasn't already enough of that! :lol:)

---

### Post by MegaJim on 2008-06-11
Simply because it is a journaling file system, which means that corruption due to crashes or power loss are less likely and more easily recoverable.

---

### Post by Paqman on 2008-06-11
Ext3 is a journaling file system. It's ext2 that isn't.

---

### Post by Victormd on 2008-06-11
> **MachFront said:**
> I do believe that 60Gigs is probably overkill all things considered. I'm not sure yet, but maybe I'll be aiming more towards the area of 20-25 total(swap and / and /home)

Don't go crazy when creating the partitions, you shouldn't need more than 512MB for your swap partition, X/K/ubuntu is very efficient memory-wise...

---

### Post by Najand on 2008-06-12
As Paqman said, ext3 is also journalized. Through 4 famous linux filesystems (EXT3, ReiserFS, XFS and JFS) EXT3 is widely used, becuase RedHat employed it a few years ago as its default filesystem. Some people say that ReiserFS is faster, but in reallity the difference between its speed is negligible. 

However, in general, any of them has its own fans and they are always reasoning that their favorite filesystem which is not very important most of the time. 

For Newbies, usually ext3 is recommended not because it is better than others, but because it is the most used Linux filesystem until now. After a while when he/she learns enough about linux filesystems, he/she can move to any filesystems he/she prefers.

---

