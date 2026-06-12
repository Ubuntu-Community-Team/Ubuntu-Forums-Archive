---
title: "Uninstall 6.06"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by bounderkirk77 on 2008-06-18
How to completely and cleanly remove 6.06? Then, I can install 8.04  from the cd, bypassing interim steps.

---

### Post by Pjotr123 on 2008-06-18
This is an easy way:
[http://ubuntutip.googlepages.com/reinstall](http://ubuntutip.googlepages.com/reinstall)

---

### Post by cariboo on 2008-06-18
Boot up your computer with the liveCD then in a terminal type:

```
sudo dd if=/dev/zero of=/dev/hda bs=1M
```

that will write all zero's to your hard drive. Make sure to change /dev/hda to what ever partiton and drive Ubunutu is on.

[COLOR="Red"]CAUTION THIS WILL OVERWRITE ALL DATA ON THE CHOSEN HARD DRIVE[/COLOR]

Jim

---

### Post by Butthead on 2008-06-18
Hmm, I just threw the DVD in the drive, and let the software do it.

There is a menu option (if I remember?) about completely erasing the HD and installing the new OS.

Seems to be working okay, no problems so far...:confused:

---

