---
title: "Copying RAW windows hard drive with ddrescue"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by Robert Timespit on 2013-02-14
I'm very new to Linux/Ubuntu, I'm just utilizing it to recover my windows drive.

Hi, my secondary 500GB internal NTFS hard drive that I use for data suddenly turned RAW, and I burned Parted Magic to try and clone the drive to a brand new, NTFS formatted 1TB drive so I can attempt to use Data Recovery Software and TestDisk on a stable drive. But I running into trouble.

I entered this into the terminal command line:

ddrescue -v -r 3 /dev/sda /dev/sdb -f

But I received similar results to this person:
[http://ubuntuforums.org/showthread.php?t=1341388](http://ubuntuforums.org/showthread.php?t=1341388)

0bytes of data rescued, and it said the errsize was 500GB, I let it go on for an hour before I cancelled it with no results. Do I need to mount my RAW 500GB drive or something? How do copy the 500GB of RAW data so I can safely operate on the files.

---

### Post by oldfred on 2013-02-14
Your link mentions mounting read only. Have you tried that?

Does testdisk show the partition. NTFS partitions have a backup of the PBR - partition boot sector. If the backkup is valid it may just restore it to NTFS. Not sure about anything else but that would only be working on PBR or first sector of partition.

Was this just one large partition one the hard drive. A few have new unformatted drives & just start writing data. That ends up causing bit issues as just about all tools expect partitions not a monster floppy drive.

       As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Mark Phelps on 2013-02-14
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

### Post by Robert Timespit on 2013-02-14
I haven't tried read-only mounting the RAW drive yet because I'm not entirely sure of the syntax.
Would it be something like:

mount -t ext3 -o ro /dev/sda

I haven't used TestDisk at all yet. All I've done (out of fear for my data) is attempt to clone the RAW drive (/dev/sda) to my newly bought, newly NTFS formatted 1TB drive (/dev/sdb). I've been told that it would be safer to clone my RAW drive to a stable drive and try using file recovery software and TestDisk on the new drive.

I'm pretty sure it's just 1 partition. I think I just formatted it to have 1 large partition will all my files/documents/images on it.
When I tried data recovery software from within windows (iCare Data Reovery, EASEUS Data Recovery), they would stall, and estimate the completion time as hundreds of hours and I was forced to terminate them.

I want to make sure that whatever I do, I don't close any doors to possible recovery options because I tried something that didn't work and corrupted my data even more.

---

### Post by Robert Timespit on 2013-02-14
I should probably mention the drive is a secondary data drive, I boot windows off of a seperate 250GB drive.

---

### Post by Robert Timespit on 2013-02-15
Should I run TestDisk from Windows or from a Linux CD?

---

### Post by oldfred on 2013-02-15
I have run testdisk from LInux, not from Windows.

If you want to use Windows then Windows tools may be better.

---

