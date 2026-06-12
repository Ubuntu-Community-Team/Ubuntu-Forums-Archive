---
title: "resolution settings"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by izanami007 on 2008-05-19
For some reason, when I logged in today, my resolution settings were all messed up.  I am not able to choose a resolution higher than 800x600.  I have read through the forums and tried just about everything I could to no avail. I have the nvidia driver, and had problems before so I disabled it. Have tried to re-enable it but that didnt work.  In the xorg configuration options there are no display options, only keyboard/mouse options to change.I cant even really edit the xorg file because I seem to be stuck with all these generic values:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
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
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
 Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

and this is what i get when i try to do the defaults:

erin@erin-desktop:~$  sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080519203809

i'm totally clueless. this just happened. there were no upgrades or anything installed so I have no idea why all of a sudden my settings changed. any help would be appreciated.

---

### Post by domace on 2008-05-19
Try booting Ubuntu in recovery mode and using the following command, this worked for me but I was using a video card I don't know if it works with on board video card and if you decide to do this read everything in the setup carefully.

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by izanami007 on 2008-05-19
> **domace said:**
> Try booting Ubuntu in recovery mode and using the following command, this worked for me but I was using a video card I don't know if it works with on board video card and if you decide to do this read everything in the setup carefully.

sudo dpkg-reconfigure -phigh xserver-xorg


tried that and included it in my previous post. didnt help.  :(

---

