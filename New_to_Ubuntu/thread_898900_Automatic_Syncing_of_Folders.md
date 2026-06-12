---
title: "Automatic Syncing of Folders"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Orwell on 2008-08-23
Just curious as to whether or not there is an app out there that would allow me to set folders to sync with other folders automatically. eg: if I were to want my documents folder to sync with a folder on my external hard-drive...every day, week, etc.

Any ideas how I could go about this?

cheers!

---

### Post by SNuxoll on 2008-08-23
That would be very easy to do with a cronjob and rsync.

Do you know how to use both?

---

### Post by AndyCooll on 2008-08-23
As SNuxoll says. You can also try Unison.

:cool:

---

### Post by Orwell on 2008-08-23
> **SNuxoll said:**
> That would be very easy to do with a cronjob and rsync.

Do you know how to use both?

No, I've never used either...I'll take a look in Synaptic, see if I can have a go...cheers!

---

### Post by SNuxoll on 2008-08-23
both are included by default in Ubuntu, a cronjob is a job run by your cron daemon, it's basically the scheduled execution of a program.  rsync is a data backup and syncing tool used to sync two folders, what you'll do is have a cronjob that runs rsync however ofter you want basically.

So read up on crontab and rsync :)

---

### Post by jblackwe on 2009-06-10
Which is the best way to sync to an external disk for files that get updated daily?
Code and results and the like, thanks!

---

### Post by reeseslover531 on 2009-06-10
you can just run unison as a cron job daily.  That probably would be easiest.

---

