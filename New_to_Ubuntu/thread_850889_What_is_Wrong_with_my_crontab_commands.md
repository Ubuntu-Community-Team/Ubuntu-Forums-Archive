---
title: "What is Wrong with my crontab commands?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by legolas_w on 2008-07-06
Hi
Thank you for reading my post
Can some one please let me know what is the problem that my computer does not shutdown in the given time? I tried to use cron jobs to schedule a shutdown but it looks like that it does not works.

when i execute ```
crontab -l
``` i see the following:


```


00 07 * * * /sbin/shutdown -P now

```

I think this command tells the cron job to shutdown the computer at 7 AM?

What is wrong with the command?


thanks

---

### Post by sdennie on 2008-07-06
If you are running "crontab -l" from your user directory, it means that you've set a cron job for that user.  The only user that has permission to shutdown the machine is root so, your command is essentially ignored if it's coming from your user crontab.  Try adding your command using:

```

sudo crontab -e

```

---

