---
title: "help needed to set up a cronjob"
date: 2013-12-16
forum: Programming Talk
---

### Post by J_Me on 2013-12-16
Could someone please help me out. My bash file looks like this ```
 #!/bin/bash foo 
``` I've made it executable with ```
chmod +x foo
```and now I have to put it in my crontab with ```
* 1 * * * /home/me/myscripts/foo
``` which should run this bash file at 1am each day. I read that I should run 'crontab -e' but doing this opens an empty file but my /etc/crontab file is not empty. Thanks

---

### Post by r-senior on 2013-12-16
The /etc/crontab file is the system crontab. It won't be empty because, on Ubuntu at least, it fires off other cron jobs from /etc/cron.daily/ and so on. These do all sorts of things: checking for updates, rotating log files, etc. The system crontab is edited directly, not with crontab -e, but you probably don't want to edit it.

Each user has their own crontab which is edited by using crontab -e. The first time you use crontab -e it will be empty. This is where you should put your jobs. The files it creates are stored for each user in /var/spool/cron/crontabs/<username> but you shouldn't edit these directly. Always use crontab -e to edit and crontab -l to view.

Note that if you use sudo crontab -e, you edit the crontab for the root user, not the system crontab in /etc/crontab.

---

### Post by J_Me on 2013-12-16
Thank you very much for your detailed explanation.

---

### Post by Habitual on 2013-12-16
> **J_Me said:**
> ```
* 1 * * * /home/me/myscripts/foo
``` which should run this bash file at 1am each day. 

1am and 60 times for every minute in that hour.

```
00 1 * * * 
```

[http://www.dataphyx.com/cronsandbox/cronsandboxgui.php](http://www.dataphyx.com/cronsandbox/cronsandboxgui.php)

---

### Post by ivan19 on 2013-12-19
[COLOR=#000000][FONT=Arial]try using "The EasyCronjobHandler" [http://codecanyon.net/item/the-easycronjobhandler/6296537](http://codecanyon.net/item/the-easycronjobhandler/6296537)[/FONT][/COLOR]

---

