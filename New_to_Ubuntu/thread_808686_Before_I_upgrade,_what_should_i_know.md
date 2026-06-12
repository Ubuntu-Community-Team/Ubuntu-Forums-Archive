---
title: "Before I upgrade, what should i know?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by dreadh3ad on 2008-05-26
I am preparing to do a fresh (reformat) install for 8.10, what should I know?

Are there any tips or tricks for upgrading?

Should I have a separate home partition?  

How much space do I actually need for the root file system?

I use rhythmbox as my music player but I often had to rename and reorganize some of my ripped music.  I would rather not do this again, is there anyway to avoid this problem?  ie: any config file I should save?

---

### Post by adobrakic on 2008-05-26
8.10? I thought the latest version was 8.04

---

### Post by bwhite82 on 2008-05-26
You might want to decide whether you want an encrypted installation now or not because you can't later encrypt the filesystem.

---

### Post by akiratheoni on 2008-05-26
> **adobrakic said:**
> 8.10? I thought the latest version was 8.04

I believe that there is an alpha or something (maybe even pre-alpha, lol) of 8.10 but I dunno for sure.


> Should I have a separate home partition? 

Yes.

> How much space do I actually need for the root file system?

About 10GB is good, though if you need to, you can go as low as about 5-7GB.

> I use rhythmbox as my music player but I often had to rename and reorganize some of my ripped music. I would rather not do this again, is there anyway to avoid this problem? ie: any config file I should save?

From my experience with music, renaming it edits the ID3 tag so you shouldn't need to rename the music as it should still be renamed.

---

### Post by iansane on 2008-05-26
Not sure how, but there are how to's on the seperate home partition.

You could do that before you reinstall and keep home partition intact to use in new installation I think.

---

### Post by sam_delta on 2008-05-26
yeah, its 8.04

about the partitioning, i think its a good idea to keep your home partition separate as this will save alot of time in further installations, and youll have same data/settings even on a fresh install.
the file system should have a good 10gig, if you want to feel safe or you have alot of HDD space, go for 15gig , btw i think 15g is alot. 20 gig its just a overkill for the filesystem

sam

---

### Post by kk0sse54 on 2008-05-26
You have to know the meaning of life.......other than that can't think of anything. I upgraded a computer to 8.04 a few weeks ago without even realizing it (yes I know wasn't paying attention #-o) but went without a hitch and it continues to work perfectly :). Another thing you might want to consider is a fresh install. Back up your home folder and just wipe the partition clean. Some people prefer this way because you start with that nice new fresh feeling.

---

### Post by kk0sse54 on 2008-05-26
O yea and I definitely agree with everyone else, consider making a separate home partition

---

### Post by akiratheoni on 2008-05-26
> **C!oud said:**
> You have to know the meaning of life.......other than that can't think of anything. I upgraded a computer to 8.04 a few weeks ago without even realizing it (yes I know wasn't paying attention #-o) but went without a hitch and it continues to work perfectly :). Another thing you might want to consider is a fresh install. Back up your home folder and just wipe the partition clean. Some people prefer this way because you start with that nice new fresh feeling.

The last upgrade I did (6.10 to 7.04 I believe) went fine as well, but I always enjoy doing a fresh install, since it's less prone to errors.

---

### Post by Unstuck on 2008-05-26
You can follow [this]("http://www.psychocats.net/ubuntu/separatehome") Psychocats how-to to create a new /home partition.  When I did it, I ran into a few problems; [here]("http://ubuntuforums.org/showthread.php?t=806909") is the thread that got me through the problem.

When you set up the partitions during installation, format the partition that will hold the OS with the ext3 file format and mount as "/"; /home will be automatically detected if you create the partition as noted above before you reinstall.

Good luck.

---

### Post by dreadh3ad on 2008-05-26
Yes i meant 8.04 my mistake.

Im looking through my home directory and there are a number of folders that begin with "."  What exactly are these?

---

### Post by Unstuck on 2008-05-26
folders that begin with a period are hidden folders.  they usually hold settings.

---

### Post by Thorndeux on 2008-05-26
> **dreadh3ad said:**
> 
Im looking through my home directory and there are a number of folders that begin with "."  What exactly are these?

They are hidden folders, which means you can only see them when you specifically ask for it (press Ctrl+H to toggle hidden folder on/off). Usually they contain configuration files for certain applications, like savegames or settings.

---

### Post by philinux on 2008-05-26
> **dreadh3ad said:**
> I am preparing to do a fresh (reformat) install for 8.10, what should I know?

Are there any tips or tricks for upgrading?

Should I have a separate home partition?  

How much space do I actually need for the root file system?

I use rhythmbox as my music player but I often had to rename and reorganize some of my ripped music.  I would rather not do this again, is there anyway to avoid this problem?  ie: any config file I should save?

Separate home partition - yes. Makes reinstalling real easy.
Root file system - 10 gig is good
Backup your home folder, bookmarks from firefox email from thunderbird etc.

---

### Post by HoldSteady on 2008-05-26
> **philinux said:**
> Separate home partition - yes. Makes reinstalling real easy.
Root file system - 10 gig is good
Backup your home folder, bookmarks from firefox email from thunderbird etc.
The thing I've yet to find is an illustrated, step-by step guide that walks a user through the manual partitioning option in the install process to explicitly show which partitions to keep (i.e., /home) and which to reformat.  Double-points for setups featuring multiple hard drives and/or Operating Systems (like mine).

I'm planning on jumping from my current Feisty install to Hardy, but even though I have my /home backed up on an external drive and JungleDisk, along with a tar of my entire current system, I'm still hesitant to pull the trigger for fear of ending up in permissions/grub/fstab hell.  I think I'll wait for 8.04.1 (and FF3 Release) anyway.

---

### Post by CrazyCanuck on 2008-05-26
I just installed Hardy 8.04 on a fresh 10 gig hard drive, and it was rather painless.  After I installed all the patches, downloaded all the packages I was interested in, I was at a 5.5 gig footprint, fully installed and working fine.  I have decided to move to Ubuntu for business with some fun (read: GAMES yay!) on the side.  Doing a fresh install means you will obviously have some customization ahead of you, but look at it this way.

You will have 8.04 around for 3 years for the desktop, and 5 years for the server version, so have at it!  Have fun with your install!

CC

---

