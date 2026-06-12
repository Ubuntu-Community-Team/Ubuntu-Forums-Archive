---
title: "automatically backup mysql database"
date: 2007-03-05
forum: Programming Talk
---

### Post by nandasunu on 2007-03-05
Hi,

Is there a way to have an automatic backup of a mysql database? I want a .sql file that will recreate the whole database if needed, something like phpmyadmin creates with their export function.

I have my database on a shared hosting if that makes a difference.

thanks.

---

### Post by ehowell on 2007-03-05
mysqldump will do it.

I made a shell script (backupscript.sh) to do daily backups and I call it with cron.

Replace things with what the word says (e.g. hostname is your database hostname)

I also gzip the file at the end but you can skip that step

```
#!/bin/ksh
echo "Backing up PHPBB database!"
/usr/bin/mysqldump --add-drop-table -u database_user -ppassword -hhostname database > /ABSOLUTEPATH/PHPBB_backup.sql
/bin/gzip -f /ABSOLUTEPATH/PHPBB_backup.sql
```

---

### Post by skeeterbug on 2007-03-06
I use the mysql admin application. In the backup section there is a schedule tab. It probably does the same thing the poster above is doing via the command line.

---

### Post by nandasunu on 2007-03-06
thanks for the tips, the mysql admin seems pretty cool, thanks for the script also! much appreciated.

---

