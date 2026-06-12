---
title: "[SOLVED] Backing up my system"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Nxion on 2008-04-30
Hi,

I am curious to know about backup for Ubuntu as I have never done them before. Well I have never done backups in Linux period.

My questions is there a way to back up the entire hard drive to lets say a NAS and after that have it do incremental after that, then if something happens to my laptop, restore it back ?  Either from the full image or one of the incremental backups ?

Thanks in advance.

---

### Post by scragar on 2008-04-30
[how to back-up and restore your system](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Nxion on 2008-04-30
I did see that article. But I still would like to know if it is possible to do incremental backups after a full one is created.

---

### Post by scragar on 2008-04-30
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

sbackup works for that, although there is a bug report on the fact that to truely restore the system you have to restore all of the backups, starting with the most recent full backup to current. Be aware of that before you start using it.

---

### Post by Nxion on 2008-09-30
thanks for the help on this

---

