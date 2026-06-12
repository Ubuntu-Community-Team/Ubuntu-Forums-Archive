---
title: "Cron Problem on  Reboot"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-09-27
I have a cron job which runs hourly. However, when I reboot my machine, the hourly cron job does not run unless I run it first by hand (so to speak). Then it will run OK.....but surely it should run automatically after a reboot without intervention?

---

### Post by LowSky on 2011-10-01
add the running program to startup applications.. one you log in it will start, and then should run hourly.

---

### Post by dunbrokin on 2011-10-01
Thank you for that..I had thought of that .......but I assumed that there must be a way of switching on the crons when you boot. I guess not....

---

### Post by papibe on 2011-10-01
Could you post your crontab and the script you are running?

Regards.

---

