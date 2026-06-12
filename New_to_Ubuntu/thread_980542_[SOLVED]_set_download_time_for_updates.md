---
title: "[SOLVED] set download time for updates????"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by stinger30au on 2008-11-12
is it possible to set ubuntu to download the updates in the background at a specific time???
i know i can set it to download updates automatically, but how do you tell it what time to go and d/l the updates???

---

### Post by handydan918 on 2008-11-12
> **stinger30au said:**
> is it possible to set ubuntu to download the updates in the background at a specific time???
i know i can set it to download updates automatically, but how do you tell it what time to go and d/l the updates???

I have no idea how you might do this in a GUI, but you could set a cron job to run (as root)```
 apt-get update && apt-get upgrade
```

---

### Post by blackened on 2008-11-12
I would also suggest using cron. [Here]("http://www.scrounge.org/linux/cron.html") is a decent description of how to setup cron jobs.

---

### Post by jamesrl on 2008-11-12
Maybe make a root crontab entry for
apt-get update --yes && apt-get upgrade --yes

E.g., add a line to /etc/crontab for a root user
(or /etc/cron.daily  /etc/cron.weekly )

See info crontab or look here for more info:
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

---

### Post by ciscosurfer on 2008-11-12
@stinger30au,

I agree that setting up a cron job is the way to go.  If you don't want to mess with the command line, you can install a GUI app from the repos called gnome-schedule (KDE has a counterpart that is popular too, though I can't think of it right now).```
sudo apt-get update && sudo apt-get install gnome-schedule
```

---

### Post by stinger30au on 2008-11-13
> **ciscosurfer said:**
> @stinger30au,

I agree that setting up a cron job is the way to go.  If you don't want to mess with the command line, you can install a GUI app from the repos called gnome-schedule (KDE has a counterpart that is popular too, though I can't think of it right now).```
sudo apt-get update && sudo apt-get install gnome-schedule
```


thanks for the tip, sure made my life easy to use gnome-schedule

i just set it up and tested it and it runs fine, i used the code from an earlier post

"sudo apt-get update --yes && apt-get upgrade --yes"

yee-haw, im in business!!! thanks so much guys:guitar:

---

