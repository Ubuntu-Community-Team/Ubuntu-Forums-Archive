---
title: "Data recovery"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by Madhukar_Seth on 2014-01-27
hi,
 i m new to linux.
I was installing linux in my 500 GB HDD with win7, had thought for dual boot. I sucessfully installed but the problem here i found is that I had given entire disk for linux and my all data are gone now. So some one please help me to come out of this.

Thank you.

MaxaM

---

### Post by jones quest on 2014-01-27
1) Stop using the hard drive. Any new data you write to it reduces your changes of recovering the data.
2) On a different computer or by booting from the ubuntu live dvd /usb download system rescure cd:
[http://www.sysresccd.org](http://www.sysresccd.org)
Ubuntu live cd might have some of these applications but this is the best rescue option.
3) READ THE MANUAL & examples for the tools
4) Have some place to put the recovered data (external hard drive etc.) 
5) Recover the lost partitions & data with appropriate tools sfdisk, Partimage, testdisk etc.

I've used Testdisk succesfully myself to recover accidentally deleted files. It is a text based but very powerful tool. Has step by step protocol (very easy to follow.) But the specific tool/steps you need depends on your setup...

---

### Post by Madhukar_Seth on 2014-01-28
Thank you Jones for the fast reply... I tired to recvoer with Testdisk but seems doesnt work. I am now watching movies to control the flow of my sentiments over those files. And will be very care full onwards. 

last but not least.. Thank you .. again.

---

### Post by fantab on 2014-01-28
Try [MiniTool Partition Recovery]("http://www.minitool-partitionrecovery.com/") since the lost partitions were NTFS.
If that doesnt help then re-try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") along with [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec")... Photorec is for recovering lost media files. 
Testdisk works.. 100% data recovery may not be possible because you have overwritten some of the data with ubuntu, but still there is lot to rescue.

Good Luck...

---

### Post by sudodus on 2014-01-28
If testdisk does not work, there might still be a chance that ***gpart*** will help you. As before, boot from another drive.

But maybe you have to resort to reading the data left on the disk surface, that is still untouched by Ubuntu, to read those data without the aid of a files system. [PhotoRec]("http://www.cgsecurity.org") from the same origin as Testdisk can identify the file headers of several file types, document files as well as photos and multimedia. But it will be a lot of work to reorganize the files that you manage to find, give them meaningful files names and organize them in directories.

I'm really sorry, if it turns out that you will lose photos and other valuable things, but don't give up yet. Many people have been able to use PhotoRec to save some of the valuable files.

---

### Post by Mark Phelps on 2014-01-28
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

