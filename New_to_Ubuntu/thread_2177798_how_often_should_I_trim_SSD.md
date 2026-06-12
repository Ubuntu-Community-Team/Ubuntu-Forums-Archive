---
title: "how often should I trim SSD"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by jon12 on 2013-09-30
I have the Samsung 840 Pro.  How often should I run the manual trim command???  My old computer doesnt offer a change to AHCI but the
the SSD works good anyway.

---

### Post by oldfred on 2013-09-30
Somewhere I saw that trim did not work without AHCI.

But I have a daily cron job to run trim.

 HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)

      
 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim

Copy & paste into trim
   ```
#!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG
```

---

### Post by jon12 on 2013-09-30
it does work   but it might work differently in distros....

---

