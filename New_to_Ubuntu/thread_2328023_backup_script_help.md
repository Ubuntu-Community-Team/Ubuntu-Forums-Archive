---
title: "backup script help"
date: 2016-06-16
forum: New to Ubuntu
---

### Post by rburkartjo on 2016-06-16
running 16.04
here is my script

#!/bin/bash

#-- enter your folders here!
backupfolder="/home/ray/systembackup"
sourcefolder="/"

cd "$backupfolder"
a=`date +%m-%d-%Y--%H-%M`
tar -czvf systembackup-$a.tgz --exclude=home/ray/systembackup/$a.tgz "$sourcefolder"
echo
echo "-------------------finished backup!-------------------"
echo "--hit ENTER to exit --"
read a
exit 0system



the backups go into /home/ray/systembackup
i just want to make sure that when i run it again that i exclude any previous backups in that folder
what --exclude would i add . maybe use a * wildcard

/tks

---

### Post by TheFu on 2016-06-16
I would put the backup to a different area on the disk - like /backups/ ... outside the /home/.
Exclude should be something like --exclude=¨*systembackup*¨, but I didn´t check it.
tar is fine for tiny backups, but as the stuff to be backed up grows, it becomes painful to use.  Check out rdiff-backup - think you´ll like it. No need to manage dates, just the total number of versions .... 30-120 versions is pretty easy.  Also, rdiff-backup has an option to exclude special files, so fifos, pipes, devices, etc. aren´t included which can cause other tools to hang.

[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) makes it pretty easy.

---

### Post by rburkartjo on 2016-06-17
fu tks will check that out

---

