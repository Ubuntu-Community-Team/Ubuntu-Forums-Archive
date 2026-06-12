---
title: "Postgresql backup Bash script"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-05-24
Hi, friends

#!/bin/bash
/usr/bin/pg_dump --host localhost --port 5432 --username postgres --format plain --no-owner --verbose --file "/home/ten10admin/multidadev/MULTIDA-DEV.sql" "MULTIDA-DEV"


i saved the above script in a file called test.sh, 
problem is; i cannot execute test.sh file in crobjob but i could execute by manually like this;
jug@fpmohan:~/Desktop/mysql$ ./test.sh

When i run manually as ./test.sh in terminal, file MULTIDA-DEV.sql exported but in cronjob its not executing.

---

### Post by lethall1 on 2013-05-24
Try
Sudo tail -f /var/log/syslog
when cron must execute it. 
But I think you just need to write the full path to your script in cron, like /home/username/desktop/scriptname

---

### Post by siddharth007 on 2013-05-27
From what i see in your script i guess you need to include the --password option as well.The password needs to be hardcoded in the script itself.

---

### Post by zeljkojagust on 2013-05-27
I also think the problem is with full path to your script in cron job.

---

### Post by pmohankumar on 2013-05-27
Hi,

My cron entry is:
01 18 * * * /home/ten10admin/scripts/test.sh

Cron job running at 6.01 PM. there is no problem in cron running.

Problem is in script, i am asking correct script to take backup of postgresql with current date and time.

Thanks,
mohan

---

### Post by pmohankumar on 2013-05-28
Hi,

kindly provide a  backup script For postgrsql with current data and time.

Thanks,
mohan

---

### Post by wealthy2 on 2013-08-05
> **pmohankumar said:**
> Hi,

kindly provide a  backup script For postgrsql with current data and time.

Thanks,
mohan

If I am not mistaken:
```
[SIZE=2][FONT=lucida console]#!/bin/bash
**DATE**=**`which --skip-alias date`**
**TODAY**=**`$DATE '+%Y-%m-%d'`**
/usr/bin/pg_dump -h localhost -p 5432 -U postgres -F plain -O -v -f "/home/ten10admin/multidadev/MULTIDA-DEV.**$TODAY**.sql" "MULTIDA-DEV"[/FONT][/SIZE]
```

In case of the archive file is to be named as the previous date:
```
[SIZE=2][FONT=lucida console]#!/bin/bash
DATE=`which --skip-alias date`
**YESTERDAY**=`$DATE -d **'1 days ago'** '+%Y-%m-%d'`
/usr/bin/pg_dump -h localhost -p 5432 -U postgres -F plain -O -v -f "/home/ten10admin/multidadev/MULTIDA-DEV.**$YESTERDAY**.sql" "MULTIDA-DEV"[/FONT][/SIZE]
```

I changed the options to shorter names, hope you don't mind ;)

---

### Post by SeijiSensei on 2013-08-06
I use this to produce dated archives:

```

#!/bin/sh

BACKUPDIR=/var/lib/pgsql/backups
ROTATE=8

ARCHIVEDIR=""
ARCHROTATE=30

USER=postgres
HOST=localhost

LOG="$BACKUPDIR/pgsql-$HOST.`date +%y%m%d`.log"
STALELOG="$BACKUPDIR/pgsql-$HOST.`date +%y%m%d --date="$ROTATE days ago"`.log"

# if a host is listed on the command line, use that
if [ "$1" != "" ]
then
    HOST=$1
fi

echo -n `date -R` >> $LOG
echo " Postgres backup procedure for $HOST starting" >> $LOG

# connect to remote host $HOST if required
CURRENT="$BACKUPDIR/$HOST.`date +%y%m%d`.pgsql"

echo "Creating current backup file $CURRENT" >> $LOG
/usr/bin/pg_dumpall -U $USER -h $HOST > $CURRENT
gzip $CURRENT

# retain monthly archival copy on 15th; delete state logs
if [ "$(date +%d)" != "15" ]
then

    STALE="$BACKUPDIR/$HOST.$(date +%y%m%d --date="$ROTATE days ago").*"
    echo "Deleting stale backup files $STALE" >> $LOG
    rm -f $STALE
    rm -f $STALELOG

    if [ "$ARCHIVEDIR" != "" ]
    then
        echo "Copying current backup to additional location $ARCHIVEDIR" >> $LOG
        rsync -av $BACKUPDIR/* $ARCHIVEDIR --delete
    fi

fi


chmod 0600 $BACKUPDIR/*

echo -n `date -R` >> $LOG
echo " Postgres backup procedure for $HOST completed" >> $LOG

```

I don't use a password on my databases because the server is bound to localhost, and only web apps access it.  If you want to include a password, you'd need to include it in the script, or store it in a separate file that the script can read.

---

