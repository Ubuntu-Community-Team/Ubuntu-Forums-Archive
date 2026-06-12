---
title: "Screwed up my X Setup"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by rayboston on 2008-10-26
Hi Folks,

This morning I found my monitor complaining that it did not support the resolution that Ubuntu wanted for the login screen.  I don't know why this changed, but I figured I'd fix it by installing the right driver for my monitor.

I installed the driver for my Dell E196FP and selected the 1280x1024 resolution.  This worked, but the performance was terrible so I tried to go back to the PlugnPlay driver.

Now I'm hosed.  When I log into Ubuntu, I cannot see the menu bar at the top, or the icon tray at the bottom.  Just the crane.  I suspect that the monitor and the software have different ideas about how big the monitor is.

I just want to get back to where I started.  Do you have any suggestions on how to restore X to its original state?

Thanks!

Ray

---

### Post by ibuclaw on 2008-10-26
Reboot your computer and select the Recovery Mode.

When Ubuntu boots into runlevel 1, select "Fix X" in the console menu screen. Then continue normal boot.
The rest you can setup once you have a functional GUI again.


Regards
Iain

---

### Post by rayboston on 2008-10-26
Hi Iain,

Thanks.  I tried that, but it didn't do the trick.  However, I've come to the conclusion that this is not a monitor problem.  Instead, I think I have messed up my GNOME installation (no idea how.) 

I'm going to open a new thread in that direction.

---

