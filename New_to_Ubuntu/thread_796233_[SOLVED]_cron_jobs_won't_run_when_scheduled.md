---
title: "[SOLVED] cron jobs won't run when scheduled"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by philphil on 2008-05-16
I have some simple Cron jobs in Hardy Heron and they won't run.  I'm using gnome-schedule to create though having tried KCron and also doing it manually from a terminal and no way is working.

I can run the tasks manually, no problem but when I try to schedule them nothing happens.  

I've done:
```

/etc/init.d/cron start

```

so I know that's running.  

The output of 'crontab -l' is this:
```

phil@phil-laptop:~$ crontab -l
40 13 * * * /usr/bin/azureus >/dev/null 2>&1

```

I've read some stuff about having to add '#! /bin/bash;' before the application path which makes the line above read: 
```

phil@phil-laptop:~$ crontab -l
40 13 * * * #! /bin/bash;/usr/bin/azureus >/dev/null 2>&1

```

but that doesn't work.

I've also read some stuff about adding 'Display=:0.0' to make the line read:
```

phil@phil-laptop:~$ crontab -l
40 13 * * * Display=:0.0/usr/bin/azureus >/dev/null 2>&1

```

but that didn't work.

Weirdly, sometimes, if I'm running 'top' from a terminal at the same time as the task is scheduled I can see 'java' come up in the list of processes (which is the name of Azureus for some reason) but it disappears almost immediately and never comes back.  Azureus is never displayed and no terminal window ever appears.

I've tried checking various logs for the output of cron errors but I can't find anything.  Apparently cron outputs its messages to /var/log/syslog.0 or /var/log/syslog but the last thing in those logs is from April 26 which is the same day I upgraded to Hardy Heron.  (Looks like I might have two separate problems.)

So:  I can run the task manually from Gnome-scheduler or Kcron but the task does not run when I have scheduled it to be run.  

Any ideas?

---

### Post by kpkeerthi on 2008-05-16
Change it to...
```
40 13 * * * **export DISPLAY=:0 && /usr/bin/azureus** > /dev/null 2>&1
```

More info here...
[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)

---

### Post by philphil on 2008-05-16
wow thanks and I really thought that might fix it, but I'm still having the same problem. At least I have a new direction to look in though: running GUI apps with Cron.

I just ran a scheduled task that ran 'mkdir blob' and it worked so I know the daemon is actually working, it's def just to do with the display thing

Edit: just to clarify, I can run 'export DISPLAY=:0 && /usr/bin/azureus' fine from the command prompt and also from gnome-schedule just not when scheduling

---

### Post by drs305 on 2008-05-16
I just installed azureus, put the following line in my crontab, and it opened fine. It ran at 0950, opening up the azureus gui. Does yours not even open the azureus program, or is it not doing something once it is opened?

```
50 09 * * * export DISPLAY=:0 && /usr/bin/azureus > /dev/null 2>&1
```

---

### Post by philphil on 2008-05-16
Thanks for helping out, nothing at all happens when the time comes around

---

### Post by drs305 on 2008-05-16
If you've changed it in any way, would you post the contents of your crontab as you did earlier?
```
crontab -l
```

---

### Post by philphil on 2008-05-16
```

phil@phil-laptop:~$ crontab -l
59 * * * * export DISPLAY=:0.0 && /usr/bin/azureus >/dev/null 2>&1 #JOB_ID_10


```
There is an empty line break there, I'll try taking it out...

and I just added a task for the root user: 
```

phil@phil-laptop:~$ sudo crontab -l
0 * * * * export DISPLAY=:0.0 /usr/bin/azureus >/dev/null 2>&1

```

---

### Post by philphil on 2008-05-16
Nope.  Neither removing the linebreak nor adding the task to the root's crontab list solved it

---

### Post by philphil on 2008-05-16
just to be certain:

```

phil@phil-laptop:~$ echo $DISPLAY
:0.0

```

---

### Post by drs305 on 2008-05-16
Put this at the top of your crontab file:

```
SHELL=/bin/bash
```

That will probably fix it. Have you run any other cron jobs successfully?

---

### Post by philphil on 2008-05-16
just corrected the root's task to include '&&' but that didn't solve it

sudo crontab -l
7 * * * * export DISPLAY=:0.0 && /usr/bin/azureus >/dev/null 2>&1

---

### Post by philphil on 2008-05-16
yeah a silly 'mkdir blob' just to check everything was working and that ran successfully.

trying your fix now

---

### Post by philphil on 2008-05-16
nope, sorry that didn't fix it

---

### Post by philphil on 2008-05-16
is there a way of printing out any errors that might occuring to a log file or something?

```

phil@phil-laptop:~$ crontab -l
SHELL=/bin/bash
15 * * * * export DISPLAY=:0.0 && /usr/bin/azureus >/dev/null 2>&1 

```

---

### Post by drs305 on 2008-05-16
Here is my entire working crontab. It runs fine with either DISPLAY:0 or DISPLAY:0.0
Hopefully someone will be able to figure out why your crontab doesn't run. 

```
SHELL=/bin/bash
HOME=/home/username
MAILTO=username

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/username/.scripts

22 10 * * * export DISPLAY=:0 && /usr/bin/azureus  >  /dev/null 2>&1

```

---

### Post by philphil on 2008-05-16
ok thanks, I copied, pasted and merged that but still nothing.  Thanks anyway for your time, it's appreciated.

To anyone else who can help me, my crontab now looks like this:
```

phil@phil-laptop:~$ crontab -l
SHELL=/bin/bash
HOME=/home/phil
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
27 * * * * export DISPLAY=:0 && /usr/bin/azureus  >  /dev/null 2>&1

```

The process azureus starts (I see it in the list of running processes) but it only stays there for a few seconds and then disappears (because it can't find a display to latch on to???) and after that nothing else happens.

---

### Post by philphil on 2008-05-16
bump?

---

### Post by philphil on 2008-05-16
yeah, fixed it, thanks to a combination of previous poster, a reboot and this guy here: 

[http://godsongera.blogspot.com/2007/09/running-x-windows-gui-applications-with.html](http://godsongera.blogspot.com/2007/09/running-x-windows-gui-applications-with.html)

who found the answer here: 

[http://ubuntuforums.org/archive/index.php/t-105250.html](http://ubuntuforums.org/archive/index.php/t-105250.html)

---

