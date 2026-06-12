---
title: "I removed windows and installled ubuntu. need help to access my files"
date: 2013-12-18
forum: New to Ubuntu
---

### Post by jayeshkhattar on 2013-12-18
I recently installed Ubuntu but removed my windows 7 because i was having some troubles with it. My bad, due to time restrictions i dod not take back-up of my data. Is my data still in the computer or it got deleted ? I can't find a proper to check whether it's there or not...I need to access to my data badly. I need help asap...

---

### Post by Bucky Ball on 2013-12-18
Welcome. Open Gparted and look for NTFS partitions. If there are none, you have no data (unless it was stored on FAT or some other filesystem partition).

No backup and launching into installing an OS you aren't familiar using an installer you've never used (I'm presuming)? Hmm ... risky. If you needed access to your data that badly this was extremely unwise course of action. But I'm telling you nothing you don't know now. :-k

Open a terminal (Apps>Accessories>terminal) and paste this in:

```
sudo parted -l
```

Put in your password and post the output here. After that: DO NOTHING! There may be some way of accessing your wiped data, if it is wiped, but the more you fool around with the computer, the more it will get scrambled and the less chance there will be of retrieving anything. 

I'm guessing you had one big Windows partition and have killed that and installed Ubuntu so I don't like your chances here. What were you thinking? Oh, never mind. ;)

---

### Post by jayeshkhattar on 2013-12-18
Sorry...My bad

---

### Post by Bucky Ball on 2013-12-18
Please attach pics by using the paperclip icon in 'Go Advanced' rather than inserting them in the body of your post. Thanks.

---

### Post by jayeshkhattar on 2013-12-18
@BuckyBall please reply

---

### Post by kwgagel on 2013-12-19
According to your screen shot you've replaced all your data with Ubuntu. You don't appear to have any other drives. So, for all intents and purposes - your data is gone.

---

### Post by QIII on 2013-12-19
Don't panic -- but don't turn on that machine just yet.

Find another machine and download a copy of TestDisk [here]("http://www.cgsecurity.org/wiki/TestDisk_Download"), burn it to disk and then have a look through the forum [here]("http://forum.cgsecurity.org/phpBB3/").

Some of your files are virtually guaranteed to have been overwritten.  Those that weren't (depending of whether you formatted your partitions, etc) ***may ***still be recoverable.  But file names are often lost and there may be a considerable amount of work in sorting out what you do manage to recover.

Do not use that machine when running from the hard drive.  When you start it up, make sure the TestDisk media is in the CD/DVD drive and make sure your BIOS/EFI is set to boot from it.

Best of luck.

---

### Post by Bucky Ball on 2013-12-19
> **QIII said:**
> Don't panic -- but don't turn on that machine just yet.

Find another machine and download a copy of TestDisk [here]("http://www.cgsecurity.org/wiki/TestDisk_Download"), burn it to disk and then have a look through the forum [here]("http://forum.cgsecurity.org/phpBB3/").

Some of your files are virtually guaranteed to have been overwritten.  Those that weren't (depending of whether you formatted your partitions, etc) ***may ***still be recoverable.  But file names are often lost and there may be a considerable amount of work in sorting out what you do manage to recover.

Do not use that machine when running from the hard drive.  When you start it up, make sure the TestDisk media is in the CD/DVD drive and make sure your BIOS/EFI is set to boot from it.

Best of luck.

This. To reiterate: Don't use that machine for anything, don't even turn on, until you have the testdisk ready to boot it.

---

### Post by Mark Phelps on 2013-12-19
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

