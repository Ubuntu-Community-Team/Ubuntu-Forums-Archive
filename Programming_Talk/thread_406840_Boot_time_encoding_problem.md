---
title: "Boot time encoding problem"
date: 2007-04-11
forum: Programming Talk
---

### Post by andrem on 2007-04-11
Hi all,

I have the following problem in 6.06 server:

I have a program that starts at boot time. I used update-rc.d to set up its script to run at level 99. This program receives and sends messages through http connections. It receives and sends messages in UTF-8. Now... when i run this program as root, everything works fine. When I let it run from boot, special characters show up as '?' in every answer.

I suppose this must be due to some sort of locale initialization that is not set when the boot script runs, but is set when i log as root.

Any ideas where to look at?

---

