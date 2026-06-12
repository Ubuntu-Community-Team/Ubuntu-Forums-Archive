---
title: "Linux sleeptimer"
date: 2005-11-06
forum: Programming Talk
---

### Post by otey on 2005-11-06
Is it possible to make a linux sleeptimer..

Or has somebody already made one?

---

### Post by wmcbrine on 2005-11-06
Could you elaborate on what you mean?

There are a number of Linux commands related to sleep and timing: "sleep", "at", "time", etc.

---

### Post by otey on 2005-11-07
A program to shutdown the computer at configureable times. 

fx. set to shut down computer 01.00

---

### Post by Susana on 2005-11-07
[QUOTE=otey]A program to shutdown the computer at configureable times. 

fx. set to shut down computer 01.00[/QUOTE]

why don't you use cron? 
[http://www.clickmojo.com/code/cron-tutorial.html](http://www.clickmojo.com/code/cron-tutorial.html)

---

### Post by otey on 2005-11-08
I've tried to run cron. can't seem to get it working though. 

What should i do to get it working?

When i type cron, it prints:

```
cron: can't open or create /var/run/crond.pid: Permission denied

```

When i type sudo cron, it prints:

```
cron: can't lock /var/run/crond.pid, otherpid may be 7608: Resource temporarily unavailable

```

As far as I know some options (like fx: 30 3 * * * user poweroff) should be written in a crontab, but when i type crontab -e and then tries to save the file. i do not have permission. Besides.. the editor thinks the file belongs in my temp folder, though it is surposed to be stored in /var/spool/cron/ something. 

So i gues my question is... What do i do now?

---

### Post by sjpwong on 2005-11-09
[QUOTE=otey]When i type cron, it prints:

```
cron: can't open or create /var/run/crond.pid: Permission denied

```

When i type sudo cron, it prints:

```
cron: can't lock /var/run/crond.pid, otherpid may be 7608: Resource temporarily unavailable

```
[/quote]
You do not want to run cron directly it is a daemon (service) that runs in the background.

You need to edit the cron table using "crontab -e" or for a system wide cron job "sudo crontab -e".

[QUOTE=otey]As far as I know some options (like fx: 30 3 * * * user poweroff) should be written in a crontab, but when i type crontab -e and then tries to save the file. i do not have permission. Besides.. the editor thinks the file belongs in my temp folder, though it is surposed to be stored in /var/spool/cron/ something. 

So i gues my question is... What do i do now?[/QUOTE]

There is no user to go in there, the *whole* table is for a specific user.

And yes, you want to save it to the tmp location as crontab parses the file *after* you finish editing it.

It will tell you if you have any errors.

Beware of problems with your PATH so I recommend using the full path/name for an app eg /usr/sbin/shutdown.

Hope that helps :-)

---

### Post by LordHunter317 on 2005-11-10
For system wide cron, you don't run a command at all, you just edit /etc/crontab as root.

---

### Post by sjpwong on 2005-11-10
[QUOTE=LordHunter317]For system wide cron, you don't run a command at all, you just edit /etc/crontab as root.[/QUOTE]

Oops!  I really meant if you want it to run as root use sudo.

---

