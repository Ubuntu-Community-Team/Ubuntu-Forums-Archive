---
title: "Graphics &quot;Mode Not Supported&quot; after boot"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by Musick Man on 2012-09-29
Hi,

My monitor broke the other day and so I had to go out and get a new one. The resolution of my old monitor and the resolution set on ubuntu is 1440x900. The new max resolution of my new monitor is 1360x768. When I select Ubuntu from the GRUB list, it shows ubuntu studio loading screen, and then goes to a message saying "Mode Not Supported" 

I can boot into recovery mode and access the recovery menu, but when I select failsafex i still get the same "Mode Not Supported" message. I can access the terminal just fine and can type in commands. 

Is there a way I can manually change the screen resolution to 1360x768 through the recovery menu or the terminal? Or to reset the resolution settings on ubuntu to 800x600? So I can at least log in?

Thank you for the help:)

---

### Post by Gone fishing on 2012-09-29
Start in recovery mode. Then pick failsafe X when you have picked this option there is a second option to reconfigure the graphics. Select that option and you should be OK.

---

### Post by Musick Man on 2012-09-29
I tried that and it flashed the terminal super fast and then went to "mode not supported" again before I could make any changes.

---

### Post by Gone fishing on 2012-09-30
Well it looks like hand editing xorg.conf, in a tty you should be able to do this. Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1975128](http://ubuntuforums.org/showthread.php?t=1975128)

---

### Post by cwsnyder on 2012-09-30
In the terminal you can also use xrandr to check what resolutions your video card supports that X knows about.  You can also use xrandr to set a new video mode and startx or /etc/init.d/lightdm to start your GUI.

The **nomodeset** kernel option is usually used to get to a 'safe' video mode, but that is if your new monitor's EDID is correctly interpreted.  This is put on the line which begins with **vmlinuz** and may be followed with **vga=792** for 1024x768 @ 60Hz 24-bit color or other modes spelled out @ [https://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](https://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

