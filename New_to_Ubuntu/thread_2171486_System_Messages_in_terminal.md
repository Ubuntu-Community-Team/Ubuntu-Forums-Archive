---
title: "System Messages in terminal"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by novice_penguin on 2013-08-31
Hi all, I just performed the shutdown -r now command to restart my machine, and unlike other times I've used this command, a message was briefly displayed before the machine was restart.  My question is, how can I look up a message that was output in the terminal by the system?  I'm curious to know because it looked like it was an error message of some sort.  I checked in the Linux Command Resources thread but to no avail.  Any help would be appreciated, thanks.  BTW I'm on 12.04 LTS.

---

### Post by nerdtron on 2013-08-31
I think it is in the /var/log/dmesg or in the /var/log/syslog

---

### Post by novice_penguin on 2013-09-02
Thank you!  I found it in var/log/syslog, but it is only showing me messages from today.  Is there a way that I can go back to a particular day?

---

### Post by nerdtron on 2013-09-02
```
cd /var/log/
ls -l
```

Output is a lot of logs:
```
....
-rw-r----- 1 syslog            adm  213254 Sep  3 11:17 syslog
-rw-r----- 1 syslog            adm   97429 Sep  3 09:00 syslog.1
-rw-r----- 1 syslog            adm   40291 Sep  2 08:58 syslog.2.gz
-rw-r----- 1 syslog            adm    4114 Aug 30 08:43 syslog.3.gz
-rw-r----- 1 syslog            adm   41273 Aug 29 08:44 syslog.4.gz
-rw-r----- 1 syslog            adm    3216 Aug 28 09:03 syslog.5.gz
-rw-r----- 1 syslog            adm    2252 Aug 27 09:01 syslog.6.gz
-rw-r----- 1 syslog            adm    3184 Aug 23 08:51 syslog.7.gz
....

```

See the dates? Those are compressed log files. Extract them and view their contents.

---

### Post by novice_penguin on 2013-09-03
Thanks!

---

