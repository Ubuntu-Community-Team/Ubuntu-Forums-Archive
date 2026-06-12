---
title: "BASH scripting help requested please"
date: 2014-03-24
forum: Programming Talk
---

### Post by NanoHawk on 2014-03-24
Hi!
I am working on backup automation of an Ubuntu 12.04 LTS instance running in Azure.  I have used the example located at [https://help.ubuntu.com/10.04/serverguide/backup-shellscripts.htm]("https://help.ubuntu.com/10.04/serverguide/backup-shellscripts.html").  I have modified it to suit my needs by changing the scope and also adding a mysqldump to grab a snapshot of the mysql database.

I am using the following code in a file called backup-wp.sh:
```


#!/bin/sh
##################################
#
# Backup script for wordpress
#
##################################


#what to backup
backup_files="/home /var/www"


#where to backup
target= "/backup"


#create archive name
day=$(date +%A)
hostname=$(hostname -s)
archive_file = "$hostname-$day.tgz"


#wordpress backup file name
wpbackup_path = "/home/admin-user"
wpbackup_file = "$wpbackup_path/$day-mysite-wordpress.sql"


#backup mysql
mysqldump mydb > $wpbackup_file


#print start status message.
echo "backing up $backup_files to $dest/$archive_file"
date
echo


#backup the files using tar
tar czf $target/$archive_file $backup_files


#print end status message.
echo
echo "backup complete"
date
echo



```

The script currently lives in my home directory and has been set to +x.

When I run the script using bash backup-wp.sh  I get the following result:


backup-wp.sh: line 12: /backup: Is a directory
backup-wp.sh: line 17: archive_file: command not found
backup-wp.sh: line 20: wpbackup_path: command not found
backup-wp.sh: line 21: wpbackup_file: command not found
backup-wp.sh: line 24: $wpbackup_file: ambiguous redirect
backing up /home /var/www to /
Mon Mar 24 23:40:51 UTC 2014


tar: Removing leading `/' from member names
tar (child): /: Cannot open: Is a directory
tar (child): Error is not recoverable: exiting now


backup complete
Mon Mar 24 23:40:51 UTC 2014


I am stuck trying to figure out what's wrong.... the example is for 10.xx but I would expect it to work.  Can someone please point me in the right direction as to why bash isn't allowing me to define a variable referencing a backup?

Many thanks.

---

### Post by NanoHawk on 2014-03-24
I managed to solve this.  It was a syntax issue.  Apparently bash likes messy code and hates spaces.

This is a no-go and will not work.
target = "/backup" 

This does work
target="/backup"

Hope that helps others who fight with this problem.

---

### Post by Vaphell on 2014-03-25
> I managed to solve this. It was a syntax issue. Apparently bash likes messy code and hates spaces.

It has nothing to do with messy code, remember that bash is used to run commands and treats spaces as parameter delimiters. Spaces actually matter here, unlike in other languages. = sign with no spaces around is how bash recognizes assignments. How would bash differentiate between assignment and command execution?

```
grep = file      # run grep looking for = in file
target = /backup # run command 'target' with 2 params: '=' and '/backup'
target=/backup   # this is an assignment

```
line 1 and 2 are the exact same situation

any bash manual mentions it in the chapter about variables.

---

