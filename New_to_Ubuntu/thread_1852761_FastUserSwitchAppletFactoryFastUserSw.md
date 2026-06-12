---
title: "FastUserSwitchAppletFactory::FastUserSw"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by dsmo223 on 2011-09-30
I am getting the following error occasionally when booting into Ubuntu.

The Panel encountered a problem while loading FastUserSwitchAppletFactory::FastUserSwitchApplet

When this happens, I loose my shutdown button, and have to manually add it back to the top panel. 

I am using Ubuntu 11.04, but in classic mode (GNOME display). Does anybody know what is causing this, and if so, how to fix it? Thank you.

---

### Post by jtarin on 2011-09-30
Try this command in a terminal to have GDM reconfigure itself and let me know if it helps.

sudo dpkg-reconfigure gdm

---

