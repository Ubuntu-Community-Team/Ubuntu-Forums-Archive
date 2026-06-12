---
title: "System Backup And Restore"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by jivabill on 2008-04-23
Couple days ago I backed up my whole hard disk (186gb) using the Tar command.  Worked good, put the backup file in root burned it to a DVD.  Cool.

So now I am planning some other things for my HD and I used GParted to resize the Ubuntu partition.

Now my question: if I now want to restore my system will the backup I made from the full HD still work on the smaller partition.  I E will the tar restore command just stuff it into the smaller partition?  There is plenty of room, the new small partition is 117gb of which I am using only about 16gb. :)

Here is the restore command  tar xvpzf /backupfilename.tgz -C /

OR will the tar command overwrite the entire HD across the area that existed when the backup was made?  :confused:

Thanks for reading

---

### Post by RealPSL on 2008-04-23
The tar command is only aware of the file system so it can not extend beyond the partition level. That is even if you backed up 16GB of data and tried to restore it to a 10GB partition tar would simply fail it would not overwrite beyond the file system/partition boundary.

---

### Post by jivabill on 2008-04-23
Hi RealIPSL, nice to meet you.  Thanks for your input.  I am still not sure things will go right.

The specific situation is this now:
I backed up a 186gb partition with TAR.  Only 16gb of that contained data, the rest was unused blank space.

Now, the partition size is 117gb as I resized it.

So if I use Tar to restore to the new smaller parition, will Tar write my date (ubuntu sysem) and then fail later when it reaches the end of the 117gb?  Or will it just fail to begin with so I can not restore?

thanks
bill

---

### Post by jivabill on 2008-04-23
RealIPSL: OOOPS made a typo in my post, the word "date" should be "data".
bill

---

### Post by mlentink on 2008-04-23
Jivabill, I reckon that tar file is about 16GB? 
tar = Tape ARchive, a file format that was designed to simply put the contants of a file system on a tape. No compression.

So what will happen when you untar that file, it will simply write your files back to that filesystem, which with 117GB is more than big enough.

In the future you might want to look at stuff like Simple Backup

---

### Post by jivabill on 2008-04-23
Hi mlentink, thanks for your help.  Actually the TAR backup file, since it was compressed during backup is 1.7gb.  Reason I used TAR it was recomended as the way to make a full system backup (the entire ubuntu partition) found it on the Ubuntu docs.

My examination of Simple Backup was that it would backup critical parts but not enough to recover from a HD failure for example where I would have to start fresh by installing 7.10 and then restoring to get my current system back.  Least that is what I thought :-) from my reading.

Here is the complete TAR command that I used:
tar -cvpzf /sysbu042008.tgz --exclude=/proc --exclude=/lost+found --exclude=/sysbu042008.tgz 
--exclude=/sysbu011808.tgz --exclude=/var/backup --exclude=/mnt --exclude=/sys --exclude=/media /

The sysbu files are my current and previous backups that are excluded
var/backup was excluded because I have Simple Backup running on a schedule and it had accumulated a lot of backups that I did not want to save over again.
bill

---

### Post by mlentink on 2008-04-23
Looks fine to me. Basically that command runs the tar through gzip to compress it.  But if your original amount of data was not more than 16GB, then you will have no trouble whatsoever to untar it in a smaller filesystem, as long as it's bigger than the amount of data.

---

### Post by jivabill on 2008-04-23
Hi Mlentink, thank you for checking out my code and problem.  I will go for it and should be able to restore and be happily running.
Again, thank you for you good help
bill

---

