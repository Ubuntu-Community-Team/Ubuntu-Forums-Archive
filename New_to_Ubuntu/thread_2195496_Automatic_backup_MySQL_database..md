---
title: "Automatic backup MySQL database."
date: 2013-12-24
forum: New to Ubuntu
---

### Post by LandArch13 on 2013-12-24
I stumbled across this [post]("http://ubuntuforums.org/showthread.php?t=1655888") and wanted to clarify a few things before I attempt this. Newbie to Ubuntu Server... so be gentle.

I have a MySQL database that I would like to automatically backup at a set frequency to a location that automatically has daily backups. So based on the post I have developed this shell script.
```
!/bin/bash
# Dump and compress all mysql databases


if [[ $1 = "" ]] ; then
        out=*desired/location/of/backup/*`date +%A`
else
        out=$1
fi


if [[ ! -d $out ]] ; then
        mkdir -p $out
fi


for db in `mysqlshow | cut -d " " -f 2 | grep -nano "\-\-\+"` ; do
        mysqldump -u root-p*databasepassword* --add-drop-table --single-transaction $db |gzip -c > $out/$db.sql.gz
done


exit 0
```

So, is this generally on the right path? some specifics that I need clarification are:

[LIST=1]
[*]out= can be anyplace that I want it and it will automatically date it?
[*]mkdir= this will make the directory in the out if it does not exist?
[*]How do i set the frequency? is that what $1 specifies?
[*]Can you specify that it deletes older versions or only keeps the last 5?
[/LIST]

---

### Post by SeijiSensei on 2013-12-24
Here's the script I run to create dated backups and rotate them on an eight-day schedule.

```

#!/bin/sh

BACKUPDIR=/root/backups
ROTATE=8
USER=root
HOST=localhost

mkdir -p $BACKUPDIR

# read in a hostname from the command line if it exists
if [ "$1" != "" ]
then
    HOST=$1
fi

LOG="$BACKUPDIR/mysql-$HOST.`date +%y%m%d`.log"
STALELOG="$BACKUPDIR/mysql-$HOST.`date +%y%m%d --date="$ROTATE days ago"`.log"

echo -n `date -R` >> $LOG
echo " MySQL backup procedure for $HOST starting" >> $LOG

CURRENT="$BACKUPDIR/$HOST.`date +%y%m%d`.mysql"
echo "Creating current backup file $CURRENT" >> $LOG

# run the backup and compress it
/usr/bin/mysqldump -u $USER --all-databases > $CURRENT
gzip $CURRENT

# retain monthly copy on 15th; delete state logs
if [ "`date +%d`" != "15" ]
then
    STALE="$BACKUPDIR/$HOST.`date +%y%m%d --date="$ROTATE days ago"`.*"
    echo "Deleting stale backup files $STALE" >> $LOG
    rm -f $STALE
    rm -f $STALELOG
fi

chmod 0600 $BACKUPDIR/*

echo -n `date -R` >> $LOG
echo " MySQL backup procedure for $HOST completed" >> $LOG


```

The script you posted has no provision for rotations.  The check for "$1" looks to see if you have specified a different output file on the command line than the default.

I don't have a root password, but you can add that easily to the mysqldump command.

To automate this process, you need to create an entry in root's "crontab" using the command "sudo crontab -e" or edit the file /var/spool/cron/root directly with your favorite editor.  You'll need sudo permissions to do that, of course.  For the syntax of crontab entries, read this: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by LandArch13 on 2013-12-27
Does it matter if the MySQL data in on another drive? MySQL sources to a 2TB RAID disc. I think having the dump may be redundant, but then the data and the dump are automatically backed up daily to cloud.

---

### Post by SeijiSensei on 2013-12-29
> **LandArch13 said:**
> Does it matter if the MySQL data in on another drive? MySQL sources to a 2TB RAID disc.

I don't know what you mean by "another drive."  Is it mounted into the root filesystem?  The directory where MySQL stores its data is /var/lib/mysql. That need not be on the same device as the root filesystem.  Linux, like Unix in general, doesn't care a whit about the devices on which data are stored.

> I think having the dump may be redundant, but then the data and the dump are automatically backed up daily to cloud.

Now I'm really confused. You posted a script that uses mysqldump.  Isn't that the point?

---

