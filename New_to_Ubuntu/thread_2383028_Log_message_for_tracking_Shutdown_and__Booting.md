---
title: "Log message for tracking Shutdown and  Booting"
date: 2018-01-20
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-01-20
Does sys.log have a log message that corresponds to shutdown & boot.  I saw boot.log but that does not have any time stamp. So it is not possible to co-relate it to sys.log
I am seeing critical error dialogs during log-in. So I am going through the SYS.log file and then google for those errors. Fix them if possible and then reboot again. Then check the sys.log again.
Problem is I am not able to track the log-in and log-out inside sys.log. 

Thanks

---

### Post by DuckHook on 2018-01-20
> **wrongusername2 said:**
> …I am not able to track the log-in and log-out inside sys.log…
Actually you can, but indirectly. *syslog* is timestamped. The first three fields are date and time to seconds. 

We know that the syslog service can't start recording until it is started, and it can no longer record after it is stopped. Fortunately, syslog does record when it starts and when it stops. On my system, that delineation point looks like this:```
Jan 19 11:46:42 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2764" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan 19 17:07:48 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2885" x-info="http://www.rsyslog.com"] start
```The system would have shut down shortly after 11:46:42. The next session started shortly before 17:07:48. The problem with syslog is that it is so data-dense that it's hard finding this delineation point within the data deluge. The trick is to identify a unique string, then grep for it:```
grep "origin software=" /var/log/syslog
```My results from 2 days ago:```
duckhook@Zeus:~$  zgrep "origin software=" /var/log/syslog.2.gz
Jan 17 10:35:56 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2781" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan 17 11:56:34 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2687" x-info="http://www.rsyslog.com"] start
Jan 17 14:13:29 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2687" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan 17 14:13:58 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2875" x-info="http://www.rsyslog.com"] start
Jan 17 16:03:09 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2875" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan 17 18:18:10 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2900" x-info="http://www.rsyslog.com"] start
Jan 17 22:24:11 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2900" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan 18 14:06:07 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2920" x-info="http://www.rsyslog.com"] start
Jan 18 14:11:08 Zeus rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="2920" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
```Note that I had to use zgrep because my logs had already been rotated out and gzipped.

You can now go through your logs knowing exactly what your reboot timestamps are.

---

### Post by wrongusername2 on 2018-01-20
> **DuckHook said:**
> Actually you can, but indirectly. *syslog* is timestamped..

Thanks DuckHook, that works well. I used it to go through recent most log-in session.

---

### Post by DuckHook on 2018-01-20
It is worth adding that you should be commended for having the patience and motivation to go through your logs. Few users do this; yet it is one of the most important things that we as users can do. It doesn't have to be done all the time, but a habit of doing so monthly or even just a few times a year would go a long way towards running healthier systems.

Good Luck and Happy Ubuntu-ing!

---

