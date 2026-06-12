---
title: "Crontab help!!!"
date: 2020-03-11
forum: New to Ubuntu
---

### Post by 4x1ks on 2020-03-11
I need to run a crontab as follows:

* * * * * cd /whatever/whatever1 sudo bash movement.sh

When I do this manually, the script returns a demand for a password.  If I enter the password, then the script runs perfectly.

I don't want to have to do this process manually.  I want it to run automatically every hour or every day.  I set up * * * * * just to see if it will work, however, since it is looking for the password, I need to enter the password.  All of this is on a cloud server.

So essentially, I want the following to happen, but I do not know the syntax

* * * * * cd /whatever/whatever  sudo bash movement.sh  &&  (now here I want to enter the password and then enter CR to enter the password to run the movement.sh script)

How do I do this?
thnx

---

### Post by TheFu on 2020-03-11
Don't use sudo. Use root's crontab.  That can be accessed using either **sudo crontab -e** or **sudoedit /etc/crontab**. These files have slightly different formats.

Don't call bash separately.  Use the #!/bin/bash header inside the script file.

Don't cd outside the script.  Actually the script should be written so that it works correctly regardless of the CWD/PWD.  What happens if the cd fails?

Cron-jobs don't have much environment, so never trust the PATH to magically find programs or scripts. Specify the full-path to the programs inside the script and have the crontab entry use the full-path-to-the script file.  A full-path always begins with a / character.

Do you really want to run this every minute?  Seems excessive.  Usually */5 is the most often any cron-job should be run - that's every 5 minutes.

As an example, here's my root crontab.
```
$ sudo crontab -l
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0-6)Sun=0 or 7 OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  command to be executed
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1
# m h  dom mon dow   command
7  0  * * * /root/bin/back-suspend.sh
```
Most of it is comments.  It runs once a day at 00:07 am.  That's when the machine runs a backup, then suspends itself.  Also, since neither stdout nor stderr are redirected, both are emails to the root@localhost account.  Cron always emails the output from jobs.  The way to prevent that it to redirect both stderr and stdout files somewhere else. Esta claro?

---

### Post by 4x1ks on 2020-03-11
Ok. I did that and the bash script is working fine.  Thanks.

---

