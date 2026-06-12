---
title: "Fail to check or mount ntfs partition in ubuntu"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by KillerEST on 2012-12-11
Original thread: [http://ubuntuforums.org/showthread.php?t=1606427](http://ubuntuforums.org/showthread.php?t=1606427)

(I hope it is not a sin to post here, I would like to mention some things)

I'm not 100% sure (I haven't have a change to do it myself), but **_probably the best solution is to use Testdisk/Photorec at the beginning, not when everything is deleted and needs recovery._**

Same problem occured on my computer. I have 2 HDDs. One is 20 Gb with 2 partitions: ~10 Gb uses Windows main system and another 10 Gb uses Linux main system. Other hard drive is 250 GB, partitions are 55 Gb (that "old stuff you want to keep, but isn't actually necessary") and 195 Gb for all the files, programs, games. One day the 195 Gb (NTFS) partition couldn't mount (I think I hadn't done anything harmful to computer, ex. restart using external button or something like that). Same errors; "segmentation fault" and "exit code 2". I, fortunately, had possibility to do things without Live-CDs. Firstly, I tried to detect something from Linux. I ran some tests (including extended file system and hard drive tests), but everything were OK according to the results. So, I read this topic and tried to fix things with chkdsk from Windows, **_big mistake_** (I googled later and found that chkdsk has caused problems for many people who were in the same situation). I tried to use Windows repair systems (chkdsk and something like "repair disk" from control panel). Chkdsk seemed to repair some errors, but I also ran "repair disk" thing (so I'm not 100% sure, which one deleted the data..maybe both). When it was already running I had a second thought and I tried to stop it, but it wasn't possible. I thought that I'd let it run (second mistake, probably). It took some time and after I finished I noticed that I have the same problem (the disk appeared to be empty, except log files). This could have been avoided, but I still did the mistakes.

So now I'm using Photorec and also trying recover as much as possible..fortunately I have a 2 Tb external drive. I need to sort a lot of files, but I have time. It doesn't need to be done in a day...and fortunately there aren't any very important files that were on the partition (again, many of these files are these "old files I'd like to keep").

// By the way, what kind of program did you use to rename bad-named files?

---

### Post by oldos2er on 2012-12-11
Post moved to its own thread.

---

### Post by KillerEST on 2012-12-14
After 47 hours I finially finished it. Interesting is that most of the pictures have only thumbnails (or atleast very small resolution, about 10 times smaller than the pictures were). Shall I try with another program? I'll do second run definitely (I found some more file extensions that could be also saved).

---

### Post by Mark Phelps on 2012-12-14
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

### Post by KillerEST on 2012-12-14
Okay, thanks. I'll try it.

---

