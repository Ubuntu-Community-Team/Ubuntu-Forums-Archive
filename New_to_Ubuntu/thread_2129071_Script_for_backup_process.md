---
title: "Script for backup process"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-03-25
Hi friends,

i need a script for mysql backup with date:month:year, date:month:year should update automatically with system date&time.

The backup format test25-03-2013.sql

Please guide me regarding this request to make it as done.

---

### Post by siddharth007 on 2013-03-25
To take backups in mysql use the **mysqldump **command.For a brief tutorial see this [link]("http://bluesteel007india.blogspot.com/2013/03/mysqllinux-creating-and-restoring.html").To do backups regularly put the mysqldump command in the cron file. In the same crontab file put these commands

```
thetime=`date +%Y-%m-%d--%H:%M:%S`
mv backupfilename.sql $thetime-backupfilename.sql
```

---

### Post by pmohankumar on 2013-04-09
[COLOR=#000000]siddharth007, your script working. thanks friend.

[/COLOR]"mysqldump -u root -proot --routines --databases codereview > /home/redmine/codereviewDBbackup/codereview.sql
thetime=`date +%Y-%m-%d--%H:%M:%S`
mv codereview.sql $codereview.sql-thetime"

Above is my complete script(without quotes) to take mysql backup with current date and time.
when i set this file which was saved as codereview.sh in cron, only the first line executed, 2nd & 3rd lines are not executed. i am getting output as codereview.sql

---

### Post by siddharth007 on 2013-04-10
Understand this

*thetime* is a shell variable which is storing the date & time when the backup takes place.As per your requirement the third line should be
```
mv codereview.sql codereview-$thetime.sql
``` 

For a complete tutorial on mysql backup visit my blog [http://bluesteel007india.blogspot.in](http://bluesteel007india.blogspot.in)

---

### Post by SeijiSensei on 2013-04-10
You might find this script helpful: [http://ubuntuforums.org/showthread.php?t=1668840&p=10368151#post10368151](http://ubuntuforums.org/showthread.php?t=1668840&p=10368151#post10368151)

---

