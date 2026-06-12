---
title: "Dual Monitor Support"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by alexmasis on 2013-10-09
Hi, I have on Ubuntu 12.04 and I have 2 external monitors connected via port replicator, the laptop monitor is not used.
The 2 monitors are mirrowed fine, but I can't **extend** the display, as I was able to do before I loaded all latest updates...
Here are some details about my setup:

# ***lspci | grep VGA***

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

#*** xrandr***
Screen 0: minimum 320 x 200, current 1680 x 1200, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+   74.9  
   1600x900       60.0  
   1280x1024      75.0     72.0     60.0  
   1440x900       75.0     59.9  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 367mm x 275mm
   1600x1200      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

In the "Settings/Settings Manager/Display" I have selected to use the output for 2 external monitors, the laptop monitor is not used.

# *** lsb_release -a***
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


I also tried the disper app, but it has an error:
 ***#disper -e***
There is no matching crtc for the output

---

### Post by oldos2er on 2013-10-09
Moved to Absolute Beginners.

---

### Post by newb85 on 2013-10-09
And if you un-check the "Mirror Displays" box in Displays, it doesn't accomplish what you want?

---

