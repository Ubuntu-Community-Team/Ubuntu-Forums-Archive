---
title: "Ubuntu logo doesn't appear on boot screen"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by denitroid on 2008-09-18
Whenever I start up Ubuntu the boot screen doesn't appear. It boots up perfectly but I'd like to fix this for aesthetic purposes. I have a Dell Dimension 2350 with integrated Intel graphics and Windows dual boot. Help would be much appreciated thanks :biggrin: !

---

### Post by MegaJim on 2008-09-18
What do you see? Can you see a textual boot up process, or is the screen just blank?

---

### Post by bobnutfield on 2008-09-18
Check your /boot/grub/menu.lst file and make sure the kernel line says "splash" and "quiet" at the end.  Also, have you installed the KDE4 desktop alongside Gnome?  If so, many find that the boot splash no longer works correctly after installing KDE4.

---

### Post by jpeddicord on 2008-09-18
> **bobnutfield said:**
> Check your /boot/grub/menu.lst file and make sure the kernel line says "splash" and "quiet" at the end.  Also, have you installed the KDE4 desktop alongside Gnome?  If so, many find that the boot splash no longer works correctly after installing KDE4.

More specifically, the kubuntu-desktop package might overwrite the boot splash. KDE itself won't mess with it.

@OP: Try the steps in the above post, and also make sure the usplash-theme-ubuntu package is installed (and reinstall it if necessary) from system > administration > synaptic.

---

### Post by bobnutfield on 2008-09-18
> **jacobmp92 said:**
> More specifically, the kubuntu-desktop package might overwrite the boot splash. KDE itself won't mess with it.

@OP: Try the steps in the above post, and also make sure the usplash-theme-ubuntu package is installed (and reinstall it if necessary) from system > administration > synaptic.

Yes, thank you for clarifying that.  The exact same occurred for when I installed KDE4 along side Gnome, which of course required installing the Kubuntu-Desktop packages.  I have never been able to restore the splash at boot, but it is of no consequence to me.  I am fine without it and actually prefer seeing what is being loaded.

---

### Post by denitroid on 2008-09-18
No I do not have KDE along-side gnome and the boot screen was visible when I first booted for the Ubuntu installer.

---

