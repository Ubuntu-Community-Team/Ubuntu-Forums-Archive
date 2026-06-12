---
title: "About to Install 8.04 -- Partitioning Advice"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by svk on 2008-05-03
Hello,

I'm planning to dual-boot Vista and Ubuntu. I have about 70 GB of unallocated space where I plan to install Ubuntu.

I'm currently planning how I'm going to partition this 70 GB of space.  Here are some things I would be interested in:

[LIST=1]
[*]In the future, I would like to try other Linux distributions, and perhaps even have more than one installed at the same time.
[*]I would like an easy way to share data between Vista and Ubuntu.
[*]Based on a couple bad experiences in the past, I want my personal files to be stored on a partition separate from the main installation (in case an upgrade goes wrong like it did last time).  I hope it would make it easier to do a fresh install but keep all my data.
[/LIST]

Based on a little research, I would not only want to have a separate /home partition, but also a separate /data partition (to satisfy interest #1).  As I understand it, the idea is that you have a separate /home partition for every distro you have installed, and just one /data partition that is shared between all distros.

I've performed the Ubuntu installation several times in the past, so I'm not too afraid of using the partitioner and actually setting this up.  However, I do have some questions about how partitions work and how I should make use of this particular partitioning scheme:

1. If all of my files will be stored on the /data partition, then I understand that I should make it pretty large.  However, how much space should I leave for a typical /home partition?  Other than storing config files for each individual distro, are /home partitions used for anything else in this scenario?

2. Suppose I have several distros installed, each with their own /home partition.  Will each distro know which /home partition it is supposed to use?  Are partitions distinguished by something other than the name of their mount point?

3. Again, suppose I have several distros installed.  Besides each distro having its own /home partition, does it also have its own root partition?

4. I had trouble finding this on google: how much space does Hardy Heron require?

5. Is it preferable to use up all the available space right now and shrink it when I install other distros? Or should I leave space unallocated?

6. How would I go about making the /data partition accessible from Ubuntu?

7. I want to be able to easily share data between Vista and Linux.  I was thinking about setting up a /share partition, formatted as FAT.  But then there's the ext2 IFS driver from [www.fs-driver.org](www.fs-driver.org), which makes ext3 accessible from Windows.  Would you recommend I make the shareable FAT partition, or is there basically no need for it?  Which is better?

I'll appreciate any advice whatsoever.  Thank you in advance for the help!

---

### Post by iSplicer on 2008-05-03
> **svk said:**
> Hello,

1. If all of my files will be stored on the /data partition, then I understand that I should make it pretty large.  However, how much space should I leave for a typical /home partition?  Other than storing config files for each individual distro, are /home partitions used for anything else in this scenario?

2. Suppose I have several distros installed, each with their own /home partition.  Will each distro know which /home partition it is supposed to use?  Are partitions distinguished by something other than the name of their mount point?

3. Again, suppose I have several distros installed.  Besides each distro having its own /home partition, does it also have its own root partition?

4. I had trouble finding this on google: how much space does Hardy Heron require?

5. Is it preferable to use up all the available space right now and shrink it when I install other distros? Or should I leave space unallocated?

6. How would I go about making the /data partition accessible from Ubuntu?

7. I want to be able to easily share data between Vista and Linux.  I was thinking about setting up a /share partition, formatted as FAT.  But then there's the ext2 IFS driver from [www.fs-driver.org](www.fs-driver.org), which makes ext3 accessible from Windows.  Would you recommend I make the shareable FAT partition, or is there basically no need for it?  Which is better?

I'll appreciate any advice whatsoever.  Thank you in advance for the help!

1. Forget about having separate /home partitions. Its useless for your scenario, so I suggest having one huge FAT32 DUMP that all linux distros AND windows can write to. Forget about /data partitions as well. No, /home partitions are just for storing data. If you dont have a separate /home partition, it will still be there as a normal directory.

2. Refer to #1

3. The only thing each distro needs is a separate /root partition and one common swap partition that all can use. If you have 2GB RAM+, you can ignore this.

4. 4GB

5. Leave space unallocated for other distros, 10-15GB for each is plenty.

6. See #1

7. See #6 (lol)

---

### Post by Paqman on 2008-05-03
> **svk said:**
> Hello,
As I understand it, the idea is that you have a separate /home partition for every distro you have installed, and just one /data partition that is shared between all distros.

Other way around. /home is a bit like the Documents and Settings folder in Windows. It contains each users config files. As many distros as you like can share one /home. User data is stored under /home/username/. Just set up different users on each distro then they won't clash with each other.

Each distro will need a seperate root partition (abbreviated /). This is where the actual system files are installed for that distro. Since you've separated your data they don't need to be big. 10GB would be enough, although I give them a bit more just in case. 

> 
4. I had trouble finding this on google: how much space does Hardy Heron require?

/ will only take up about 3Gb-ish on a clean install, but that climbs as you install packages. You might also need space for temp files and such.
/home can be as big as you like. If it's not storing data i'd give it no less than 5GB for multiple user setups though. If it is storing data, max it out.

> 
5. Is it preferable to use up all the available space right now and shrink it when I install other distros? Or should I leave space unallocated?

Up to you. I tend to have two 20GB partitions that I use as root partitions. Sometimes one is a spare if i'm only using one distro. It's nice to have it standing by if you get a sudden urge to try another distro. Shrinking and moving partitions can be very slow, so you don't want to do it to often.

> 
7. I want to be able to easily share data between Vista and Linux.  I was thinking about setting up a /share partition, formatted as FAT.  But then there's the ext2 IFS driver from [www.fs-driver.org](www.fs-driver.org), which makes ext3 accessible from Windows.  Would you recommend I make the shareable FAT partition, or is there basically no need for it?  Which is better?

FAT32 is terrible, I wouldn't use it. If you really need a shared data partition NTFS is probably easiest, since both Windows and Ubuntu can use it. The drawback is that it will need to be defragged.
If you're going to store data on it's own partition, you don't need such a big /home, since it'll only have config files in it.

One problem you will encounter is that you will need to use an extended partition. A hard drive can only contain a max of four primary partitions. Your setup would call for at least six: 

#1 NTFS Windows
#2 Ext3 Linux / 
#3 Ext3 Linux / (spare)
#4 Ext3 Linux /home
#5 NTFS Shared Data
#6 Swap

You can get around this by creating a special type of primary partition called an extended partition. This can contain as many partitions as you like.

---

