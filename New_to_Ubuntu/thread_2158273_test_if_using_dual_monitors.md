---
title: "test if using dual monitors"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by micahpage on 2013-06-28
Is there a way to test if the computer is using dual monitors or not regardless of which graphics card is being used? I was looking for more of a terminal approach, one that would return false or true, or be able to parse the output for the same type of answer?

---

### Post by cwsnyder on 2013-06-29
Look at the output of **xrandr** and scan for _connected_ in the output.

---

### Post by micahpage on 2013-06-29
This being my computer with two mintors
```
metulburr@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 3840 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 886mm x 498mm
   1920x1080      60.0*+   59.9     30.0     24.0     30.0     24.0  
   1776x1000      59.9     24.0     30.0  
   1680x1050      60.0     59.9     24.0     24.0  
   1400x1050      60.0     59.9     24.0     24.0  
   1600x900       59.9     24.0  
   1360x1024      60.0     59.9     24.0     24.0  
   1280x1024      60.0     24.0  
   1440x900       59.9     24.0  
   1280x960       60.0     24.0  
   1360x768       60.0     24.0  
   1280x768       60.0     24.0  
   1280x720       60.0     59.9     24.0  
   1024x768       24.0     60.0  
   1152x648       59.9  
   800x600        24.0     60.3  
   720x480        24.0     30.0     60.0     30.0     59.9  
   640x480        24.0     60.0     59.9  
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
metulburr@ubuntu:~$ 


```
so CRT@ and DFP2 would be the two mintors?


and this being another one of my comuters with just one monitor:
```
metulburr@Ubuntu:~$ xrandr
Screen 0: minimum 8 x 8, current 1280 x 800, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
HDMI-0 disconnected (normal left inverted right x axis y axis)
metulburr@Ubuntu:~$
```

So i am assuming that one connected means one moneitor, and two connected means two? Is that right?

But then if i shut off my 2nd monitor, i get what i think is the same response:
```
metulburr@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 3840 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +   59.9     30.0     24.0     30.0     24.0  
   1776x1000      59.9     24.0     30.0  
   1680x1050      60.0     59.9     24.0     24.0  
   1400x1050      60.0     59.9     24.0     24.0  
   1600x900       59.9     24.0  
   1360x1024      60.0     59.9     24.0     24.0  
   1280x1024      60.0     24.0  
   1440x900       59.9     24.0  
   1280x960       60.0     24.0  
   1360x768       60.0     24.0  
   1280x768       60.0     24.0  
   1280x720       60.0     59.9     24.0  
   1024x768       24.0     60.0  
   1152x648       59.9  
   800x600        24.0     60.3  
   720x480        24.0     30.0     60.0     30.0     59.9  
   640x480        24.0     60.0     59.9  
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
metulburr@ubuntu:~$ 


```

---

### Post by cwsnyder on 2013-06-30
Your computer never knows when the monitor is on except when the computer is booting and attempting to read the EDID of the monitor , so, yes, when you turn off a monitor, the computer still thinks it is connected.  If you are looking for something to check when a monitor is turned off, that is a different color of horse.

---

### Post by HermanAB on 2013-07-01
Technically, there is nothing stopping you to talk to the screen serial port directly and see whether there is something out there.  It may even be as simple as using echo to send a string to a device in /dev and cat or read to get the response, but I never tried it.

---

