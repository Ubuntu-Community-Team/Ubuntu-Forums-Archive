---
title: "Yet Another Ubuntu Graphic Problem"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by censusgray on 2008-07-30
[FONT="Georgia"]Long story short - no full-screen games work.  I've tried Warsow, Alien Arena, Tremulous... none of them work.  Warsow crashes to the desktop and zooms in, Alien Arena and Tremulous just flicker briefly for a second and then crash.  Not only this, but screensavers that require 3D acceleration don't work either!

I'm going nuts!

I know I need to provide you guys with some information, but I'm an absolute beginner here, and don't know what you need, or what I should do.

Help![/FONT]

---

### Post by halitech on 2008-07-30
lets start with some info :)

what version of Ubuntu?

how much Ram do you have in the machine?

open a terminal and post back the output of
```
lspci
```

this will get us started

---

### Post by yaztromo on 2008-07-30
If you have ATI or Nvidia graphics, have you installed the restricted drivers for them?

---

### Post by Vorian Grey on 2008-07-30
If you have Desktop Effects enable you may need to disable them.

---

### Post by tuxxy on 2008-07-30
If your using ATI card, you may have to put up with some driver issues, I would recommend nVidia card for flawfless effects and 3D

---

### Post by censusgray on 2008-07-30
I have Ubuntu 8.04 LST (Hardy Heron, I think).  Restricted drivers ARE installed, as well as NVIDIA X-Server Settings module.  Before I upgraded to 8.04, games worked but they were extraordinarily slow (even Armagetron) - and even though my computer is old and ancient it ran World of Warcraft on Windows XP (on low settings, but still) without a hitch.

I've uninstalled compiz-fusion (I did a little poking around before I posted here :-P) and everything related to it (at least, I think I have - I uninstalled all the options it gave me in Synaptic, but it didn't change a thing).

Here's my output for *lspci*:

```
censusgray@censusgray-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 21)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:04.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:0d.0 Multimedia audio controller: Rockwell International Unknown device 4310
00:0d.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
00:0d.2 Input device controller: Rockwell International Unknown device 4312
00:0e.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:10.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

Thanks in advance.  :KS

PS - 512 Ram

---

### Post by halitech on 2008-07-30
I'm guessing an AMD processor of some sort, an older Nvidia video card with a maximum of 128meg of ram and waht looks like a sound card that has no drivers installed

[color=red]00:0d.0 Multimedia audio controller: Rockwell International Unknown device 4310[/color]

I'm going to hazard a guess that you also have no sound on the computer

---

### Post by censusgray on 2008-07-31
I dunno if sound drivers are installed or not.  There is sound, but the quality leaves something to be desired.

I just wish I could play some games every now and then.  :-\

---

### Post by blazercist on 2008-07-31
it is possible that the upgrade botched your drivers, what happens if you try to run nvidia-settings ?  do you get any errors?

---

### Post by censusgray on 2008-07-31
No, settings come up as normal: no errors.  Are there any alternative drivers for NVIDIA cards I could try?  The restricted drivers utility only lists one, and I'm currently using it.

---

### Post by blazercist on 2008-07-31
you could try the nvidia closed source driver, i like it better but there are some caviats.

you will need to reinstall each time there is a kernel update.

to install the closed source driver, get the file from nvidia.com

1. download the driver to your home directory.
2. sudo apt-get install build-essential <-- this needs to be done only once
3. ctrl+alt+f1  <-- this drops you to virtual terminal so I suggest you write down these instructions
4. login
5. sudo chmod +x NV*  <-- makes the driver file executable
6. sudo /etc/init.d/gdm stop  <-- this stops the X server so you can install the drivers
7. sudo sh NV*  <-- this actually runs the installer
8. You can hit yes yes yes accept accept till the installer finishes.
9. sudo /etc/init.d/gdm start  <-- restarts X server and brings you back to GUI

thats it...  Before doing this I recommend you uninstall the current driver that you have installed and you may possibly need to blacklist the current module.

next time there is a kernel update all you have to do is

1. ctrl+alt+f1
2. sudo /etc/init.d/gdm stop
3. sudo sh NV*
4. yes yes yes yes, accept accept
5. sudo /etc/init.d/gdm start

good luck and enjoy

---

### Post by censusgray on 2008-07-31
do you mean blacklist the restricted driver?

I'm not sure what is meant by blacklisting the module...

(total linux n00b here, sorry)

---

### Post by censusgray on 2008-07-31
::sigh::

no dice...

I went to the NVIDIA drivers page, told them what kind of setup I had, and downloaded the driver to my home folder.

Then I went into restricted drivers and unchecked the drivers to uninstall them, then proceeded to follow instructions.

Upon restarting, there was a pop-up telling me Ubuntu had to start in low-graphics mode... now I can't go past a 800x600 resolution.  When I click the NVIDIA X Server Settings utility, it tells me the X server is not installed!

Not only this, but games don't even seem to register when I click on them now.  Not even a flash of black screen... nada.  I click on them and it does nothing.

I tried rechecking the restricted driver, but it was the same issue...

Any suggestions?

:-\

---

### Post by blazercist on 2008-08-01
Ok, give output of the following commands:

```
 lsmod | grep nvidia 
```

```
 cat /etc/X11/xorg.conf 
```

Also, were you paying attention when you tried my instructions?  Are you sure it said that it was successful?  It won't hurt to repeat the process and watch for any errors the installer may throw...

---

### Post by censusgray on 2008-08-02
Okay, I installed an older version of the NVIDIA patch, following your instructions... I have my normal resolution, but games still don't work... they still drop me to the desktop...

here is the output for those commands:

```
censusgray@censusgray-desktop:~$ lsmod | grep nvidia
nvidia               7825792  24 
i2c_core               24832  2 nvidia,i2c_viapro
agpgart                34760  2 nvidia,amd_k7_agp
censusgray@censusgray-desktop:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
 #        
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:0:16:0"
    Screen          0
EndSection

Section "Device"
 #        
    Identifier     "device1"
    Driver         "vesa"
    BoardName      "vesa"
    BusID          "PCI:0:16:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
        Modes      "800x600@72" "800x600@75" "800x600@56" "800x600@60" "640x480@75" "832x624@75" "640x480@72" "1024x768@75" "640x480@60" "1024x768@70" "1024x768@60" "1152x864@75" "1280x1024@75" "1280x960@60" "1280x1024@60" "1280x960@75" "1400x1050@60" "1600x1200@60"
    EndSubSection
EndSection

Section "Screen"
 #        
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

censusgray@censusgray-desktop:~$ 

```

---

### Post by johnlvs2run on 2008-08-02
You might browse this thread for some additional suggestions.
[http://ubuntuforums.org/showthread.php?t=822315](http://ubuntuforums.org/showthread.php?t=822315)

---

### Post by blazercist on 2008-08-03
if you try to run the fullscreen games froma terminal are there any errors in terminal?

---

### Post by johnlvs2run on 2008-08-03
Thanks to Jualin for the part in bold, the resolution is finally staying put.

download latest driver from Nvidia
[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)

sudo apt-get install build-essential libxft-dev
alt-cntr-F1
sudo /etc/init.d/gdm/ stop
cd /home/loginname/Desktop/downloads/
sudo sh NVIDIA-Linux-x86-177.13-pkg1.run
yes, ok, yes, ok
cd ... (optional)
cntr-alt-del ... (or sudo /etc/init.d/gdm restart)

> applications > accessories > terminal
**sudo nvidia-settings**
leave the terminal on until all steps are completed

back to the desktop 
> applications > system tools > nvidia X server settings
> X server display configuration 
> "tab" to resolution
> "space bar" to open
> "arrow" to 1280x800 or whatever you want 
> apply > save to X > quit.

---

