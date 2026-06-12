---
title: "what if i don't make a home partition?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-09-23
will my user and settings be stored in the root partition?

---

### Post by RequinB4 on 2008-09-23
Yes.  In effect, you could just create a / partition and on that partition would be everything - /home is just a folder in the / partition.  Putting /home in its own partition just tells to mount the "home" partition as the "/home" folder in the / partition

In other words, it's fine.

---

### Post by OutOfReach on 2008-09-23
Yes if you don't make a /home partition everything will be stored in the root partition. It's perfectly fine not to have a /home partition, alot of people don't (including me).

---

### Post by jemate18 on 2008-09-23
/home partition if not created in the partitioning part of the installtion will simply be inside the /

Having a separate /home is  suggested since having it in another partition will make it easier to backup and when changing distros, you can opt out not to wipe out your home partition, so that even if you change distro, your data is still there

---

