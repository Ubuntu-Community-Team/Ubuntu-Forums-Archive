---
title: "Internal card reader can cause excessive disk access"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by silkstone on 2008-06-25
Mods - in a way this is a duplicate thread, but I thought it could be worthwhile to post a specific warning.

I've been trying to trace the cause of regular disk access - every few seconds - when idle. It turned out that kern.log was updating every second, and the cause was an internal card reader that I fitted last week.

If anyone else has a similar problem, it may be worth checking this. The original thread with a dump from kern.log is at...

[http://ubuntuforums.org/showthread.php?t=839313](http://ubuntuforums.org/showthread.php?t=839313)

---

