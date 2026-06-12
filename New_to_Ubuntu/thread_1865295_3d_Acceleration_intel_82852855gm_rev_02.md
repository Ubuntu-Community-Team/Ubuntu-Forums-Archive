---
title: "3d Acceleration intel 82852/855gm rev 02"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by cwkooistra on 2011-10-19
Hey all, I just installed Xubuntu on my Dell Inspiron 1150.  Running perfectly, except for the lack of 3d acceleration.  I understand that the machine and its hardware are old, probably dating to 2004 or 2005.  However, I was wondering if there was an off chance it was possible to enable 3d acceleration.
Relevant result of lspci

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

### Post by cwkooistra on 2011-10-20
Fairly simple fix.  Added the xorg-edgers ppa, ```
sudo add-apt-repository ppa:xorg-edgers && sudo apt-get update
``` updated and rebooted.  Now I have 3d acceleration.  My apologies to the mods for the duplicate post.

---

