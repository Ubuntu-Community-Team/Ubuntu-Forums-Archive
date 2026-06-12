---
title: "The X Server does not support the XRandR Extension"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by lgastmans on 2008-04-30
Dear All,

Just upgraded from Gutsy to Hardy Heron.

I have an ATI graphics driver.

I know that the refresh rate should be 70 and not 75 (my display wobbles with 75 Hz), but when I try to select System | Preferences | Screen Resolution I get the following error message:

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

Below is my xorg.conf file listing:
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
        Load            "glx"
EndSection

Would greatly appreciate some help here

thanks

Edit : just solved it but using 

sudo displayconfig-gtk

---

### Post by lsutiger on 2008-10-23
> lgastmans  	
Re: The X Server does not support the XRandR Extension
just solved it but using

sudo displayconfig-gtk 
I have the same problem, and that command works, but the setting does not save...when I reboot/logout/start X, the refresh rate regresses to the previous setting.
Does yours save?

---

### Post by steve_baker on 2009-03-04
i just had to resolve this problem on on of my intrepid machines and running:

sudo dpkg-reconfigure -phigh xserver-xorg

then rebooting did the trick

---

### Post by lsutiger on 2009-03-06
Thanx steve for the reply!

Unfortunately, that disables my Nvidia driver . When I re-enable the Nvidia driver, I am back at point-zero.

---

