---
title: "When cron.daily starts whole system goes unresponsive and Firefox greys out."
date: 2008-09-07
forum: New to Ubuntu
---

### Post by philinux on 2008-09-07
Always happens 5 minutes after logon as anacrontab shows. Why does this slug the pc?

```
# /etc/anacrontab: configuration file for anacron
# See anacron(8) and anacrontab(5) for details.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# These replace cron's entries
1    5    cron.daily     nice run-parts --report /etc/cron.daily
7    10    cron.weekly     nice run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly nice run-parts --report /etc/cron.monthly

```

syslog
```
Sep  7 20:37:17 philcb-desktop anacron[5537]: Job `cron.daily' started
Sep  7 20:37:17 philcb-desktop anacron[6092]: Updated timestamp for job `cron.daily' to 2008-09-07
Sep  7 20:39:01 philcb-desktop /USR/SBIN/CRON[6124]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
```

---

### Post by philinux on 2008-09-08
Ok where are the experts hanging out. :lolflag:

---

### Post by Thingymebob on 2008-09-08
Really need to know what scripts are in your /etc/cron.daily folder but I would imagine its apt updating the package lists, you can do one of two things here.

change the line in /etc/apt/apt.conf.d/10periodic that reads
```

APT::Periodic::Update-Package-Lists "1";

```

to
```

APT::Periodic::Update-Package-Lists "0";

```

This effectively turns off automatic updates

a better solution would be to move the apt script from /etc/cron.daily to another period, e.g. /etc/cron.weekly or /etc/cron.monthly which would make your system check for updates at these intervals rather than daily.

---

### Post by philinux on 2008-09-08
Default I guess, I've not added anything as I've not dabbled in this.

---

