---
title: "how do i enable multiple monitors"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by minibeardeath on 2008-05-05
i am running ubuntu 7.10, and i would like to know how i can enable dual monitors. i have an nvidia BFG 8800 GTS 320mb (and the newest drivers). i need a short, simple, and easily repeatable method because i will be using my computer for a presentation in a few weeks, and i will not have a lot of time to set everything up. currently i have an hp l2045w as my primary, and a samsung syncmaster 152n as my (hypothetical) second monitor. i would like to be able to move a window (like firefox or something) between the monitors if that is possible. any help is appreciated. thanks

---

### Post by lemming465 on 2008-05-05
I'm not sure about moving stuff between the monitors when they aren't identical.  I can do it on a Redhat enterprise 4.6 system with an nvidia chip, but the monitors there are are identical.

If possible, upgrade to Ubuntu 8.04, because the multiple monitor support supposedly got a lot better with the newer xrandr.

---

### Post by PeterJS on 2008-05-05
The nvidia X config tool is a wonderful thing, in Hardy it can be found at System > Administration > NVIDIA X Server Settings. It does open up much too small, but if you stretch the window first thing after you open it you'll be fine.

---

### Post by energy. on 2008-05-06
run "sudo nvidia-settings" in a terminal.  

then in the window that pops up click on "X Server Display Configuration" and enable the second monitor (it'll detect it if it is connected).  the configuration that you'll be looking for is "TwinView" if you want to drag windows between the monitors.

---

### Post by minibeardeath on 2008-05-06
> **lemming465 said:**
> I'm not sure about moving stuff between the monitors when they aren't identical.  I can do it on a Redhat enterprise 4.6 system with an nvidia chip, but the monitors there are are identical.

If possible, upgrade to Ubuntu 8.04, because the multiple monitor support supposedly got a lot better with the newer xrandr.

i actually had 8.04, but i9 reverted back to 7.10 because i did not have any sound support, and my wireless was not working in 8.04, but it all works in 7.10. 

i have two monitors w/ different resolutions, is there any way to prevent programs from disappering into the non-existent space? also, is there a mode that would allow me to simply clone the desktop onto both screens?

---

### Post by minibeardeath on 2008-05-07
bump. anyone?

---

### Post by minibeardeath on 2008-05-09
bump

---

