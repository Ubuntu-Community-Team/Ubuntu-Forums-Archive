---
title: "crontab scheduled jobs not working"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by dynamethod on 2008-06-03
sudo crontab -l:

```
# m h  dom mon dow   command
0 0 * * * aptitude -y update && aptitude -y upgrade

```

though it never happens, i currently have 26 updates available, but the cron job wont take place, am i doing something wrong here?

---

### Post by barnex on 2008-06-03
try supplying the full path to the binary: ```
/usr/bin/aptitude
```. I believe cron uses sh instead of bash, which may not have its $PATH set the same way as bash.
Hope this helps.

---

