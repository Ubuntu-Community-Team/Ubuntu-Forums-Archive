---
title: "ddrescue very slow any ideas?"
date: 2015-01-03
forum: New to Ubuntu
---

### Post by simon76 on 2015-01-03
Have used gddrescue for first time and learning as I go.  But keen to get some input from experienced users please.

I am trying to recover files from a HDD that was dropped and won't boot or mount.  Set ddrescue going on 28/12/14 and it has run almost continuously since.  So far it has recovered 117G of a 500G dirve.  It is painfully slow.  Of the 117G it has recovered 100G at the end of the disk using command

 sudo ddrescue -n -i400G /dev/sdb ~/Desktop/CMS-raw-image-link/cmsimage.dd ~/Desktop/CMS-raw-image-link/rescue.log

There were no errors and the average rate was 400-600kB/s.

DDrescue is now recovering from the start of the drive.  There are over 4000 errors but ddresuce always slows to 20-50kB/s after 15-30mins of a restart.  Initially the recover rate can be 100-400kB/s peaking up to 6000kB/s.

I only want to recover the files, not the operating system

How can you help?
- is there any way to speed up dddrecue (I have tried using -b and -K but they don't appear to make much difference)?
- is there any way to recover only the areas of the disk that have files on - although the disk was 500Gb I think the files only occupied approx 100Gb or 200Gb?
- since I don't need the os partition is there anyway to just mount the files partition?

Last estimate the recovery was going to take another 40days.Yikes!

Thank you

---

### Post by TheFu on 2015-01-03
Having a backup is much easier than this, right?  Got backup religion now?

ddrescue does what it does. That takes time.  Besides reducing the retry count for the first pass to see how much data is really going to be difficult, I don't have any ideas.  It takes what it takes.

I suppose you could try testdisk and badblocks.

Your situation shows another reason why it is best to put the OS and Apps onto a different partition than where you put /home and data.  If you did that, perhaps running ddrescue against those specific partitions, not the entire HDD would be better?

---

