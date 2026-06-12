---
title: "Hourly cron"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-05-29
I was just wondering if this is supposed to return my desired effect from a cron:

```
00 * * * * /home/<username>/somecommand
```

For this running this command every hour on the hour?

---

### Post by quelx on 2008-05-29
Yep, however you only need one 0 (I don't know if two will matter, but one definitly works)

```
0 * * * * /home/<username>/somecommand
```

use **crontab -e** to put it in your schedule

If you don't want to receive email every time it runs put **2>&1** after the line

---

