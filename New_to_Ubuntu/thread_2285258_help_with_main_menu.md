---
title: "help with main menu"
date: 2015-07-04
forum: New to Ubuntu
---

### Post by Anton_Heidebrink on 2015-07-04
hello ubuntu friends

i have a problem and for me to see this it is annoying see picture
it is dubbel menu at the top en the screen background it is on a 22 inch wide screen with reselution 2560x1600 pixels
also i cant run flash player in google chrome browser latest version 

can some one help me out ?

sorry for the rubbish english 

greatings anton

---

### Post by GrouchyGaijin on 2015-07-04
That is annoying.  Just out of curiosity what happens when you change the resolution of the monitor?

---

### Post by ajgreeny on 2015-07-04
Is the 2560x1600 resolution what you are really using or just the native resolution of the monitor?
Let's see the output of ```
xrandr
``` in terminal.

What graphic card do you have?
Let's see the output this time of ```
lspci | grep -i vga
``` in terminal.

Please copy, and then post the output in code tags (See **Code-tags** in my signature for a "how-to".

---

### Post by Anton_Heidebrink on 2015-07-05
hello friends

2560x1600 pixels is the maximum size of the picture
actual screen reselution is 1680x1050 (16:10) 

if screen reselution is set on 
1680x1050 pixels (16:10) dubbel menu
1440x900 pixels(16:10) dubbel menu
1280x1024 pixels (5:4) i have a normal screen no dubbel menu 

Code Xrandr: 

flappie@flappieToshibaSatellite-M70:~$ xrandr
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 32767 x 32767
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       58.1*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        59.9 +
   640x480        59.9 +
   1024x768       59.9  
   800x600        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

Code: lspci | grep -i vga

lspci | grep -i vgaflappie@flappieToshibaSatellite-M70:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

---

### Post by dino99 on 2015-07-05
is it the same issue if you are logged with gnome-shell instead of unity ?
which graphic card/chipset is used and with which driver ? (how it has been installed)

---

### Post by Anton_Heidebrink on 2015-07-05
that i do not know dino 

this is a new install from usb stick made with unetbootin
ubuntu 14.4 i386 version
everything was detected autmaticly

---

### Post by grahammechanical on 2015-07-05
Are you using a VGA cable to connect the TV to the computer? If it is possible, use either a DVI or HDMI connection. Digital TVs did not exist when VGA was introduced as a video graphic specification. I have found that VGA will limit the screen resolution when I use it on my 24 inch digital TV. But HDMI is good.

You can try going to System Settings>Screen Display and click Detect Displays. See if that changes anything.

Regards.

---

### Post by mansonfan78 on 2015-07-05
You have two monitors connected, right?  If that is the case, what you are seeing is the "smaller" monitor's image being stacked on top of the "bigger" monitor.  Go to your monitor/display settings and see how it is set up, try changing one of them so that it is "to the right of" (or left) of the other one.  I speak from experience.

---

### Post by Anton_Heidebrink on 2015-07-06
thank you very much manso it was exactly as you say it was a dubbel monitor output on the external  vga port problem resolved :D:D:D:D:D:D
 now that this problem is been resolved do i need to close this subject ??

---

### Post by mansonfan78 on 2015-07-06
You're welcome.  You can mark this as "solved" by clicking on the "thread tools" drop down on the bar near the top of the screen (below the facebook thing).

---

