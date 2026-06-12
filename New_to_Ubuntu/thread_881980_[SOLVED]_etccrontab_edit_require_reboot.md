---
title: "[SOLVED] /etc/crontab edit require reboot?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Sydius on 2008-08-06
This is actually on a CentOS server, but I figure the concept is probably the same.

If I change /etc/crontab, do I need to reboot the machine? Is there a way to avoid rebooting? It's on a server that has to stay up.

Also, is there another way to add a cron schedule, or than dropping items in /etc/cron.daily? I made a symbolic link to the script I wanted to be executed in /etc/cron.daily.  Is this the normal way to schedule something?

---

### Post by pytheas22 on 2008-08-06
You shouldn't need to reboot the machine.
> 
Also, is there another way to add a cron schedule, or than dropping items in /etc/cron.daily? I made a symbolic link to the script I wanted to be executed in /etc/cron.daily. Is this the normal way to schedule something?

I always add cronjobs by opening up /etc/crontab directly in a text editor and adding in the line to call whichever script I need, e.g. something like:
```

00 01 * * * 'sh /home/me/myscript.sh'
```

I don't know if this is the "proper" way to do it, but it's always worked fine for me, and I've never needed to restart the machine in order for the job to be run.

---

