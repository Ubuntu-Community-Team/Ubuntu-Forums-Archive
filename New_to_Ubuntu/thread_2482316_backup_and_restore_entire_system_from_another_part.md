---
title: "backup and restore entire system from another partition not usb."
date: 2022-12-28
forum: New to Ubuntu
---

### Post by tenet246 on 2022-12-28
Hi guys, I am trying to backup the system and restore it when the system failed. The backup will be stored in another partition and the failed partition will restore by the backup image automatically. Please help me with the procedure...

I tried by using dd and rsync, but not working.

Thanks.

---

### Post by sudodus on 2022-12-28
I suggest that you try with [Clonezilla](https://clonezilla.org).

See also [this link](https://askubuntu.com/questions/958242/fastest-way-to-copy-hdd/958248#958248).

---

### Post by yancek on 2022-12-28
Not sure how you plan to do this but if it is backing up to another partition on the same disk, I would think that is not a good idea.  If the disk fails, you have no reason to expect only one partition will fail.  If you mean another partition on another disk, use clonezilla as suggested.

---

