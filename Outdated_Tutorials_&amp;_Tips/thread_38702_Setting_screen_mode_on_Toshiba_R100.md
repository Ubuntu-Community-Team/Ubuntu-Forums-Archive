---
title: "Setting screen mode on Toshiba R100"
date: 2005-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by birnbacs on 2005-06-01
All,


I am using kubunto 5.04 on a Toshiba R100. Have read about tricky display problems with Debian, but don't see the need to exchange the driver or put up with 8 bit colors. Here is what happens:

When I power the laptop on, I am in about 4 bit colors. Accessing the control panel is a pain. I then log in and select the display control panel to change from 1024 X 768 to any other resolution and activate the change. Seeing the confirmation window, I click **Cancel**, which returns me to 1024 x 768 pixels, but this time everything is in (estimated) 16 or 24 bit depth. Hip-Hip-Hurrah! Only visible change in the panel is that the picture frequency has changed from 61 to 0 Hz. If I could make this setting permanent, I'd be all happy.
For a start, how can I retrieve the precise current video settings? Have tried xorgcfg (messy) and fbset (no /dev/fb* device) so far. How then can I activate changes without having to reboot the machine? CTRL-ALT-BACKSPACE sure kills XOrg, but how can I restart it with all the KDE and stuff?


    Thanks, Sebastian

---

### Post by ?rious on 2006-01-19
Anyone using vesa drivers on their r100 (advisable considering the speed of the trident drivers) need only press Ctrl-Alt-F1 then Ctrl-Alt-F7 at the GDM. It has the same effect at this guy's suggestion, but less hassle.

---

