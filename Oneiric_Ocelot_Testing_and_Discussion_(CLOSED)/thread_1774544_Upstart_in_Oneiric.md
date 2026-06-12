---
title: "Upstart in Oneiric?"
date: 2011-06-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xeizo on 2011-06-03
Is there any easily manageable way to REALLY control what services/jobs starts in Oneiric?

It looks like a mess with scripts spreadout under /etc/init, /etc/init.d and /etc/rcN.d

Mess enough that bootup nowadays displays warning messages about old scipts moved to upstart jobs but still being there, how to get rid of those messages?

I'm curious  :)

---

### Post by wnelson on 2011-06-04
I use sysv-rc-conf for /etc/init.d config's. I simply move any .conf files from /etc/init to /root and that disables those services. Read the config files to see what they do and if you feel that you don't need them either sysv-rc-conf to disable them or move any /etc/init file. You and always re-enable or move them back.

---

