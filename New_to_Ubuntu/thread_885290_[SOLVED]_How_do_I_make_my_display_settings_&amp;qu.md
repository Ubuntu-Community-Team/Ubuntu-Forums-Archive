---
title: "[SOLVED] How do I make my display settings &amp;quot;stick&amp;quot;?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by vikramaditya on 2008-08-09
Everytime I start hardy, I have to go into system > administration > nvidia x server settings > x server display configuration and reset my refresh rate to "automatic" (for some reason it always loads at a seizure-inducing 56 khz).  The new settings load ok, but when I try to save them a popup informs me that it's "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.  How do I make the configuration permanent?

P.S. - There's a guaranteed "Thank You" for the first reply that works!  ;-)

---

### Post by cdtech on 2008-08-09
lol, I like your PS........

Have you tried to set the configuration within your /etc/X11/xorg.conf file?

Maybe boot into recovery mode then:
sudo dpkg-reconfigure xserver-xorg
That will reset you xorg.conf file so if all you have is a setting issue I would try the xorg.conf file first.

**P.S.**
this is the way my settings are within my xorg.conf (Monitor Section) file:
```
Section "Monitor"
    Identifier     "Generic Monitor"
    ModelName      "Custom 1"
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1152x768@54" 65.0 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
    ModeLine       "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x720@50" 60.5 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
EndSection
```

---

### Post by kaibob on 2008-08-10
Try entering the following in a terminal window:

```
sudo nvidia-settings
```

The option to "Save to X Configuration File" should then work.

---

### Post by vikramaditya on 2008-08-10
> **kaibob said:**
> Try entering the following in a terminal window:

```
sudo nvidia-settings
```

The option to "Save to X Configuration File" should then work.
By cracky, that seems to've worked!  I'm gonna reboot now & see what happens.  Thanks!

---

