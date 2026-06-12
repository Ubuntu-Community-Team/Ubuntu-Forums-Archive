---
title: "Create crontab and use crontab for schedule"
date: 2009-03-09
forum: Programming Talk
---

### Post by ChrisBuchholz on 2009-03-09
Hi,

[B]Update:
I have sorted out the thing about getting cron to run the crontab. Now it's the part about adding/removing a crontab from within the app, I'm looking for help with.[/B]

I have written a python application that does such a simple thing as checking a gmail account and using the notify-osd engine to indicate incoming emails. Because the app only have so much to do, and only needs to do something every x minut, I have chosen to use Cron instead of just letting the app sleep while waiting for the next check. I have some difficulties with this, though.

My crontab looks like follow:
```
*/02 * * * * /usr/local/bin/gnotify
```

I'm certain of that /usr/local/bin/gnotify works - I've tried in both "Run" and in shell, and it works perfectly. I can also see that cron runs the job, but it doesn't "run it", if you get me?

Also, I wonder how I can make the program create and delete a crontab. There's gonna be a configure/set feature, and the app has to then automaticly go in a delete the old crontab and create a new one.
How do I do that? Can you link me to some reference or something?

Thanks.

---

### Post by ChrisBuchholz on 2009-03-09
I have been looking around, and it seems that the reason my app is not getting fired by cron, is caused by a lag of permissions. I have giving it chown cb:crontab and chown 774 without luck. Also tried with 777, just to check, but that didn't work either.

---

### Post by ChrisBuchholz on 2009-03-09
Okay, so I figured out than what I need, was to specify the display environment for the crontab.

```
*/2 * * * * DISPLAY=:0.0 /home/cb/Documents/Projects/gnotify/gn.py
```

I also discovered that it only needed to have chmod +x, and not everything else like adding crontab to its permissions group and that stuff.

**UPDATE**
But I'm still looking for some enlightenment on how to add/remove crontabs from the python app.

---

### Post by Tibuda on 2009-03-10
You should look the source code of [gnome-schedule]("http://gnome-schedule.sourceforge.net/").

---

### Post by ChrisBuchholz on 2009-03-11
I figured out how to create a crontab entry from within python, by simply running the bash command (*echo '...' | crontab e*) with the os.system module, and also how to remove again (*crontab -r*).
The only problem is that crontab -r purges the whole crontab-user-file, and I have not found a way to only remove the desired crontab-entry.

Any suggestions?

I'm looking for a hint in the gnome-schedule source, but until then, it would be cool if some of ya' could point me in the right direction.

**UPDATE**
I didn't get much out of gnome-schedule, but I found a way of using *crontab -l* to do the thing.
First you pipe *crontab -l* in a file, then you do the changes on the file, and then you pipe the changed file back via *crontab -*.
It works really great!

---

