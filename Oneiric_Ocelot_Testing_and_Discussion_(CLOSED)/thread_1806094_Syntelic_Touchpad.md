---
title: "Syntelic Touchpad"
date: 2011-07-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by master_b on 2011-07-17
I have an MSI CX640 laptop which has a Syntelic Touchpad, seen by Ubuntu 11.10 as a USB device.

Under LinuxMint 10. this was able to be turned on/off by running scripts (modified) found on the MSI Forums.

Details:-

#!/bin/sh
#touchpad_disable
echo -n manual > /sys/module/psmouse/drivers/serio2\:psmouse/bind_mode
echo serio1 > /sys/module/psmouse/drivers/serio2\:psmouse/unbind

#!/bin/sh
#touchpad_enable
echo -n auto > /sys/module/psmouse/drivers/serio2\:psmouse/bind_mode
echo serio1 > /sys/module/psmouse/drivers/serio2\:psmouse/bind

(the touchpad is seen as serio2)

saved as /usr/local/bin/touchpad_disable and /usr/local/bin/touchpad_enable respectively and chmod +x as root on both.

the following 

ACTION=="add", SUBSYSTEM=="input", KERNEL=="mouse[1-9]" ENV{ID_CLASS}="mouse", RUN+="/usr/local/bin/touchpad_disable"
ACTION=="remove", SUBSYSTEM=="input", KERNEL=="mouse[1-9]" ENV{ID_CLASS}="mouse", RUN+="/usr/local/bin/touchpad_enable"

was saved into /etc/udev/rules.d/01-touchpad.rules

I could then

 gksu -- /usr/local/bin/touchpad_disable 

or 

gksu -- /usr/local/bin/touchpad_enable

run from desktop launchers

These scripts dont work in 11.10 Alpha2 as the filesystem is apparently different.

Could some knowledgeable person please provide modified scripts?

I need  Ubuntu/Xubuntu 11.10 alpha 2 as the 10.x versions do not see or operate the "Sound Out/Headphone" jack

Thanks

---

### Post by master_b on 2011-07-22
as user, in terminal, run

xinput list

to get listing of input devices, including device id #, which is 13 for my Sentelic touchpad

than, as user ,in terminal, run

xinput set-prop 13 "Device Enabled" 0

to turn touchpad off

change 0 to 1 to turn touchpad on again.

---

