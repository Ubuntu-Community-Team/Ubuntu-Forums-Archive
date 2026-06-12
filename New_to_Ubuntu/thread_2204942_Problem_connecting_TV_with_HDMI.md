---
title: "Problem connecting TV with HDMI"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by isthevene on 2014-02-11
Hi everybody :) first of all forgive me for my bad english (i'm italian ;) ). 
I bought a HDMI cable to connect my pc to my tv (its resolution is 1366x768p) but in the monitor setting there isn't this resolution. Can someone help me? unfortunaly the italian community didn't give me an answer to my problem. Thank you :D

---

### Post by benjismith on 2014-02-11
Here you can find some information on this: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
Look for the "adding undetected resolutions" section.
Hope it helps :)

---

### Post by isthevene on 2014-02-11
unfortunaly it doesn't work :/ 
i did these steps: 
1) cvt 1680 1050 60
and it gave me this 
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
2) xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
and it gave me this error
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  31
  Current serial number in output stream:  31

can you help me?:(

EDIT: i read the instruction of the tv and the max resolution is 1366x768.. so i added this resolution without errors but it doesn't fit on it...

---

### Post by isthevene on 2014-02-12
It works!!! I followed the step in the guide you linked me but i couldn't save the resolution permanently. so i did this:

1)  $ gksudo gedit /usr/sbin/lightdm-session 

2) added xrandr configuration with my modeline inside the file:
# xrandr configuration
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode HDMI1 1368x768_60.00
xrandr --output HDMI1 --mode 1368x768_60.00


thank you very much :) ):P

---

