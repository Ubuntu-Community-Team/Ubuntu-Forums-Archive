---
title: "Post install partition question"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by gyozu on 2012-01-31
Background:
HP6140 8GB ram   ~900gb HD
Dual boot install with Win7 - Ubuntu 10.04 LTS 64bit containing  a Virtualbox install of Linux Mint 12 32bit.

I upgraded from Vista and 9.04.
Everything went well and all three systems seem to perform properly.
I did the initial partition using the Windows tool. That left me with about 500GB for Windows and ~400GB for Ubuntu.

I have not reinstalled my backup files, photos, docs, video etc into Ubuntu.

In reading around, it seems it might have been a good idea to generate a /home partition. something about being easier to back up or reinstall. Not really sure why.

So, before i get any farther along, I think I would like to accomplish the following:

*Further reduce the Win7 partition as i don't think I want to devote that much space to an OS I will only use occasionaly. The Windows partition tool showed ~500GB as the lowest it would go.

*Add this space to Ubuntu.

*Add a /home partition.

*if possible, retain the VirtualBox install of Mint 12.


Question.
Can I do this on my existing setup or would it make more sense to go back to into Win7 to work on the partition and just rebuild everything all over?

Hope this all makes sense.

Here are a couple of screen shots that may be of use.
[IMG]http://i164.photobucket.com/albums/u13/gyozu/278c8a0f.png[/IMG]



[IMG]http://i164.photobucket.com/albums/u13/gyozu/965bcfa2.png[/IMG]

---

### Post by Mark Phelps on 2012-02-01
You CAN use Linux tools to shrink the Win7 OS partition as much as you want -- but shrinking farther than the Win7 tool allows risks filesystem corruption.

But, this can be fixed if you have an optical drive in your PC that you can boot from.  To do this, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  This can be used to repair the Win7 boot loader if you shrink the partition too much.

You can also try downloading and installing the FREE version of Partition Wizard in Win7.  It may allow you to safely shrink the Win7 OS partition more than does MS.

---

### Post by centaurusa on 2012-02-01
> **gyozu said:**
> 
I did the initial partition using the Windows tool. That left me with about 500GB for Windows and ~400GB for Ubuntu.


Both partitions are huge in terms of what is probably required.  Windows probably doesn't use more than about 40 GB and Ubuntu will run in 4 GB so, unless you have lots of apps installed, you should have a large amount of free space in either partition.  I would suggest creating a bootable GParted CD and use this partition manager to shrink one of the partitions and create an empty one.  

(See:  [FONT=Arial][SIZE=2][COLOR=#000000]http://www.dedoimedo.com/computers/gparted.html[/COLOR][/SIZE][/FONT])

You might also consider formatting the new "data" partition as NTFS. In this case, both Windows AND Ubuntu will be able to see the new "drive" and can access precisely the same files.  This also means that you can back up all of your data files easily since now they are separate from the operating system and the installed applications.
   


[FONT=Arial][SIZE=2][COLOR=#000000][/COLOR][/SIZE][/FONT]

---

### Post by cortman on 2012-02-01
> **centaurusa said:**
> 

You might also consider formatting the new "data" partition as NTFS. In this case, both Windows AND Ubuntu will be able to see the new "drive" and can access precisely the same files.  This also means that you can back up all of your data files easily since now they are separate from the operating system and the installed applications.


This. Keeping your personal files away from any OS also means they are much more safe and recoverable if your OS would crash.

---

### Post by Bartender on 2012-02-01
Did you recently install W7?

Here's why I ask.  Would it make more sense to simply start over again from scratch instead of trying to manipulate what's been installed?

If you've installed 7 and Ubuntu recently, and you have your personal data backed up safely, then it sounds to me like starting over might be much better.

gparted gives a better visual image of your partitions.  See screenshot attached.  I took this screenie a coupla minutes ago from gparted.  What you're seeing is a bog-standard dual-boot with separate /home partition. I don't know why or how the small unallocated bits were created but I'm not losing sleep over it.

In order to make screenshots like this, the simplest thing to do is to install gparted after installing Ubuntu.  After you've installed Ubuntu, go to Synaptic and search for "gparted" w/out the quotes of course.  I get 3 returns on our 10.04 rig.  Ignore the first one (drobo-utils) and the third one (partitionmanager).  You want the middle result, described as "GNOME partition editor".  Install it, find it under System>Administration.

If you decide to start over, I described what I like to do a coupla days ago in this [thread]("http://ubuntuforums.org/showthread.php?t=1915536&page=2").

I like to create the primary ntfs partition for Windows *first*.  Before installing Windows.  IMO this is way better than installing Windows first, then trying to tell Windows to move over.  Since Windows will ignore ext4 partitions, you can set up your Linux partitions first also, or just leave the space where you intend to install Linux unallocated.  I'm not sure about this, but Windows *might* try to incoporate unallocated space, so creating and formatting your ext4 and linuxswap partitions at the start might be the better way to go.

Question for you.  Have you made Vista recovery discs?  If you have, I'm guessing that the "Factory Image" partition shown in your screenshot can be blown away.  The machine came with Vista, right?  If so, that Factory Image would be Vista.  If you have a genuine W7 install disc, and you probably will not be going back to Vista anyway, all the more reason to delete it and use the space.

The last time I made recovery discs on a new HP, the HP instructions specifically stated that the factory image partition would be unavailable after making the discs and even suggested deleting the partition.  That's a gutsy thing to write in a user's manual intended for the general public...

If there's any such thing as a general consensus in the Linux community, I'm gonna go out on a limb and say that in general it's recognized that creating a separate /home partition is useful because you can install a new version of Linux to the / partition and leave all of your /home data alone.

There are four - well at least four - things to watch out for if you've created a separate /home folder and you're about to install a new version of Linux.  

Let's say that you're about to upgrade from 10.04 LTS to 11.04 LTS.  Your 10.04 LTS has a separate /home folder.  
1) You have to install the new version of Linux manually.  
2) You have to make absolutely sure to tell the installer to mount /home to your existing /home folder.
3) You have to make absolutely sure that you tell the installer NOT to format the /home folder.
4) You have to make absolutely sure that you use the same username/password as before.

I think I've probably done #2, #3, and #4 wrong at least once.  With #4, if you install using a different username, the installer will create a new /home folder with the new username.  You'll end up with TWO /home folders, and the OS will go to the new one automatically, NOT the old one.

---

### Post by gyozu on 2012-02-01
Thanks for the detailed reply.

A fresh install of Ubuntu and adding Mint 12 in Virtual box is certainly doable. Just takes a bit of time. From what you have posted I should be able to delete the exiting partitions and set them up with Gparted without to much difficulty.

> Question for you.  Have you made Vista recovery discs?  If you have, I'm  guessing that the "Factory Image" partition shown in your screenshot  can be blown away.  The machine came with Vista, right?  If so, that  Factory Image would be Vista.  If you have a genuine W7 install disc,  and you probably will not be going back to Vista anyway, all the more  reason to delete it and use the space.
Windows is a bit more of a problem and that may be due to something peculiar to this HP setup. Simply put, the Win7 home premium discs that HP sent me when they were available are an upgrade not a whole fresh install. I used the product key from Vista for the install. Literally took 14 hours to change things over from Vista. The kicker (from the installation sheet) is that if Vista pukes, I then need to reinstall Vista and then go back through the upgrade to Win7. However, I have not tried to generate a set of Win7 recovery discs since I did not think it was possible.

EDIT: Actually, I may be wrong here, but not sure how to confirm it. It may be possible to use the Win7 disk to do a clean install, it just won't transfer over my settings. Not sure and can't figure out how to sort that. However, it may be quicker to do this as a fresh instal rather than and upgrade. Any thoughts?

Two questions:

> Both partitions are huge in terms of what is probably required.  Windows  probably doesn't use more than about 40 GB and Ubuntu will run in 4 GB  so, unless you have lots of apps installed, you should have a large  amount of free space in either partition.  I would suggest creating a  bootable GParted CD and use this partition manager to shrink one of the  partitions and create an empty one.  Will I run into any problems using Gparted to reduce the Win7 partition to say ~100Gb?
I figure that is more than enough room, but the Windows disc tool wont go under the 500Gb setting.

The files that I backed up, using Crashbox, were on a FAT32 formated partition. Will trying to reinstall them on a NFTS partition cause any problems? Usual files, jpgs, avi pdfs, txt, mp3.

---

### Post by centaurusa on 2012-02-01
> **gyozu said:**
> 
Will I run into any problems using Gparted to reduce the Win7 partition to say ~100Gb?
I figure that is more than enough room, but the Windows disc tool wont go under the 500Gb setting.

The files that I backed up, using Crashbox, were on a FAT32 formated partition. Will trying to reinstall them on a NFTS partition cause any problems? Usual files, jpgs, avi pdfs, txt, mp3.

100GB should be lots.  I have Win 7 running in 20 GB on a 40 GB partition (with the pagefile moved to another drive, and the hibernate file deleted on a desktop machine).  I would be surprised if GParted wouldn't be willing to make the partition smaller than 500 GB, but I don't know why the Windows utility is objecting.

It won't make any difference to copy your "FAT32" files to an NTFS partition.  They will remain as .JPG, etc.  You could also format the new data partition as FAT32 if you wish.  Ubuntu and Windows won't really care.

---

