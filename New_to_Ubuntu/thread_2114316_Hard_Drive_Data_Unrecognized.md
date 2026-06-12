---
title: "Hard Drive Data Unrecognized"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by jimmy107 on 2013-02-09
A few months ago I built my computer and dual booted Windows 7 and Ubuntu 12.10 off my 128 GB SSD.  I also have a 1 TB HDD for all my files.  Both of these hard drives are partitioned for Windows 7 and Ubuntu.  Just last week, I bought a laptop and in order to preserve my warranty I used dd to create an image of my SSD from my laptop onto an external drive.  I then wiped it clean and installed Ubuntu.  

The problem I have now is that I moved the image which was gzipped to 60 GB onto the Windows Partition of my HDD (note this is not the drive Windows boots from).  The next day when I booted into Windows, I noticed it could no longer locate any of my files on my HDD.  When I opened up my HDD in Explorer, no files were to be found, not even the gzipped image.  I booted into Ubuntu and even there, no files were to be found on the Windows 7 partion.  Check Disk ran immediately after this happened and found no bad sectors.  The Ubuntu partition of my HDD is perfectly fine.  Any thoughts on what might have happened and how to fix it?  Thanks in advance.

---

### Post by Mark Phelps on 2013-02-09
First of all, can't help you regarding the gzipped image as, I don't use dd, and have found through experience that making image backups of Windows partitions is best done using Windows tools -- the best of which are available for FREE these days.

Second, if the partition that is supposedly blank is formatted NTFS, is could simply be that the filesystem is corrupted, thus, Linux can't read the partition information.

If that's the case, you might be able to fix that partition using CHKDSK, but you would have to run that from within Windows as there is no Linux equivalent of it.

If you simply want to recover files from that partition, then do NOT run CHKDSK but instead, you need to connect that drive to a PC running Windows, and run a Windows data recovery app.  If you're interested in following that approach, read on ...

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

### Post by howefield on 2013-02-09
Threads merged.

One really is sufficient.

---

### Post by tgalati4 on 2013-02-09
You say you copied the gzipped, 60GB file.  Is it possible that you simply dragged it from one folder to another folder in Nautilus?  Nautilus has a nasty habit of showing that a file transfer has finished, when it really hasn't.  If you shut down or rebooted shortly after, it's possible that the file was not copied at all.  This usually happens to large files.  And 60GB is a large file.

---

### Post by jimmy107 on 2013-02-10
Unfortunately, I've already run chkdsk.  I can't remember if I used Ubuntu or Windows to copy the 60 GB file, but I think it was Ubuntu in which case I used nautilus.  Does the recovery tool no longer work if I've done chkdsk?

---

### Post by tgalati4 on 2013-02-10
testdisk and photorec will scan the disk regardless of what you have done to it.  How many files that are recovered will depend on how much of the disk was rewritten.

I don't know how chkdsk works.  I presume it's a Windows program?

You will have to retrace your steps to figure out what happened.  We can only speculate, and that is not helpful.  Data loss moving between Windows and Linux partitions is common.  Installing dual-boot can frequently result in data loss as folks accidently install Ubuntu over Windows instead of next to it.  Having a robust backup strategy is important, because these things happen.

The fact that you were copying a large file to an external USB drive confirms my suspicion of slow file transfer of a single, large file.  If the entire file is not copied before a reboot, then there is a good chance to lose the entire file.  At 5GB per minute copy speed, you are looking at 12 minutes.  Did you shut down or reboot the machine before those 12 minutes?

---

### Post by jimmy107 on 2013-02-10
I'm pretty certain the transfer completed.  I left my computer on for hours after the transfer started and there were no power surges.  Also the other files I had on the drive are missing.  Not just the gzipped file.

---

