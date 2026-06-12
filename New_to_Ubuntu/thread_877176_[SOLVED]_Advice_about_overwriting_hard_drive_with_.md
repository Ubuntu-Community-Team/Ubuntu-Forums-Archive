---
title: "[SOLVED] Advice about overwriting hard drive with Ubuntu?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Epetai on 2008-08-01
Hello - I'm brand new and I've looked in the forums to see whether anyone has asked this before, but I don't think so...

**Background:** 14 months ago I bought a Gateway PC Desktop that ran Vista.  A couple of months ago, I successfully partitioned the hard drive and installed Ubuntu 7.10.  All was well with my dual boot, everything worked fine.

**The Problem:**  My Vista has suddenly become horribly unstable  with repeated crashes.  I cannot fix it myself and I'm not sure what's wrong, but Ubuntu seems to be working just fine.  So I've decided I want to bin Vista and I want to completely *overwrite both operating systems* with Ubuntu 8.04.  

**My Question:**  (I'm a complete newbie at this...)  I want to go back to a single partition with a single operating system (Ubuntu).  Should I "reformat" my hard drive first?  A friend told me about GParted and I have successfully installed it - should I use it to get rid of the "Windows side" of the partition first?  Or should I just boot straight from a Live CD and overwrite when it gives me the option?

What's the safest, most stable way to go?  

Technical stuff (from memory): Gateway PC, 2Gb RAM, 1.8GHz, 160Gb hard drive

---

### Post by LowSky on 2008-08-01
ubuntu live cd has an option to use the entire hard drive while installing. BUT What I would do is choose manually set up partitions,  delete all existing partions, create a / partion, then a /home partition, then a swap partition. goive / (root) like 15GB, home (as much as you would like) and swap (512MB) a good idea is to creat a forth extended partion for files you may want to share like media

---

### Post by DGortze380 on 2008-08-01
1) Be sure you have actual recovery disks from gateway. You'll need them if you ever change your mind. If you don't have recovery disks, you probably have a recovery partition. Check in windows if there is a way to create recovery disk.

2) Back up all the files you need off both Operating Systems, they will be gone forever after step three.

3) Boot the Ubuntu Live CD, choose Install Ubuntu, when the installer asks about partitioning, choose guided, use entire disk.

4) Wait for the install, put all your files back on, you have a clean install of Ubuntu and the best part... no more Vista

---

### Post by Elfy on 2008-08-01
It would certainly be the easiest way to use the "install to whole drive" option in the installation procedure - it will do that and reformat it.

That will overwrite the vista and the existing ubuntu - if there is anything you need to keep back it up - by from the tone of your post I'd assume not.

Personally I would probably use gparted to resize the existing ext3 to ~10GB and create a new ext3 in all the remaing space to use for /home or as a data partition.


Edit - regarding swap - if you hibernate then you will need swap to equal or be greather than your RAM

---

### Post by Epetai on 2008-08-01
These are all very helpful - thank you.  I think (for me) the easiest option would be to install from the Live CD as has been suggested.  And if you think that's going to be a safe as well as an easy way of doing it, great.

(Back-ups are already made, but thanks for the reminders anyway! :)

---

### Post by t0p on 2008-08-01
> **Epetai said:**
> I think (for me) the easiest option would be to install from the Live CD as has been suggested.  And if you think that's going to be a safe as well as an easy way of doing it, great.


I'm very glad for you that you've decided on an Ubuntu-only installation.  And yes, installing from the CD to use the whole disk is indeed the easiest option.  But I'm a little curious what you mean here by "safe".

You said you intend to scrape the Vista off your hard disk drive.  So obviously you don't mean it'll be "safe" because it will leave Windoze data intact.  And you're writing over your previous Ubuntu install, so you don't mean it's "safe" because it leaves the previous Ubuntu partition intact.

Maybe I'm worrying over nothing - but I would like to know what you mean by "safe".

---

### Post by DGortze380 on 2008-08-01
> **t0p said:**
> I'm very glad for you that you've decided on an Ubuntu-only installation.  And yes, installing from the CD to use the whole disk is indeed the easiest option.  But I'm a little curious what you mean here by "safe".

You said you intend to scrape the Vista off your hard disk drive.  So obviously you don't mean it'll be "safe" because it will leave Windoze data intact.  And you're writing over your previous Ubuntu install, so you don't mean it's "safe" because it leaves the previous Ubuntu partition intact.

Maybe I'm worrying over nothing - but I would like to know what you mean by "safe".

Sounds like he's afraid of screwing up the partitioning, which really isn't a problem because everything will get deleted anyways, you can always just repartition again.

---

### Post by louieb on 2008-08-01
Just something to think about. 
Why not just fire up the live CD and reformat your vista partition to ext3.  Then you can use it to store your music, photos  ...  whatever.  The nice thing about having your data on another partition is it stays out of the way  when doing upgrades or a reinstall.

---

### Post by Epetai on 2008-08-01
> I'm a little curious what you mean here by "safe".

You said you intend to scrape the Vista off your hard disk drive. 
I absolutely, completely want to get rid of Vista.  Everything (data, programs) that I want from that hard drive has been backed up.  I want nothing except Ubuntu as an operating system, and I don't want to keep the partitions I set up a couple of months ago.

What I meant by "safe" (and you're right, it's possibly the wrong choice of word) was that Ubuntu would install and run okay if I just overwrote the entire hard drive using the Live CD.  I didn't want to find out afterwards that I "should" have done something else first, like manually delete the Vista partition.  And I also wanted to be absolutely sure I would remove any trace of Vista by doing this.  (I'm not Vista-bashing in this thread, but I *really* don't get on with it and I want it off my machine...)

I've never done this before, and my query stems from the fact that I played with the partitions a couple of months ago (using the Vista partition manager) and wasn't sure if that would make it difficult for me to replace everything with a single Ubuntu OS.  (And I'm very new to Linux, which makes me a nervous, little newbie.)

As for advice related to reformatting the Vista partition to ext3 - thank you.  I understand why you're suggesting it, but I'm trying to stick to a "Keep It Simple Stoopid" approach so I'm less likely to muck stuff up.  :)

---

### Post by Elfy on 2008-08-01
Well if you want be absolutely safe - as far as you can, then before you actually install with the 8.04 cd make sure everything works with it. At the moment you have a working installation, albeit 7.10.

I would ensure that all my hardware was working before I installed the newer version - you wouldn't be the first to find you have problems.

If you do find there are problems then research them before you upgrade to 8.04.

---

### Post by kansasnoob on 2008-08-01
> My Question: (I'm a complete newbie at this...) I want to go back to a single partition with a single operating system (Ubuntu). Should I "reformat" my hard drive first? A friend told me about GParted and I have successfully installed it - should I use it to get rid of the "Windows side" of the partition first? Or should I just boot straight from a Live CD and overwrite when it gives me the option?

What's the safest, most stable way to go? 

If you have a GRUB screen show up at "boot" that gives you the option of booting either OS then do this:

If you want to keep your Ubuntu just as it is and delete Windows partition(s), I'd first go to Administration > Partition Editor to identify all your partitions by number! Not there? Cool - just go to synaptic and install gparted! Then have a look. Make sure you know which partition is which!

Then boot an Ubuntu Live CD and go to Partition Editor. There you can delete what you want and resize the partitions you want to keep!

Clear as mud:confused:

---

### Post by Epetai on 2008-08-01
Forestpixie - That's a really good point.  (D'oh!)  I will indeed check a copy of 8.04 before installing it.  I've still got my original 7.10 CD (and I even have the original Gateway Vista CD if it all goes horribly wrong...)  

Kansasnoob - Got it - not unclear at all!  :)  I'm going to try booting from the CD.  

Thanks to everyone for their advice.  I have to wait until Sunday to actually do anything to my machine because I'm in a different city... But I know what to do now.

---

