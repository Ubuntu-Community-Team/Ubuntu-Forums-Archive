---
title: "Backup software for NAS"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by steve57 on 2013-10-08
Hi! Could you recommend me a software to back up a NAS. I`ve found an utility ([Handy Backup]("http://handybackup.net/what-is-nas-storage.shtml")), and I don`t know whether I'm coming the right path.
Share your experience please.

---

### Post by Lars Noodén on 2013-10-08
I would use plain [rsync](https://help.ubuntu.com/community/rsync).  It has many provisions for copying and is fast and reliable.  If you look at the advanced settings you can even make it do incremental backups.

---

### Post by steve57 on 2013-10-09
Many thanks Lars Nooden.

---

### Post by Bucky Ball on 2013-10-09
I use Luckybackup myself. Front end for rsync as far as I know.

Handy Backup looks third-party and like it costs (or a free demo). LuckyBackup is in the repositories and is free.

PS: Update: Handy Backup is not for Linux by the looks of it. Are you actually running Ubuntu? Or Linux?

---

