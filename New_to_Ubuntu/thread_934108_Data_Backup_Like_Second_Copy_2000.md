---
title: "Data Backup Like Second Copy 2000?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by raywood on 2008-09-30
I have a data partition and an external backup drive.  I want the external drive to contain a mirror of the data partition and to keep it updated.

Ideally, it would not be an immediate, RAID-like mirror (though that would be an option if necessary).  Instead, it would check every few hours to see if anything has changed and needs to be replaced on the external drive.  I have used that external drive to retrieve changed versions of files.  It has been very helpful at times.

I don't want a black-box solution that requires me to use a program to interpret what I have on the external drive.  I want to be able to navigate to that drive in Nautilus and see directly what is there.  Sbackup is not giving me that:  the file counts between the two partitions don't match up.

I have taken several looks at rsnapshot and rsync, but I have not yet succeeded in setting them up properly for this purpose.

Any ideas?

---

### Post by garyed on 2008-09-30
I would check out cron scripts. I've just been looking into them myself but it looks like it will do exactly what you want with rsync & cron.

---

### Post by hyper_ch on 2008-09-30
rsync (with hardlinks) and cron

---

