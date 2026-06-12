---
title: "How to set the resolution of a second monitor"
date: 2014-12-01
forum: New to Ubuntu
---

### Post by MaxiPigna on 2014-12-01
I connected a monitor to my laptop, but I can not set the recommended resolution 1280x1024 because it is not listed in the display settings. What is the easiest and safest way to add it?
The second monitor is connected by using a HDMI adapter to a VGA plug.
```
$ xrandr | grep -e " connected [^(]" | sed -e "s/\([A-Z0-9]\+\) connected.*/\1/"LVDS1
HDMI1

```

---

### Post by nerdtron on 2014-12-01
> The second monitor is connected by using a HDMI adapter to a VGA plug.
There is a max cable length and resolution on a VGA cable.

---

### Post by MaxiPigna on 2014-12-01
What do you mean? I am pretty sure that if I add that resolution it works. I used it for years!

---

### Post by MaxiPigna on 2014-12-01
I made this test and it worked. 
```
$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
$ xrandr --addmode HDMI1 "1280x1024_60.00"
$ xrandr --output HDMI1 --mode "1280x1024_60.00"
```
Now I do not know how to change the xorg file to save permanently the changes. This is my current xorg file.
```

Section "ServerLayout"
    Identifier "amd-layout"
    Screen 0 "amd-screen" 0 0
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    Option "AccelMethod" "uxa"
    BusID "PCI:0@0:2:0"
EndSection


Section "Device"
    Identifier "amd-device"
    Driver "fglrx"
    BusID "PCI:1:0:0"
EndSection


Section "Monitor"
    Identifier "amd-monitor"
    Option "VendorName" "ATI Proprietary Driver"
    Option "ModelName" "Generic Autodetecting Monitor"
    Option "DPMS" "true"
EndSection


Section "Screen"
    Identifier "amd-screen"
    Device "amd-device"
    Monitor "amd-monitor"
    DefaultDepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by coldcritter64 on 2014-12-01
Only yesterday I posted this suggestion for a script and start up entry to always set the resolution [[COLOR=#0000ff]--in this post--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2254520&p=13177921#post13177921")

That was for an xfce DE to always set the resolution using similar commands as yours every session log in. 

Not a proper xorg.conf file entry, but will do the job on each start up for setting a resolution. Adapt the script for your hardware identifiers and other values to suit your install if you try this method.

If you specifically require the changes set in the xorg.conf file, wait for further responses.

---

### Post by MaxiPigna on 2014-12-02
Thank you for your suggestion. If I will not find a way to change the xorg file, I think this is the only solution.

---

