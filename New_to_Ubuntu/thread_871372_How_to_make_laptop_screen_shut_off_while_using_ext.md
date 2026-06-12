---
title: "How to make laptop screen shut off while using external display"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by hockeyfighter09 on 2008-07-26
I got my laptop running Xubuntu hardy up and running with an external display.  But how do I make it so that my laptop screen shuts off when I am using the display instead of having it on cloning my screen.  Also when I shut my laptop all the way the screen turns off for a second then comes back on with the lid closed, how do I solve this?

I have a dell xps m1210 with an intel gma 950 graphic set.

---

### Post by ajmorris on 2008-07-27
> **hockeyfighter09 said:**
> I got my laptop running Xubuntu hardy up and running with an external display.  But how do I make it so that my laptop screen shuts off when I am using the display instead of having it on cloning my screen.  Also when I shut my laptop all the way the screen turns off for a second then comes back on with the lid closed, how do I solve this?

I have a dell xps m1210 with an intel gma 950 graphic set.

Hi there,
try adding ```
Option "DPMS"
``` to the monitor section of your /etc/X11/xorg.conf file. And to make sure that ACPI is active, to /boot/grub/menu.lst, in the kernel line, apend ```
acpi=on
``` That should fix your problem with the screen closing. As for turning of 'clone' mode when connected to an external VGA device... you could do something with xrandr i suppose...
like:

  ```
xrandr --output LVDS --off --output VGA --mode <resolution>

```

and then if that works, create some sort of bash script for it...
e.g:

```
if xrandr -q | grep -q  "VGA connected"; then
  xrandr --output LVDS --off --output VGA --mode <resolution>
else
  xrandr --output VGA --off --output LVDS --mode <resolution>
fi
```

if that does not work, it may be something as simple as adding:
```
Option "Clone" "false"
``` to your "device" section for your graphics chip.

also, you may like to take a look at this application:
```
sudo apt-get install i810switch
```
I believe that is mainly for connecting to external CRT monitors, but it may work for your VGA device also.

AJ

---

### Post by Immolatus on 2008-07-27
Thats a motherboard operation so it should depend on the mobo. I wasn't aware that dell made an XPS with integrated graphics...hm. aaannyhoo, I have an inspiron  and my external switch is the F8 key (Fn+F8). I bet it's in the manual for the machine on the dell site.

---

