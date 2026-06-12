---
title: "crontab jobs backup"
date: 2020-12-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-17
running ubuntu 20.04
found this script to add to crontab that will backup all my crontab jobs
is the below correct 
@daily          crontab -l > $HOME/.crontab
this just uses the @daily expression

---

### Post by TheFu on 2020-12-17
Seems you either found incomplete advice or didn't understand it.

If you want a copy of your userid's personal crontab, then
```
crontab -l > ~/some-backup-directory/crontab.$USER
```
is how I'd do it.  But this doesn't capture crontabs for other users or all the crontabs in /etc/, which you almost certainly want.

If you want to see the contents while this command runs, use
```
crontab -l |tee ~/some-backup-directory/crontab.$USER
```

~/some-backup-directory/ must already exist.  I have a ~/backups/ directory to hold stuff like this and I include that in my backup script to other storage. A backup that is on the same physical HDD/SSD isn't really a backup. It is a copy, but just as likely to be lost when the HDD/SSD dies.  All storage is going to die - hopefully after a very long life, but sometimes they die after a few months too.

---

### Post by rburkartjo on 2020-12-17
thats what i thought the advise was incomplete
i am running this command
set up so i can get notification if run by crontab or in the terminal

#!/bin/bash
crontab -u ray -l > /home/ray/cron-backup.txt
echo "job finished @$(date +'%T')" >> /home/ray/cron-backup.txt

/usr/bin/env DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus /usr/bin/notify-send  -t 0 'scan done'


/usr/bin/env DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
/usr/bin/yad --text "scan is done" & exit

---

### Post by TheFu on 2020-12-17
**crontab -u ray**
is redundant. 'ray''s crontab can only be viewed by ray or root.

By default, cron jobs send output via email.  Run a local mail client, like Mail and check that you aren't filling /var/ with old cron output. I bet you have been.
Copying a file like that is 0.00002 seconds. Do you really need notification about that?  OTOH, I had popup notiifations and ensure I don't get interrupted with any. OTOH, I love getting an email about automation tasks, but only if they have an error. If they complete without any error, don't say anything.  That's the Unix way and cron has methods to make that work.

The /usr/bin/env doesn't make sense to me.  Perhaps you want **export DBUS_SESSION_BUS_ADDRESS=unixath=/run/user/1000/bus** instead? I don't know. Don't use DBUS myself.

With your method, what happens if the cron job runs and you aren't logged in?

---

### Post by rburkartjo on 2020-12-17
tks fu
while probably not the best way i wanted a desktop reply when crontab job was completed not pretty but it works. always appreciate you advise. and i am the only one on this computer

---

