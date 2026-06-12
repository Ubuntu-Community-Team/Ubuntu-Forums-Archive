---
title: "Dual monitor resolution problems under Ubuntu 12.04 w/ nVidia"
date: 2013-12-06
forum: New to Ubuntu
---

### Post by digian on 2013-12-06
Hi Guys,

I have a dell laptop here that im trying to run in a dual screen configuration using an external monitor via DVI.

Its running an nVidia GT218M (NVS 3100M) chipset, under Ubuntu 12.04 LVS with current updates applied.

The issue im having is the primary laptop screen runs ok at 1440x900 full screen, however the external second monitor runs at 1680x1050 with black bars on the sides.

Both screens do work, however no matter what I try, the second external screen has black bars on each side, almost as if it looks 4:3 instead of the proper fulls creen 16:10 ratio, I think you call it pillarbox (black bars on both sides), as opposed to letterbox (black bars top and bottom).

I've put on the additional nvidia drivers, taken them off and tried a bunch of different settings in the display but cannot get this second monitor to stretch to the full screen width without the black bars.

Can anybody please help, this is driving me nuts. Thanks :-)

---

### Post by Bucky Ball on 2013-12-06
Welcome. Letterbox actually. Have you tried installing arandr and seeing if that can help? 

sudo apt-get install arandr

... or get it from Synaptics or Software Centre. Go Ouputs>Name of second Monitor>Resolution.

---

### Post by digian on 2013-12-15
Ok, i've now installed arandr. It shows my laptop as 1440x900 and extra screen as 1650x1050 which should be correct.

In the image below, there is no sign of letterboxing or sides being cut off on the second screen DP-0 (however the sides are still cut off and 4:3). 

I noticed I cannot choose any alternate resolutions besides 1440x900 on laptop (DP-3), but I can select a bunch of resolutions on monitor 2  (DP-0)....

Any other ideas how I can fix monitor 2 sides being cut off ?

[IMG]http://i43.tinypic.com/2mdjb0h.png[/IMG]

Maybe this will also help?

~$ xrandr

Screen 0: minimum 8 x 8, current 3120 x 1050, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)

DP-0 connected 1680x1050+1440+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+   60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  

DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)

DP-3 connected 1440x900+0+0 (normal left inverted right x axis y axis) 303mm x 189mm
   1440x900       60.0*+   40.0  

DP-4 disconnected (normal left inverted right x axis y axis)

---

### Post by Bucky Ball on 2013-12-17
This might sound stupid, but you are hitting the green arrow when you make any changes in arandr?

---

