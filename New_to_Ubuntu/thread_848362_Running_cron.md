---
title: "Running cron"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Cowpoke on 2008-07-03
I have Xubuntu 8.04 installed, and working; except for crontabs.

I am new to Xubuntu, coming over from Windows XP and Cygwin.  In Cygwin, I had/have crontabs working perfectly.  I am missing some rudimentary settings in Xubuntu though, not sure what.

...where do I start?  What should I be looking at/for?

Thanks,
Cowpoke
:confused:

---

### Post by superprash2003 on 2008-07-03
basically you go to the terminal and type crontab -e and insert your cron tasks

---

### Post by Cowpoke on 2008-07-03
Thanks, I know how to do that part (crontab -e)...  In my installation, it just doesn't work yet. :mad:

My original query is/was vague; still, I am trying to figure out if there are file permissions I should be setting, mail settings I need to set up, stuff like that.

In general, I want a particular script to run at a specific time, and I want messages to be written (/usr/bin/wall *blah blah*) to my terminal screen at other times (kind of like an alarm clock).

I keyed in those entries with crontab -e, but the scripts aren't running, and no messages are being displayed on my screen.

Cheers,
Cowpoke

---

### Post by ibuclaw on 2008-07-03
Crontabs by default redirect all stdout and stderr messages to your mailbox.

I don't think you can have text printed inside a terminal on screen, but you can have apps starting with something like
```
DISPLAY=:0.0 gcalctool
```
Instead of just "gcalctool" as your command.

If you want some sort of text alert/alarm, zenity may be your answer to that.

```
sudo apt-get install zenity
```

And have
```
DISPLAY=:0.0 zenity --info --text="GO TO SLEEP"
```

Regards
Iain

---

