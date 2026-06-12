---
title: "backing up"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by smile-its-smiley on 2008-05-01
How do i go about baking up my entire ubuntu system to a cd. in windows i can use system restore or back up manager i think they call it.

---

### Post by kosmic on 2008-05-01
There is a lot of tools to help you out, like "rsync, dd, cpio, bacula....

Have a look at this site, it should help you out ;)

[http://www.bluehaze.com.au/unix/cdbkup.html](http://www.bluehaze.com.au/unix/cdbkup.html)

---

### Post by Monicker on 2008-05-01
> **smile-its-smiley said:**
> How do i go about baking up my entire ubuntu system to a cd. in windows i can use system restore or back up manager i think they call it.


Sbackup is worth looking into.

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")

---

### Post by LinuxRocks713 on 2008-07-31
Or you can just DIY:

```

dd if=/dev/sda1 of=ubuntu.bin.img #where sda1 is your ubuntu partition
# and when you want to restore: (execute the following from livecd)
dd if=ubuntu.bin.img of=/dev/sda1

```

---

### Post by acidsolution on 2008-07-31
I think this will certainly help you ...

[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

---

