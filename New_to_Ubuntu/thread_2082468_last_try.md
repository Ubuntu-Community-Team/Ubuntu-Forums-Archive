---
title: "last try"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by squrl on 2012-11-09
About a year or two ago I bought a dlink dns321 intending to use it for automatic backups. I run ubuntu 10.04 and like 99% of it. I have never been able to configure or get grsync or sbackup to allow me to point to the nas drives for a backup. This is my last try. I have tried about every how to on the net with no success. If I dont succeed this time it goes in the trash.

I am asking for suggestions or help to get this setup. All I want is to be able to schedule backups every few days automatically. I'm not even moxy enough as to what information I need to include here.

Thanks in advance for any help that might be offered.

---

### Post by daslinkard on 2012-11-09
> **squrl said:**
> About a year or two ago I bought a dlink dns321 intending to use it for automatic backups. I run ubuntu 10.04 and like 99% of it. I have never been able to configure or get grsync or sbackup to allow me to point to the nas drives for a backup. This is my last try. I have tried about every how to on the net with no success. If I dont succeed this time it goes in the trash.

I am asking for suggestions or help to get this setup. All I want is to be able to schedule backups every few days automatically. I'm not even moxy enough as to what information I need to include here.

Thanks in advance for any help that might be offered.
Maybe this [link]("http://ubuntuforums.org/showthread.php?t=1070167") can help you out...

---

### Post by Paqman on 2012-11-09
What part is tripping you up?

Essentially all you need to do is:
[LIST]
[*]Mount the NAS storage locally by adding an entry to /etc/fstab
[*]Add a short rsync script to /etc/cron.daily (for example) and it will back up to that location daily
[/LIST]

Can you get access to the NAS at all? Or is it the backup part that's foiled you in the past?

---

### Post by SysBoot on 2012-11-09
if all else fails you can set up a backup with rsync and crontab

Example:
 I want to back up everything in my documents to my drop box directory. I made a file called backup_schedule.sh and put this in it:
```

#/bin/bash

rsync -avzu /home/sysboot/Documents /home/sysboot/Dropbox/Documents/Mark-1

``` 

and set up the schedule with:

```
 
crontab -e

```

it'll give you the option to choose a text editor and it'll give you something like:

```

# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
# Job to call /home/sysboot/.backup_schedule.sh at 9:00 pm every monday night
0 21 * * 1 sh /home/sysboot/.backup_schedule.sh

```

Just google how to use crontab.
now all you have to do is chmod the backup script for it to work
```

chmod u+x /path/to/file

```

test it to make sure it works.

---

### Post by Paqman on 2012-11-14
> **SysBoot said:**
> 
Just google how to use crontab.


For a desktop anacron is the way to go. You don't have to actually do anything to make it work, just drop your executable script into the appropriate folder (eg: /etc/cron.weekly) and it'll work. Nice and easy.

---

### Post by Phil Binner on 2012-11-14
This may bve related to a question I was about to post.

I have also a D-Link NAS which holds all my data and is accessed by both Ubuntu and Windows.  When I search for files in Ubuntu there it is, and I read the files, no problem.

When I want to access the files directly from an application, however, the NAS is just not there on the list.  That means, for instance, that if I want to attach a document to an email in Thunderbird, I have to download it from the NAS first.

As far as I can gather all applications use the same list when getting files, and the network is just not on it.  I would surmise that there is an applet (library, subroutine, whatever) that developers inherit from Ubuntu, and that the fault lies with what they are offered by Ubuntu.

Is there some setting in my system I can use to rectify this.

Appologies if I have butted in, but is this the same problem you are having.

---

### Post by Paqman on 2012-11-14
> **Phil Binner said:**
> 
Is there some setting in my system I can use to rectify this.


Yup.

When you mount things through browsing to them in your file manager it temporarily mounts them to a slightly weird location in your home folder. You could point applications there if you knew where to look, but it's a bit of a faff.

Best thing to do is have your shares mount automatically at boot time to a folder you designate. Most people choose to mount them somewhere like /mnt, but you can choose anywhere you like. YOu could make a mount point called /banana/trousers if you want.

If your NAS shares using the Windows networking protocols (which it probably does) then you want to [read this]("http://ubuntuforums.org/showthread.php?t=288534"). It's actually not as complicated as that guide makes it look, essentially you install one package, make some folders, and add one to a text file.

If your NAS is able to use NFS then you'll want to [do that instead]("http://ubuntuforums.org/showthread.php?t=249889") (just the client side bit).

---

### Post by Phil Binner on 2013-04-28
That sorted it for me. I trust Squrl is also good now. The NAS is now searchable from all the programmes I use, as well as the file manager, so I can use my system normally.

Thanks for the help.

---

