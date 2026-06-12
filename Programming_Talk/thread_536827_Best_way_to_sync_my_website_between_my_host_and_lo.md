---
title: "Best way to sync my website between my host and local server"
date: 2007-08-28
forum: Programming Talk
---

### Post by OOzypal on 2007-08-28
What is the best way to sync my website including MySQL database between my web host and local server. I have Ubuntu Feisty with Apache and MySQL.

---

### Post by Mirrorball on 2007-08-28
rsync, lftp, subversion...

---

### Post by leibowitz on 2007-08-29
Like Mirrorball said, an RCS program for the files[1].

With MySQL it's a bit more tricky. I don't know a way to upload changes only. So I end up doing a dump of the database with phpMyAdmin


[1]Bazaar is easy to learn (5 to 10 minutes): [http://bazaar-vcs.org/](http://bazaar-vcs.org/)
Uploading only newly edited files is as easy as doing this:
bzr push [ftp://myserver.com](ftp://myserver.com)

---

### Post by KCPokes on 2007-08-29
I use an rsync script ran via cron, if it is allowable on your host.  As far as the DB goes, you could either just grab a complete backup of the database data on the server or use PhpMyAdmin to take a backup.

---

### Post by Mirrorball on 2007-08-29
For MySQL backup, I have a cron job running on my server that creates a MySQL backup weekly and a cron job running on my computer that downloads this backup. But it's not an incremental backup, I download it all every time. :/

---

