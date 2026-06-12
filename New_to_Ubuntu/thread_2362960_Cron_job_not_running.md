---
title: "Cron job not running"
date: 2017-06-04
forum: New to Ubuntu
---

### Post by sniper8752 on 2017-06-04
I have the following in root's crontab:

```
22 04 * * * /usr/local/bin/pulledpork.pl -c /etc/snort/pulledpork.conf -l
```

I don't see this running in the syslog log file.  How do I get this to run?

---

### Post by TheFu on 2017-06-05
Most of the time when a cron script fails it is due to missing or incorrect environment variables.  Cron doesn't provide the same full environment that a login session has.  For example, HOME is not set, but there are lots of other differences.  

If you can open a terminal and run:
```
/usr/local/bin/pulledpork.pl -c /etc/snort/pulledpork.conf -l
```
directly, then it is always a missing/incorrect environment variable(s).  You can compare the crontab environment and your personal login environment by having a script dump the output of **env** to a file during a cron run.  You will see many, many, difference.

---

### Post by christianc123 on 2017-06-16
Add a >>/tmp/testlog.log to the end of your crontab entry to redirect  output to a file you can investigate or check if it's running,  additionally a 2>&1 would include output from the error console

Regards,
Christian
[http://cloudappsportal.com/](http://cloudappsportal.com/)

---

