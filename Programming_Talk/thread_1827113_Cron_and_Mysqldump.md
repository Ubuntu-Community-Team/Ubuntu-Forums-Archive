---
title: "Cron and Mysqldump"
date: 2011-08-17
forum: Programming Talk
---

### Post by itsamemario on 2011-08-17
Hi,

I have just written a script that dumps my sql databases and then deletes dumps that are older than 3 days.

```

mysqldump -u backup -h localhost -p xxxx dbname | gzip -9 > $drupal_dbfile
mysqldump -u backup2 -h localhost -p xxx dbname | gzip -9 > $glt_dbfile

#remove SQL backups older than 3 day...
sqldir=/backup/daily/sql
if [ -d $sqldir ]; then
  find $sqldir -type f -ctime +3 -exec rm -f {} \;
fi

```

While this works, I am worried about the long term. I want to put in a safety net that will e-mail me if the sqldump errors out and stops the removal of old good dumps. Does anyone have an idea?

Mario

---

### Post by slavik on 2011-08-18
check for return code via the $? variable.

---

### Post by Habitual on 2011-08-18
Maybe add set -x in the 1st line of the script and run it manually, it will show you the exact error.

---

