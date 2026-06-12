---
title: "a cron question"
date: 2006-12-21
forum: Programming Talk
---

### Post by zetsumei on 2006-12-21
Okay, I wanted to setup a cron script to play a music file from my home dir's Music folder at a certain time everyday (I wanna use my computer as an alarm clock) how would I go about setting up the cron script, pretty much how would I set all of this up to work correctly?

---

### Post by ansi on 2006-12-21
> **zetsumei said:**
> Okay, I wanted to setup a cron script to play a music file from my home dir's Music folder at a certain time everyday (I wanna use my computer as an alarm clock) how would I go about setting up the cron script, pretty much how would I set all of this up to work correctly?

```
man 5 crontab
```

As player you can use **mpg123**. E.g.:
```
/usr/bin/mpg123 ~/music/alarm.mp3
```

If you would like random song every day, you can use:
```
/usr/bin/mpg123 --list ~/music/alarm_playlist.lst --shuffle
```
Where **alarm_playlist.lst** is an ordinary text file with filenames on each line.


[COLOR="Silver"]P.S. IMHO, you question is far from the programming.[/COLOR]

---

### Post by 23meg on 2006-12-21
Type ```
crontab -e
``` and enter the command you want executed and specify the time. You can learn about the crontab format [here]("https://help.ubuntu.com/community/CronHowto"), or just create the line using [this]("http://www.clockwatchers.com/cron_tool.html").

---

### Post by munkar on 2006-12-28
i'm trying to do the exact same thing, but i can't seem to get the thing to work....my cron doesn't seem to run anything at all, not even echo "hello". ](*,)

this is what my file looks like:

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

15 19 * * * /usr/bin/mpg123 ~/Desktop/alarm.mp3

```

---

### Post by Ragazzo on 2006-12-29
> **munkar said:**
> i'm trying to do the exact same thing, but i can't seem to get the thing to work....my cron doesn't seem to run anything at all, not even echo "hello". ](*,)

this is what my file looks like:

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

15 19 * * * /usr/bin/mpg123 ~/Desktop/alarm.mp3

```

Cron runs the command in a new shell.  If you want to send a message you can see on another terminal, you could use the wall command:
```

* * * * * echo "hello there" | wall

```

Use "export DISPLAY=:0" to run a GUI command. This should start Firefox every minute:
```

* * * * * export DISPLAY=:0 && firefox

```

---

### Post by munkar on 2006-12-29
export display did it! thanks so much :)

---

