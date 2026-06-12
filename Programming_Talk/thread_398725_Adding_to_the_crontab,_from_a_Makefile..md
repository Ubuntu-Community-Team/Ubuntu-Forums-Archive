---
title: "Adding to the crontab, from a Makefile."
date: 2007-04-01
forum: Programming Talk
---

### Post by f0rmula on 2007-04-01
Is there an easy way to append to the crontab from within a Makefile?

doing '$crontab newcronjob' replaces the crontab entirely.

So far, I'm planning on doing:

$crontab -l > cronfile
$echo "0 * * * * /bin/whatever" >> cronfile
$crontab cronfile
$rm cronfile

I realise this is rather grim.  Please tell me there's a easier (and probably obvious) way I don't know about. :)

James

---

### Post by foxylad on 2007-04-04
Yes - it's much easier to put a file in the /etc/cron.hourly, /etc/cron.daily, /etc/cron.weekly or /etc/cron.monthly directories. Anything in these directories will be run at the relevant time.

Enjoy!
FoxyLad.

---

### Post by kpatz on 2007-04-04
If you want more precise control than offered in cron.hourly etc., such as running at specific times or as a specific user, you can create a file in /etc/cron.d containing your crontab entries.

The format for files in /etc/cron.d are different than regular crontabs.  In particular there is a user field after the times and before the command.  So instead of:```
0 * * * * /bin/whatever
```you'd have```
0 * * * * root /bin/whatever
``` (if you want the program to run as root).

---

