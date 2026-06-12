---
title: "Need basic help with cron."
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Madman6510 on 2008-05-07
I got a backup script that backs up all of the files in a certain directory to a Samba share.

I looked for some guides, but they only said how to make the cron job run on certian days, not EVERY day.

Can someone tell me how to make a cron job that runs every night at 3 AM?

EDIT: I also need to know how to make the cron job run as root automatically. (It's a clean script, I checked).

---

### Post by tagra123 on 2008-05-07
sudo gedit /etc/crontab

#heres a everyday script
# a script running as root
01 03 * * * root /home/someusername/bin/myscripts/rsbackups/backup.sh

# a script running as some user
01 03 * * * yourusername /home/someusername/bin/myscripts/rsbackups/backup.sh
0

---

### Post by quelx on 2008-05-08
If you want the cronjob added to the crond immediatly after editing it you need to use ```
sudo crontab -e
``` instead.  The cron daemon will re-read the file when you're done rather than waiting for a reboot or restart of the crond process.

you can use ```
sudo crontab -l
``` to see the job list after you are done.

---

