---
title: "Backup entire hard drive to removable hard drive"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Jim Rimedio on 2008-10-31
Hello:

	I have a Linux computer running Ubuntu 8.04.  I have two removable hard drives that I want to use alternatively to make an exact backup copy of my entire computer.

	I am in the learning stage and have located “Simple Backup Config”, but do not know what to put in the “Include” box to backup everything.  I have been unable to find anything in the man pages using “Simple Backup man”, Simple_Backup man”. “man Simple Backup”, or ,”man Simple_Backup.

	Initially I want to backup the entire hard drive, thereafter in want to daily incremental backups for 30 days and then change to the second removable hard drive.

---

### Post by Duck2006 on 2008-10-31
You can backup your drive with part image.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by handydan918 on 2008-10-31
You can also do it natively with rsync. 
grsync allegedly provides a gui. 

Something like ```
rsync -av / /target_directory
```, but see man rsync for specifics.

---

### Post by Tichondrius on 2008-10-31
> **Jim Rimedio said:**
> Hello:

	I have a Linux computer running Ubuntu 8.04.  I have two removable hard drives that I want to use alternatively to make an exact backup copy of my entire computer.

	I am in the learning stage and have located “Simple Backup Config”, but do not know what to put in the “Include” box to backup everything.  I have been unable to find anything in the man pages using “Simple Backup man”, Simple_Backup man”. “man Simple Backup”, or ,”man Simple_Backup.

	Initially I want to backup the entire hard drive, thereafter in want to daily incremental backups for 30 days and then change to the second removable hard drive.

complete backup (to removable drive partition /dev/sda1)

dump 0uf /dev/sda1 /

incremental backup

dump 1uf /dev/sda1 /

Restore

cd /
restore -f /dev/sda1

---

