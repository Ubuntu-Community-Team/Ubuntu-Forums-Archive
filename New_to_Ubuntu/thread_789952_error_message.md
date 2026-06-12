---
title: "error message"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Sisyphus48 on 2008-05-11
Can anyone translate this error message for me?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by nynoah on 2008-05-11
you just had a problem that for some reason interrupted your updates.

when you are updating or running synaptic or apt get do not run anything else at the same time.  If you are on a slow computer it can overload the system and cause an error.

open your terminal and type this and let it run its course.

sudo dpkg --configure -a

---

### Post by Sisyphus48 on 2008-05-11
Tried what you suggested and got the following error message:
dpkg: error processing havp (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 havp

Also my computer has 4 GB of ram and an AMD Athlon 64x2 Dual Core Processor 6000

---

### Post by Nudgeworth on 2008-05-18
Thank you Nynoah :)
 I was having the same problem, and now it's fixed.
 I haven't used the terminal in a long time and I had forgotten about using sudo in front of commands lol

---

