---
title: "Screen resolution Part II"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by yoramdavid on 2008-10-21
Hi, I wanted to edit my last post on Screen resolution, but could not. Perhaps it is too old. It can be found here, nothing changed on my architecture:
[http://ubuntuforums.org/showthread.php?t=401613](http://ubuntuforums.org/showthread.php?t=401613)

I have recently updated from Ubuntu 7 to Ubuntu 8.04 and if before I struggled to have a higher screen resolution to work, now after the update, Ubuntu starts with a screen resolution of 2048 X 1536 (the maximum the screen can have!) and a painful refresh rate of 60 Hz. I would like to have a screen resolution of 1280 X 1024 @ 80 Hz so I can read without a magnifying glass.
When I change to a lower resolution, the screen fills with scan-lines and I cannot see a thing. Rebooting or pressing Ctrl+Alt+Backspace makes it to go back to the original resolution (2048 X 1536).

I noticed in the xorg.conf that these words were added after each screen modeline line: "-hsync +vsyn"
Example:
modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync

:confused:

Yoram David

---

### Post by dcstar on 2008-10-21
> **yoramdavid said:**
> 
.........
I have recently updated from Ubuntu 7 to Ubuntu 8.04 and if before I struggled to have a higher screen resolution to work, now after the update, Ubuntu starts with a screen resolution of 2048 X 1536 (the maximum the screen can have!) and a painful refresh rate of 60 Hz. I would like to have a screen resolution of 1280 X 1024 @ 80 Hz so I can read without a magnifying glass.
.........


Leave the native screen resolution as it should be and increase the default font sizes in: System-Preferences-Appearance-Fonts

---

### Post by yoramdavid on 2008-10-23
> **dcstar said:**
> Leave the native screen resolution as it should be and increase the default font sizes in: System-Preferences-Appearance-Fonts

Thank you for the reply.
That solved some visual problems for now, but not all and the screen resolution is still at 60Hz :( and the computer slow... 
Now after I rebooted, the computer booted with the resolution of 1280 X 1024 which is the one I wanted... but where it came from now? I says it is at 50Hz thought, but it looks to me it is at more, perhaps at 80Hz

Yoram David

I am now getting the welcome screen zoomed in, I can barely see the form where I have to put my username and password. It is at the right-bottom corner of the screen now. Any idea how to get that right? The rest seems good. :)

---

