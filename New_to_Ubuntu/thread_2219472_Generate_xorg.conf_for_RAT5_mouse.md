---
title: "Generate xorg.conf for RAT5 mouse"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by verymadpip on 2014-04-24
Hi everybody.
I have a RAT5 mouse which needs a section added to my xorg.conf.  Unless that's changed with Trusty, which would be nice.
Sorry, I should have said this is for when I install Trusty.

1. How do I do that as simply as possible (sudo Xorg -configure?)

2. While using Saucy I changed from  an AMD GPU to an Nvidia, consequently my current xorg.conf looks like this:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "InputClass"
    Identifier "Mouse Remap"
    MatchProduct "Mad Catz Mad Catz R.A.T.5 Mouse"
    #May also be "Mad Catz Mad Catz R.A.T.5 Mouse" depending on production date.
    MatchDevicePath "/dev/input/event*"
   #Option "AccelerationProfile" "1"
   #Option "ConstantDeceleration" "5"
    Option "ButtonMapping" "1 2 3 4 5 6 7 8 9 10 11 12 0 0 0"
    Option "ZAxisMapping" "4 5 6 7"
EndSection

```

Could I just use this as is? (After generating a new xorg.conf maybe?  Copy & paste it in there?)
Would there be any ill effects from deleting the sections with "ATI" in them?
I do use the Nvidia proprietary drivers.

This is the basic setup I'm currently using:
Ubuntu Saucy 64 bit
i52500k CPU
GTX760 GPU
Sabertooth Z77 mobo
8GB RAM

---

### Post by verymadpip on 2014-04-25
Could I just make the xorg.conf by writing it manually with the relevant section
It'd be the only thing in there.
I'm going to try it.

---

