---
title: "Ubuntu Studio 20.04 problems with crontab"
date: 2020-08-13
forum: New to Ubuntu
---

### Post by kyronlaube on 2020-08-13
Hello everybody! I've installed Ubuntu Studio and in my Auth.log file it states this:  01:17:01 (username)  CRON[8897]: pam_unix(cron:session): session opened for user root by (uid=0) 01:17:01 (username)  CRON[8897]: pam_unix(cron:session): session closed for user root  01:30:01 (username) CRON[8897]: pam_unix(cron:session): session opened for user root by (uid=0) 01:30:01 (username)  CRON[8897]: pam_unix(cron:session): session closed for user root  It happens multiple times every day and it also seems when I open the terminal and do: sudo crontab -l   it displays no crontab for (username)  SO Im really puzzled. I have checked in the cron folders, and there are some files: 0anacron , logrogate , man-db , apport , apt-compat , bsdmainutils , dpkg , update-notifier-common , popularity- contest and e2_scruball   Is this a virus? It does appear on the log every 15min and alternate to every 30min sometimes..  Thanks for the help!!

---

### Post by spjackson on 2020-08-14
Everything you mention is completely normal on Studio 20.04. What makes you think there is a problem?

If you need some reassurance, the CRON messages in auth.log will match with CRON messages in syslog where you can find the commands that are being run. If you want to find which package provides these things and what those packages are, the following commands are one way to do it.
```

dpkg -S /etc/cron.daily/popularity-contest
apt-cache show popularity-contest

```
And similar for whatever else you are suspicious of.

---

