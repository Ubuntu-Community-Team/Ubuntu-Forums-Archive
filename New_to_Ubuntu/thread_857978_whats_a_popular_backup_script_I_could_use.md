---
title: "whats a popular backup script I could use???"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by callagga on 2008-07-13
Hi,

I want to set up nightly backups to a remote computer using rsynch. I've been looking for the most popular scripts to use, and so far have the following two below.  If you know of any more well known & tested backup scripts than these can you let me know?

* [http://rsnapshot.org/]("http://rsnapshot.org/")

* [HOWTO: Backup nightly via rsync]("http://ubuntuforums.org/showthread.php?t=639979")

Thanks

---

### Post by hyper_ch on 2008-07-13
I use my own script:

backup.sh
```

#!/bin/bash
unset PATH


# USER VARIABLES
BACKUPDIR=/backup                               # Folder on the backup server where the backups shall be located
EXCLUDES=/backup/exclude_list                   # File containing the excluded patterns
DAYS=90                                         # The number of days after which old backups will be deleted


# PATH VARIABLES
SH=/bin/sh                                      # Location of the bash bin in the production server!!!!

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
PASSWORD=*******************
HOST=localhost

for i in $(echo 'SHOW DATABASES;' | mysql -u$USER -p$PASSWORD -h$HOST|grep -v '^Database$'); do
  mysqldump                                                     \
  -u$USER -p$PASSWORD -h$HOST                                   \
  -Q -e -C --add-drop-table --add-locks --quick --lock-tables   \
  -B $i                                                         \
  $i > /mysql_backup/$i.sql;
done;

```

exclude_list
```

/backup/current/
/backup/old/
/backup/test/
/bin/
/boot/
/dev/
/initrd/
/lib/
/lost+found/
/media/
/mnt/
/proc/
/sbin/
/sys/
/tmp/
/usr/
/var/backups/
/var/cache/
/var/local/
/var/lock/
/var/log/
/var/mail/
/var/opt/
/var/run/
/var/spool/
/var/tmp/

```

---

### Post by callagga on 2008-07-13
tks hyper_ch - what's your script roughly doing re the line "$CP -al $CURRENT/* $NOW"?   It seems to be not a remote backup (just local).  Can you actually recover a full set of files from say 11 days ago using this?  (I see you had 90 days as limit)

---

### Post by hyper_ch on 2008-07-13
(1) of course you could make a remote backup... either use rsync over ssh use sshfs to bind the remote dir into the local filesystem....

(2) that line will make hardlinks... hence incremental snapshotstyle backups... dating back for 90 days (or whathever you wish). In "current" you have the latest backup and in "old" you have the previous ones.

---

### Post by callagga on 2008-07-13
> **hyper_ch said:**
> (2) that line will make hardlinks... hence incremental snapshotstyle backups... dating back for 90 days (or whathever you wish). In "current" you have the latest backup and in "old" you have the previous ones.Still don't quite understand.  I looked up -al so this is archive & link.

But what happens if you modify a file over time.  Wouldn't the hard link from yesterday just point to the current file and hence it wouldn't reflect how it was yesterday :confused:

---

### Post by hyper_ch on 2008-07-13
[http://en.wikipedia.org/wiki/Hard_link](http://en.wikipedia.org/wiki/Hard_link)

if the file is modified it makes a new entry ;)

---

### Post by callagga on 2008-07-13
unfortunately the penny hasn't dropped yet for me...

I created a test file in ./new and then created a hard link via "cp -al ./new old".  They have the same inodes when doing "ls -ri".  

When I changed the text file in ./new and then did a "cat ./old/testfile.txt" it had also changed?  This would have implied you'd lost the detail of how the file looked previously?

---

### Post by hyper_ch on 2008-07-13
rsync is not the same as editing

---

### Post by callagga on 2008-07-13
oh..I'll read up on rsynch then..thanks

---

### Post by hyper_ch on 2008-07-13
[http://www.mikerubel.org/computers/rsync_snapshots/#Incremental](http://www.mikerubel.org/computers/rsync_snapshots/#Incremental)

---

### Post by control_guy on 2008-09-28
Thank you hyper_ch very much for the useful script.

---

