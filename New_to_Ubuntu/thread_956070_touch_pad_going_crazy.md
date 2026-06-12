---
title: "touch pad going crazy"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by mike_pasara on 2008-10-22
I use a mouse and the touchpad on my xps m1530. whenever I use the touchpad it goes crazy on me! I try to move slowly and it doesn't respond i move my finger aroudn in a circle on the pad and it opens and minimixes and clicks on things all while i touch the pad and the mouse pointer moves all over the place... I honestly have no idea what is happening.

Mouse works fine though.

---

### Post by PocketDog on 2008-10-22
Ah. If you'll notice, if you move your finger along the bottom of the trackpad it'll either scroll sideways or zoom, depending on page/application context. The right hand side will scroll up/down or zoom.
Moving your finger in circles will drive your pointer mental, which isn't a bug; it's a feature ;)

---

### Post by mike_pasara on 2008-10-22
i'm aware of the scroll feature... but the fact is anywhere i touch it effs everything up. like i can't move the pointer anywhere without it trying to delete something exit a program minimize all within a quarter of a second. if i can make this any clearer... there is no way i can move the pointer to where i want it to without the use of a mouse.

---

### Post by prematurebaby on 2008-10-22
This has happened to me before. All you need to do is clean the touch pad with rubbing alcohol or a damp cloth.

---

### Post by mike_pasara on 2008-10-23
Touch pad is clean. my computer was set back to dell and they even cleaned it for me, so now there is no dust or anything, well now it does but it came back clean.

The issue does not occur anymore, but now I have a new issue. The touch pad has gone super slow.

I had this issue before. And here is what I did/do.

gksudo gedit /etc/X11/xorg.conf

I then put

Section "InputDevice"
Identifier “Synaptics Touchpad”
Driver “synaptics”
Option “SendCoreEvents” “true”
Option “Device” “/dev/input/mice”
Option “Protocol” “auto-dev”
Option “ZAxisMapping” “4 5&#8243;
Option “Emulate3Buttons” “on”
Option “SHMConfig” “on”
Option “LeftEdge” “85&#8243;
Option “RightEdge” “1010&#8243;
Option “TopEdge” “85&#8243;
Option “BottomEdge” “730&#8243;
Option “FingerLow” “25&#8243;
Option “FingerHigh” “30&#8243;
Option “MaxTapTime” “180&#8243;
Option “MaxTapMove” “220&#8243;
Option “VertScrollDelta” “100&#8243;
Option “MinSpeed” “0.20&#8243;
Option “MaxSpeed” “0.70&#8243;
Option “AccelFactor” “0.35&#8243;
Option “HorizScrollDelta” “0&#8243;
EndSection

Then I save that.

I install gsynaptics. But when I go to run it, it says to set the value from on to true for SMHConfig.


Now the issue I am having is that when I reboot to apply the settings, if i don't change the value from on to true then my settings are bought back to default. But if i change to true it keeps the settings but doesn't apply them, the touch pad remains slow and i still get the same error message to change the value to true.

Here is a log of my Xorg.0.log file says this...
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(WW) Configured Mouse: No Device specified, looking for one...

---

