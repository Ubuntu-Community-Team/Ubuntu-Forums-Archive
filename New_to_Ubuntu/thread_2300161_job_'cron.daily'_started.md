---
title: "job 'cron.daily' started"
date: 2015-10-24
forum: New to Ubuntu
---

### Post by myron2 on 2015-10-24
hello

i have a problem with my syslog every 24 hours my log stop cause of this, the porpuse i created this syslog to log all mg networking switch. can anyone enlighten me how to fix this.

thank you very much

myron

---

### Post by ajgreeny on 2015-10-24
Let's see the output of ```
ls /etc/cron.daily
cat /etc/cron.daily/logrotate
``` to see if you have added any daily cron jobs that are causing this, or your logrotate, the only daily job affecting logs on my system, has been changed on yours from the default.

---

### Post by myron2 on 2015-10-27
hello sir this is the output 

root@fblogserver-Lenovo-G460:~# cat /etc/cron.daily/logrotate
#!/bin/sh

# Clean non existent log file entries from status file
cd /var/lib/logrotate
test -e status || touch status
head -1 status > status.clean
sed 's/"//g' status | while read logfile date
do
    [ -e "$logfile" ] && echo "\"$logfile\" $date"
done >> status.clean
mv status.clean status

test -x /usr/sbin/logrotate || exit 0
/usr/sbin/logrotate /etc/logrotate.conf

thanks

---

