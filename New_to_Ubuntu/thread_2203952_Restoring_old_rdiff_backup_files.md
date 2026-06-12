---
title: "Restoring old rdiff backup files"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by albert14 on 2014-02-06
Hello. I am attempting to restore files from an RDiff back-up performed  some  2/3 years ago. I have tried the rdiff-backup -r command but not  getting very far. Here is a screen grab of the files I have.
Could anyone please tell me how to restore the back up files?  BTW - the  increments folder is empty. Bakup log lists all the files backed up.  (See attachments)Thanks in advance.

---

### Post by TheFu on 2014-02-06
The last backup is just a mirror. You can restore with any method to copy the files that you like.  Don't forget that special files are not handled well by "cp" so either **rsync** or **tar** are a good way.

Everything will be done from a terminal. Here is what a normal rdiff-backup area looks like:
```
drwxr-xr-x 101 root root  4096 2014-01-29 06:26 etc/
drwxr-xr-x   3 root root  4096 2012-06-16 08:13 home/
drwx------   3 root root 28672 2014-02-06 01:10 rdiff-backup-data/
drwx------   5 root root  4096 2013-02-01 10:57 root/
drwxr-xr-x   3 root root  4096 2012-06-16 07:58 usr/
drwxr-xr-x   3 root root  4096 2014-01-18 06:06 var/
```
Everything NOT under rdiff-backup-data is the mirror of the backup for this specific server. The rdiff-backup-data/ directory contains reverse incremental data about the last 30 days of backups, but not any data from 1:10am this morning (that is when my backups happen). To see the backups and sizes, use:
```
# **rdiff-backup --list-increment-sizes /path/to/backup/directory**
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Feb  6 01:10:08 2014         11.9 MB           11.9 MB   (current mirror)
Wed Feb  5 01:10:07 2014       520 bytes           11.9 MB
Tue Feb  4 01:10:08 2014       520 bytes           11.9 MB
Mon Feb  3 01:10:07 2014       520 bytes           11.9 MB
Sun Feb  2 01:10:06 2014       520 bytes           11.9 MB
Sat Feb  1 01:10:08 2014       520 bytes           11.9 MB
Fri Jan 31 01:10:07 2014       520 bytes           11.9 MB
Thu Jan 30 01:10:08 2014       520 bytes           11.9 MB
Wed Jan 29 01:10:08 2014       644 bytes           11.9 MB
Tue Jan 28 01:10:07 2014       520 bytes           11.9 MB
 .
 . 
Sat Jan 11 01:10:08 2014         1.28 KB           11.9 MB
Fri Jan 10 01:10:08 2014       644 bytes           11.9 MB
Thu Jan  9 01:10:06 2014       520 bytes           11.9 MB
Wed Jan  8 01:10:07 2014       520 bytes           11.9 MB
```
This server is just an email gateway, so it doesn't have much data at all.

Copy/paste text please with "code" tags (Adv Reply), like I did above. See how everything lines up nice? What does the backup area show?

---

