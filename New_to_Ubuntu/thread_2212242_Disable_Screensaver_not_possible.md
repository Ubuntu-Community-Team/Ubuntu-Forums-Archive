---
title: "Disable Screensaver not possible"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by UniveralRobi on 2014-03-20
Hello,

we use the Mainboard Aaeon EPIC-CV07 with a ATOM D2550. The Display is connected to the LVDS and a Touchscreen via USB.

We use Lubuntu 13.10 including the Bugfix "@/usr/bin/xfce4-power-manager &" in the **~.config/lxsession/Lubuntu/autostart**.

The problem is, we disabled all screensaver and power saver, but after a few minutes unused the System the Display Switch to black. We use firefox in Kiosk mode and we don’t like to have the black Screen. I must be run 24/7.

Any idea what we can do?

Robert

---

### Post by Dennis N on 2014-03-20
For Lubuntu 13.10, see:

[http://ubuntuforums.org/showthread.php?t=2206340](http://ubuntuforums.org/showthread.php?t=2206340)

for a solution.

xscreensaver is not installed by default in Lubuntu 13.10, so someone installed that. If installed, it can be disabled from Preferences > Screensaver > Mode = Disable Screen Saver. You could uninstall it too.

The autostart command you give looks like it would start the power manager, when you need to prevent it from starting. Why is the command there?
In any case you don't need the @ symbol in that autostart file in 13.10.

---

