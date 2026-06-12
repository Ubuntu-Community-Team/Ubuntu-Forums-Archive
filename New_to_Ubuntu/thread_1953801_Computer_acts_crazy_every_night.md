---
title: "Computer acts crazy every night"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by Troy McClure on 2012-04-06
Every night at exactly the stroke of midnight, my computer starts working hard.  Fans at max, hard drive spinning, lasts about 30 seconds.  It's much noisier than when I'm using it during the day.

It wakes me up every night, but by the time I turn on the monitor, open a terminal and see what's running, it's over.

What the heck is it?  And how can I figure it out without staying up to ambush it?

---

### Post by jonnyboysmithy on 2012-04-06
I know that the dmesg command spits out the latest events. Maybe you could change the time so that its 12:00 right now and see what the output is. Anyone else got any idea?

---

### Post by bodhi.zazen on 2012-04-06
Review your cron tasks, they are listed in the /etc/cron.daily directory

My guess would be logrotate and mlocate

See [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Troy McClure on 2012-04-07
OK first I looked at cron.daily (never knew that existed).  Lots of scripts in there, but when I ran them all the computer barely blinked.

Then I tried your idea of setting the time to 23:59 to recreate the problem while "top" was running in a terminal.  It worked. Xorg and xfce4-panel each take about 50% of the cpu.

I don't know what these do or why they feel the need to party every night at midnight.  Any ideas?  Thanks for the info so far.

---

