---
title: "GNOME Desktop Manager fails on start up"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by DarchAengel on 2008-08-21
My gf is going to kill me.  I was trying to help her get some stuff install on her comp but when I went to restart because things were hanging I get a fail on start up where GNOME Desktop Manager is concerned.  I tried running xorg and I ran recovery mode and chose repair pkgs.  Neither one of them worked.  Any help would be greatly appreciated.

---

### Post by meanburrito920 on 2008-08-21
what is the error it gives you (when X crashes)?

---

### Post by DarchAengel on 2008-08-21
When I boot the comp up I get the opening Ubuntu splash with the orange meter.  It then switches to a text boot.  Everything comes up with [OK] except GNOME Desktop Manager where I get a red [fail].  Then it goes to a text login.  I tried running startx but when I do it tells me that it is waiting for X server to shutdown FreeFontPath: FPE "usr/share/fonts/x11/misc" ref count is two should be one : fixing.

---

### Post by meanburrito920 on 2008-08-21
Kill xserver (do a ps -e to find the pid) and gdm if it's running.

then try startx

---

### Post by DarchAengel on 2008-08-21
I ran ps -e and neither xserver nor gdm is running.

---

### Post by rodh on 2008-08-22
I had simular problem earlier this month,  I reinstalled gdm and am back to normal.

---

### Post by DarchAengel on 2008-08-22
Could you help walk me through how to re-install gdm?  I tried running apt-get update after I login and I get a bunch of errors.  I think this problem may be a symptom of something much more severe.

---

