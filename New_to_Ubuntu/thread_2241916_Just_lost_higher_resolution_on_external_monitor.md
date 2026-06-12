---
title: "Just lost higher resolution on external monitor"
date: 2014-08-29
forum: New to Ubuntu
---

### Post by lesliek2 on 2014-08-29
I'm using version 12.04 on a laptop with an external monitor connected. Things are set up so that only the external monitor displays. The laptop screen is blank. After accepting new updates this morning, I find that my external monitor is only displaying at 1600x900 instead of at 1920x1280, the way it was before the updating.

When I run xrandr, I get:

Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
VGA-0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x900       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
LVDS connected (normal left inverted right x axis y axis)
   1600x900       60.1 +
   1440x900       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4

When I open /usr/share/X11/xorg.conf.d/10-monitor.conf, I get:

Section "Monitor"
  Identifier "Monitor0"
  Modeline "1600x900"  119.00  1600 1696 1864 2128  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "VGA-0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1600x900"
  EndSubSection
EndSection

According to my feeble understanding, I need to amend the 10-monitor.conf file to include information about device LVDS.

Is that right?

If so, is there some simple guide that I can follow to find the correct information to add and to add it in the correct way?

Thanks,

Leslie

---

