---
title: "Can't find my answer... kbd_backlight?"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by exxid on 2014-09-29
Searched, found similar topics, but none of the solutions have worked for me thus far. Granted, I'm still fairly new to Ubuntu, etc.


*When I run Windows on my Asus laptop, the keyboard is backlit, great, I keep my room dark as ****. When I run Ubuntu, no backlighting, tried everything I know to get it to work.

/sys/devices/platform/asus-nb-wmi/leds 

^..brings up kbd_backlight, so great, I think I'll be able to adjust brightness from there. Neg, no such file or dir.



On 14.04, computer is ASUS Q550LF ..

Any and all help is appreciated. Feel free to dumb down any information as well, like I said, I'm relatively new to this.

---

### Post by sandyd on 2014-09-29
Moved to *New to Ubuntu*

---

### Post by xc3RnbFO8P on 2014-09-29
What is the output of:
> gedit /etc/modules-load.d/asus-nb-wmi.conf

---

### Post by exxid on 2014-10-01
asus-nb-wmi

Nothing else.

---

### Post by xc3RnbFO8P on 2014-10-01
Try add this line:
> /sys/devices/platform/asus-nb-wmi/leds/asus::kbd_backlight
and restart

---

### Post by exxid on 2014-10-01
> **Ringi said:**
> Try add this line:

and restart



That worked, unbelievable. Can't thank you enough, Ringi.

---

### Post by exxid on 2014-10-06
Well it worked once, now it no longer works. Added line is still there, just no kbd_backlights.

---

### Post by xc3RnbFO8P on 2014-10-06
Thats because you didnt mark it solved ;)
I dont know, try:
> sudo apt-get install --reinstall linux-image-$(uname -r) 
and restart

---

