---
title: "cron job"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by lol22 on 2011-09-20
hi m trying to run this file for cron job 
 
/var/www/vhosts/MySiteName.com/httpdocs/mail.php
 
i currently have tried this path but its not working
/usr/bin/php -f /var/www/vhosts/MySIteName.com/httpdocs/mail.php
 
which path shud i use for command path??  
 
m using following:
GNU/Linux Ubuntu 10.04-LTS.
Plesk V10.1.1 (64BITS)

---

### Post by philipballew on 2011-09-23
cron jobs typically go in your cron folder. [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by idi0tf0wl on 2011-09-23
So you've actually ceated the cron file and verified that your time syntax is correct? Usually commands from paths have a dot, set up an alias for the php command and run it manually to make sure it's working properly, then in your cron you can reference it with the alias. Wrap your path in quotes (it's a good habit).

---

