---
title: "Setting manually the monitor / TV which is connected to Ubuntu 14.04"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by joostnieuws on 2014-06-16
I just installed Ubuntu 14.04 on a new system (Intel NUC) which I want to use as a new media player and connected this via HDMI to my Harman Kardon and this connects to my 42 inch Panasonic TH-42PY70.
If I look at the display settings while having the TV on, I see that this is recognized as a 47 Inch Panasonic, but the resolution of 1920 x 1080 is OK.
The problem occurs when I did not use my amplifier / TV for a while and try to connect to this system by TeamViewer.
After first having no clue and being unable to connect to this system remotely I found that the issue is that the display / monitor settings are lost / cannot be found by the TeamViewer process and thus it is not opening a display for me ( it tries to connect, but never gives me a visual x environment).
I would like to have the setting to be hardcoded for my monitor that 1. I have the correct resolution (1920 x 1080) and 2. this resolution is always advertised, even if the monitor / TV is not connected to the system, so that TeamViewer always knows which resolution it should connect with.
I don't know where to adjust these setting and if I would find the config file, I wouldn't know what text to modify or put in.

---

### Post by joostnieuws on 2014-06-22
Is there really no one who knows which config file I should modify and where the location is?

---

### Post by johnsen.geir on 2014-06-27
Hi.

I´m having the same problem. If no TV/monitor is connected to my computer during startup, ´X´ does not seem to start up, and when trying to connect using [COLOR=#000000]TeamViewer, I just get a black screen. 
Hope someone are able to help [/COLOR]:cry:[COLOR=#000000]

I don´t know if this is of any help, but here is the output from xrandr and lspci [/COLOR]:rolleyes:[COLOR=#000000]

[/COLOR]_[COLOR=#000000][FONT=Arial]xrandr[/FONT][/COLOR]_[COLOR=#000000]
[/COLOR]Screen 0: minimum 320 x 200, current 1280 x 720, maximum 8192 x 8192
HDMI-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 1434mm x 806mm
   1280x720       50.0*+   60.0     59.9  
   1920x1080      60.0     50.0     50.0     59.9  
   1920x1080i     60.1     50.0     60.0  
   1440x576i      50.1  
   1440x480i      60.1     60.1  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9  
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)



[COLOR=#000000][FONT=Arial]_lspci_
[/FONT][/COLOR]00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 7340]

---

