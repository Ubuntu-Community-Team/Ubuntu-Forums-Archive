---
title: "cron job understanding"
date: 2012-08-15
forum: Programming Talk
---

### Post by BrianBlaze on 2012-08-15
I need to understand coding better... I have a cron job that is using vnstat... I am curious what is going on, I hope someone can help...

```

if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi

```

Thank you

---

### Post by BrianBlaze on 2012-08-15
If "/usr/bin/vnstat" exists and is executable, and the number of files in "/var/lib/vnstat/" is equal to or greater than one, then run the program "/usr/bin/vnstat" with the update flag...

I love answering my own questions lol

---

