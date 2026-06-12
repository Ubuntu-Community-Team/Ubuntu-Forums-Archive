---
title: "Hard disk data recovery after formatting to ext"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by achu91 on 2014-02-21
i have a external hard disk which had ntfs file system used as backup.Accidentally instead of  installing Ubuntu on laptop hard disk i installed on external hard disk with erase disk option .The external hard disk was  connected via USB .After installation i realized the mistake and by that time i lost all data in the hard disk.Is there any way to recover the data.

Achuthan

---

### Post by fdrake on 2014-02-21
try thin in a windows machine [http://sourceforge.net/projects/freerecover/files/?source=navbar](http://sourceforge.net/projects/freerecover/files/?source=navbar)

---

### Post by achu91 on 2014-02-21
but sir at present its having a linux partition.should like change to ntfs (format once again)to use recover or directly i can use.

---

### Post by fdrake on 2014-02-21
good point , the best thing is not to edit the disk . the program should retrive the original (ntfs) files even in a ext  like that.  if it is not able to see them then try with testdisk ([http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)) the second option is much popular and well know , much more promising! :D

---

### Post by sudodus on 2014-02-21
You can try to use ***Testdisk***, which can help restore an old partition table in some situations. If that is not possible, it can still be possible to recover data, that was not overwritten, when you installed the new operating system. Then you have to resort to ***PhotoRec***, which can recover files from the data that are still available, even though the partition table and file system are no longer available. It means a lot of work, and the directory structure and file names are lost. See this link

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

So if there are some important files, that are not available anywhere else, start with Testdisk, and if no luck, continue with PhotoRec. But if it is 'only' backup data, that are available in other places, it is much easier to re-partition and re-format the USB HDD and run the backup program(s) again.

---

### Post by varunendra on 2014-02-21
A big +1 to testdisk. Here is a Step-by-Step guide showing how to use it to restore the previous partition structure : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

And a +2 to the suggestion to just repartition and backup again if the original data is stored somewhere else. While recovering the partition may be easy, the recovered files on it may not be reliable, especially if the partition was significantly fragmented.

---

### Post by Mark Phelps on 2014-02-21
> and the directory structure and file names are lost.

This is a BIG problem -- when you're trying to recover files and folders.

If you're willing to spend some money and have access to an MS Windows PC, then read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

### Post by fdrake on 2014-02-21
+1 @ Mark Phelps
I also think windiws is the best at reovering its own partitions. Sometime even a windows installation cd/dvd is good at recoverying your data (but i do not think it will work in this case since if has been refformatted. not sure..)

---

