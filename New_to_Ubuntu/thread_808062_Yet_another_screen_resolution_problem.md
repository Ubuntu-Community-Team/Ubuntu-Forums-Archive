---
title: "Yet another screen resolution problem"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by oldrocker99 on 2008-05-26
Problem solved!

I went into the /etc/X11/ directory and found a xorg.conf.backup file. I copied it to the /etc directory, renamed it to xorg.conf, renamed the misbehaving xorg.conf file, pasted the backup file into the X11 directory, restarted, and the resolution i back where I wanted it.

Pretty simple, actually...:oops:

---

