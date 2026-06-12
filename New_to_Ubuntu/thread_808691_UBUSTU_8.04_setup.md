---
title: "UBUSTU 8.04 setup"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by MWSTX on 2008-05-26
I'm only about 4 days into my linux experience and I am already 100% sold.  Since I will still have XP on my machine at work, and after looking long and hard to make sure there wasn't something in Vista I would miss on my laptop, I have decided to strike all reference to microsoft from it.  For several reasons (including "well, it can't hurt...") I am running DBAN on it right now.  Since I have a few more hours to kill, I thought I'd see if I can get a few questions answered.

Aside from wasting hours on the web, my primary use for this computer will be audio recording (Ardour2 looks cool so far).  Once DBAN is done I am going to do a fresh install of Ubuntu Studio 8.04 (64 bit).  The machine is an HP Pavillion dv9225us w/ AMD Turion64x2 (2gig) with 2G of RAM and one 160G hard drive.  I have the following questions regarding partitioning:

1)  If I understand correctly, I can install everything on the drive without partitioning it.  However, I have read a lot over the last few days (translation: read enought to get myself into trouble) about increasing performance and making it easier to re-install/update the OS by putting /Home on a seperate partition.  Any reason for a linux noob not to do this?
2)  If I do put it on another partition, how much space will Ubuntu Studio 8.04 require (how can I figure out how big to make the root)?
3)  I've read some differing opinions on swap partitions.  Given what I want to do with this machine, how big should I make it?  How big is too big?  Does there cease to be any benifit after a certain size?
4)  Where should I put the swap partition? (beginning, middle, end?...)
5)  Having figured out those two partitions, I'm wondering if I should make others for current or future needs.  Would it be a good idea to have the data files associated with the audio recording (Ardour2) on their own partition?  I have read (misc. article, not related to Ardour) that you should make several partitions since due to the way partitions are set up you can only add to the end of one.  If you wanted to increase the size of partition 'X' you would have to have space available after 'X' (an empty partition, or one that could be emptied), although I'm not sure if that applies to logical partitions.  I might someday get an external hard drive either to keep the recording files on and/or to back up all of my personal/data files and I want to keep that in mind as I plan.
6)  If I do make several partitions, in what order should I put them (for hard drive efficiency) and what type of file system should I use (should they all be ext3 or could one or more of the partitions be better served with a different file system depending upon what is on that partition).

I've tried to research all of this but I feel like I'm only gleaning bits and pieces from several web sites and posts, all of which pertain only partially to what I'm trying to figure out.  I thought it would be better to describe my machine & goals and see what people suggest.  Like I mentioned earlier, I'm a complete noob to Linux but I was more than just a point & click user of windows (not an I.T. pro but more advanced than your average layman).  I'm excited about getting this installation off to a good solid start.

---

### Post by cardinals_fan on 2008-05-26
> **MWSTX said:**
> 
1)  If I understand correctly, I can install everything on the drive without partitioning it.  However, I have read a lot over the last few days (translation: read enought to get myself into trouble) about increasing performance and making it easier to re-install/update the OS by putting /Home on a seperate partition.  Any reason for a linux noob not to do this?
2)  If I do put it on another partition, how much space will Ubuntu Studio 8.04 require (how can I figure out how big to make the root)?
3)  I've read some differing opinions on swap partitions.  Given what I want to do with this machine, how big should I make it?  How big is too big?  Does there cease to be any benifit after a certain size?

1. Having your data on a separate partition is a good idea.  Making it /home is fine, but sharing a partition mounted as /home in more than one OS can be very dangerous.

2. You can install Ubuntu Studio right on top of regular Ubuntu.  Read this for Hardy (8.04): [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy)

3. With 2 gigs of RAM, you won't use much swap.

---

### Post by oedha on 2008-05-26
1. separate /home will be lot of help in re-installing ( i didnt make this...will be answered later on )

2. Ubuntu consume less space than windows...i just made only 8GB for root

3. Swap usually 1.5 - 2 times of RAM but since you have a big RAM...just make it 512MB only ( some people said you dont need swap anymore...... )

4. i put my swap at very end of partition table

5&6. i made 4 partitions on my drive
              1st = ntfs for my windows system
              2nd = ntfs for both of winlin data
              3rd = ext3 for /
              4th = swap
   for you....if you want to make separate /home...you have to make at least 5...if not...you can just   do like what i did...and i used NTFS for data partition and working well for me since ubuntu 7.04

maybe you should read :==> [http://psychocats.net/ubuntu](http://psychocats.net/ubuntu)
and [http://help.ubuntu.com/community](http://help.ubuntu.com/community) 
( for more help :) )

EDIT : my 2nd partition is not defined as /home but as sharing partition for both data

---

### Post by MWSTX on 2008-05-27
Thanks for the help but now I have bigger problems.  After a complete and total wipe of my hard drive, I tried to use the Ubuntu Studio 8.04 DVD that I burned for the 64 bit installation and almost got through it without problems.  On what looks like the last step of the installation process (right before I should see a pretty UBUNTU STUDIO graphic) I got a message that told me that the installation failed. It asked me if I wanted to go back and fix the failed step ("install new software" or something like that).  Doing that does not help.  None of the menu options would do anything to fix the problem or get me out of the set up menus so I gave the machine the 3 finger salute and now it will only boot to a linux command prompt:   blahblah@blah:~$
It WILL NOT go back to the Ubuntu Studio setup and it WILL NOT boot from a live cd (I have a regular Ubuntu 8.04 cd that I have sucessfully used a few days ago).  My dream of a clean install has backfired.  How do I get this machine to do anything other than blah:~$  ?

---

### Post by MWSTX on 2008-06-04
Thanks for all the help.  What I thought was my regular Hardy live CD turned out to be a mislabeled disk.  Everything worked out once I burned a new copy of the Ubuntu Studio DVD (from a different site).  My system seems to be healthy know and I'm just working through a few quirks.

---

