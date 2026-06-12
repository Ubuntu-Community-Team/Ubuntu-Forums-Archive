---
title: "After upgraded, cron doesn't work."
date: 2008-11-20
forum: New to Ubuntu
---

### Post by singlebook on 2008-11-20
Hello, my ubuntu is 8.04.

I used cron to shutdown my ubuntu box automatically. But after sudo apt-get upgrade. ubuntu cannot be shutdowned automatically by crontab.

ps -e | grep cron

1705 00:00:01 cron

Thank you very much!

---

### Post by cmnorton on 2008-11-20
Before doing the following, please note this is for testing purposes, and you will need to undo this within five minutes.


Add this to /etc/crontab (using sudo)

* * * * * root echo test

You should start getting emails. 

Don't forget to remove the line from /etc/crontab.

If you don't get email, look in messages or syslogd to see what's up.

---

