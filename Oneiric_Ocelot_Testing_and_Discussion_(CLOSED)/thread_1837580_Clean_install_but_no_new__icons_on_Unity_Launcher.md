---
title: "Clean install but no new  icons on Unity Launcher"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cor2y on 2011-09-02
So i did a clean install on this test machine that was running 11.04  but left my /home partition untouched only formatted root to 11.11 beta 1, it went well, but the icons on unity launcher are the same that was in 11.04 for example the software center icon is still the same one from 11.04 rather than the new 11.10 one.
Obviously since i didnt replace the /home partition theres some setting in there that has the Launcher Displaying the old icons from 11.04, if i launch the Dash the icons are different.
Anyone know how to reset the icons to the current ones that are showing on the Dash?

---

### Post by cariboo on 2011-09-02
You could try:

```
unity --reset-icons
```

but be warned that the command will also remove any icons you've already placed in the launcher.

---

### Post by cor2y on 2011-09-02
Yep tried that nothing happened and then i tried unity --reset the last one temporarily reset unity and the icons  but when i logged back in the old icon was there again

---

### Post by mc4man on 2011-09-02
For S-C you might want to try removing the icon from the launcher, log out/in.
Then start S-C, either from /usr/share/applications, Dash or Alt+f2
For Alt+f2 use
software-center-gtk3

Then pin to launcher..

---

### Post by jbicha on 2011-09-02
The new software-center didn't completely replace the old one just in case the new one didn't work out well enough. The naming will be fixed before final release.

---

### Post by Bowmore on 2011-09-02
The reason is that the icon /usr/share/icons/hicolor/scalable/apps/softwarecenter.svg has not been updated to the new one yet and thus the new software center icon only pops up in the launcher when that icon is not used, i.e for launcher sizes 46-50

Bug: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/835798](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/835798)

---

### Post by Bowmore on 2011-09-02
Here's a workaround
```
sudo cp /usr/share/icons/hicolor/48x48/apps/softwarecenter.svg /usr/share/icons/hicolor/scalable/apps/softwarecenter.svg
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```

---

### Post by cor2y on 2011-09-02
Thanks Bowmore that did the trick

---

