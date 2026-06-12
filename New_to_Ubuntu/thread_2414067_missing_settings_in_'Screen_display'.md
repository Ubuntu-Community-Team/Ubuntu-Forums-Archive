---
title: "missing settings in 'Screen display'"
date: 2019-03-05
forum: New to Ubuntu
---

### Post by vin0209 on 2019-03-05
Hi, I am trying to set up a second monitor from my Dell G5 (2018). However, there seems to be no way to do so. It only shows 'built-in screen display' in 'Setting->Devices->Screen Display'

The output of ```
xrandr
```:
```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080    120.00*+  60.01    59.97    59.96    59.93  
   1680x1050     84.94    74.89    69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     85.00    74.76    70.00    59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     85.02    75.02    60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      85.00    60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864     100.00    85.06    85.00    75.00    75.00    70.00    60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      85.00    75.05    60.04    85.00    75.03    70.07    60.00  
   1024x768i     86.96  
   960x720       85.00    75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   832x624       74.55  
   960x540       59.96    59.99    59.63    59.82  
   800x600       85.00    75.00    70.00    65.00    60.00    85.14    72.19    75.00    60.32    56.25  
   840x525       85.02    74.96    69.88    60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       85.08    74.76    70.06    59.98  
   800x450       59.95    59.82  
   640x512       85.02    75.02    60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       85.09    60.00    85.01    72.81    75.00    59.94  
   720x405       59.51    58.99  
   720x400       85.04  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98    85.08  
   576x432      100.11    85.15    85.09    75.00    75.00    70.00    60.06  
   640x360       59.86    59.83    59.84    59.32  
   640x350       85.08  
   512x384       85.00    75.03    70.07    60.00  
   512x384i      87.06  
   512x288       60.00    59.92  
   416x312       74.66  
   480x270       59.63    59.82  
   400x300       85.27    72.19    75.12    60.32    56.34  
   432x243       59.92    59.57  
   320x240       85.18    72.81    75.00    60.05  
   360x202       59.51    59.13  
   360x200       85.04  
   320x200       85.27  
   320x180       59.84    59.32  
   320x175       85.27  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
```

what I tried:
- select 'workspaces span displays' in Gnome Tweak Tools
- ```
arandr
```

---

### Post by Autodave on 2019-03-05
Have you installed the Nvidia driver?  If so, what one and where did you get it from?  If you have installed a driver, then go into the Nvidia control and choose your second monitor.

Also, are you sure that your cable is good?  I have also seen more than a few laptops where the display port has failed.

---

### Post by oldrocker99 on 2019-03-06
> **Autodave said:**
> Have you installed the Nvidia driver?  If so, what one and where did you get it from?  If you have installed a driver, then go into the Nvidia control and choose your second monitor.

Also, are you sure that your cable is good?  I have also seen more than a few laptops where the display port has failed.

Yes, this is true. **Any** cable can faIl, even ones that have stayed in the same position for a long time. External hard drives' cables can scare you, when the drive suddenly cannot be mounted, as has happened to me. Replace the cable, as I did, and all was swell.

---

