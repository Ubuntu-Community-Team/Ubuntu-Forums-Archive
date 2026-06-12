---
title: "Only one resolution listed for T61p Monitor"
date: 2017-04-30
forum: New to Ubuntu
---

### Post by dualhammersw on 2017-04-30
The only resolution of the monitor listed in the Xrandr is 1920x1200, which is the physical resolution of the monitor. How do I add new resolution options? I want to be able to have resolutions such as 1440x900 show up in the dropdown menu for games I'm playing.

---

### Post by Autodave on 2017-04-30
Is this a desktop or laptop? What video card is in it and have you installed any drivers for the card? If so, what driver and where did you get it from?

---

### Post by dualhammersw on 2017-04-30
Rig details:

Lenovo T61p Laptop:
Nvidia Quadro 570m GPU
Drivers: Nvidia Binary 340.102

Here's the terminal output when I tried to add a Newmode via xrandr

```
~ $ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 8192 x 8192
VGA-0 disconnected primary (normal left inverted right x axis y axis)
LVDS-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1920x1200     60.00*+  50.00  
DVI-D-0 disconnected (normal left inverted right x axis y axis)

~ $ xrandr | grep maximum
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 8192 x 8192
dualhammers@dualhammers-ThinkPad-T61p ~ $ xrandr --newmode "1280x800_59.90"  83.32  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync


~ $ xrandr | grep maximum
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 8192 x 8192
dualhammers@dualhammers-ThinkPad-T61p ~ $ xrandr --newmode "1280x800_59.90"  83.32  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync

~ $ xrandr --addmode LVDS-0 1280x800_59.90
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

~ $ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 8192 x 8192
VGA-0 disconnected primary (normal left inverted right x axis y axis)
LVDS-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1920x1200     60.00*+  50.00  
DVI-D-0 disconnected (normal left inverted right x axis y axis)
  1280x800_59.90 (0x2ac) 83.320MHz -HSync +VSync
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock  49.60KHz
        v: height  800 start  801 end  804 total  828           clock  59.90Hz

```

---

### Post by Autodave on 2017-05-01
Where did you d-l the driver from? And, have you tried a newer driver? I am not sure if that card is supported by a newer driver, but it might be worth a try.

---

### Post by dualhammersw on 2017-05-02
I used the "Additional Drivers" app and it gave me two options for my card: 340 and 304 as well as Neuveau driver. I tried all three: same problem with the two nvidia drivers and the neuveau driver didn't allow me to launch games at all.

---

