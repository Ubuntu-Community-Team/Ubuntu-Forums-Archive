---
title: "laptopmouse trackpad not working"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by scrumpypaul on 2008-09-12
hi

i have a gericom ego laptop.

last night the mouse trackpad was working fine, today it is stuck - no motion, no clicking.

using a usb mouse at the mo which is fine


any ideas how i can fix it?


paul

---

### Post by dhtseany on 2008-09-12
This may seem like a dumb question but does your laptop have a hardware button somewhere on the chassis to turn the trachpad on and off?

Peace
Sean

---

### Post by scrumpypaul on 2008-09-12
hi dhtseany - thanks for your response but i found out how to cure it.

power laptop up on battery, then shut down. remove battery, wait 5 mins, then power up on mains power. this resets the mouse.

---

### Post by k33bz on 2008-09-12
Thats good you got it working with something simple. But if anyone else runs into this problem, they may want to fix it with this:

sudo gedit /etc/X11/xorg.conf


ADD THESE LINES BELOW THE MOUSE SECTION:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
EndSection


ADD THIS LINE IN THE SERVERLAYOUT SECTION:

InputDevice "Synaptics Touchpad"

---

