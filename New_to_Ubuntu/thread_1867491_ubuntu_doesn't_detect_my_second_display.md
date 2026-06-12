---
title: "ubuntu doesn't detect my second display"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by sallam on 2011-10-23
Greetings

I have 2 screens connected to my computer through 2 wired connections to my display card (ATI Radeon 5670), one vga to hdmi connection, and the other is hdmi to hdmi connection. The first connects to an LCD monitor, and the second connects to an LCD TV, which I use to watch movies with the family. In Windows 7, when I switch on the TV, the display automatically moves from the monitor to the tv screen.

Ubuntu detects only the monitor. I tried to click the "detect displays" button found in the Display window, but the tv didn't show up.

(btw, I'm using ubuntu display driver, not ATI/AMD proprietary driver. I tried the ATI driver, but the display shrinked and big black edges showed up on all 4 screen sides, so I uninstalled it and switched by to ubuntu default driver.)

Can you suggest any solution to this problem please?

---

### Post by Redblade20XX on 2011-10-23
Do you have the proprietary drivers loaded or the open source ones? :p
- Red

---

### Post by sallam on 2011-10-23
I have the ubuntu open source one. I did install the proprietary driver but it messed up, resulting blank edges on all 4 sides of the screen, so I uninstalled it and went back to the open source driver provided by ubuntu.

A minute ago, I tried again after rebooting, and at last 2 screens showed up in "Display". But ubuntu detected my other screen wrong, silicon 36 inch. Mine is 42 inch. The display in the TV is zoomed out, ie. the display is too big, so the edges of the desktop are lost. If only I could scale it down to match the tv edges, that would be great.

Any idea how to adjust scaling for the open source driver?

---

### Post by sallam on 2011-10-24
..anyone please?

---

### Post by uriel1998 on 2011-10-24
I'm still running about on 10.04, but if you have (or can install) xrandr, the solution I [posted in this thread]("http://ubuntuforums.org/showthread.php?t=1615093") may be helpful.  I have a bash script there that works for me;  I explain the logic in [this blog post]("http://ideatrash.net/2011/10/dual-monitor-single-monitor-and-hdmi.html") if you're new to bash scripting.

---

