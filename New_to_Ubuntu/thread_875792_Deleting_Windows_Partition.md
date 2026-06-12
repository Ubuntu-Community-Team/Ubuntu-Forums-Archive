---
title: "Deleting Windows Partition"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by marshall1001 on 2008-07-31
This is gonna sound like a really n00bish question to ask, but I'm not brilliant with partitions. I've already guessed how to do it, but I'm scared to mess around in case I click the wrong thing.

I made the switch from using Wubi to a partitioned install of Ubuntu a while back, and ever since I've been using windows less and less, to the point where I only ever used it to sync my iPod, recently my Windows partition contracted a bucket-load of viruses and I decided I have no longer any real need for Windows on my harddrive as there is no data on there since all my music etc. is stored in an external.

How do I delete my windows partition and give Ubuntu an extra 35gb of filespace?

---

### Post by RuleMaker on 2008-07-31
1) Boot from the live CD
2) In terminal type "gparted"
3) Find you windows partition in list and delete it, it will tako only a few seconds.
4) The partition you deleted in the first step will now become "unallocated space"
5) If your ubuntu partition is next to unallocated space you'll be able to resize it, otherwise you'll have to copy your ubuntu partition in unallocated space and then to resize it. (the resizing takes longer, depending on haw much data you have).

This may sound hard but it really isn't, good luck!

---

### Post by marshall1001 on 2008-07-31
Cheers, I'll try that when i get back from work

---

### Post by vanadium on 2008-07-31
> This may sound hard but it really isn't,

It may not be that trivial depending on your current partitioning scheme. You may want to post the output of "sudo fdisk -l" here so that we can see what your current partitioning looks like and how easy or difficult it is going to be to change it.

An very easy and safe solution would be to just reformat the current Windows partition to ext3, after which you can use the partition for data storage. Setting appropriate permissions and using symbolic links, you can then have very easy access to that partition from within your home directory.

---

### Post by marshall1001 on 2008-08-04
Turns out it wasn't that trivial. I';ve just been able to burn a Hardy disc to use as a live session this week, since we've been out of cds for a while now. I've deletedmy windows partition no bother, and I know have around 40gb "Unallocated space". The only problem is that when I try to resize my Ubuntu partition, it will only allow me to make it smaller, and not expand it into the unallocated space. Why is that?

---

### Post by ingeva on 2008-08-04
> **marshall1001 said:**
> Turns out it wasn't that trivial. I';ve just been able to burn a Hardy disc to use as a live session this week, since we've been out of cds for a while now. I've deletedmy windows partition no bother, and I know have around 40gb "Unallocated space". The only problem is that when I try to resize my Ubuntu partition, it will only allow me to make it smaller, and not expand it into the unallocated space. Why is that?

That's probably because Windows is in a primary partition, while the others are logical partitions inside an extended partition.
The best solution, although it takes some time, may be to backup all your files, use a live CD to make new partitions on the disk (Make the OS partition active/bootable!) and then restore the files. If you need more than one partition in addition to the swap partition, you may still have to start with a primary partition, since it can't be divided, since I'm not sure if you can make a disk bootable if it doesn't have a primary partition.

Afterthought: It may be possible to remove the primary partition first, THEN expand the extended partition and the logical partition inside it. I don't really know, but it's worth a try because it could save some time. You should leave a small primary partition though, just for safety (you can probably use the minimum size which is one disk track).

---

### Post by marshall1001 on 2008-08-05
Data isn't a concern to me. Literally ALL of my msuic and files are stored on a 500gig external.

Would you suggest, for simplicity's sake, booting using a liveCD and then deleting the hardy partition, then installing ubuntu again?

---

### Post by hyper_ch on 2008-08-05
if data isn't a concern, the quickest way would be a total new install.

However if you have time and want a bit to twinker around and get to know the system and its workings better, try to expand the logical partition and extended one. If you fail, you'll just do a complete new install... if you can make it work, you've learned something that you can use maybe at a later time ;)

---

### Post by marshall1001 on 2008-08-05
Good stuff, I'm going to have a play around with it yeah, however i do think I'll have a fresh install ready whatever the outcome.

---

### Post by Bucky Ball on 2008-08-05
Like hyper_ch says, if you have the time and the inclination, fiddle about until you have totally broken your ubuntu install, then do fresh install. Take this opportunity to experiment and learn a few things without fear of total disaster!!! Good luck ...

---

### Post by jmsgz on 2008-08-14
yeah have been watching this discussion and would like to know the following: ,,,because i would like to give the BOOT to XP "no pun intended"!!!!!! [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

am i understanding you folks correcting by paraphrasing that the general procedure for getting rid of the xp portion of a dual boot system is to either

1.) resize the existing ubuntu partition -or-
2.) deleting the existing xp partition - or-
3.) formating the xp partition to linux file type and using it with 
    the ubuntu system. (is about 20 gig) -or-
4.) if all else fails just reinstall using entire hd???
    (doing all of this from live CD, because you cannot 
    do it while hd is mounted.))????

also where does the dual boot program reside?  on the xp or ubuntu side or neither??????? Do i have to worry about it if performing the above less option 4?

thanks in advance jmsgz

data & programs on xp partition are of no further use therefore caution is not required, however, to learn the system more i can mess with it some instead of deleting but was worrying about the boot situation?

---

### Post by cprofitt on 2008-08-14
Yeah if data is no issue... I would do a new install and use the entire disk.. depending on where that Windows partition was you may not be able to re-size your Linux partition(s) to use it.

---

### Post by Bucky Ball on 2008-08-15
[QUOTE=jmsgz]to learn the system more i can mess with it some [/QUOTE]

Excellent idea! You will reach a section in the Ubuntu install that is the partitioner. You can have Ubuntu do this automatically (partition) or you can play around with sizes manually. Do the latter (after having sat down and made a bit of a plan, that is).

My personal preference? Start in the manual partitioner by deleting everything on the drive, then start creating your partition or going the automatic method. I am assuming here that you don't have Ubuntu on your machine at the moment, only XP which you want to get rid of.

You might have some fun with this page ...

[html]
https://help.ubuntu.com/community/HowtoPartition[/html]

Good luck ...

---

