---
title: "No permission to write..."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Innernet on 2008-04-26
Good day!

I run pluggable hard drives, only one plugged at a time; each with ONLY ONE operative system, 6.10; 7.04; 7.10; WinXP; etc..., and an external USB hard drive with no operative system where only data is kept.

Removed the 7.10 in daily use, inserted the 7.04 hard drive to archive something into the USB data drive and got the message :

"You do not have permissions to write to this folder."

That never happened before, there is never been any other user on my compfuser, and could not find much about the subject.

Suggestions please ?

---

### Post by nhandler on 2008-04-26
When exactly did the message appear? Did it come up immediately after you tried logging into Ubuntu? Did it appear as you tried copying the files from the 7.04 drive to the drive that doesn't have an OS on it? Or did it appear at a different time?

I'm going to assume it happened as you attempted to copy the files (since this is the most likely place for the message to come up). What type of file system is set up on the no OS drive? You can find out by going into a terminal, and entering "sudo fdisk -l". This will show all of your connected drives and all the partitions on them. Locate the partition on the drive with no OS that you were attempting to copy files to, and note what it says under "System" (the last column). If it has a type of "Linux" you should be able to use chmod to fix it. Something like "sudo chmod 744 -R /mount/point/of/no/OS/drive". That will allow you to read, write, and execute files, and allow everyone else to only read the files.

---

### Post by Innernet on 2008-04-26
Thanks for responding.   It happens exactly after dragging the file to the folder in the USB data-only external drive; operation that works fine on 7.10 and XP; the 'data' drive has many gibabytes of good readable folders, subfolders, files, pictures, .flacs and documents.

Clicking the external drive icon shows several folders with permissions : " dr-xr-xr-x "  owner: root.  Only one file not in folder shows permission " -r-xr-xr-x "


As per your instructions:

--------------------------------------------------------
externet@externet-desktop:~$ fdisk -l

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS
externet@externet-desktop:~$ 

------------------------------------------------------------

And hope screen snapshots attached here

---

