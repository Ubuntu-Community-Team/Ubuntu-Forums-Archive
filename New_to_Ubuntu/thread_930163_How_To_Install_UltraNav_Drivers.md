---
title: "How To Install UltraNav Drivers?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by StunnerAlpha on 2008-09-25
Yo. So I have a Thinkpad T60 which has UltraNav buttons that I want to function properly in Ubuntu. how would I go about installing the drivers for my specific machine? Thanks.

On Windows I installed things like the Intel Matrix Storage Driver and the likes... Do I need to install these drivers for Ubuntu as well?

---

### Post by StunnerAlpha on 2008-09-25
Bump. Anyone?

---

### Post by StunnerAlpha on 2008-09-29
Bump....

---

### Post by tdilworth on 2008-09-30
i have a R50 with Ultranav, and i am also looking for a way to enable the blue scroll button.

---

### Post by DomesDKG on 2010-03-10
Did any of you ever figure this out?  There's another thread on this topic, [http://ubuntuforums.org/showthread.php?p=8947043#post8947043](http://ubuntuforums.org/showthread.php?p=8947043#post8947043), but no answer has been posted yet.  I'm having the same issue with a T400

---

### Post by J V on 2010-03-10
With most peripherals I just go to shortcuts and add them there, but idk about laptop mice...

---

### Post by bagender on 2011-05-08
anyone ever figure this out?

is it thru ndiswrapper?

---

### Post by kyozo on 2011-05-23
Hi all,

I currently have a fresh installation of Fedora, and have not configured this yet. But on Ubuntu (10.10 i think) I got it working like this

> try installing gpointing-device-settings, this seems to work ok. cannot get it to work in 10.04

Scrolling
middle mouse button is 2 - enable mouse wheel emulation

Using xinput
use xinput list to see all devices - usb ultranav keyboard typically has 2 identical entries. Use xinput test <id> to see which is the trackpoint and which is the touchpad.
Disabling a device "xinput set-int-prop <id> "Device Enabled" 8 0"
Configuring Mouse Wheel emulation - set the following int props
xinput set-int-prop 11 "Wheel Emulation" 8 1
xinput set-int-prop 11 "Wheel Emulation Button" 8 2
the following could also help - they were set by default (perhaps by gpointing-device-settings)
    Evdev Wheel Emulation Axes (237):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (238):    10
    Evdev Wheel Emulation Timeout (239):    200

Also take a look at this page
[http://www.thinkwiki.org/wiki/Synaptics_TouchPad_driver_for_X](http://www.thinkwiki.org/wiki/Synaptics_TouchPad_driver_for_X)

Cheers Kyozo

---

### Post by walt.smith1960 on 2011-05-23
Gpointing referenced above works.  Button #2 for scroll instead of the default #4.

---

