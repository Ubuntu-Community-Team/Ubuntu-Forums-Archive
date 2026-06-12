---
title: "Passing command line parameters in a cron job"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by siddharth007 on 2013-10-21
Hi everyone,

I have a bash script which takes incremental backup of mysql databases.However,i need to provide the database name and login credentials on command line when i run the script.Something like this 
```
echo "usage $0 <dbname> [dbcredentials]"
```

Some key points are
[LIST=1]
[*]I run the script manually everytime to take the incremental backup
[*]The script takes backup of only 1 database and its tables at a time.
[/LIST]

To automate the incremental backup process,i have decided to run the script as cronjob.I can specify the credentials in root's crontab.However, it would be very inconvenient to have 5 different cron jobs for 5 different databases.Any suggestions to ease my work.

---

### Post by drmrgd on 2013-10-21
Commandline args passed to the script are stored in the variables "$1", "$2", etc.  So, you could take advantage of that when you call the script so that in the script:

```

#!/bin/bash

dbname=$1
dbcredentials=$2

<rest of script>

```

You could also use **getopts** if you want to name your options when you are passing them:

[http://wiki.bash-hackers.org/howto/getopts_tutorial](http://wiki.bash-hackers.org/howto/getopts_tutorial)
[http://mywiki.wooledge.org/BashFAQ/035#getopts](http://mywiki.wooledge.org/BashFAQ/035#getopts)

Yet a third way is to roll your own with a case statement, which is probably not the preferred way.  Here's another example of the above methods and a case statement example:

[http://linuxcommand.org/wss0130.php](http://linuxcommand.org/wss0130.php)

---

### Post by TheFu on 2013-10-21
Here's the script that I use to backup a DB.
```
#!/bin/bash
DB_NAME=redmine_default
BACKDIR=/root/backup/
/usr/bin/mysqldump -u root \
    -p`cat ~root/bin/$DB_NAME.passwd.root` $DB_NAME | \
    gzip > $BACKDIR/${DB_NAME}_`date +%Y%m%d`.gz
find  $BACKDIR -type f -name $DB_NAME\* -atime 60 -exec rm {} \;
```

Then the contents of the **$DB_NAME.passwd.root** is just the password. That file is owned by root with 600 perms and stored inside a directory that no other userid can access.

It would be easy to make this script accept a different DB_NAME, since everything is parametrized off that variable.

The **Advanced Bash Scripting Guide** could be used to learn about stuff like this. Google will find it easily.

---

### Post by btindie on 2013-10-21
> **siddharth007 said:**
> I can specify the credentials in root's crontab.However, it would be very inconvenient to have 5 different cron jobs for 5 different databases.Any suggestions to ease my work.
It's too inconvenient to have 5 lines in a crontab to backup different databases??

If that's your view then create a wrapper script that reads the credentials from a text file and calls your main backup script. e.g.
```
# database:username:password
db1:user1:pass1
db2:user2:pass2
db3:user3:pass3
```

```
#!/bin/bash

CONF=$1

sed -e '/^$/d;/^#/d' $CONF | while read LINE; do
  dbNAME=${LINE%%:*}; LINE=${LINE#*:}
  dbUSER=${LINE%%:*}; LINE=${LINE#*:}
  dbPASS=${LINE}
  database_backup $dbNAME $dbUSER $dbPASS
done
```

Then add a line to your crontab with the command as follows:
```
database_backup-wrapper /root/dbbackup.conf
```

---

### Post by Vaphell on 2013-10-21
> **btindie said:**
> 
```
#!/bin/bash

CONF=$1

sed -e '/^$/d;/^#/d' $CONF | while read LINE; do
  dbNAME=${LINE%%:*}; LINE=${LINE#*:}
  dbUSER=${LINE%%:*}; LINE=${LINE#*:}
  dbPASS=${LINE}
  database_backup $dbNAME $dbUSER $dbPASS
done
```

not too pretty ;-)
```
while IFS=: read -r dbname dbuser dbpass
do
  database_backup "$dbname" "$dbuser" "$dbpass"
done < <( sed -r '/^#|^$/d' "$conf" )
```

---

### Post by TheFu on 2013-10-21
Don't forget to check that something was entered for the argument, otherwise, bail out.

```
if [[ -z "$1" ]] ;  then
   echo "DB argument missing for $0"
   exit -500
fi
```

Of course, there are 50 other ways to do the same thing. ;)

---

### Post by siddharth007 on 2013-10-23
Thank you everyone for the response.I got it :p

---

