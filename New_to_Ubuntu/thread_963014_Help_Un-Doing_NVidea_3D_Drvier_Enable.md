---
title: "Help Un-Doing NVidea 3D Drvier Enable"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by locbart5 on 2008-10-29
I'm running Hardy 8.04 on a Dell Insp 8200.  I just enabled my NVidea 3D Graphics driver using the Hardware Information interface. After rebooting, my display goes away (lcd goes completely dark and de-energizes) right before I get to the login prompt.  Ubuntu is still running - I can listen for the sound prompt for my username, enter it and my password, then hear the startup music for Ubuntu. This happens even when I boot in recovery mode, or from an earlier kernel.

Is there a way to get to a command prompt and disable the 3D driver during boot up?

---

### Post by fooman on 2008-10-29
if you can boot into recovery mode...choose the xfix option and see if that helps.

---

### Post by geogeer on 2008-10-29
I have a similar issue, hope you don't mind I tag along with this thread instead of starting another one.
I too enabled the Nvidia 3D driver.  I do get a login screen, visible on the monitor, but as soon as I login, I get a black screen with "out of range" on my monitor.

I read somewhere about trying ctrl+alt+[numpad - or +] to change resolutions, but it doesn't help anything...

---

### Post by phidia on 2008-10-29
> **geogeer said:**
> I have a similar issue, hope you don't mind I tag along with this thread instead of starting another one.
I too enabled the Nvidia 3D driver.  I do get a login screen, visible on the monitor, but as soon as I login, I get a black screen with "out of range" on my monitor.

I read somewhere about trying ctrl+alt+[numpad - or +] to change resolutions, but it doesn't help anything...

Try > sudo dpkg-reconfigure -phigh xserver-xorg
Let us know if that works.

---

