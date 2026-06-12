---
title: "Mounting drive"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Draconiator on 2013-03-09
I'm a brand new user of Ubuntu (12.10) apparently, as I am using this as a rescue operating system to save data since my Windows 7 hard drive is dying on me.   I cannot seem to mount the failing drive though, which is unusual because I can mount it just fine in another Linux flavor (Lucid Puppy 5.2).

It tells me "Adding Read for uid 999 to `/media/ubuntu' failed: Operation not supported

I'm running it from an SD card, which is being used as a mini-SSD of sorts.

....How do you pronounce it anyway?  "you-BUNN-too"?  "ooo-BOON-too"?   Whatever it is, it looks great, and I've been dying to learn Linux anyway, so there ya go :)

---

### Post by arpanaut on 2013-03-09
> ooo-BOON-too

Use watever works to recover your data, first things first, then worry about getting a new OS working on your system.

---

### Post by Impavidus on 2013-03-09
If you can mount your HD using puppy linux, do that and copy all data you want to save to an external drive. Then get a new drive and consider installing Ubuntu.

By the way, using [IPA]("http://en.wikipedia.org/wiki/IPA") Ubuntu is pronounced [u'bun.tu]. Can't be easier. Some regional variation is allowed though.

---

### Post by Mark Phelps on 2013-03-09
Linux routinely refuses to mount NTFS filesystems that are corrupted.  So, if that is the case, trying to use Linux to harvest data from your drive may not work.

Instead, you should consider using MS Windows data recovery apps.

best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

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

