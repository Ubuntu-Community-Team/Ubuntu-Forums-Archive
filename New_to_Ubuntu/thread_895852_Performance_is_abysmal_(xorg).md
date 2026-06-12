---
title: "Performance is abysmal (xorg)"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by rocsco on 2008-08-20
After the last update to 8.04, I noticed performance was very sluggish.
Looking at top, I see Xorg running at between 60 - 95% CPU.
I switched Compiz off, no change.

Researched the various posts on the subject - no joy.

My Xorg.conf is attached (if that helps)

Confronted with this - now I know I am a beginner!

Can any help please.

-------------------------------------------------
xorg.conf

Section "InputDevice"
  Identifier  "Generic Keyboard"
  Driver    "kbd"
  Option    "XkbRules"  "xorg"
  Option    "XkbModel"  "pc105"
  Option    "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver    "mouse"
  Option    "CorePointer"
EndSection

Section "Device"
  Identifier  "Configured Video Device"
  Driver    "nvidia"
  Option    "NoLogo"  "True"
EndSection

Section "Monitor"
  Identifier  "Configured Monitor"
EndSection

Section "Screen"
  Identifier  "Default Screen"
  Monitor   "Configured Monitor"
  Device    "Configured Video Device"
  Option    "RenderAccel" "true"
  Option    "TwinView"
  Option    "MetaModes" "1920×1200 1920×1200"
  Defaultdepth  24
EndSection

Section "ServerLayout"
  Identifier  "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
  Load    "glx"
EndSection

---

### Post by satipera on 2008-08-20
what is your graphic card perhaps glx new is needed trying to help with very little knowledge

---

### Post by LowSky on 2008-08-20
boot into recovery mode from GRUB and reconfigure your Xorg file.

---

### Post by sdennie on 2008-08-20
Is it a laptop?  If so, maybe try: [ HOWTO: Improve NVidia Laptop Graphics Performance]("http://ubuntuforums.org/showthread.php?t=828369")

---

### Post by rocsco on 2008-08-20
Thanks for getting back to me.

The card is a 512mb Geforce 8800GT   BFC  OC Version  PCI Express.

Hope this gives you a clue.

What is glx new? I am that far behind.

---

### Post by rocsco on 2008-08-20
Any chance you could be a little more specific.

I can boot into GRUB no woories bgut reconfigure the Xorg file changing what?

Regards

---

