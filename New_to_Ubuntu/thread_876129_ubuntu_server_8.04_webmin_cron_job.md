---
title: "ubuntu server 8.04 webmin cron job"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by ddragas on 2008-07-31
Hi all

I want to make cron job every time box is turned on, using webmin.

I'm using ubuntu server 8.04 and webmin installed.
path to php script is /var/www/BackupDatabases.php

Problem is when I create cron job, save settings, again enter in edit mode for that cron job and press Run Now button I get output

Output from command /var/www/BackupDatabases.php ..

/bin/sh: /var/www/BackupDatabases.php: not found


at the top of php file I've put #!/usr/bin/php


please if someone can help me and point me in right direction

kind regards

ddragas

---

### Post by pytheas22 on 2008-07-31
I think there are a few things wrong.  First of all, it's trying to run the PHP script with bash, not php.  What line did you put in crontab (can you paste /etc/crontab here?)?  I know that in your script itself, you tell it to use php, but apparently for some  reason it thinks it should use bash.

Second, you say that you want to run this whenever the machine is turned on.  As far as I know (which isn't too much so I could be wrong), there's no way to tell cron to run a job every time the machine is turned on--you can only tell it to do stuff at certain times of day.  If you want to run a command every time your machine starts, you should write a startup script, not use cron.  There on good instructions [here]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") on doing that.

As for the error about /var/www/BackupDatabases.php not being found, check the permissions on that file.  It needs to be readable and executable by whichever user is supposed to execute it (probably root).

If you have more questions, please post.

---

### Post by ddragas on 2008-07-31
crontab:
5 19 * * * /var/www/BackupDatabases.php #Database Backup

there is in webmin possibility to run cron job when system boots on
please find screenShot in this post.

What should I write as command in cron job to execute this script ?

---

### Post by pytheas22 on 2008-07-31
I admit that I don't know about webmin or how it works.  I'm thinking, however, that it may expect all of the cronjobs to be bash scripts, which is why it won't use php to parse your script.

You could try doing this: first, make sure that you have the php parser installed (I'm not sure if it comes preinstalled on Ubuntu server edition or not):
```

sudo apt-get install php5-cli
```

then, in webmin, in the field labeled "Command," enter the line:
```

php /var/www/BackupDatabases.php
```

That may force the script to be run with php.

If that doesn't help, does your script run if you type in a normal bash shell (i.e., a normal Linux command line):
```

sudo php /var/www/BackupDatabases.php
```

---

### Post by ddragas on 2008-08-01
thank you for reply

I'll try it when I get home, and let you know results

kind regards

ddragas

---

### Post by ddragas on 2008-08-01
Thank you for your help

I works great

---

