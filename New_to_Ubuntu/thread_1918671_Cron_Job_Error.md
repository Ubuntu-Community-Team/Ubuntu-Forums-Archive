---
title: "Cron Job Error"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2012-02-01
Hi

Just need some advice on a cron job.

I am backing up my Joomla database on a daily basis, by using the following cronjob which works:

/usr/bin/mysqldump -u [db_user] [db_name] -p[db_password] > /home/floss/floss_db_backup.sql

Now, I want the date to be added to the filename, so I used:

/usr/bin/mysqldump -u [db_user] [db_name] -p[db_password] > /home/floss/floss_db_backup.sql-`date "+%Y%m%d"`

However, I get the following error message:

/bin/sh: -c: line 0: unexpected EOF while looking for matching `"'
/bin/sh: -c: line 1: syntax error: unexpected end of file

I have played around with the apostrophes and quotes, but are none the wiser.


Any advice will be appreciated.

Kind Regards

ARNOLD

---

### Post by Lars Noodén on 2012-02-01
It's preferred to [use $(...) over backticks](http://mywiki.wooledge.org/BashFAQ/082).  You could try like this:

```

... /home/floss/floss_db_backup.sql-$(date "+%Y%m%d")

```

---

### Post by arnold.pietersen on 2012-02-01
Hi Lars

Thanks for your response.

I now have the following:

/usr/bin/mysqldump -u floss_arnie floss_flossnet -ppassword > /home/floss/flossnet_db_backup-$(date "+%Y%m%d").sql;

I get the following error message:

/bin/sh: -c: line 0: unexpected EOF while looking for matching `"'
/bin/sh: -c: line 1: syntax error: unexpected end of file

Any other suggestions?

Kind Regards

ARNOLD

---

### Post by Lars Noodén on 2012-02-01
No real suggestions, but it's getting complex enough that you might separate it out into its own script and then call the script from cron.  That might make a difference in debugging.

---

### Post by arnold.pietersen on 2012-02-01
Hi Lars

I got it working. The trick was using the escape (\) command.

Thus, my final cron job looks as follows:

/usr/bin/mysqldump -u floss_arnie floss_flossnet -ppassword | gzip > /home/floss/flossnet_db_backup-`date '+\%d\%m\%Y'`.sql.gz;

Thanks a million for your advise.

Kind Regards

ARNOLD

---

