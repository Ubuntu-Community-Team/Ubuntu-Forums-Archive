---
title: "Hard freeze on HD access"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by ib042129 on 2008-07-28
I installed Ubuntu on an older machine. I have a whole lot of hard drives on it.  Now, my problem is, that it often freezes completely. Hard freeze, no system log.  BUT. I think it does that on hard drive access.Also, for some reasons after reset, all the hard drive device names get jumbled.(Like sda becomes sdb.) Then if I reset it again, the names go back to normal.

Any suggestions?

---

### Post by mssever on 2008-07-29
> **ib042129 said:**
> I installed Ubuntu on an older machine. I have a whole lot of hard drives on it.  Now, my problem is, that it often freezes completely. Hard freeze, no system log.  BUT. I think it does that on hard drive access.Also, for some reasons after reset, all the hard drive device names get jumbled.(Like sda becomes sdb.) Then if I reset it again, the names go back to normal.

Any suggestions?
The second problem can be solved easily by using UUIDs instead of device names in /etc/fstab. That sort of situation is common in the removable device world, so the solution is there for you to use, as well.

I don't know anything about your first question. Consider this a free bump.

---

