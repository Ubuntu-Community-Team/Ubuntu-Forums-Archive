---
title: "Want to Recover Drive Data"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by lemmingrebel on 2013-02-03
Running 12.04.  

Did a stupid thing ... installed Ubuntu on a different drive than intended ... ended up wiping out a bunch of my files.  Would like to recover as much as possible.

So basically I have an external usb drive with what looks like the Ubuntu file structure (bin, boot, cdrom, dev), but I'm actually running Ubuntu on my hard drive.

The external disk was originally formatted as FAT32 but now Ubuntu folder properties is saying that the file format is "ext3/ext4".

Can someone please walk me through what I need to do to find as many of my files as possible?

---

### Post by Bartender on 2013-02-03
OK, I'm just guessing here because your description isn't very clear to me.  I think what you're saying is you had a FAT32 formatted external HDD with your personal data on it.  And your PC is running Ubuntu.  And you booted the PC from an Ubuntu LiveCD, then installed Ubuntu by mistake to the external HDD.

Is that right?

If so, I'd say your FAT32 data is gone.  Maybe some data recovery genius could help you out.

---

### Post by lemmingrebel on 2013-02-03
That's correct ... I'm was trying to use something called PhotoRec to search for the files, but to no avail.

So if my FAT32 files are gone and the HDD is ext3/ext4, is there any easy way to set it back to FAT32?  Any reason to?

---

### Post by Mark Phelps on 2013-02-03
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by lemmingrebel on 2013-02-03
Gave that a try.  Really neat tool.  But is for loss.  :(

Oh well.  Thank you anyway!

---

### Post by sdowney717 on 2013-02-03
easeUS partition recovery 5.6.1
I used that to recover once a windows partition.

[http://www.softpedia.com/get/System/Back-Up-and-Recovery/EASEUS-Partition-Recovery.shtml](http://www.softpedia.com/get/System/Back-Up-and-Recovery/EASEUS-Partition-Recovery.shtml)

---

