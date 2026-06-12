---
title: "No signal on hdmi on startup of Ubuntu 18.04"
date: 2018-08-29
forum: New to Ubuntu
---

### Post by samoorelex on 2018-08-29
I have a logic supply computer with an Intel graphics chip.
The display and cable are ok as they  work fine with my Mac.
When I boot the computer all I get is no signal.
Temporarily I've setup a vga alongside and viola it displayed as the secondary display.
I switched it to make the hdmi the primary in settings.
As long as I have the VGA plugged in, the hdmi will start up fine.
If I remove the connection I get no signal from the display.

Here is my xrandr settings:
samoore@samoore-PD10BI:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-1 connected (normal left inverted right x axis y axis)
   1366x768      59.79 +
   1280x1024     60.02  
   1280x960      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
   720x400       70.08  
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+  59.94    30.00    24.00    29.97    23.98  
   1920x1080i    60.00    59.94  
   1280x1024     60.02  
   1360x768      60.02  
   1152x864      59.97  
   1280x720      60.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08  

Thanks for any help

---

