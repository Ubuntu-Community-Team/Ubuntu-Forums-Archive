---
title: "NTFS partition - no data?"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by dcvc on 2012-07-22
Hi,
On my laptop (lenovo) i have dual boot, win xp and ubuntu.
I have a partition NTFS, which i called "shared" where i store my music, photos, etc.

I was trying to automount it in ubuntu and i think i did something wrong. 
Now i can't remember what i did exactly. And i'm sure i made things worst by trying to fix it.

Anyway, if i boot in windows, the partion looks like empty, in ubuntu we just few MB data.. which is not possible  :-k

could somebody help me??  ...i don't  have a full backup of that partition :(

---

### Post by oldfred on 2012-07-22
Does testdisk show anything or then you may have to run photorec which is part of testdisk. Photorec just scans drive for anything that looks like a file, only recovers by type (no file name as that is missing) and takes a long time.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by dcvc on 2012-07-24
i didn't do testdisk. I will try tonight.

thanks

---

### Post by dcvc on 2012-07-24
i need help, i runned testdisk - deep search but seems that can't find anything.. 
Or ... Not sure. My hard disk is a mess.

Anyway 2 out of  3 NTFS partions have damaged filesystem and the only one i can list files, doesn't have the music,photos etc. i lost.


To add some information, I followed this [link]("http://www.liberiangeek.net/2012/04/auto-mount-windows-ntfs-partitions-in-ubuntu-12-04-precise-pangolin/") []("http://www.liberiangeek.net/2012/04/auto-mount-windows-ntfs-partitions-in-ubuntu-12-04-precise-pangolin/")in my trial to automount the partition.

---

### Post by oldfred on 2012-07-24
It is showing two NTFS partitions, one is shown twice with slightly different starts & ends. If you try to recover those does it work?

---

### Post by dcvc on 2012-08-01
> **oldfred said:**
> It is showing two NTFS partitions, one is shown twice with slightly different starts & ends. If you try to recover those does it work?

no.. it recovered some file i had (on purpose) delete

---

### Post by oldfred on 2012-08-01
Bummer, the next choice is long, slow and requires a lot of manual work to find & rename everything. There are tools that just scan drive for anything that looks like a file.

I used photorec. I had lost some text files that I regularly saved. It took many hours to scan drive and found all the old deleted copies. I had old backup and with lots of comparing got most of each text file back but it was a lot of work. It only finds extension, so first I had to find which copies were the same file and then compare each to try to see which was more up to date.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

Other tools:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Mark Phelps on 2012-08-01
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

