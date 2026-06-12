---
title: "Need help to make Restart script!"
date: 2010-09-20
forum: Programming Talk
---

### Post by Joacom on 2010-09-20
Hello Good Fellows! 

I Wonder if anyone has a Script i can use for restart the ubuntu machine every 20 Day.

Thanks in advance!

Joacom

---

### Post by r-senior on 2010-09-20
You should be able to make a crontab entry for shutdown, so something along these lines:

$ sudo vi /etc/crontab 

(use whatever editor you prefer but must be sudo/gksudo)

then add an [appropriate crontab](http://www.unixgeeks.org/security/newbie/unix/cron-1.html) line, e.g.

```
0 4 1 * * root shutdown -r +10
```

This should perform a reboot at 4am on the first day of every month with a 10 minute grace period for anyone who is logged into the machine to save work or abort the reboot.

Making this happen every 20 days is left as an [exercise for the reader](http://www.unix.com/shell-programming-scripting/117137-scheduling-command-run-every-3-days-through-cron.html) (who may decide that life's too short and settle for monthly instead ;))

For more information:

$ man shutdown
$ man 5 crontab

---

