---
title: "Backup/NAS/desktop/laptop/rsync"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by il pepe on 2014-01-14
Hi,
I have some issues (2) with automation of my backup.

first:
What I want:
-> 1 backup every week
-> no manual input

Setup
-> NAS
-> Laptop

How do I do this? I have a working rsync script.
```
rsync -avz -e "ssh -p2222" --numeric-ids --delete  --exclude-from=/home/XXXX/backup.exclude --stats --link-dest="../`date  +%Y-%m`" /home/XXXX/Documents  "XXXX@XXXXX:/Path/to/destination/`date  +%Y-%m-%d`/"
```
I suppose I have to make ssh keys.
My laptop is mobile, so the script should check whether I'm at home (so if the NAS is available or not). How do I do this?

second:
Same story for my desktop but the other way around. I would like one backup every week of my NAS. The desktop is not always on. How do I automate this, without over using the desktop at startup so it is still useable...

---

### Post by ian-weisser on 2014-01-14
> **il pepe said:**
> 
My laptop is mobile, so the script should check whether I'm at home (so if the NAS is available or not). How do I do this?
Try the **nmcli** command. The output is greppable, and you can use shell logic on the result. For example:
```
[$(nmcli con status | grep -q MySSID)] && echo Not Found || echo On Network
```

> **il pepe said:**
> Same story for my desktop but the other way around. I would like one backup every week of my NAS. The desktop is not always on. How do I automate this, without over using the desktop at startup so it is still useable...
This seems like the kind of task cron and anacron were created for...
Is there a reason it can't be a cron.weekly job?

---

### Post by il pepe on 2014-01-15
Hi,
Thanks for the tip.
With cron, i'm just afraid what is going to happen if my desktop is off. Then I suppose the NAS or the desktop (whether the script starts from) is going to try once a week. But what if my desktop is off at that moment... Then now backup that week? Or I shutdown the desktop to early... Then only a partial backup.

I think I might have come up with a solution myself. Probably not the best one, but still.
I would make a log file, where I write the date of e.g. the 5 last backups and a backupflag. If last date is less than 7 days ago, nothing should happen except if the backup flag is 0 (meaning in an incomplete backup.) I would also be using the last 5 complete backup date to purge the backup folder with older backups...
What do you think? To complex? stupid idea?

---

### Post by rubylaser on 2014-01-15
> **il pepe said:**
> Hi,
Thanks for the tip.
With cron, i'm just afraid what is going to happen if my desktop is off. Then I suppose the NAS or the desktop (whether the script starts from) is going to try once a week. But what if my desktop is off at that moment... Then now backup that week? Or I shutdown the desktop to early... Then only a partial backup.

I think I might have come up with a solution myself. Probably not the best one, but still.
I would make a log file, where I write the date of e.g. the 5 last backups and a backupflag. If last date is less than 7 days ago, nothing should happen except if the backup flag is 0 (meaning in an incomplete backup.) I would also be using the last 5 complete backup date to purge the backup folder with older backups...
What do you think? To complex? stupid idea?

You could setup wakeonlan from your NAS to "wakeup" your desktop via a cronjob.  I would setup a simple bash script that first runs etherwake (uses wakeonlan) to wake up the deskop, then have the script sleep for 600 seconds to allow your desktop to wakeup completely.  After the sleep duration is done, I would write a simple loop to ping the desktop to make sure it's available.  If so, have it run your backup job, if not have it email you and write to the log.

---

### Post by ian-weisser on 2014-01-15
> **il pepe said:**
> With cron, i'm just afraid what is going to happen if my desktop is off. 

Then anacron will run the job next time your desktop is on. Just like all the other jobs in /etc/cron.weekly
That's what anacron does. That's *all* anacron does.

Depending upon your backup method, you can get faster, shorter backups with daily (instead of weekly) jobs.
Worrying about an incomplete job implies that perhaps those jobs take too long...or perhaps your shutdown is not checking for backup completion and killing a running backup process.

You don't need to reinvent the wheel on backups. Lots of great tools for backing up.
One great tool for scheduling backups (cron/anacron).
One great tool for monitoring a running process and preventing shutdown (Upstart).

---

