---
title: "questions about sharing partition between windows and ubuntu to store common files"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by 3-u1untu-2 on 2013-11-12
I just installed ubuntu over the weekend, after LOTS of hours reading and trying to understand what I needed to do get everything setup for dual boot on my notebook.  here's where I am now...

100MB (FAT32?) boot partition created by windows
40GB (NTFS) primary partition for Windows 7
40GB (NTFS) primary partition for Windows 8 (blank for now, will install someday)
10GB (ext4) logical partition for ubuntu root
2GB (swap) logical partition for ubuntu swap
340GB (ext4) logical partition for ubuntu /home

the 340GB was just the remaining space after the above partitioning.  I thought I needed a separate /home partition to allow installation of other/new Linux distros (based on the reading I've done).  I thought I'd be able to use the 340GB in both windows and ubuntu, but now that I'm all done, I realize that I can't do that at the moment.  First of all, I realize now that Windows will not recognize ext4 partitioning, so that needs to change.

So, do I just change the formatting of that partition to NTFS (or something else/better), or do I need to further partition that down to give a smaller /home partition for ubuntu (if so, what size?), then use the remaining space to share between OS's?

Sorry if this is covered somewhere, I've read and searched so much my brain hurts, and I've not found anything that addresses this specific question, so I thought posting here would be best/easiest.

Thanks in advance for any help!

---

### Post by Bashing-om on 2013-11-12
3-u1untu-2; Hi Welcome to the forum .

You have the guist of it right. To share data between Windows and ubuntu will require a separate "data partition" formatted NTFS.
For a shared /home 30 gigs is more than enough; Those with experience in that realm make it with 10 gigs and symbolic links.

This link is informative and may answer all your questions, else post back !
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[INDENT][INDENT]just my little bit to help
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-11-12
I originally started with Windows on one drive, Ubuntu on another and a shared FAT32 partition. Since converted shared to NTFS because of all the FAT32 limits and then stopped using XP, but have not converted shared NTFS data to my shared Linux formatted partition yet.

 I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

   Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by Nostronna on 2013-12-16
I have an additional question about shared partition..... I hpe it's the right thread...

I have ubuntu 13.10 and windows 8 in dual boot. I already have my DATA Partition NTFS, perfectly visible by both the OS, so up to now all good.
Only problem is: I'd like to have a few links to the folders I use most on my Ubuntu desktop....and I've made them but apparently every time I shut off my laptop they get broken and when I turn it on again they don't work anymore.
My guess is that this happen because every time I turn off Ubuntu, it unmount the DATA partition....is it? 
Whatever the reason....is there any way to make this links permanent? Now I need to re-made the links every time I turn on Ubuntu, and that doesn't make much sense!

Thanks!

---

### Post by Nostronna on 2013-12-16
Sorry...don't know why it's been submitted twice....how do I delete the wrong one???? :confused:

---

### Post by Irihapeti on 2013-12-16
Nostronna;

The duplicate post has been deleted for you.

In future if this happens, click on the "report post" button and report it as a duplicate. Staff will then take care of it.

Sometime the forum software plays up, which causes double posts.

---

### Post by jimmyh1972 on 2013-12-16
[[COLOR=#000000]3-u1untu-2[/COLOR]]("http://ubuntuforums.org/member.php?u=1880622")[COLOR=#000000] fisrt of all - you don't have to apologize helping & sharing information & knowledge is what the open source community is all about.
now about your issue - to share information / files between Linux & windows partitions must be formatted to NTFS or FAT (NTFS is better) 
[/COLOR][COLOR=#000000]Linux[/COLOR][COLOR=#000000] systems can read the NTFS format but windows cant read EXT4
if you want to dual boot your machine you should make a partition of EXT4 (for Ubuntu 100Giga is more than enough assuming your gonna' share your doc's video music etc.)
you should specify a start point to Ubuntu - / (for root)
/home is not really needed in will be included in your system and if you will share your files its u[/COLOR]nnecessary.
Allocation to SWAP is necessary also (10 -20 % of the system size is good) 
[COLOR=#000000]ant last put GRUB on the main hard drive and not on one of the partitions (otherwise windows won't boot)
Good luck - enjoy Ubuntu:-)


[/COLOR]

---

### Post by Mark Phelps on 2013-12-16
Windows 8 automatically hibernates when you do a shut down -- unless you have gone to the extra effort to disable Fast Startup.  Unlike with previous Windows versions, the hibernation in Win8 keeps the OS partition, and any data partition you had open when you shut down, still MOUNTED -- which then prevents you getting access to it from outside.

That's probably why your links won't work when you boot into Ubuntu.

You would have to disable Fast Startup in Win8 in order to truly share the data partition.

---

