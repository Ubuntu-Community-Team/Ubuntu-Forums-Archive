---
title: "nvida dual monitors"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by TechDragon on 2008-06-09
IBM T61. Nvidia quadro integrated graphics card.

I am trying to set up dual monitors and nothing is working. I have the drivers installed using Danger mouses script and am using the nvidia control panel. Everytime I set something it just reverts back to it default. It is acting like I need to run it as root, so it can change the Xorg.conf. Problem is I don't know the command line name of this utility.

Help please, also if you use nvida and have dual monitors I would like to see your Xorg.conf just for comps.

One more thing, I am used to fighting the ATI fight. I am a tech director at a corporation so I just ordered myself an nvidia laptop problem is now I have to learn the new quirks with nvidia, any help would be appreciated.

---

### Post by MaxVK on 2008-06-09
Hi.

I don't know the name of that program either, but I can tell you how to get it!

Its obviously in the menu, so Right click the menu item and add it to the desktop. You can then Right click it on the desktop, select properties and the command will be shown (On the last tab I think).

Regards

Max

---

### Post by signseeker on 2008-06-09
try 

sudo nvidia-settings

---

### Post by TechDragon on 2008-06-09
This laptop is attached to a docking station while I am at work, the docking station has two dell 19" lcds connected to it. Thanks to your help I now have the laptop displaying correctly while it is on the docking station.

The problem is when I take it off the docking station it does not revert back to the laptop lcd, it tries to spread the laptop over two monitors.

any ideas, on how to fix?

I kind of figured that it would probe the monitors and use the one available. I know this can be done because Kubuntu does it automatically. I am hoping someone can tell me how to do this in ubuntu.

Thanks

---

### Post by ds6 on 2008-06-09
Hey TD - I have the same docking station setup and i am only able to get one of the two Dell screens to work. Could you post your xorg.conf? I'd like to compare with mine. 

Thanks!

---

### Post by JoshuaRL on 2008-06-09
If you're on Gnome, use displayconfig-gtk.  It's the GTK port of displayconfig from KDE and should solve your problem.

---

### Post by fwre01 on 2008-06-09
> **TechDragon said:**
> IBM T61. Nvidia quadro integrated graphics card.

I am trying to set up dual monitors and nothing is working. I have the drivers installed using Danger mouses script and am using the nvidia control panel. Everytime I set something it just reverts back to it default. It is acting like I need to run it as root, so it can change the Xorg.conf. Problem is I don't know the command line name of this utility.

Help please, also if you use nvida and have dual monitors I would like to see your Xorg.conf just for comps.

One more thing, I am used to fighting the ATI fight. I am a tech director at a corporation so I just ordered myself an nvidia laptop problem is now I have to learn the new quirks with nvidia, any help would be appreciated.

TechDragon, what kind of dual monitor setup are you looking for? just to simply plug into the docking station, shut the laptop and have the display on an external monitor? or to have an extended desktop? or clone?

---

### Post by TechDragon on 2008-06-09
actually, I can only get one of the external monitors to work myself.  I have 3 distros installed trying to get this to work on any one of them :)

when plugged into the dock I want "twinview" spread across both external Dell 19" lcds

When not plugged into the dock I want just the single laptop LCD to function.  

This works out of the box on Kubuntu but I simply prefer gnome and want to get it working on ubuntu.

Thanks

---

### Post by JoshuaRL on 2008-06-09
TechDragon, you might try displayconfig-gtk.  That should help.

---

### Post by TechDragon on 2008-06-09
yes, used that tool in 7.10 but I read that it would trash your system if you tried to use it with 8.04

true or false?

---

### Post by JoshuaRL on 2008-06-09
I'm not sure, I hadn't heard that.

---

### Post by TechDragon on 2008-06-10
okay,  I think I got it working, but it was difficult to figure out.

What finally worked was setting both of the Dell monitors to "seperate x servers" and disable the built in laptop lcd.  Then once that was working and several reboots later I disconnected the laptop from the docking station having no choice but to use the laptop lcd, it did just that but at an absolutely huge resolution I then ran the utility again and adjusted the laptop resolution.   

It is to early to declare victory but it seems to be working.

Also, I ran the tool from a terminal 
sudo nvidia-settings

---

### Post by JoshuaRL on 2008-06-10
Glad to hear it.  If you have any more problems, you might give displayconfig-gtk a try.  I just talked to bodhi zazen and I think it may be safe for use.

---

### Post by fwre01 on 2008-06-11
> **TechDragon said:**
> okay,  I think I got it working, but it was difficult to figure out.

What finally worked was setting both of the Dell monitors to "seperate x servers" and disable the built in laptop lcd.  Then once that was working and several reboots later I disconnected the laptop from the docking station having no choice but to use the laptop lcd, it did just that but at an absolutely huge resolution I then ran the utility again and adjusted the laptop resolution.   

It is to early to declare victory but it seems to be working.

Also, I ran the tool from a terminal 
sudo nvidia-settings

So are you running seperate x-servers for each monitor? iv found in the past that this really slows my pc down. and that i cant drag windows between the two, is this not a limitation of what you were trying to achieve?

---

### Post by TechDragon on 2008-06-11
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1908FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "IBM"
    HorizSync       53.2 - 63.9
    VertRefresh     50.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "IBM"
    HorizSync       53.2 - 63.9
    VertRefresh     50.0 - 60.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "1280x1024 +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP-1: 1280x1024 +1280+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP-1: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x1024 +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard1"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1440x900 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

this works flawlessly for me

---

### Post by JoshuaRL on 2008-06-12
Dude, are you running gutsy?

---

