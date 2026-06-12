---
title: "Need some assistance with anacron in Ubuntu"
date: 2016-01-13
forum: New to Ubuntu
---

### Post by Grigoriy on 2016-01-13
Hello!

I've got Ubuntu 14.04 I try to learn about using anacron. And there're 3 things so far that I can't understand. Please explain!

1.) WHEN does the anacron command (tast) should be executed for the FIRST TIME?
Let's say today is Wednesday 2 p.m. (14:00) and I've just made a new  weekly task for anacron. So when should I be expecting the first  execution of it? In other words, what's the starting point here? Weekly,  starting from...???

2.) Let's say I've got 3 commands. So this MUST be a script OR... I can  stuff all three commands in ONE single anacron task? To be more  specific, I want to stop the process, delete the file's content and then  to re-start the same stopped process.

3.) Where should I put the commands for anacron? They say that in  /etc/anacrontab, but there I see 3 default lines of commands that govern  the cron (if I understand that correctly). Should I write my own  commands in the same place just below those three?

---

### Post by TheFu on 2016-01-13
When cron jobs run is slightly different on different systems. Most of my daily tasks run around 6:25am, but on one machine, the setup made the time 6:35am instead. Don't know why - perhaps to prevent NAS/SAN abuse from too many different systems?

Anyway, on your system, you can check the /etc/crontab for the weekly line - the time used is normal crontab time, so you'll be able to decipher it.
```
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
```
Mine runs at 6:47am every Sunday. See how that works?  The crontab manpages (there are different ones) will have more details.

You can make complex 1-line tasks or put them all into a script/program and have anacron call them. Just know that cron jobs don't have much environment and usually run as root, so settings for YOUR userid don't apply and the environment for cron tasks won't get any JAVA_HOME or other stuff like that. The PATH and LD_LIBRARY_PATH will be minimal too. This all means you should follow scripting "best practices" and never trust the environment outside of the script, set anything you need set inside the script.

Where to drop script files run as root?  I don't have  /etc/anacrontab file/directory, so I'd create any new scripts to be run weekly and place those files either in /usr/local/bin or /root/bin ... depending on the sensitivity of the script files. If only root should see the contents, it would be /root/bin - that location isn't publicly viewable.  If it doesn't matter who can read the script, then /usr/local/bin is fine.

---

### Post by Grigoriy on 2016-01-13
Thanks for your reply!

So are you trying to say that cron decides on when anacron should run? In that file... /etc/crontab I see mentioning of a weekly anacron and 6:47 am time. So is it when (by default) weekly anacron is supposed to run its tasks?

One more question... Let's say the computer was off when anacron was supposed to execute its jobs. Let's say it's a weekly job. Then I turn on my PC and anacron does its job, okay? Now... what I don't understand is if after that anacron counts a week from the time of last operation OR it continues its previous weekly count as if my PC was constantly on?

---

### Post by ian-weisser on 2016-01-13
> **Grigoriy said:**
> So are you trying to say that cron decides on when anacron should run?
Not quite.
Cron decides when hourly/daily/weekly/monthly tasks run.
Anacron merely tracks the last time the daily/weekly/monthly jobs actually ran in /var/spool/anacron.
At boot (and wakeup from suspend), anacron compares those timestamps to the current time to determine if any cron jobs were missed. If so, it runs those jobs a few minutes after boot.
Anacron does not replace cron. Anacron is a useful complement to cron.


> **Grigoriy said:**
> In that file... /etc/crontab I see mentioning of a weekly anacron and 6:47 am time. So is it when (by default) weekly anacron is supposed to run its tasks?
6:47 is when cron runs. Anacron runs at boot/wakeup.
If, at boot/wakeup, cron.weekly's timestamp in /var/spool/anacron is over seven days old, then cron.weekly didn't run (because the system was not running), and anacron will run the cron.weekly tasks a few minutes after boot/wakeup.

---

### Post by Grigoriy on 2016-01-16
Thanks for your reply!

Okay, if I want my script to run **daily** with a 3 minute delay. Then I should put it in etc/anacrontab and should I make it like so?

```
1  3  cron.weekly /home/myname/bin/script.sh
```

OR...
```
1  3  cron.daily /home/myname/bin/script.sh
```

---

### Post by ian-weisser on 2016-01-16
Neither. Don't reuse the existing cron.daily/weekly labels. Make a new label (like grig.daily), or your logs will be confusing ('why did cron.daily run twice?').

However, best practice for daily jobs is instead to simply add the job to the existing cron.daily directory:
Move the script from /home/myname/bin/script.sh to /etc/cron.daily/my_script
The script must be owned by root (not your user) and executable for cron to be able to run it.
The script must run headless, output only to log or email. It has no access to your display or other environment variables. It will run regardless of who is logged in...or not logged in.
The script filename must contain no dots(.) or most other special characters, or run-parts will skip it. Special chars denote hidden or backup or experimental files.

(Optional) Edit the existing anacron entry from 5 minute delay (or so) to 3.

The change to anacron delay suggests that close-to-boot/wakeup seems to be important.
Alternately, you may want your script to run under your username, or only after you login, or it may output to your display.
If either or both of those are true, using init instead of cron to trigger the script under the right conditions may also be an appropriate solution.

---

### Post by Grigoriy on 2016-01-16
Thank you!

---

### Post by kevdog on 2016-01-16
Off topic ... but my favorite cron scheduler is fcron.  More full featured.

---

