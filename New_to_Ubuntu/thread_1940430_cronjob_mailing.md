---
title: "cronjob mailing"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by slaz on 2012-03-13
Hi,

I am trying to figure out how to use cron from the terminal. I want the server to email log files. I looked at the crontab file in /etc/crontab but when I add the variable MAILTO=myemal.com nothing gets mailed. Could someone point me in the right direction.

thanks,
Slaz

---

### Post by doctorzeus on 2012-03-13
> **slaz said:**
> Hi,

I am trying to figure out how to use cron from the terminal. I want the server to email log files. I looked at the crontab file in /etc/crontab but when I add the variable MAILTO=myemal.com nothing gets mailed. Could someone point me in the right direction.

thanks,
Slaz

I think your email has to be marked as a string,

i.e. MAILTO="myemail.com"

(put "" quotes around your email)..

See if that works..

---

