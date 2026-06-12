---
title: "How to run a command at a specific time?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by HyperHacker on 2008-06-11
I know this is possible with some command like crontab or something ('at' in Windows) but I have no idea how to use it. :confused:

---

### Post by abhiroopb on 2008-06-11
I suggest searching for the GUI program: gnome-schedule in synaptic and installing it. It is basically a GUI for cron. Its really easy to use.

---

### Post by ad_267 on 2008-06-11
If you are interested in using cron from the command line, read this: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by anthropoidster on 2008-06-11
Ok, installed gnome-schedule but still a little lost.
Could this be used to shut off Rhythmbox at, say 11PM, and then shut down the system completely?
That would sure make life a little easier.
 What would the commands be for something like that?

---

### Post by forger on 2008-06-11
open up gnome terminal and do:
```
gksu gedit /etc/crontab
```
in a new line add the code
```
  00 23 * * * /etc/rhythmanddown
```
"Every day of the month, every month, every day of the week, at 23:00 (11pm), run the script /etc/rhythmanddown"

now create the /etc/rhythmanddown script:
```
gksu gedit /etc/rhythmanddown
```

type in:
```

#!/bin/bash
rhythmbox -q
killall rhythmbox
shutdown -P now
```

now make it executable:
```
sudo chmod +x /etc/rhythmanddown
```

---

### Post by gustabuntu on 2008-06-11
Hi

If you want to shutdown the system, why don't you use shutdown command? You can specify the time. And the new version of Rythmbox actually saves the PlayQueue when quitting, I just figure it out.

You also have the command sleep, that you can run just before something else in a script.

There is also another command called 'at'.

I am still new, but I found the manuals for any command quite good (in the console type for instance: man at) (or man COMMAND_NAME).

G

---

### Post by kpkeerthi on 2008-06-11
GUI applications need some "special handling" while cronning. See..

[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)
[http://ubuntuforums.org/showthread.php?t=105250](http://ubuntuforums.org/showthread.php?t=105250)

---

### Post by ad_267 on 2008-06-11
Edit: Ignore, hadn't read post properly.

---

### Post by KingTermite on 2008-06-11
> **gustabuntu said:**
> Hi

If you want to shutdown the system, why don't you use shutdown command? You can specify the time. And the new version of Rythmbox actually saves the PlayQueue when quitting, I just figure it out.

You also have the command sleep, that you can run just before something else in a script.

There is also another command called 'at'.

I am still new, but I found the manuals for any command quite good (in the console type for instance: man at) (or man COMMAND_NAME).

G

Correct. I just put together a script mostly copied from a book ("Linux Desktop Hacks") and it uses the "at" command to help you set up reminders to pop up on the screen.

do a "man" or "info" on "at" and see how easy it is to use. Something "at 2:45pm <command>" I believe.

---

### Post by HyperHacker on 2008-06-12
I tried using 'at' and it seems to want me to enter commands into stdin (passing them on the command line doesn't work), but nothing happens when I do (have to Ctrl+C), so I don't know if it's accepted them or not. Same with editing /etc/crontab, I can't tell if it's going to actually work. gnome-schedule is easy enough, we'll see if it works tomorrow... I just hope I don't end up with like 6 instances of the same thing running. <_<

Is there a way to have 'at' list all the scheduled tasks so I can tell whether it accepted them?

---

### Post by forger on 2008-06-12
> **HyperHacker said:**
> Same with editing /etc/crontab, I can't tell if it's going to actually work.
i forgot to mention to reload the crontab configuration:
```
sudo /etc/init.d/cron reload
```


open up a terminal and execute: ```
/etc/rhythmanddown
```
If it shuts down, you did it :)
You could set the time for a minute or two afterwards, say the time is now 11:15 am, you put in /etc/crontab:
```
  18 11 * * * /etc/rhythmanddown
```

save it, and reload the cron:
```
sudo /etc/init.d/cron reload
```

---

### Post by HyperHacker on 2008-06-12
OK, well I used gnome-schedule to start gmplayer, and it started but the window never appeared. :confused: I could hear it playing in the background (much quieter than normal) but not see it.

---

### Post by forger on 2008-06-12
uh... the plan was to run the shutdown test, not start gmplayer, i've no idea what gmplayer is anyway :)

you could always use mplayer instead of gmplayer

---

### Post by HyperHacker on 2008-06-12
That was anthropoidster who wanted to shut down, not me. gmplayer is just mplayer in GUI mode.

---

### Post by dddw on 2010-05-01
great post forger! I´ve tried this on numerous attempts, but only now succeeded thanks to you!

---

### Post by mm7977 on 2010-05-01
see also...


[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)
[http://ubuntuforums.org/showthread.php?t=105250](http://ubuntuforums.org/showthread.php?t=105250)

---

