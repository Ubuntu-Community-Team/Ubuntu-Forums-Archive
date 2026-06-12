---
title: "[SOLVED] If I make my linux partion bigger, will fsck  take longer?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-05-25
I am filling up my Ubuntu partition, but I want to know if fsck will take longer, if I wipe out XP and expand that partition before I do it.

---

### Post by sdennie on 2008-05-25
Yes, it will.  But, if you are using something like ext3, it should only be running fsck every 30 boots or so.

Edit:
That's not completely true.  It will run fsck on every boot but, that should only take a noticeable amount of time around every 30 boots.  Making the partition larger won't have any noticeable effect on normal boot times.

---

