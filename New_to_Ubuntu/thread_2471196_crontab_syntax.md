---
title: "crontab syntax"
date: 2022-01-23
forum: New to Ubuntu
---

### Post by rburkartjo on 2022-01-23
running 21.10

i want this script to run every 4 hours starting at 00.30

30 00,04,08.12.16.20  * * * xmessage -display :0.0  “one bell!!!"

is the above correct or is there a better syntax to use
/tks

---

### Post by TheFu on 2022-01-23
Cannot have any GUI program running under cron.  It doesn't interact with GUI sessions.

You can use "wall" to interrupt all consoles and terminals on a system, if you like.
This is incorrect:
```
[s]30 00,04,08.12.16.20 * * * xmessage -display :0.0 “one bell!!!"[/s]
```
We aren't allowed to mix , and . separators.  X/Windows stuff cannot/should not be used.
```
I'd do it this way (a helpful header added):
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command --arg1 --arg2 file1 file2  > /tmp/log.file  2>&1
30 */4 * * * /usr/bin/wall "one bell"
```

If you just want a 4 our timer, check out **alarm-clock-applet**. The package is in the repos.

---

### Post by rburkartjo on 2022-01-23
then why does this crontab job work
not written by myself


00 11,16 * * * xmessage -display :0.0 "COFFEE BREAK DUDE !!!"

tks

---

### Post by TheFu on 2022-01-23
Just because something works, doesn't make it a good idea.
Did you see where I said you can't use periods?
If you want something that ALWAYS works, don't attempt to use GUI programs in a crontab.  It won't always work.

---

### Post by rburkartjo on 2022-01-23
tks fu still learning at 72 and those were suppose to be commas
always appreciate your help and advise

---

### Post by TheFu on 2022-01-23
> **rburkartjo said:**
> tks fu still learning at 72 and those were suppose to be commas
always appreciate your help and advise

There's always more to know. Always. For everyone.

I don't know if Wayland supports the idea of a DISPLAY environment variable.
I don't recommend using any GUI program (X/windows program or Wayland) in any crontab, since they don't always work. Use alarm-clock-applet or wall.  But if you insist, you could use 
```
DISPLAY=:0 /path/to/some/X-program 
```
as the command.  

I don't use wayland and haven't looked at it in about a year, so I have doubts that any xwindows program will continue to work under it.

I use alarm-clock-applet for periodic reminders, since hours can disappear without it.

---

