---
title: "small bash backup script q"
date: 2008-01-14
forum: Programming Talk
---

### Post by thnn on 2008-01-14
I have a db_dump script, and a second script that uploads the files to an amazon s3 bucket for backup. 

I wrote the bash script below, and put it in /etc/cron.weekly

Now, I can run this script manually ( sudo /etc/con.weekly/my_bak_script ) and it uploads fine. Every week cron does in fact call the script, because I get the email, but none of the files are uploaded.

It's a noob question - but why would it behave differently in these two cases? Is there something wrong with the script? Or is it something else?

thx

```

#!/bin/bash
# remove previous backups so we dont end up re-uploading to S3
if [ -d /tmp/bak ]; then rm -r /tmp/bak; fi
python /home/djprojects/macmain/db_dump.py -d /tmp/bak/`date "+%Y/%b/%d"` --settings=macmain.live_settings dump
cd /tmp
find bak | /usr/local/bin/update_s3_priv
echo "hooray" | mail [email]my@email.com[/email] -s "BAK Complete"

```

---

### Post by jrib on 2008-01-14
Whose crontab is the script being called from?
Check your local mail from your cron daemon to see what the errors were.

---

### Post by thnn on 2008-01-14
ah ok - there are messages in roots inbox. Thanks for the tip

---

