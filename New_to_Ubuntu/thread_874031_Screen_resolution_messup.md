---
title: "Screen resolution messup"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by rhenium3 on 2008-07-29
So, I posted this in help and nobody has been able to help me as of yet, so thought I'd post it here since I've been with ubuntu since friday (i.e. major beginner):

Hello, I need help! I tried to set up my dual screen mode in ubuntu. I have a MSI PR200, and I used the instructions found here:

[https://wiki.ubuntu.com/LaptopTestingTeam/MSIPR200](https://wiki.ubuntu.com/LaptopTestingTeam/MSIPR200)

which says to add this:

Section "Device"
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
Option "MonitorLayout" "CRT,LFP"
Option "Clone" "Off"
EndSection

Section "Monitor"
Identifier "Philips 170S"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
Monitor "Philips 170S"
DefaultDepth 24
SubSection "Display"
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
Virtual 2624 2048
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

EndSection

to /etc/X11/xorg.config I did so and the resolution of the screen is way to big and I can't access the menu bar, only a few icons my desktop. I backed up the original file, and when I put it back the screen resolution is still too big. I tried right clicking on the desktop to change it, but alas, I am no longer in windows.

Please help, I can barely use ubuntu with the screen like this and I have no idea how to fix it :(

Thanks!

---

### Post by LowSky on 2008-07-29
I know it not a fix but Hold the Alt Button while moving the mouse to access the rest of the screen

otherwise you might need to fix your xorg.conf file
boot into safe mode, if your using 8.10 it should give an option to fix xorg.
if not got to a terminal prompt and type

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cdtech on 2008-07-29
You might try "sudo displayconfig-gtk" also.

---

### Post by rhenium3 on 2008-07-29
Restoring the xorg file does not help, it only disables the second screen.  Pressing ALT and moving the mouse does not let me access other parts of the screen.

Someone recommended deleted gnome configuration files... any idea how this is done or if it will work? :confused:

btw, thanks for the post, at least you tried some suggestions, I'm willing to try anything at this point

---

### Post by LarsW_Tierp on 2008-07-29
Hi

Have you read this thread?: [http://ubuntuforums.org/showthread.php?t=869635&highlight=dual+screen]("http://ubuntuforums.org/showthread.php?t=869635&highlight=dual+screen")

---

### Post by rhenium3 on 2008-07-29
> **cdtech said:**
> You might try "sudo displayconfig-gtk" also.

Hi,
I tried this... I guess my laptop the default screen would be plug and play?  I try to test it and it fails...  Also, are there drivers I should download? (though it worked before, so I'm not sure why it wouldn't work now)

Thanks again everyone for all replies... even if it doesn't help me solve it, each failure is one step closer to the solution!

---

### Post by rhenium3 on 2008-07-29
so after going to "sudo displayconfig-gtk" I get tihs message, that ubuntu is running in low graphics mode, etc etc... Don't know what I did then :(

---

### Post by rhenium3 on 2008-07-29
> **LarsW_Tierp said:**
> Hi

Have you read this thread?: [http://ubuntuforums.org/showthread.php?t=869635&highlight=dual+screen]("http://ubuntuforums.org/showthread.php?t=869635&highlight=dual+screen")

Yeah, I did now, but I'm passed trying to set up the dual screen. I just want my normal screen back! :(

---

### Post by cdtech on 2008-07-29
Have you looked in the System > Administration > Hardware Drivers to make sure your Proprietary drivers are enabled?

Or in your System > Administration > Software Sources and make sure your "Proprietary drivers for devices" is checked then do a "sudo apt-get update".

Hope this helps......

---

### Post by rhenium3 on 2008-07-29
> **cdtech said:**
> Have you looked in the System > Administration > Hardware Drivers to make sure your Proprietary drivers are enabled?

Or in your System > Administration > Software Sources and make sure your "Proprietary drivers for devices" is checked then do an "sudo apt-get update".

Hope this helps......

I cannot go to system > administration because I don't have the launch menu and can't access it. Is there another way to get there?  via terminal maybe?

---

### Post by rhenium3 on 2008-07-29
A step closer my friends! gnome-panel was missing!  I installed it, and now the panel is there! However I'm getting errors, going to try to search on forums for more answers... thanks everyone!

---

