---
title: "250,000 directories to delete failing miserably"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by bogeybartsimpson on 2014-06-30
I screwed up some backup software on Windows and since Windows can't handle really long paths or names, I am trying to delete the directories and files using lubuntu on a memory stick.
Basically, the backup software ended up taking backups of backups and so on and so I have 250,000 directories as well as files within those.

I tried to just delete the root directory of all the backups however then everything was of course moved to .Trash-999
I'm trying to delete it all using sudo rm -vrf .Trash-999 however from the pace at which it's going it looks like it will take days. For some reason even with the arguements it stops and tells me that the directories are not empty (the ones with files in)

Is there a faster way that I could do this? Could I partition the drive, shift the Trash to there and then format it?

Any help is appreciated.

---

### Post by steeldriver on 2014-06-30
it might be quicker to move the stuff you want to KEEP off of the stick and then format it - anything that involves moving stuff around ON the stick is going to be slow (even slower if it needs to go across partitions i.e. actual read/writes instead of just messing with inodes)

---

### Post by bogeybartsimpson on 2014-06-30
Sorry, I might not have made this clear. I am only running lubuntu off a memory stick so I don't need to install it to my main hard drive along side Windows. The files and directories that I am trying to delete are on my main hard drive and moving 500GB of data would not be faster in that case.

---

### Post by tgalati4 on 2014-06-30
Running a Live session means that you are running strictly in RAM.  Deleting large numbers of files requires RAM, so it is possible that you are running out of memory for this operation.   I would buy another drive, put it in an enclosure, then perform a copy/clone of the 500 GB drive.  Then work off of the external drive with a machine that has a normal installation of Linux.  Then you can recover files that you need and delete the rest.

Performing large file delete operations on a drive that does not have adequate backups puts your main drive at risk of failure.  Once you have recovered and backed up your critical files, then you can use tinycore linux or slitaz and boot a live session and use that to perform your mass deletions.  Lubuntu probably takes too much RAM to perform mass deletions in this case.

---

### Post by sandyd on 2014-06-30
moved to absolute beginners section

---

