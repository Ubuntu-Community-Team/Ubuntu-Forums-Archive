---
title: "gnome classic - kb layout indicator is not indicatory"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Jessii_6 on 2011-10-11
this is a regressin as far as I'm concerned. The Keyboard indicator, which used to show the selected layout, is now showing an icon of keyboard. nice - not as useful.

---

### Post by crdlb on 2011-10-11
This works fine in upstream gnome 3 fallback, where a status icon is created by gnome-settings-daemon's keyboard plugin (with most of the work done in libgnomekbd). Prior to 10.10, Ubuntu patched gnome-settings-daemon to use [libappindicator for the keyboard layout selector]("https://bugs.launchpad.net/ayatana-ubuntu/+bug/599844"). That library uses the indicator applet on gnome 2 and similar functionality in unity's panel.

Ubuntu didn't port the gnome-panel indicator applet to gtk3, so it is not available in the fallback session. Therefore, libappindicator falls back to creating a status icon, but not the one upstream gnome would have used. So, Ubuntu either needs to port the indicator-applet, or make the indicator patches only apply within unity.

---

