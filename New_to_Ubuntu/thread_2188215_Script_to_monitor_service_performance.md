---
title: "Script to monitor service performance?"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by termvrl on 2013-11-16
Hi All,

I want to ask, how we can monitor services performance, for e.g, apache cpu & nic usage, using script.
I want to use this script with syslog server, if the apache cpu & nic usage is high, so, stop the syslog services because it will generate haevy logs.

Thnaks in advanced.

---

### Post by tgalati4 on 2013-11-16
Turning off system logs due to high CPU load is contradictory, because you need the logs when something breaks, otherwise troubleshooting is nearly impossible.

Perhaps describe in more detail what you are trying to accomplish.  If you want to add entries to your syslog based on performance criteria look at:

```
man logger
```

---

### Post by Habitual on 2013-11-16
[http://collectl.sourceforge.net/](http://collectl.sourceforge.net/)

---

