---
title: "Can't boot into linux"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Glurf on 2008-11-19
I've been running a dual boot of Windows XP and Ubuntu. I wish I could get rid of the xp, if only Ubuntu could run games, but that's beside the point. I reinstalled the xp, on the same partition, so I didn't touch the linux partition, and now it automatically boots into xp. I checked, the linux partition is still there, its just not giving me the option to choose what to boot. How can I fix this?

---

### Post by taurus on 2008-11-19
You just need to reinstall GRUB to MBR so you can boot either Ubuntu or windows again.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Maverick1712 on 2008-11-19
It looks like when you re-installed xp it also affected the mbr. Check out this link, it explains how to re-install grub:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

Cheers,
Adam

edit: Ah taurus beat me to it, and seems he has a better link

---

### Post by Glurf on 2008-11-20
Ah, muchas gracias. Everything works fine now

---

