---
title: "Computer keeps crashing"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by wd289206 on 2008-11-05
Ok, so I updated to the newest version of ubuntu yesterday afternoon. Everything seemed to be running smoothly until my computer completely froze up sometime last night. I didn't think it was a big deal, but it happened once again last night and another time this morning, and I'm not sure what the problem could be.

When it happens, the caps lock light will flicker on and off. Also, each time it's happened, I've had firefox open. If anyone has any idea what's happening, I'd like to know...

Thanks.

---

### Post by mapes12 on 2008-11-05
If you had a stable version of Ubuntu such as 8.04 or 7.10 working OK before installing 8.10 then it may be better to go back to that version until updates are available for any bugs still apparent in 8.10.

Provided you keep your /home directory on a separate partition you can try different version but still keep your files, personal settings, bookmarks and the like nice and safe.

---

### Post by nhasian on 2008-11-05
I enabled the linux-backports-modules-intrepid and no more lockups.

in a terminal type

```
sudo apt-get install linux-backports-modules-intrepid
```

> System lock-ups with Intel 4965 wireless

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.) 

---

