---
title: "Cron Configuration"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by harsh_ on 2008-07-09
have a simple script which i want to execute everyday at 00:05 hrs..
The script is stored in /usr/local/bin and named as starter which contains just 1 command "perl ./router" which is-obviously a perl script and invokes the router.pl (execuatble) to reboot the router.. When i just type ./starter by being in /usr/local/bin/ the router lights get off and on i.e the router gets rebooted but if i enter the same command in cron it doesnt!

There are 2 different configs in crontab -l and gedit crontab... Why so???
I login as harsh and there is another user harshil....Please consider the thing... I myself as harsh am the administrator...

---

### Post by superprash2003 on 2008-07-09
to create a crontask in the terminal type crontab -e .. and then try adding the following line
00 00 * * * perl /usr/local/bin/router

presuming that router.pl is under /usr/local/bin .. cause you need to mention the full path while doing this in cron

---

### Post by lamego on 2008-07-09
Please consider reading the crontab manual, on the terminal type:
man crontab
man 5 crontab

---

