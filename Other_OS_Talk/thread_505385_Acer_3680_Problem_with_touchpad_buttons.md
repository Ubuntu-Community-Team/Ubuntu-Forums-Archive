---
title: "Acer 3680 Problem with touchpad buttons"
date: 2007-07-20
forum: Other OS Talk
---

### Post by Siph0n on 2007-07-20
I just bought an Acer Aspire 3680 laptop and the touchpad/buttons dont seem to be working. So far i've used Vista Basic (that it came with), Damn Small Linux, and Backtrack 2. I can move the mouse around, when I try and click the left or right touchpad buttons, it does nothing. This makes it almost impossible to do anything in linux, except with the command line. In Windows I found that if i hit ctrl alt delete, and than exit out of that window, the mouse works fine... Has anyone else had a problem? I tried using the touchpad fix I saw in another post which has this:

edit /etc/X11/xorg.conf

And add these lines below the mouse section:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
EndSection

Add this line in the ServerLayout section:
InputDevice "Synaptics Touchpad"


I just noticed I didnt add that one line to the ServerLayout section, but does anyone know if this fix will help me with my touchpad buttons? or if its only to recgonize the moving of the cursor? Any help would be appreciated!!! :)

---

### Post by Hershey on 2007-07-21
Just picked up the same thing yesterday. I haven't had any issues with the touch pad though.  I would comment out the "Configured Mouse" section and down in the ServerLayout section.  Not sure if having both that and the touch pad stuff in xorg.conf at the same time will cause issues.

---

### Post by smoker on 2007-07-22
> So far i've used Vista Basic (that it came with), Damn Small Linux, and Backtrack 2. I can move the mouse around, when I try and click the left or right touchpad buttons, it does nothing.

if it doesn't work in vista as well as linux, it may be a hardware problem. it is possible for the connection ribbon from the touchpad to the motherboard to work loose. the only way to tell is to take it apart, so if under warranty, take it back and get it checked out.

---

### Post by Siph0n on 2007-07-23
Just as an update. I returned it to circuit city, and they made me pay a 55$ (15%) restocking fee because it was opened and I didn't exchange it for something else. I got the Gateway MT6711 instead and so far so good :)

---

### Post by smoker on 2007-07-24
> **Siph0n said:**
> Just as an update. I returned it to circuit city, and they made me pay a 55$ (15%) restocking fee because it was opened and I didn't exchange it for something else. I got the Gateway MT6711 instead and so far so good :)

hi, was it a hardware fault? if so, you shouldn't have been charged any fee :(

anyway, best of luck with your new machine :)

---

### Post by Siph0n on 2007-07-25
Yea it was hardware I think... The touchpad buttons didnt work at bootup. I had to hit ctrl alt delete to get them to work. They said I could have exchanged it for another computer in the store, but all the other laptops were 300$ or so more... and I didnt want to pay that much. Plus this newer one is WAY better :)

---

