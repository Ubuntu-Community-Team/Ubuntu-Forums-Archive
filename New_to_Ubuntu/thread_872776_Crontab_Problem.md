---
title: "Crontab Problem"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by ahbb on 2008-07-28
Hi there,

Im running pisg on it's all nice and running no problem with the program.

But when i added it to sudo crontab -e and insert this line

*/5 * * * * /root/pisg --silent so that it can run every 5 min to update the stats.

But it just dont update the stats @ all.

What am I doing wrong?

Thanks

Andrew ](*,)

---

### Post by mali2297 on 2008-07-28
Try **/usr/bin/pisg** instead of /root/pisg.

---

### Post by ahbb on 2008-07-28
HI,

Must i remove the --silent as well?

Thanks

Andrew

---

### Post by ahbb on 2008-07-28
The other problem is i cant use /usr bin as I installed it in my root DIR did not know pisg was on ubuntu.

The program run 100% and work when i do it manual, i just want it to update every 5 min with crontab.

Please help.....

Thanks

Andrew

---

### Post by Potatoj316 on 2008-07-28
I didnt know you could do */n.  It seems everyone has crontab problems.

Try crontab -l to make sure that this line gets put in your crontab

---

### Post by ahbb on 2008-07-28
this is the entry in the crontab

0,5,10,15,20,25,30,35,40,45,50,55 * * * * /root/pisg --silent

But it still dont work let me paste you the log out of the log file.

Jul 28 23:15:01 shells /USR/SBIN/CRON[26419]: (root) CMD (/root/pisg --silent)

BUt it still dont ubdate the stats?

Hope you can help.

Thanks

---

