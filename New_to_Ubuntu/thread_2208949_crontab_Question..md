---
title: "crontab Question."
date: 2014-03-03
forum: New to Ubuntu
---

### Post by freerole83 on 2014-03-03
HI.
To stop auto-run crontab, what should I do? 
Stop state when the reboot.
thank.
ubuntu v.12.04

---

### Post by IvoGuerreiro on 2014-03-03
Hi, 
Have you tried this (But do do the opposite):
[http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login).

---

### Post by Dave_L on 2014-03-03
> **freerole83 said:**
> HI.
To stop auto-run crontab, what should I do? 
Stop state when the reboot.
thank.
ubuntu v.12.04

The crontabs are handled by the "cron" service, which can be controlled with the "service" command:
[http://manpages.ubuntu.com/manpages/precise/en/man8/service.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/service.8.html)

There are different crontabs: user crontabs, system crontabs.

Is there a specific task, or tasks, that you do not want to run?

---

