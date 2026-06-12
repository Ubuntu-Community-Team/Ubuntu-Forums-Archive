---
title: "Command line backup advice"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by stevege on 2012-11-13
Hi All,
I've been given the task of setting up a wiki for my employer. I've been given an old server running VMWare and installed Ubuntu Server 12.04 as a virtual machine (could not get the desktop version installed, so no GUI). I've got mediawiki (plus Apache, mySQL and php) up and running pretty well, and the wiki is going 'live' across the company very soon.
My question is what would be the best way of making regular backups of the system/data? bearing in mind I'm _very _new to Linux and I dont have a GUI!
Thanks in advance
Steve

---

### Post by nothingspecial on 2012-11-13
I would suggest rsync

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by Lars Noodén on 2012-11-13
rsync is the way to go.  You'll also have to get the MySQL database backed up.  One way to do that is to use mysqldump.

---

### Post by stevege on 2012-11-13
Hi, thanks for the response.
I wasn't sure whether I'd have to backup the database seperately to the system. Wouldn't rsync backup all of it, assuming I tell it where the database is? and if so, would the database backup be restoreable? Also, I'm guessing I'd need to either take the wiki off-line or make it read-only when making the backup?
Thanks again for the help
Steve

---

### Post by Cheesemill on 2012-11-13
As you're running your server as a virtual machine another option is to just stop the VM and copy its files. The exact method depends on which VM solution you are using.

---

### Post by stevege on 2012-11-13
Is there any way of doing incremental backups with rsync? (or is this expecting too much??)
Steve

---

### Post by stevege on 2012-11-13
It does look as though rsync does support incremental backups, so I reckon that is the way to go!
Thanks guys!

---

### Post by Lars Noodén on 2012-11-13
Yes, rsync can do incremental backups, but that's not in the community documentation.  You'll have to search around for a guide or howto.

Apropos virtual machines, if you are running a virtual machine you can make a snapshot for one form of incremental backup.

---

