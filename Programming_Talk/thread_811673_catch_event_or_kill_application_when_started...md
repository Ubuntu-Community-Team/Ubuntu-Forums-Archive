---
title: "catch event or kill application when started.."
date: 2008-05-29
forum: Programming Talk
---

### Post by atheistkun on 2008-05-29
hi,
i wish 2 write a program to prevent user from starting an application say firefox during a time period. 

how can i catch the event when the application is started? one way is to check every minute/second using pgrep or ps. 

Is there any other better way?

---

### Post by jsmiith on 2008-05-29
Another way would be to use chmod to turn off/on its executable permissions.

---

### Post by Zugzwang on 2008-05-29
> **jsmiith said:**
> Another way would be to use chmod to turn off/on its executable permissions.

It really depends on how good the solution is intended to be.
The idea above is ok, but can be circumvented pretty easily (copy firefox to the temp directory and then use chmod to get executable permission again). The ps version of the OP can be circumvented similarly. Also, no one can prevent one from downloading & compiling firefox (provided that either file copying onto pen drive or internet access is possible).

The usual way here is to restrict a user by using chroot to some special environment and then mapping the respective part of the system to this environment.

---

### Post by barnex on 2008-05-29
Setting permissions is probably the best way, but if you really want to kill firefox, you could just execute:
```

killall firefox

```
you can do this every minute, e.g., by adding this line to the root's crontab.

---

