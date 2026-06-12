---
title: "Anacron broken?"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by DetroitDoc on 2013-05-13
I have a laptop with an SSD with Ubuntu 13.04 on it.   I wanted to set it up to run fstrim daily.    Since it's a laptop I can't guarantee when it'll be on so I decided to use anacron by dropping a script in the /etc/cron.daily directory.

It has not been running so I started to do a little searching.  anacron is not in the process table.    It is in /etc/init/anacron.conf and in /etc/init.d.    I can see logs in syslog that look normal stating it will run the cron.daily / cron.weekly in X minutes.   However the pid it's logging under is no longer in the process table.

---

### Post by DetroitDoc on 2013-05-13
Very strange.... I ran anacron by hand with the -d option and it completely successfully.  I reset the date back in /var/spool/anacron/cron.daily to the a few days ago and rebooted the system and now it appears to be working.

I did happen to notice the apt script in /etc/cron.daily has a random sleep in it that can be very long.   It looks like run-parts runs the scripts sequentially so this sleep in the apt script can hang the process up for a very long time.  

I'll have to watch it again tomorrow.

---

