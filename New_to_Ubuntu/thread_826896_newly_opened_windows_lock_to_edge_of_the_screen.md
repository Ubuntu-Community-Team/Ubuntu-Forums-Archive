---
title: "newly opened windows lock to edge of the screen"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by mo.reina on 2008-06-12
everytime i open an application, the window opens up at the edge of the upper left corner.  how do i get this to stop?  it's quit annoying, not to mention that i had to autohide the upper panel so that i could access the window's titlebar and move it.

---

### Post by Joeb454 on 2008-06-12
Go to System > Preferences > Appearance

Check the desktop effects settings, what are they set to?

---

### Post by _sphinx_ on 2008-06-12
Actually I don't know how to stop windows to start at top left but you can also move the window easily by hitting alt+F7 and moving, without autohiding.

---

### Post by mo.reina on 2008-06-12
you mean the visual effects tab?  non are highlighted, i think because i'm running compiz-fusion with emerald

---

### Post by Joeb454 on 2008-06-12
Do you have the CCSM installed? If you do it would be System > Preferences > Advanced Desktop Effects.

Go into there, and there's an option about snapping windows to the edge of your screen, you most likely want that disabled :)

If you don't have the above installed, open a terminal and run ```
sudo apt-get install compizconfig-settings-manager
``` Hope that helps :)

---

### Post by BDNiner on 2008-06-12
Yes there is also an option called "Place Windows" that lets you specify where windows open on the screen. mine is currently set to centered for all windows.

---

