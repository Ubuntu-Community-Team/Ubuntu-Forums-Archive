---
title: "log file location?"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by goodbye-windows(tm) on 2012-07-18
Where is the log file that shows the history of all the software installs?

TY.

Art

---

### Post by oldos2er on 2012-07-18
/var/log/apt/history.log*

---

### Post by richpri on 2012-07-18
You can find a lot of different log files in the /var/log directory.

To see all available log files [but not compressed archives] use:

```
ls --ignore=*.gz /var/log
```

---

