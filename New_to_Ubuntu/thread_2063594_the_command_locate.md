---
title: "the command locate"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by EkiLibRiuM on 2012-09-27
. The operating system can be configured to do this automatically with a cron  job. For example on my Ubuntu 12.04 I’ve this job scheduled with the file  /etc/cron.daily/mlocate  which is responsible for updating the database once a day...i try to update the db whit command " lmlocate" but i get this error:

/etc/cron.daily/mlocate
touch: cannot touch `/var/lib/mlocate/daily.lock': Permission denied
if somebody can help me.....thank you for understanding...best regadrs.

---

### Post by Lars Noodén on 2012-09-27
You can update the locate and mlocate database with [updatedb](http://manpages.ubuntu.com/manpages/precise/en/man8/updatedb.8.html)

```

sudo updatedb

```

---

