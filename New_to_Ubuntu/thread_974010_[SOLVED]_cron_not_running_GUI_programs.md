---
title: "[SOLVED] cron not running GUI programs"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by lemuriens on 2008-11-07
Hello all,

I've been trying to set vlc to run every morning to use as an alarm clock. However, setting a cron task to run vlc (or any other GUI programs, for that matter) doesn't appear to work. After reading these forum threads:
[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)
[http://ubuntuforums.org/showthread.php?t=752498](http://ubuntuforums.org/showthread.php?t=752498)
I found that running "sudo crontab -e" would allow me to enter a new task into cron, and that any GUI programs had to be prefaced by "export DISPLAY=:0 && ". I created a script to run as follows:
```
#! /bin/bash
/usr/bin/vlc 
"mms://wmlive-acl.bbc.co.uk/wms/radio4/radio4_nb_e1s2?BBC-UID=74a7c929ba1d1db781e46027205005eb90d10a7f1040912444dfe8117ceae58f_n&amp;SSO2-UID="
```
and have put it in my /usr/bin directory to ensure it was in my PATH. A crontab entry of 
```
* * * * * export DISPLAY=:0 && /usr/bin/alarmclock.sh
```
does not work. Someone mentioned sending the output to /dev/null, and I tried this too:
```
* * * * * export DISPLAY=:0 && /usr/bin/alarmclock.sh 1> /dev/null 2> /dev/null
```
with no luck. To prove that cron was working, I put into crontab
```
* * * * * /usr/bin/uptime > /var/tmp/uptime.log
```
and uptime.log contained the output of the uptime command. Similarly, creating a script of the above uptime test and putting that into crontab as
```
* * * * * /usr/bin/uptimetest.sh
```
works as expected.

I've also tried just
```
* * * * * export DISPLAY=:0 && /usr/bin/vlc
```
and about every possible permutation - with or without full path, without "&&", without "export", "DISPLAY=:0 /usr/bin/vlc" - that I can think of, and I've tested it with other GUI programs (audacious, firefox, xterm) and none seem to work.

Normally I end up figuring things out by reading these forums and a little trial and improvement, but I've tried everything I can think of here! 
Does anyone know what I can do to get this working?

---

### Post by sisco311 on 2008-11-07
try to set the DISPLAY variable in your script:
> #! /bin/bash
DISPLAY=:0 /usr/bin/vlc 
"mms://wmlive-acl.bbc.co.uk/wms/radio4/radio4_nb_e1s2?BBC-UID=74a7c929ba1d1db781e46027205005eb90d10a7f1040912444dfe8117ceae58f_n&amp;SSO2-UID="
and run crontab as your user(not as root):
```
crontab -e
```

> * * * * * /path/to/script.sh

---

### Post by lemuriens on 2008-11-07
That's got it working - vlc has just popped up, and it's playing Radio 4!

Many thanks!

---

### Post by talktwomey on 2009-01-23
just to add to this:

I was pulling my hair out having tried all of the above commands without success. 

I then realised that I'd done all of the above sudo's as root. if you create a crontab as root, the DISPLAY option won't work if root isn't allowed access the x server. make sure you do everything as the same user / the user allowed use the x server.

---

