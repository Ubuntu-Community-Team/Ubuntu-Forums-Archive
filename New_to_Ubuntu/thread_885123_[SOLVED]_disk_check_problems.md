---
title: "[SOLVED] disk check problems"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Zopiac on 2008-08-09
when loading the disk check thingy at reboot, at the usplash, i run into problems. it says a bunch of stuf i cant exactly remember, but inclused i need to do some sort of...manual fsck? i dont know what to do :( what does the disk check DO anyways that benefits me? i only know of it as a time consumer and NOW it is a problem...if it doesnt do much of a benefit, how do i disable it?

---

### Post by Diabolis on 2008-08-09
You do need it, as it will check and repair your file system.

Probably this happens when you boot up, a message that says "maintenance shell" shows up.

Just type:
```
fsck -y
```

When done press <Ctrl>D to finish the maintenance shell and the boot up should continue.

---

### Post by InfinityCircuit on 2008-08-09
To force a one-time fsck on boot, you can do this:

sudo touch /forcefsck

If this doesn't work either, you will need to boot a rescuecd and try using fsck from there.

---

