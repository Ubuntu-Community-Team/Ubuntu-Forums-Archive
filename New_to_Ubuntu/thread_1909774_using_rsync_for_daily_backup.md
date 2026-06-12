---
title: "using rsync for daily backup"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by JohnDillinger43 on 2012-01-15
I'm new to Ubuntu and still trying to sort out my backup situation.  After looking around I think rsync (I've been playing around with grsync) pretty much fits what I'm looking for -- I have backup folders on a backup drive that I want to update daily with files that have been created/modified in the corresponding desktop folders.  One of my questions is about rsync itself, that I haven't been able to find an unambiguous answer to online -- when I specify a source and destination, does the source always remain unchanged (which is what I want), or will rsync update source files if the "destination" has a newer version of the same file (for whatever reason)?

The other question is about grsync -- I'm wondering if it's possible to set up a single profile that syncs multiple separate folder pairs.  I've come across people talking about running batches in rsync, but as I said I'm fairly new to this stuff and don't know how to do that.

The final question is a general question about task scheduling -- assuming I get everything in rsync set up the way I want, how do I schedule it to run at a certain time every day?

---

### Post by papibe on 2012-01-15
> **JohnDillinger43 said:**
> does the source always remain unchanged
Yes.

> **JohnDillinger43 said:**
> will rsync update source files if the "destination" has a newer version of the same file (for whatever reason)?
Only if you reverse the order (source <-> destination).

> **JohnDillinger43 said:**
> how do I schedule it to run at a certain time every day?
You can use crontab. Take a look at [this ]("https://help.ubuntu.com/community/CronHowto")tutorial.

Hope it helps.
Regards.t

---

### Post by bluexrider on 2012-01-15
Because rsync is such a powerful engine it has a lot of configurations available. you can check the "man" pages of rsync by opening a terminal an using ```
man rsync
``` I use grsync as the front end to rsync for local backups.

---

### Post by JohnDillinger43 on 2012-01-29
Thanks for clearing up those issues.  I'm in the process of backing up my documents, which I haven't done in a while because I wanted to make sure I understood what was going on with rsync.  I haven't used crontab yet but the tutorial looks fairly easy to understand.

The one remaining issue I'm having is that grsync doesn't seem to have an option for syncing multiple source folders to multiple destination folders.  I read a bit about creating a script to tell rsync to run a number of sync operations, but the only script writing I've done is for a couple specific programs (e.g., R); I don't really know where to being for a script in Ubuntu.  Is there an easier way to go about this, or can anyone give me the basics on what a script to run several rsync backup operations would look like?

---

### Post by dixonstalbert on 2012-01-29
I use luckybackup (in repositories) frontend for rsync. 

you could set up a 'task' which backs up  originalfolder1 to backupfolder1 at 9:00am , then set up another 'task' that backs up originalfolder1 to backupfolder2 at 10:00a.m. 

Is that what you want?

you could do the same thing with 2 scripts set with crontab to run at different times. Both use the same source folder but different target folders

---

### Post by entropy1 on 2012-01-29
See the thread

[http://ubuntuforums.org/showthread.php?t=1319155]("http://ubuntuforums.org/showthread.php?t=1319155")

In post #5, I give a sample rsync script to back up different folders.  In that thread, others talk about cron.

---

### Post by JohnDillinger43 on 2013-02-19
Thanks everyone for the advice.  I ended up writing an rsync script to backup individual folders to individual backup folders, and crontab to run it every night at 3am.  I'm actually about to replace the drive, so I'll probably do a different setup so I'm not copying so many separate folders.

---

