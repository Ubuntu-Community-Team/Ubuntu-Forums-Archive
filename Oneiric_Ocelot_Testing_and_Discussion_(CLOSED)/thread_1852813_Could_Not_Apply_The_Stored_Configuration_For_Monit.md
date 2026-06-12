---
title: "Could Not Apply The Stored Configuration For Monitors"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by suprman2020 on 2011-10-01
Basically every time I log into my desktop (both Gnome-Shell and Unity), I get a message taking up half of the screen saying "Could not apply the stored configuration for monitors" along with more lines about the different settings that were tried.

I was having some issues earlier with booting the computer. It would getting stuck at initial ramdisk. Eventually I was able to fix that but lightdm was still not loading. I was able to use one of the tty to log in and somehow fix it.

This whole mess started because I was trying to use my monitor with laptop. I was able to use nvidia-settings to get the monitor to work and I saved the configuration xorg.conf. I think this is where I screwed. Can anybody help get rid of the error message?

Edit: I attached a screenshot of the window. This is much smaller than before. I reset the settings in nvidia-settings.

---

### Post by castrojo on 2011-10-01
Removing .config/monitors.xml should fix this

---

### Post by suprman2020 on 2011-10-01
> **castrojo said:**
> Removing .config/monitors.xml should fix this

You sir are a genius. You don't know how long I've been struggling with this (simple) problem. I really appreciate the help.

One more thing though. Is it possible to use the 'Displays' in System Settings rather than nvidia-settings to configure my monitor?

Once again, thank you very much.

---

### Post by castrojo on 2011-10-04
If you're using nvidia's drivers then you need to use the nvidia-settings tool.

---

### Post by i64X on 2011-10-04
I was getting this same error today after a slew of updates. Removing this file fixed the issue! Thanks!

---

