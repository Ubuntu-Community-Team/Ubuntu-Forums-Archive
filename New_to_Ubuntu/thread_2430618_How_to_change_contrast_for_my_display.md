---
title: "How to change contrast for my display?"
date: 2019-11-04
forum: New to Ubuntu
---

### Post by shiv190 on 2019-11-04
I installed Ubuntu 19.10 on my Asus Vivobook which came preinstalled with a Win10 license. I'm also using an external display (Dell SE2219HX). On my inbuilt display, some of the colors are coming off to be too washed out, especially the white point seems to be a little unbalanced. So much so that I was prompted to install some extensions to GNOME as well as Firefox to make the whole desktop look dark. My purpose has been served well and 99% of my desktop is now in dark theme, hence saving me from eye strain (I wear spectacles as it is). However, sometimes I need to switch to lighter themes, specifically when viewing certain webpages that do not fully support the dark theme extension for FF. I've gone through several questions here on the forums as well as askubuntu and come to know of `xrandr`with --gamma and --brightness attributes. While they serve well I'm unable to correct the white point or the contrast correctly for the inbuilt display. There is also the displayCAL app and xcalib but the former came out as useless since I have no colorimeter.

Can someone guide me on how I can reduce the extremely bright white light in my inbuilt display? It is so bright that it eventually overpowers even the dark font that I'm typing. Changing brightness levels from the upper menu did not help much. Rest of the colors seem quite fine. The machine uses an Intel HD 620 GPU.

Thanks.

Output for xrandr:
```
xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 16384 x 16384
eDP-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.01 +  60.01*   59.97    59.96    59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
HDMI-1 connected primary 1920x1080+1920+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  

```

The display I'm trying to tweak is eDP-1.

---

### Post by Holger_Gehrke on 2019-11-05
Have you tried whether 'xbacklight' works on your machine ? 

If it doesn't, you might want to look in '/sys/class/backlight'. If there's a way to control the brightness of the backlight on your machine, there should be a directory in there named after your graphics driver with _bl appended (example: radeon_bl on my machine). In that directory should be (virtual) files which you can read from and write to to control the backlight brightness of your display. Example: ```
cat /sys/class/backlight/radeon_bl0/max_brightness
``` outputs 255. ```
echo 128|sudo /cat /sys/class/backlight/radeon_bl0/brightness
```
changes my display to half the maximal brightness.

Holger

---

