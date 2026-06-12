---
title: "Quick mounting question?"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by ylafont on 2013-12-07
My Media Center PC auto mounts my NAS Volumes on startup via FSTAB.   This work as expected without any issues.  I wanted to add to a few lines the FSTAB file the command to mount a some ISO located on one of the NAS Volumes.  However I got some errors stating the files was not available. I am assuming that the NAS volumes has not fully mounted which is why I got errors.
is there a preferred method for me to accomplish this?  thanks

---

### Post by tgalati4 on 2013-12-07
Does this work?

Open a terminal:

```
sudo mount -a
```

If so, then presumably you have a timing issue with mounting.  In that case you would want a mount statement for the ISO in your /etc/rc.local or /etc/bootmisc.sh or any other place that gets called after the system fstab mounts.

If *mount -a* shows some errors then you would need to fix them first.

---

### Post by ylafont on 2013-12-07
Argh!  

No errors i had test the commands with the same command proir. Guess I will have to place in rc.local

thanks for the reply,

---

### Post by DuckHook on 2013-12-07
Also consider [*autofs*]("https://help.ubuntu.com/community/Autofs").

---

