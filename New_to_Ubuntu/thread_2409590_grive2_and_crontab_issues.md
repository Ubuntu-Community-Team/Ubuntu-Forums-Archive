---
title: "grive2 and crontab issues"
date: 2019-01-04
forum: New to Ubuntu
---

### Post by teckthekid on 2019-01-04
Hello, I have been fighting with it for last two days.
I have no idea what I am doing wrong.
I installed grive2 to sync with my google drive.
It works perfectly.
So I wanted to make a crontab so that directory would get synced every 60 minutes.

This are the crontab entries I tried:
30 * * * * grive -p /home/user/GoogleDrive
30 * * * * /home/user/GoogleDrive/grive
30 * * * * cd /home/user/GoogleDrive && grive

I also tried to run it from script:
#!/bin/bash
cd GoogleDrive
grive


If I run these commands and script by it self it works fine, once used in crontab it does not work.
What I am doing wrong?

Please help, I feel like I am going insane...

---

### Post by TheFu on 2019-01-04
Just a guess, but cron doesn't provide the same environment that a full login session provides. This is a common issue.
Also, cron cannot run GUI programs.

Look up "best practices for crontab" for all the important details.  I've posted info about this at least 10 times in these forums.

---

### Post by teckthekid on 2019-01-04
Can't find it here...
It is a command line script not GUI.

---

### Post by oldrocker99 on 2019-01-05
To edit the cron configuration, I use this:
```
sudo nano /etc/default/cron
```

You may wish to use another editor, but nano is quick and easy, and my go-to editor for a decade. The menus are on the border.

---

### Post by TheFu on 2019-01-05
> **teckthekid said:**
> Can't find it here...
It is a command line script not GUI.

[https://ubuntuforums.org/showthread.php?t=2398585&highlight=crontab+-e+thefu](https://ubuntuforums.org/showthread.php?t=2398585&highlight=crontab+-e+thefu) is a start. It links to other places.  Pay special attention to setting up the environment and never assume a PATH is what you want in cron.  It is much smaller than the PATH a normal login session gets.

---

