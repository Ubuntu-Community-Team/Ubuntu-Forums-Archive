---
title: "[SOLVED] Grub issue"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by LeadHop on 2008-06-29
I just installed Hardy over my Gutsy via the update function, but i'm finding that whenever my GRUB loads at startup it gives several options to start up - there's two for hardy (normal and safe mode), two for gutsy (normal and safe mode), one for memtest and one for windows.  how do i get rid of the ones for gutsy?  the partition manager shows three partitions (two for windows and ubuntu) like it always used to, but idk why it shows up weird on startup.  ty in advance!

---

### Post by wormser on 2008-06-29
Try using startupmanager.
[FONT=monospace]
[/FONT]```
sudo apt-get install startupmanager
```

---

### Post by LeadHop on 2008-06-29
That did the trick!  thanks!

---

