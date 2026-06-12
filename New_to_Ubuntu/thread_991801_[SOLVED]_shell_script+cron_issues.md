---
title: "[SOLVED] shell script+cron issues"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-11-24
I have a script that works perfectly when launched from the terminal, but won't work if launched by cron.

The script basically grabs entries from a sqlite database, compare a value with the current time and, if they match, starts recording from the TV card.

The script is running when launched by cron, but it isn't executed properly. Here is the code:

```
[COLOR="Blue"]#!/bin/bash

DATE=$( date +%Y-%m-%d )
TIME=$( date +%H:%M )
sqlite3 ~/videoteca/catalog/tvshows.sqlite "update record set status='ON' where start='${DATE} ${TIME}' and status='SCHEDULED'"
STATUS=$(sqlite3 ~/videoteca/catalog/tvshows.sqlite "select [status] from record where start='${DATE} ${TIME}'")
RUNTIME=$(sqlite3 ~/videoteca/catalog/tvshows.sqlite "select [runtime] from record where start='${DATE} ${TIME}'")
SCHEDULE=$(sqlite3 ~/videoteca/catalog/tvshows.sqlite "select [rowid] from record where start='${DATE} ${TIME}'")

if [ "$STATUS" = "ON" ] ; then
killall zenity
killtvtime
killall transcode[/COLOR]
[COLOR="Red"]transcode -x v4l2,v4l2 \
        -g 640x480 \
        -i /dev/video0 \
        -p /dev/dsp1 \
        -e 32000,16,2 \
        -N 0x1 \
	-J resample,levels,smartyuv \
        -w 4000 \
        -y ffmpeg \
        -F mjpeg \
	-c ${RUNTIME} \
	-o ~/virtual/pvr/${DATE}-${TIME}.avi & zenity --text "Recording started at ${TIME} with ${RUNTIME} preset time" --notification[/COLOR]

[COLOR="Blue"]killall zenity
killall transcode 
sqlite3 ~/videoteca/catalog/tvshows.sqlite "update record set status='RECORDED' where rowid='${SCHEDULE}'"

else
  echo "Doing nothing"
fi
```[/COLOR]

The lines in blue are those successfully being executed, while the ones in red are not, which are exactly the part responsible for capturing the video from the TV card and saving it to the home directory.

I have searched the web a lot and there are tons of people with the same issues, but none of the solutions worked for me. Any ideas how I can fix this?

Is there any viable alternative to scheduling this script without cron?

---

### Post by ajgreeny on 2008-11-24
As I understand things when bash is run through cron there is a reduction in the bash capabilities, or something like that.  I can't remember where I read that comment, but it did apparently make some difference to what was possible using script files with cron; simple scripts were no problem, more complex scripts were a problem.

I'm afraid it will require someone with more knowledge than me to give you any more information on this, but I hope this is a start in your search, and also that I am not giving you a bum steer, with things having moved on and this comment being now untrue.

Good luck; I hope you get it sorted.

---

### Post by Trail on 2008-11-24
ajgreeny is probably to the bash script running in non-interactive mode.

If only the part in red is not getting executed, are you sure the $PATH is correct? Maybe try to hardcode it like "/usr/bin/transcode" instead and see if it makes any difference. Are there any errors generated? Also make sure that this is getting executed as the correct user?

Last resort, since i'm out of other ideas, is to set the bash debugging mode on. Though, I don't remember atm how exactly to do it.

---

### Post by lovinglinux on 2008-11-24
> **ajgreeny said:**
> As I understand things when bash is run through cron there is a reduction in the bash capabilities, or something like that.  I can't remember where I read that comment, but it did apparently make some difference to what was possible using script files with cron; simple scripts were no problem, more complex scripts were a problem.

I'm afraid it will require someone with more knowledge than me to give you any more information on this, but I hope this is a start in your search, and also that I am not giving you a bum steer, with things having moved on and this comment being now untrue.

Good luck; I hope you get it sorted.

Thank you. It would be nice if someone could confirm the capability reduction, then I would move on to alternatives instead of trying to fix it.

I tried to schedule this script with alarm-clock. Despite the fact that it runs nicely, alarm-clock only have options to repeat the schedule daily and monthly. Do you know any application that could also repeat the schedules every 15 minutes or so?

---

### Post by fwre01 on 2008-11-24
When i was using cron i had to use absolute path names on everything that was being called in the script

...and i mean EVERYTHING. But it did work in the end :-). I dont think cron has any environment variables.

---

### Post by lovinglinux on 2008-11-24
I tried hardcoding the paths as suggested, but it doesn't work either.

Then I tried these simple scripts:

```
#!/bin/bash

tvtime
```

```
#!/bin/bash

/usr/bin/tvtime
```

```
#!/bin/bash

firefox
```

```
#!/bin/bash

/usr/bin/firefox
```

None of them work. Anyway, I guess is not a path problem, because the sqlite3 commands are executed properly and sqlite3 does not have a hardcoded path.

---

### Post by unutbu on 2008-11-24
Neat script, lovinglinux! The script might not be working when run by cron because the DISPLAY variable has not been set.

[list]
[*]You can make your cron environment feel more like home (pun intended!) by adding 
the following lines to the top of your personal crontab (the one you access with "crontab -e").
```

USER=lovinglinux
HOME=/home/lovinglinux
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/lovinglinux/bin
DISPLAY=:0.0
MAILTO=lovinglinux
```

Defining the HOME variable allows you to use tildes (~) in your paths.
fwre01's suggestion of using absolute paths addresses the same problem in a different way.
[*]Consider removing the calls to zenity, at least at first. Scripts that employ graphics are certainly possible, but they depend on more things being setup right. (You need the DISPLAY variable set, and you need to own your ~/.Xauthority, for example.) As a text-based alternative, you could add log entries to /var/log/syslog this way:

logger -t 'TV' "Recording started at ${TIME} with ${RUNTIME} preset time" 

In any case, try to get the simplest script to succeed first, then build it up incrementally.
[*]A minor point: in your big transcode line, you use 
```

transcode ... & zenity ...
```
This means run transcode in the background, and run zenity even before transcode finishes.
If you want the zenity command to only run if the transcode completes without errors, then you want to use the bit-and operator &&:

```

transcode ... && zenity ...
```
[/list]

---

### Post by lovinglinux on 2008-11-24
> **unutbu said:**
> Neat script, lovinglinux! The script might not be working when run by cron because the DISPLAY variable has not been set.

[list]
[*]You can make your cron environment feel more like home (pun intended!) by adding 
the following lines to the top of your personal crontab (the one you access with "crontab -e").
```

USER=lovinglinux
HOME=/home/lovinglinux
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/lovinglinux/bin
DISPLAY=:0.0
MAILTO=lovinglinux
```

Defining the HOME variable allows you to use tildes (~) in your paths.
fwre01's suggestion of using absolute paths addresses the same problem in a different way.
[*]Consider removing the calls to zenity, at least at first. Scripts that employ graphics are certainly possible, but they depend on more things being setup right. (You need the DISPLAY variable set, and you need to own your ~/.Xauthority, for example.) As a text-based alternative, you could add log entries to /var/log/syslog this way:

logger -t 'TV' "Recording started at ${TIME} with ${RUNTIME} preset time" 

In any case, try to get the simplest script to succeed first, then build it up incrementally.
[/list]

THANK YOU!  

It works now after adding those variables to crontab and also adding ">/dev/null 2>&1" to the cron job.

> **unutbu said:**
> 
A minor point: in your big transcode line, you use 
```

transcode ... & zenity ...
```
This means run transcode in the background, and run zenity even before transcode finishes.
If you want the zenity command to only run if the transcode completes without errors, then you want to use the bit-and operator &&:

```

transcode ... && zenity ...
```


That is intentional. If I use the bit-and operator, then zenity alert will be launched only when the recording is finished. The intention is not to alert that the recording finished, but to alert that the recording has started. So, sending transcode to the background also allows to click the zenity alert icon to interrupt the recording manually.

---

