---
title: "GeForce4 MX 4000 AGP 8x not suport"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by heckarim on 2008-05-16
i have AGP card and the vga onboard (NV18 [GeForce4 MX 4000 AGP 8x]). When i set primary onboard vga, i have no problem for "startx". When i set primary PCI card, i can't get in Ubuntu. it stop at waitting screen and nothing happen. When i get in recover mode, there is error (loop with no end) at restricted driver step. So, what i can do to slove this problem? Please help me.
(Sorry, i don't good at english).

---

### Post by ukripper on 2008-05-16
I have got this card in my ubuntu server and had no problem with startx.

---

### Post by Sef on 2008-05-16
Moved to Absolute Beginners.

---

### Post by heckarim on 2008-05-18
Thank for reply, now i think it's ok (just one problem). I have primary onboard, set up monitor to Nvidia card, reinstall envy, install nvidia driver, enable restricted driver. And i configure: sudo dpkg-reconfigure xserver-xorg. Now, when i turn on my computer, Nothing in my monitor for 60 seconds. After that, there is logon screen of Ubuntu.
 This is one problem but it isn't troublesome.
 (If i have primary Nvidia card and disable onboard, Ubuntu not overcome the step "restricted driver").

---

