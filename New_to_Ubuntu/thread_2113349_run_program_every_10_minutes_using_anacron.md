---
title: "run program every 10 minutes using anacron"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-07
Hi all, 

how do I run program every 10 minutes using anacron?

---

### Post by surfer on 2013-02-07
why anacron?

cron does what you want:

(from [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto"))

minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), user, command


[FONT="Courier New"]# every 10 minutes:
*/10 * * * * someuser /usr/bin/somedirectory/somecommand[/FONT]

save these lines to the file [FONT="Courier New"]/etc/cron.d/somecron[/FONT].

**attention** with the filename in /etc/cron.d:
from man cron:


[FONT="Courier New"]As  described above, the files under these directories have to be pass some san&#8208;
       ity checks including the following: be executable, be  owned  by  root,  not  be
       writable by group or other and, if symlinks, point to files owned by root. Addi&#8208;
       tionally, the file names must conform to the filename requirements of run-parts:
       they  must  be entirely made up of letters, digits and can only contain the spe&#8208;
       cial signs underscores ('_') and hyphens ('-'). Any file that does  not  conform
       to  these requirements will not be executed by run-parts.  For example, any file
       containing dots will be ignored.  This is done to prevent cron from running  any
       of the files that are left by the Debian package management system when handling
       files in /etc/cron.d/ as configuration files (i.e. files ending  in  .dpkg-dist,
       .dpkg-orig, and .dpkg-new).[/FONT]

---

### Post by marchelloUA on 2013-02-07
> **surfer said:**
> why anacron?
[FONT=Courier New][/FONT]

Well, my computer is not turned on all the time. 
Is it possible to use cron for this purpose without 100% uptime?

---

### Post by Impavidus on 2013-02-07
Yes, it will run every ten minutes as long as your computer is switched on.

The difference between cron and anacron is that daily activities may be scheduled by cron at three at night to prevent any inconvenience, but this will not work when you switch off your computer at night. Anacron would make sure the daily jobs run every day, whenever the computer is on, not needing a fixed time.

---

