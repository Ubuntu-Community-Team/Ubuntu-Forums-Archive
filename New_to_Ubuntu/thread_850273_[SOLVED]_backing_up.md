---
title: "[SOLVED] backing up"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-05
Hello,

I've got a nice system going now and I'd like to back it up onto seperate partitions.  There's this thread on another forum that seems to have a good list of what you should back up (why is it a good or bad list and is there anything you'd add?).

[http://linuxmint.com/forum/viewtopic.php?t=3969](http://linuxmint.com/forum/viewtopic.php?t=3969)

I also would like to partition the most important files onto different partitions that way if I completely screw my OS up (it's happened several times before) getting it back will be fairly easy.  I want to back up on a regular basis and was wondering if I could get a cron job to do this; or is that not recommended?  Are there any codes like this already made that I could just C&P and learn the syntax from there?  I have these recourses if not:

[http://www.aota.net/Script_Installation_Tips/cronhelp.php3](http://www.aota.net/Script_Installation_Tips/cronhelp.php3)
[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

Is this a possible and recommended way of backing up and repartitioning my data?  Thank you!

---

### Post by neurostu on 2008-07-05
I would recommend using:
```

rsync

```
It is a really amazing program that does a lot. The main feature is after your first major backup it only copies data that has been changed. This makes for faster backups.

Yes setting up a cron job is ideal. 

As far as backing up different thing to different partitions you can easily write a script that will accomplish that for you.

Just google: backup with rsync
and you should get some good how tos poping up.

---

### Post by AnLGP on 2008-07-05
Thanks.  

[http://www.linux-backup.net/App/](http://www.linux-backup.net/App/)

That page seems to be a good start.

---

### Post by AnLGP on 2008-07-05
[http://i297.photobucket.com/albums/mm213/musicauniversalis/2008-07-05-135139_1280x1024_scrot.png](http://i297.photobucket.com/albums/mm213/musicauniversalis/2008-07-05-135139_1280x1024_scrot.png)

There's my current partitions (as you can see I bit the bullet and downloaded gparted).

I get the idea of burning a live CD of gparted and using it because the system has to be unmounted but I'm curious how would I move certain files to the new partitions once the partitions are set?

---

### Post by mgranet on 2008-07-05
You might try CloneZilla. It's a LiveCD. You simply reboot into it, and it ghosts the image of a partition, compresses it to your liking, and saves the image file to another partition. It's step-by-step, easy as heck to use. When you toast your current config, just reboot with the LiveCD in, and select restore to parition, and it's like nothing ever happened.

---

### Post by hyper_ch on 2008-07-05
I also vote for rsync and hardlinks ;)

---

### Post by AnLGP on 2008-07-05
mgranet, that sounds good but I'd really like to be able to set backups periodically.  I can see having an image and the use of it to revert to an old system if that's necessary but having my current one consistantly backedup is important to me as well.  I got sbackup and have been talking to a friend.  He recommends dd.

Can it do that?

---

### Post by hyper_ch on 2008-07-05
constant backups: rsync.... it will sync the altered files.... very fast... with hardlinking you can even create snapshots of older backups without increasing memory usage too much

---

### Post by AnLGP on 2008-07-08
I'm going to use rsync and mark this thread solved.

---

### Post by maniacmusician on 2008-07-08
> **AnLGP said:**
> [http://i297.photobucket.com/albums/mm213/musicauniversalis/2008-07-05-135139_1280x1024_scrot.png](http://i297.photobucket.com/albums/mm213/musicauniversalis/2008-07-05-135139_1280x1024_scrot.png)

There's my current partitions (as you can see I bit the bullet and downloaded gparted).

I get the idea of burning a live CD of gparted and using it because the system has to be unmounted but I'm curious how would I move certain files to the new partitions once the partitions are set?
GParted already has its own liveCD. If you visit the project website ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) ), you can find it on their download page.

To move the files, you would just have to mount the new partitions that you made. I have a feeling that Ubuntu will probably do that for you automatically.

---

### Post by hyper_ch on 2008-07-08
if you need a "simple" backup script for making snapshot-style backups with hardlinks, let me know ;)

---

### Post by AnLGP on 2008-07-08
sure :D uh, as in..  can I have it?

---

### Post by hyper_ch on 2008-07-08
backup.sh
```

#!/bin/bash
unset PATH


# USER VARIABLES
BACKUPDIR=/backup                               # Folder on the backup server where the backups shall be located
EXCLUDES=/backup/exclude_list                   # File containing the excluded patterns
DAYS=90                                         # The number of days after which old backups will be deleted


# PATH VARIABLES
SH=/bin/sh                                      # Location of the bash bin
CP=/bin/cp;                                     # Location of the cp bin
FIND=/usr/bin/find;                             # Location of the find bin
ECHO=/bin/echo;                                 # Location of the echo bin
MK=/bin/mkdir;                                  # Location of the mk bin
SSH=/usr/bin/ssh;                               # Location of the ssh bin
DATE=/bin/date;                                 # Location of the date bin
RM=/bin/rm;                                     # Location of the rm bin
GREP=/bin/grep;                                 # Location of the grep bin
RSYNC=/usr/bin/rsync;                           # Location of the rsync bin
TOUCH=/bin/touch;                               # Location of the touch bin
DF=/bin/df;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING NECESSARY FOLDERS
$MK $BACKUPDIR
CURRENT=$BACKUPDIR/current
OLD=$BACKUPDIR/old
$MK $CURRENT
$MK $OLD
# CREATING CURRENT DATE / TIME
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
NOW=$OLD/$NOW
$MK $NOW

# RUN MYSQL BACKUP
# Comment this out if you don't have mysql dbs
$SH /backup/my.sh

# RUN RSYNC INTO CURRENT
$RSYNC                                                  \
        -aplvz --delete --delete-excluded               \
        --exclude-from="$EXCLUDES"                      \
        /                                               \
        $CURRENT;


# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current
# MAKE HARDLINK COPY
$CP -al $CURRENT/* $NOW

# REMOVE OLD BACKUPS
for FILE in "$( $FIND $OLD -maxdepth 1 -type d -mtime +$DAYS )"
do
        $RM -Rf $FILE
#       $ECHO $FILE
done

$DF

exit 0

```

my.sh
```

# Make MySQL Backups
#!/bin/bash
# Remove old file
mkdir /mysql_backup
rm -f /mysql_backup/*

#Dump new files
USER=root
PASSWORD=****************************
HOST=localhost

for i in $(echo 'SHOW DATABASES;' | mysql -u$USER -p$PASSWORD -h$HOST|grep -v '^Database$'); do
  mysqldump                                                     \
  -u$USER -p$PASSWORD -h$HOST                                   \
  -Q -e -C --add-drop-table --add-locks --quick --lock-tables   \
  -B $i                                                         \
  $i > /mysql_backup/$i.sql;
done;

```

backup_exclude
```

/backup/current/
/backup/old/
/bin/
/boot/
/dev/
/lib/
/lost+found/
/mnt/
/opt/
/proc/
/sbin/
/sys/
/tmp/
/usr/
/var/cache/
/media/
/mnt/

```
make sure to not create loops in the backup... so I exculde /backup/current (where the current sync will be done to) and /backup/old (where the older backups are)... depending on how you setup your system, you want to backup /media also...
For more in filter/inculde/exclude rules, check out here: [http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html) (about 3/4 down the page: FILTER RULES + INCLUDE/EXCLUDE PATTERN RULES).

basically it's very simple:

(1) define some vars
(2) define some system binaries (as I run an unset PATH first that is required)
(3) get current time and make a backup directory
[(4) backup the mysql dbs into a given folder]
(5) sync the real data now with the "current" folder
(6) hardlink the "current" folder to the created new backup directory in step (3)
(7) remove backups that are older than X days
(8) run df -l at the end (because I have cron mailing me the results of the backup script, so I will see how much diskspace is still empty)

---

### Post by hyper_ch on 2008-07-08
ups - shouldn't have happened

---

