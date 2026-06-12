---
title: "NVIDIA X SERVER (How to get separate screens working?)"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by leotemp on 2008-05-01
I got twinview working but this shares the desktop which means full screen apps stretch across both screens and my menu items are on the wrong monitor, i know i can just move the menus but i would like to be able to full screen the left monitor for movies, apps or whatever and twinview doesn't appear to be the right way to do this. So i tried the next option "separate X screen" but when i enable this and reboot it never activates the second screen the way that twinview would (the monitor is not receiving a signal) so whats the secret?

Also, how do i specify the driver for my second monitor so i can set a higher rez then 640x480?

---

### Post by conehead77 on 2008-05-01
You need to edit your xorg.conf manually. I had it working as you described in Gutsy without modification, but Hardy needed the xorg edit.

Look at the Screen section and add a metamodus like i did in my xorg:
```
Section "Screen"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
# Removed Option "metamodes" "CRT: 1280x1024 +0+0, DFP: 1600x1024_60 +1280+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
[COLOR="MediumTurquoise"]    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 1650x1050_60 +1280+0"[/COLOR]
EndSection
```
I added the colored line (it was removed by the nvidia-settings tool). Obviously you have to change the data to match your screens/resolution.

Good luck!

---

