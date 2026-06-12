---
title: "Can Ubuntu send a report whenever a process stops (pref. on email)?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by telekarlsen on 2008-08-05
I would like to be informed whenever a process on my server (8.04) stops.
Can this be done?
- Can Ubuntu generate a report and notify me by email with details like when, why and such?

And is there a log I can look at locally at the server for general faultfinding?

---

### Post by hyper_ch on 2008-08-05
depending on the process it has already mail notification included...
or you could make a cron that checks every now and then if a process is still running and if not, have it send you an email.

as for logs: /var/log

---

### Post by tusharhiwse on 2008-08-05
you can find the log in system=>administration=>system log or in terminal
by using command #top
&
you also find the processes in system=>administration=>system monitor=>processes

---

### Post by kirsis on 2008-08-05
For daemons you prolly need to set up a cron job that routinely checks the processes and sends reports.

However, if you start a non-daemon from terminal, then you could just pair two commands, for example:

```

some_app && echo "some app closed"

```

Only instead of echoing, you'd be emailing a report.

---

