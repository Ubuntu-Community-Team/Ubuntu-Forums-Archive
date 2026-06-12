---
title: "Backup tool, please?"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by daniel3ub on 2008-10-11
Hi, there.

I don't know if this should be under "Absolute Beginner Talk" or "desktop", but I'm posting this here, anyway.

I am searching for a backup solution (for a external HDD) for my desktop computer with the following features (all of them):

. Not compressed backup
. incremental backup
. scheduled, automated backup
. an easy to use graphical interface
. let me set up daily, weekly and monthly backups (and store them separated)
. do not lock the files being backed up

I've been testing some programs the last couple of days, and I can tell that I could not find one to meet all my requirements. Next, I'll try to list all the programs I have been testing and why each one is not good for me. Please, if I am wrong about any of them, I'd love to know.
Note that I don't have any knowledge about scripting or programing.

**SBackup (Simple Backup):**
. Not compressed backup [NO]
. incremental backup [YES]
. scheduled, automated backup [YES]
. an easy to use graphical interface [YES]
. let me set up daily, weekly and monthly backups [YES]

The only problem with sbackup, fo me, is that it uses tar instead of rsync, and I need to keep my files uncompressed on my destination directories.

**Conduit**
. Not compressed backup [YES]
. incremental backup [NO]
. scheduled, automated backup [NO]
. an easy to use graphical interface [YES]
. let me set up daily, weekly and monthly backups [NO]

More a sync tool than a backup solution.

**rsync**
. Not compressed backup [YES]
. incremental backup [YES]
. scheduled, automated backup [NO]
. an easy to use graphical interface [NO]
. let me set up daily, weekly and monthly backups [NO]

Seems the ideal tool, but since I know nothing about script programming and I'd prefer a graphical interface, I think it will have to wait

**Grsync**
. Not compressed backup [YES]
. incremental backup [YES]
. scheduled, automated backup [NO]
. an easy to use graphical interface [YES]
. let me set up daily, weekly and monthly backups [NO]

Still not there. If there is a way to call it from a shell script for each profile it saves, it would be almost nice.

**Unison**
. Not compressed backup [yes]
. incremental backup [no]
. scheduled, automated backup [no]
. an easy to use graphical interface [YES]
. let me set up daily, weekly and monthly backups [NO]

Another sync tool, not backup solution.

**Flyback**
. Not compressed backup [YES]
. incremental backup [NO]
. scheduled, automated backup [YES]
. an easy to use graphical interface [YES]
. let me set up daily, weekly and monthly backups [NO]

Snapshot backups. Gross...

**Restore**
A web based solution. You must have apache/mysql up and running in order to use this.

So, this is the results of my testings so far.

Could you guys help me pointing another programs or solutions, or even mistakes in my tests? I really do not want to keep updating scripts or cron tabs or file lists as parameters to do this.

Another question: if I schedule a backup and my computer in not turned on OR my usb hdd is not plugged in, will the backup be deferred or it will not be made at all? this is important, as my usb hdd is not always plugged in.

Thanks a lot, pals!

---

### Post by oldos2er on 2008-10-11
Why not use cron to run grsync when you wish?

---

### Post by Keen101 on 2008-10-11
try this. I don't use it, but it might work for you.

[http://restore.holonyx.com/](http://restore.holonyx.com/)

---

### Post by daniel3ub on 2008-10-11
> **oldos2er said:**
> Why not use cron to run grsync when you wish?

Because I think I cannot run grsync from a cronjob, calling a specific profile (or all of them). Right me if I am wrong, please.
Anyway, i'd need to configure 3 profiles (daily, weekly, monthly) for each file/dir I want to backup (what would take a gigantic amount of space). I need a way to add a directory to my backup scheme easily.

@Keen101:

I'll try this one, and I'll come back to tell the results.

Thanks, guys!

---

### Post by handydan918 on 2008-10-11
I don't know if yo can run grsync from cron or not, but you can definitely run rsync.
Life is a series of compromises.

---

### Post by stinger30au on 2008-10-12
> **daniel3ub said:**
> Hi, there.

I don't know if this should be under "Absolute Beginner Talk" or "desktop", but I'm posting this here, anyway.

I am searching for a backup solution (for a external HDD) for my desktop computer with the following features (all of them):

. Not compressed backup
. incremental backup
. scheduled, automated backup
. an easy to use graphical interface
. let me set up daily, weekly and monthly backups (and store them separated)
. do not lock the files being backed up


easy

i do this right now for free

first install wine

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

once wine is installed, get a windows freeware backup called syncback freeware right here

[http://www.2brightsparks.com/downloads.html](http://www.2brightsparks.com/downloads.html)

scroll down and find syncback freeeware and install and run it

it will do everythink you have just asked for


enjoy

---

### Post by eriqjaffe on 2008-10-12
> **daniel3ub said:**
> Because I think I cannot run grsync from a cronjob, calling a specific profile (or all of them). Right me if I am wrong, please.According to grsync's web site, you should be able to:

> Shell script for batch, crontab use etc. provided (grsync-batch)

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---

### Post by altonbr on 2008-10-12
I have a script for backing up nightly with rsync and SSH: [http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

But if you're looking for something graphical, try QuickStart, by mdpalow: [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

---

### Post by daniel3ub on 2008-10-13
> **altonbr said:**
> I have a script for backing up nightly with rsync and SSH: [http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

But if you're looking for something graphical, try QuickStart, by mdpalow: [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

QuickStart is not open source, and it makes only compressed backups :(

---

### Post by daniel3ub on 2008-10-13
> **stinger30au said:**
> easy

i do this right now for free

first install wine

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

once wine is installed, get a windows freeware backup called syncback freeware right here

[http://www.2brightsparks.com/downloads.html](http://www.2brightsparks.com/downloads.html)

scroll down and find syncback freeeware and install and run it

it will do everythink you have just asked for


enjoy

The only drawback is that it uses the very buggy Windows Task Scheduler for scheduling the backups. Did you get it to work on Ubuntu?

---

### Post by daniel3ub on 2008-10-13
> **Keen101 said:**
> try this. I don't use it, but it might work for you.

[http://restore.holonyx.com/](http://restore.holonyx.com/)

Thanks, but it's a web based program, and I didn't want to keep an apache/mysql server running just to make local backups :S
Main post updated.

---

### Post by Keen101 on 2008-10-14
They do have a live-CD version.....

> RESTORE Live
RESTORE Live is a Live CD with a runnig Xubuntu based RESTORE system on it. It is also fully installable! RESTORE Live is THE easiest way to get RESTORE running on a computer!

---

### Post by nikkkko on 2008-10-16
I've been using Keep, (KDE gui, uses rdiff-backup ([http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)) as backend), for a year or so, but I never looked to see if you can schedule. I'm pretty sure you can. I am a total amateur but I managed to set it up to do what I want between two computers and an external disk.

---

