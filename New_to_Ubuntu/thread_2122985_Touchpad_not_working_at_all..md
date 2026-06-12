---
title: "Touchpad not working at all."
date: 2013-03-06
forum: New to Ubuntu
---

### Post by Cremacious on 2013-03-06
I decided to install Ubuntu (12.10) for the first time, and everything is working except for my laptop's touchpad. It is 100% unresponsive. 
I have a Toshiba Satellite A505-S6985 64bit.

---

### Post by squakie on 2013-03-06
I didn't look for the spec sheet online - do you know what manufacturer's touchpad is actually installed in the laptop?  Most should work, but it's possible it's Alps (they may all work now too for all I know) or some other brand that needs special attention - such as a driver.  Perhaps some entries need to be made in the configuration files for X.  Just look up the actual touchpad that is in the laptop and post it back here.  If nothing else - check Toshiba's site for your laptop model and see what they list.

---

### Post by Cremacious on 2013-03-06
It is a Synaptics touchpad.
I do not have the touchpad tab in Settings>Mouse and Touchpad and I think my touchpad is being read as PS/2

[IMG]http://img6.imageshack.us/img6/8349/screenshotfrom201303062.png[/IMG]

---

### Post by squakie on 2013-03-07
I believe it should have been installed, but you could try installing the X synaptics driver:

sudo apt-get install xserver-xorg-input-synaptics

If that shows as already installed, you may want to try:


sudo apt-get install gsynaptics

sudo apt-get install tpconfig

then try running via:

tpconfig

or

gsynaptics

I can look around if none of that helps.

---

