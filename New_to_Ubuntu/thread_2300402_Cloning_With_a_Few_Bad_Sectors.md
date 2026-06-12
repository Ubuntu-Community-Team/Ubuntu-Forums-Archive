---
title: "Cloning With a Few Bad Sectors"
date: 2015-10-25
forum: New to Ubuntu
---

### Post by briar rabbit on 2015-10-25
Hello

I have a good computer that does give the occasional problem, it will not copy/move files from the local disk to an external drive because of "input output errors".
The pc works fine other than the loss of the occasional file primarily pictures and audio and video files, never any data files. My work around is to put them directly on an external drive and work with copies on the pc.

SMART data view;

- - Current Pending Sector Count - -
"Number of sectors waiting to be remapped.  
If the sector waiting to be remapped is 
subsequently written or read successfully, this 
value is decreased and the sector is not 
remapped.  
Read errors on the sector will not remap 
the sector, it will only be remapped on a 
failed write attempt"

There are no "Uncorrectable Sectors".


All of this implies that the "bad sectors" are repairable.

What I have read about "TestDisk" is that it recovers lost partitions and repairs damaged FAT/NTFS boot sector.   But this is not my problem as best I can tell.

I have read that ddrescue should not be used if there are "input output errors".

I want to clone the HD to keep the new OS and setup.
I did Clonezilla rescue and though it seemed to work, I got the following errors when I went to use it:
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
run-init: /sbin/init:  No such file or directory
[    1.895135] Kernel panic - not syncing: Attempted to kill init!

Does anyone have experience with doing a Clonezilla clone with "a few bad sectors"?

Is there a plan for repairing "remapping" Bad Sectors?

thanks

---

### Post by tgalati4 on 2015-10-25
Run *badblocks* on that bad boy.  If the count is more than a few, I would retire the drive or partition around the bad sectors if they are in a small group.

```
sudo badblocks /dev/sdg1
```

Your drive number will be different.

---

### Post by briar rabbit on 2015-10-26
Hi, thanks for the help.

The partial results are;

Bad Blocks Started at 54404928 - I stopped it at 55364037 because I found a warning screen - "DISK FAILURE IMMINENT".  I do not know how long the warning had been there because the screen had blacked out (screen saver) and the busy light was trucking along and it never stopped giving more results.
I did a hard shutdown and restarted to find all is as it was before searching for "Bad Blocks" except I had 21 Bad Sectors - Now I have 392 Bad Sectors.
That's a total of 959109 blocks though not every one between those numbers was bad.

Maybe a partition of blocks 54404928 to 55364037 and then try the clone again.

I am thinking that every time the pc comes across a bad block it causes another one or more bad blocks trying to read the bad block.

---

### Post by philinux on 2015-10-26
Once a disk starts failing it's time to backup anything important and get a new disk drive.

---

### Post by tgalati4 on 2015-10-26
Yes, if the *badblocks* are increasing over time, it could be a worn out head or swing arm.  I have successfully used the partitioning method, but only on drives that have only a few bad sectors and not increasing over time.  Data backup is important.

---

