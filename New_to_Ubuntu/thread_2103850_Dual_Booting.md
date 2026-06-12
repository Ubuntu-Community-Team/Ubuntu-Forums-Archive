---
title: "Dual Booting"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by StardustLuna on 2013-01-11
Okay guys so around September my windows crashed and basically erased itself while I was trying to recover factory settings. So I installed ubuntu by itself on my laptop. Worked perfect except for a few minor details that I was slowly fixing. (brightness issues, getting Blu Ray disks to work). 

And then came thanksgiving. At the airport the TSA guy was rough with my laptop which resulted in me needing to send it in to get fixed. The solution was that they replaced it. Now I have the same laptop, except for the fact that I have a working form of Windows 7 on it. 

Now, I would be more than happy to just wipe it again and install Ubuntu. However I am an dig art student, so I need to use Photoshop, Illustrator, along with several other programs for the online classes I'm taking. I know that there is wine. And I've seen Photoshop CS6 working in 12.04 (the version of ubuntu I have), but I know that it is a pain to do so. 

**Bottom line I really, really, really, would like to dual boot. **

My problem? My USB which has the installation and 'live CD' setup on it detects 'multiple operating systems' because windows made 4 primary partitions and so my only choice is the 'do something else'. Which I know requires to manually partition the hard drive. I've seen people do it with the disk manager on windows and with GParted. I've also seen people make separate partitions for swap, root, and home, and some who just made a swap and root. And of course there's the question of how much swap I need. Some say twice as much as ram, others say 1.5x, and some say only 2GB is needed regardless of ram. I also need to delete one of my primary partitions. And so I need to know how to do that as well and pick one that isn't, ya'know, super important. :/

[IMG]http://i226.photobucket.com/albums/dd149/SpyroxCynder/DiskSpaces_zps184c3269.png[/IMG]

I have windows all backed up and recovery disks made in case of an error. Though I really want to avoid that obviously. 

[B]System Specs:

HP Pavilion dv7
i7 processor
750 GB hard drive
6 GB RAM
Windows 7 Home Premium 64 bit

Version of Ubuntu I want to Install: 12.04 LTS 64-bit.

[/B]Since I'd only be using windows for art stuff, and Ubuntu for all of my music, papers, and such, I think I'd only need 250GB for windows, and the rest, 500, for Ubuntu. I also have a sizable external Hard Drive that I'd save most of my work to anyway. Therefore, having enough space isn't an issue. I just want to make sure that I allocate enough to each of my partitions for both windows and Ubuntu to work properly. 

I know people have asked this before, but I'm just weird in that I need a process to use that's specifically for my situation. I need someone to say "do A, B, and C, and hit Enter" sort of thing. 

Sorry about the long post, but it took the repair place almost a month to get my laptop back, and now that school has started I cannot lose it.

~Stardust

---

### Post by audiomick on 2013-01-11
Hi. 

This will lead you to some good info on partitioning.
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

This is a bit bare, but will show you more or less the steps involved in setting up a dual boot.
[https://help.ubuntu.com/community/DualBoot/Windows]("https://help.ubuntu.com/community/DualBoot/Windows")

Now to your specific situation:

Do not forget to back up any important files you have on the machine before you start doing any partition work. This is important. The process is not dangerous as such, but something like a power out or a tragic mistake can have dire consequences.

You will need to get rid of one of those partitions, but you know that. If you have created your recovery disks, you should be able to remove the recovery partition without a worry. The other candidate might be the HP tools one. I don't know what is in there, and it is possible, I suppose, that you might lose some special HP functionality if you remove it. I have read that there is nothing much useful in there, I think, but I can't guarantee that. Perhaps a little searching in the internet would yield some info on what is in there, although I believe I have also read that it is hard to find out exactly what is there. You definitely need to keep the small system partition at the front and the large NTFS partition.

Use the windows tool to resize the windows partition. (You can use the Linux tools to delete whichever it is that goes.) The windows tool is easy to use, and it is the one the manufacturer intended to be used on that system. Shrink it down to whatever you want to give to windows. If you really are consisitent about saving your data to a data partition or an external, you can probably go down to as little as 50GB or so. I believe 30, or maybe 40, is the recommended minimum for Win7. I would suggest having an NTFS data partition, but I will get to that.

Oh, you should do a de-frag before you resize. Since the laptop is new, it probably wont be all that necessary, but you should do it. On an older drive that has seen a lot of use, I gather it can be beneficial to de-frag a couple of times.

Once you have re-sized the windows partition, you should re-boot a couple of times and give Windows a chance to run the disk repair utility if it wants to. Once you have Windows happy, you can move on.

I use gparted from the ubuntu live environment to do my partitioning. That means: boot into the "try without installing" option from the (preferably USB: runs faster) installer. 

Regarding Swap: the real deal is that you need an appropriately sized swap space if you want the hibernate function to work. If you don't, you might well be ok with as little as 1GB swap. The advice to use swap=twice RAM is obsolete. It dates back to times when 256MB was a real lot of RAM. ;)

However, you say that you are not that concerned about drive space, and that you are a Digi art student. The latter implies that you are likely to be doing RAM intensive work like image editing and perhaps video editing, so I would suggest being generous with the swap rather than scrounging every last GB on the drive for storage space.

The thing with hibernate is that it writes the contents of RAM into the swap space to be recovered when the computer is woken up. The required size for this is swap = RAM in GiB, not GB. I tend to use about a half a GB more swap than I have RAM. I don't have much of a bother with drive space, so I don't miss what is used for swap. I tend to see 1GB here or there as storage space to be more or less irrelevant. If I need to worry about 1GB, then it is probably time to start looking at alternative storage space.

On to partitioning: the first step of all is to create an extended  partition in the empty space. Everything else can be a logical partition inside that.

I would suggest doing that, and creating a swap partition first of all. I like to put my swap down at the end of the drive, or in this case the logical partition. The reason for this is that if I have to change around the other partitions for any reason, if the swap is at the end it is not in the way and doesn't have to be moved.

When you have your swap, you might like to re-boot the live environment. It will mount any swap it finds on the drive and use it. This should make the subsequent steps faster.

I like to create a separate /home partition. Doing this has saved me considerable bother a number of times when I have done fresh installs. An existing /home partition, assuming it is not corrupted, can be simply re-mounted during the install process, meaning that any data and user config files will be in place when the new install is finished, rather than having to manually put them back in.

Given that you are dual booting, you might like to make an NTFS data partition. To be quite honest, I don't know if your windows system would then find this automatically, or if you would have to mount it manually somehow in windows. If you make it before you do the Linux install, you can mount it during the process. Alternatively, it will appear in the file manager and can be mounted as needed by clicking on it.

The advantage of an NTFS data partition is that it can be read by both windows and Linux. In my case, this is useful for stuff that I get for work via e-mail. I don't go in the internet with windows if I can possibly avoid it, so generally I download the attachments in Ubuntu and store them onto the NTFS data partition on my laptop from there to be available when I am booted into windows for work.

Also, according to what I have read, it is possible that writing to the windows system partition, particularly with Win7, could give you trouble with the windows install. I can't vouch for the truth of it, but I feel better about having the data on a separate partition. If you should have to re-install the windows, you might be able to re-mount it there too. I'm not sure about that, though.

Given all of that, partition sizes:

We have dealt with swap.

This machine has used less than 4GB for the 10.04 install that is on here. On the other hand, I recently had to enlarge the / partition for a friend of mine (for the second time) because the available 7GB or so was full. Doing this is a pain. Not difficult, but time consuming. In the light of this, I like to allow at least 15GB for the system in /. I think my desktop, which has an 80GB SSD just for the system and 2.5TB on top of that, has around 20GB for the current / on there. The rest of the SSD might get used for experimental installs at some time in the future.

For the /home partition: that depends on how much space you have in total, how much of it you give to a possible NTFS data partition, and how you deal with your home partition. 

/home will contain a /home/username partition for every user you create on the system. In this directory, the system saves all the personal configuration files for that user (as hidden files), and the default store path leads to there or directories like Documents and Downloads and Pictures and so on in there. You should leave the hidden config files in peace. I don't even know how to change how the system deals with them, and I don't think it advisable to even try to mess with that. As far as the personal data files go, you can either let the various programs store to there, change the default storage path in the various programs, or use "save as" to specify a different location (which is what I usually do).

If you leave the defaults as they are, you can use symlinks in the /home/username directories to link to the actual data files in another location. I have read here of one user who claimed that by doing this, he could keep his /home as small as 1GB, but I don't bother with this method.

Basically, you have to decide how you are likely to be dealing with your files and divide the available space accordingly. If you want to use an NTFS data partition, you might do well to go half and half for it and your /home and see how things develop. Put them next to each other, and then if you need to shuffle space in the future it is just a matter of shrinking one and growning the other into the space. If they are not adjacent, you would have to move the partition in between, which makes the process considerably longer.

A word to the wise to close with: you are most unlikely to guess a perfect partition plan the first time, so just go with your best guess. You might have to shuffle a bit at a later date, but that is not too tragic. Put / at one end of the extended partition and /swap at the other, and you shouldn't have much bother with doing that if you need to.

---

### Post by oldfred on 2013-01-11
II think audiomick has covered all the issues.

I do really also recommend the separate NTFS shared data partition. I liked having Firefox & Thunderbird with all the same info in both systems. I have the profiles in my shared NTFS and use the same profile in all my installs.
Best to set the Windows system partition as ReadOnly in Ubuntu. Then you are less likely to cause issues in Windows from Linux. Windows just does not like too much outside activity or we as users often corrupt something.

Also good to have your own repairCD. Best to have repairCD or liveCD/DVD/Flash for the current version of every system you have installed.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
    
       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by StardustLuna on 2013-01-11
Thank you both so much! Right now I'm trying to catch up on homework, but once that's all said and done I'll try and tackle this. I can't believe that HP and Windows made all the partitions primary! I bet it was to deter people like me to go through the process of dual-booting. 

Also, I created a Recovery Disc, and then made a System Image on my external Hard Drive. That should take care of back up and all right? Or do I need to create a separate installer disc? 

Just to be sure though, when I partition my hard drive, it'll then look something like this:

Windows Installer partition
150 GB for windows (I'm choosing this much so that I won't have to worry about it for a while. Photoshop and Illustrator are ginormous now, not too mention In Design and any others that I'll eventually get)

----Extended Partition----
30 GB for /
550 GB for NTSF & /home
10 Gigs for /swap. This might be overkill, but I'm not hurting for space and as long as it won't hurt it, I won't mind. 

Oh, and which one of the Linux partitions will be a primary partition? Or should I just make them all logical ones inside the Extended Partition?

~Stardust

---

### Post by oldfred on 2013-01-11
You have to keep both Windows boot 100MB and main install as primary. If you keep recovery and only delete tools, you only have one primary which must then be the extended partition. That then can hold all the Linux partitions and a NTFS data partition if you want.

So all the new partitions will be logical. You cannot make /home NTFS as it has to be Linux formatted. Only a separate shared data partition will be NTFS.

---

### Post by StardustLuna on 2013-01-11
So the extended partition will become the new fourth primary correct?

And I think that I'll leave the HP Tools partition, and just delete the recovery one. Since apparently if you upgrade the HP software, it'll re-add the partition. That seems like something that I would do or enable without really thinking. ahaha.

---

### Post by audiomick on 2013-01-12
> **StardustLuna said:**
> So the extended partition will become the new fourth primary correct?


Yes, this is correct.

Sounds like you have a plan, then. Good!

---

