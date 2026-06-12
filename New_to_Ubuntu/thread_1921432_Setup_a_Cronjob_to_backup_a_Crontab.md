---
title: "Setup a Cronjob to backup a Crontab"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by duceduc on 2012-02-06
I am trying to setup a cronjob to backup my crontab but it just creates an empty file. Here is what I input in my crontab -e.
> 
00 01 * * 0 /usr/bin/crontab -l > /media/store02/`/bin/hostname`_`/bin/date +\%Y-\%m-\%d`_crontab_bkup 2>&1

---

### Post by lechien73 on 2012-02-07
That is strange. I've just tried adding the same command to my crontab and it works fine.

The only thing I would suggest is to test if it creates the file properly if you specify your home directory, rather than something mounted through /media.

Additionally you should see something like the following in syslog:

```
Feb  7 16:50:01 lechien-x CRON[28539]: (lechien) CMD (/usr/bin/crontab -l > /home/lechien/`/bin/hostname`_`/bin/date +%Y-%m-%d`_crontab_bkup 2>&1)
Feb  7 16:50:01 lechien-x /usr/bin/crontab[28542]: (lechien) LIST (lechien)
```

---

### Post by duceduc on 2012-02-07
You are correct in that it doesn't seem to work saving in a drive that is mounted. That was where I had it. This crontab was running for awhile now and I didn't bother to check the contain until recently. However, I did test it prior to using this code but I saved it in my primary drive thinking it would work on anywhere saved.

How can I fix this since I do like it to save in an external drive incase my primary fails.

---

### Post by lechien73 on 2012-02-08
If you check syslog after the cron job has run, it will likely give you a reason for the error.

You could try directing the cron job to a subdirectory of /media/store02, which is set to 777 permissions.

---

