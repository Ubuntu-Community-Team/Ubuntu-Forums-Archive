---
title: "notify-send from crontab in 16.04"
date: 2016-07-13
forum: Programming Talk
---

### Post by c0n7r4 on 2016-07-13
trying to write a script using notify-send in a crontab entry and its not working. ```
sudo crontab -e
* * * * * export DISPLAY=:0 && export XAUTHORITY=/home/user/.Xauthority && /usr/bin/notify-send test test

``` This used to work in older versions of ubuntu, but not 16.04, anyone got any ideas?

---

### Post by ian-weisser on 2016-07-13
When that root cron job runs, how do you know that 'user' will be logged in and using that particular display?

I generally avoid the problem by separating root and non-root functions into separate services, connected and triggered by dbus.
However, while it's a robust and safe design, it might be a more complex answer than you seek.

---

### Post by jamesr on 2017-03-02
Hi,
I know that this is an old message but I have a similar problem with some scripts that I have called from a root cron job. The notify-send messaging does not work. Any suggestions

---

### Post by Habitual on 2017-03-02
Root cron runs scripts. Scripts run notify-send (to a user's environment) when run as root cron job.  Correct?  Show us the relevant parts of the scripts?

---

