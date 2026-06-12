---
title: "Help: error: failure reading *hexadecimal* from &quot;hd0&quot;"
date: 2015-10-25
forum: New to Ubuntu
---

### Post by darkhelmet2 on 2015-10-25
Hi,

New linux user here. I've got an old computer running windows xp that I'm trying to install lubuntu 14.04 on. I did the install then rebooted, but on startup I got the message "error: failure reading *some hexadecimal* from "hd0" ", then grub rescue started up. I tried running boot repair to no avail (it didn't even offer the option of repairing it). Here is the paste url: [http://paste.ubuntu.com/12950645/](http://paste.ubuntu.com/12950645/) . I searched the forums and  hard drive failure kept coming up, which I really hope isn't the case. Could someone please help me figure this out?

Thanks!

---

### Post by Vladlenin5000 on 2015-10-25
Hi and welcome.

It's an hardware failure in almost all certainty and that is exactly what should be expected with old hardware.
There's a GUI utily - Disks - you can use in a live session booting from the installation media as you did to install (tip: in top right corner, the icon made of 3 parallel horizontal lines is the Menu button; choose the option SMART and, in the emerging dialog/window you'll find the button to choose and start the HDD tests in the lower left corner).

---

### Post by sandyd on 2015-10-25
As Vladlenin5000 noted above, it is likely filesystem corruption.
If you need to recover data, see [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

