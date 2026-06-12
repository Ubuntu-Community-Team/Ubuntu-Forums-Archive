---
title: "Cronjob"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Badoxide on 2008-08-14
Hello.All

I need your help please I am trying to use a cronjob this is how I am going about it.

sudo crontab -e

I then add this here.
MAILTO=My [email]name@something.com[/email]
30 15 * * * /usr/sbin/chkrootkit && /usr/bin/updatedb

I then do.

:wq

I get no errors.

I also use this to check

crontab -l 

Well my problem is I don't see anything happening at all I am not getting any E-Mail. Any help at all on this please would be great.

Thank you

Badoxide

---

### Post by cariboo on 2008-08-14
You need to have some sort of MTA running to have your log emailed to you. You should probably install postfix and courier to do what you want. Both packages are available in the repositories.

I just had a look at the cron-job rkhunter sets up and it specifies sendmail, but you change that to the email server of your choice.

Jim

---

### Post by Badoxide on 2008-08-14
Hello.cariboo907

I thank you, for taking the time to help me. Is there some way for me, to know if I have them installed just not running now. As you can well tell new to all this ubuntu thing. ;)

Thank you

Badoxide

---

### Post by Badoxide on 2008-08-16
Hello.To all

Have a safe weekend. Now could someone anyone please till me, how in gods name do I send an E-Mail to myself using a cronjob, or crontab. Do I need to install anything if, so then what please help me.

Thank you

Badoxide

---

