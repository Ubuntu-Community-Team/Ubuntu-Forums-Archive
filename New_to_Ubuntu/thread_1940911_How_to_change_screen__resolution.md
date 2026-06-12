---
title: "How to change screen  resolution"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by kanjiline on 2012-03-14
I need help changing my screen resolution.

Please, I already searched the forum and found numerous threads, but they all seem to veer off at some point into a link to an older thread with dozens of terminal commands

I tried reading and understanding those but they made my head explode. I need step by step instructions, not a link to something that exceeds my powers of comprehension.

When I click on "Systemeinstellungen" (system settings) and then "Darstellung" (appearance/presentation) a box opens with a picture of my monitor and in the upper right hand corner it shows the current resolution: 1920 x 1280. There is nowhere that I can change the resolution. 

I opened a terminal window and typed xrandr:
```
line@line-SN95V20:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      75.0*    75.0     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
VGA-1 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)

```I have no idea how I can reduce screen resolution from 1920x1280 to something intermediate, maybe 1280x1024 would be a good choice?

---

### Post by The Cog on 2012-03-14
According to xrandr, you are already using 1280x1024 on VGA0. Then it lists all possible resolution and rate settings. If you want to reduce it to 1024x768 then the command is ```
xrandr -s 1024x768
```If you want to set the rate at the same time, something like ```
xrandr -s 1024x768 -r 60
```
P.S. 1920x1280 is not listed as a possible resolution for your display.

---

### Post by kanjiline on 2012-03-14
The Cog, thank you for your reply, however, I am fairly sure that the information that I get from the "control panel" or whatever it's name is in Ubuntu, is correct: 1920x1280. It is a large monitor and the size of letters on screen is very small. There are vastly more pixels here than on my notebook computer, which has some 1300 by 768 pixels.

Therefore, xrandr cannot be right. Since xrandr cannot be trusted, should I still use it to change resolution to 1280x1024? How would I do it?

> **The Cog said:**
> According to xrandr, you are already using 1280x1024 on VGA0. Then it lists all possible resolution and rate settings. If you want to reduce it to 1024x768 then the command is ```
xrandr -s 1024x768
```If you want to set the rate at the same time, something like ```
xrandr -s 1024x768 -r 60
```P.S. 1920x1280 is not listed as a possible resolution for your display.

---

### Post by kanjiline on 2012-03-15
It just occurred to me that I read somewhere that LCD panels have only one (1) resolution that they are optimized for and unlike CRT monitors, changing screen resolution brings bad results.

Can you confirm this? If so, then there is a reason why the control panel only shows 1920x1280 with no option for changing, and this thread can be closed... or you can tell me if there is a setting in Ubuntu for keeping screen resolution the same but increasing letter sizes.

As for xrandr, hopefully the author of the software will read this and take note: your program is not always accurate.

---

### Post by The Cog on 2012-03-15
I can't help you there. I use Xubuntu which probably has a different GUI screen control. I have never known xrandr be wrong though, and would have thought that a GUI control would simply be a pretty wrapper round xrandr.

You could try the xrandr commands anyway and see what happens.

---

### Post by usefulidiot on 2012-03-15
Follow the fairly simple commands the following link and you should be fine. I had no problems changing the resolution for my LCD. In my case 1368x768 seems to get the best out of my laptop and TV.

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Let me know if this works, and if you have any questions!

---

