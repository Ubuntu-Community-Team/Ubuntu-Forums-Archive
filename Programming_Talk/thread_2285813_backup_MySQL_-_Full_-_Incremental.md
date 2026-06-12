---
title: "backup MySQL - Full - Incremental"
date: 2015-07-08
forum: Programming Talk
---

### Post by Drenriza on 2015-07-08
Hi all

I am thinking if anyone has experience with Debian / Ubuntu and backing up a MySQL database, first by taking a full backup and than taking an incremental backup.

If anyone has a useful script, link to a good article about the subject or who can tell me where i should look i would be super grateful.

Thanks on advance
Kind regards

---

### Post by SeijiSensei on 2015-07-08
I just make a full backup every day with "mysqldump --all-databases".  The files aren't that large to begin with, and you can always compress them with gzip or bzip2.  I use an eight-day rotation, with one backup per month preserved as an archive.  Restoring a full backup in MySQL (or PostgreSQL which I also use and prefer) is much easier than using incrementals.

---

### Post by Drenriza on 2015-07-10
Hi SeijiSensei

Thanks for your reply :) I will look at if i can make something like this work for my setup

---

### Post by SeijiSensei on 2015-07-10
> **Drenriza said:**
> Hi SeijiSensei

Thanks for your reply :) I will look at if i can make something like this work for my setup

Here's a starting point:  [http://ubuntuforums.org/showthread.php?t=2218776&p=12997721&viewfull=1#post12997721](http://ubuntuforums.org/showthread.php?t=2218776&p=12997721&viewfull=1#post12997721)

---

### Post by Habitual on 2015-07-10
[http://bash.cyberciti.biz/backup/backup-mysql-database-server-2/](http://bash.cyberciti.biz/backup/backup-mysql-database-server-2/)

---

