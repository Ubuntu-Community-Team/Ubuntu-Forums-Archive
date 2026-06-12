---
title: "compiz cube troubles"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-06-28
i have compiz installed and the compiz manager,i can get the wobbly windows 
and flames when you close a window but i dont know how to get the cube to work,i checked them off in the menu but nothing happens?what can i do ?
also when i check off extra in the visual effects it some times disappears but the effects still work.can somone help please,thank you
rixtr:confused:

---

### Post by Darkade on 2008-06-28
What's exactly the behavior you get when you press CRTL+ALT+RightArrow or leftArrow

could you please run the compiz config settings manager in a terminal by typing this
```
ccsm
```
and then pase the output when you try to enable the cube?

---

### Post by ConMan318 on 2008-06-28
For the cube, you also have to make sure you have 4 columns of workspaces.  So enable it, as well as right-click in the bottom right corner of your desktop on the workspaces, select 'preferences', and set it to 4 columns and 1 row.  Then press Alt + Ctrl + Left-click and you should have the cube effect.

---

### Post by gila_monster on 2008-06-28
Did you enable both "Desktop Cube" and "Rotate Cube?" You'll need both to get the rotation effect.

---

### Post by mbarvian on 2008-06-28
> **ConMan318 said:**
> For the cube, you also have to make sure you have 4 columns of workspaces.  So enable it, as well as right-click in the bottom right corner of your desktop on the workspaces, select 'preferences', and set it to 4 columns and 1 row.  Then press Alt + Ctrl + Left-click and you should have the cube effect.

not necessarily, I'm running it with 10 columns :)

---

### Post by ConMan318 on 2008-06-28
> **mbarvian said:**
> not necessarily, I'm running it with 10 columns :)

True, I just meant that he should be sure he changed it from the default 2, or it could have the cube enabled but wouldn't look like it.

---

### Post by Malibyte on 2008-06-30
I'm having issues with it, too.  I think something got clobbered after an upgrade, because I had the cube and other effects working fine until this weekend.  Now I no longer have the cube (and I did reset the desktop to four columns from two).  I also have "wobbly windows" enabled, and that's no longer working either...so I figure something's amiss with a global desktop environment configuration someplace.  Maybe compiz isn't actually running ;-/


Here's what's in /etc/compizconfig/config:

[general]
integration = true
backend = ini

[gnome_session]
integration = true
backend = gconf

[kde_session]
integration = true
backend = kconfig


If anyone can clue me into whatever obvious fix I'm missing, I'd appreciate it!
Thanks
Bob

---

### Post by RomeReactor on 2008-06-30
Hi. What video card do you have? Post the output of this:
```
glxinfo | grep rendering
```
If you're unsure whether Compiz is active or not, open the System Monitor (System->Administration->System Monitor) and see if you can find **compiz.real**; if you find **metacity**, then Compiz is not enabled.
Or, to try to enable Compiz:
```
compiz --replace
```
and post the output if it doesn't run.

---

### Post by Vindicate86 on 2008-06-30
I cant enable Wobbly Windows or Fire or Cube... Here's what happens when I do your code thinger..

xxxxx@xxxxx-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by RomeReactor on 2008-06-30
Vindicate86: Your current display setup is not allowing you to enable Compiz; this might be due to having VIA or SiS integrated video, or having an ATI or nVidia card, but without enabling their restricted drivers in 'System->Administration->Hardware Drivers'. What video card do you have? Run this to find out:
```
lspci -nn | grep VGA
```
and post the output.

---

### Post by hopelessone on 2008-06-30
>  Originally Posted by mbarvian  View Post
not necessarily, I'm running it with 10 columns 

Wouldn't that then be a pentagonal trapezohedron or deltohedron not a cube?

hehe..

---

### Post by Malibyte on 2008-06-30
Hmmm....

```

rcs@yoda: ~]$ glxinfo | grep rendering
Error: glXCreateContext failed

```


Here's the /etc/X11/xorg.conf file (no change from previous)
```


Section "Extensions"
        Option  "Composite"     "Enable"
EndSection

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons" "true"
EndSection

Section "Module"
        Load "dbe" # Double-Buffering Extension
        Load "v4l" # Video for Linux
        Load "extmod"
        Load "type1"
        Load "freetype"
        Load "glx" # 3D layer
        Load "fbdevhw"
        Load "record"
        Load "/usr/lib/xorg/modules/extensions/libglx.so"
EndSection

Section "Device"
        Identifier      "7600GT #0"
        Driver          "nvidia"
EndSection

Section "Module"
        Load "dbe" # Double-Buffering Extension
        Load "v4l" # Video for Linux
        Load "extmod"
        Load "type1"
        Load "freetype"
        Load "glx" # 3D layer
        Load "fbdevhw"
        Load "record"
        Load "/usr/lib/xorg/modules/extensions/libglx.so"
EndSection

Section "Device"
        Identifier      "7600GT #0"
        Driver          "nvidia"
        Busid           "PCI:3:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NvAGP" "1"
        Option          "NoLogo"        "False"
        Option          "UseEvents"     "True"
        Option          "SLi"           "False"
        Option          "TwinView"
        Option          "TwinViewOrientation" "Clone"
        Option          "MetaModes" "1920x1200, 1920x1080_60 @1920x1200; 1920x1200, 1808x1016_60 @1808x1200"
        Option          "HorizSync"   "CRT-0: 30-80;  DFP-0: 30-90"
        Option          "VertRefresh" "CRT-0: 50-61;  DFP-0: 50-75"
        Option          "ConnectedMonitor" "CRT, DFP"
EndSection


Section "Monitor"
        Identifier      "ViewSonic LCD"
        HorizSync       30-80
        VertRefresh     50-61
        Option          "DPMS"
        Modeline        "1920x1200" 150.75 1920 2016 2048 2185  1200 1202 1208 1235
        Modeline        "1680x1050" 119.12  1680 1728 1760 1840  1050 1052 1058 1080
        Modeline        "1440x900"  119.12  1440 1728 1760 1840  900 1052 1058 1080
EndSection

Section "Monitor"
        Identifier      "Samsung HDTV"
        VendorName      "Samsung"
        ModelName       "HLT-5687S"
        HorizSync       30.0-90.0
        VertRefresh     50.0-75.0
        ModeLine        "1808x1016_60" 152.5 1808 1920 2112 2416 1016 1017 1020 1052 -hsync +vsync
        ModeLine        "1920x1080_60" 172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
        ModeLine        "1600x900_60"  119.00  1600 1696 1864 2128  900 901 904 932  -HSync +Vsync
        ModeLine        "1280x720_60"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "7600GT #0"
        Monitor         "ViewSonic LCD"
        Defaultdepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1920x1200" "1680x1050" "1440x900" "1600x1200" "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        Inputdevice     "Generic Keyboard"

        Inputdevice     "Configured Mouse"
EndSection

Section "ServerFlags"
        Option          "BlankTime"     "15"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "30"
EndSection

```

It appears that glx should be getting loaded.  However, it looks like something's amiss with the nvidia driver (I compiled it myself rather than using the deb package).  This is odd, because it worked last week.  From /var/log/Xorg.0.log:

```

 (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.05
(II) NVIDIA(0): Detected PCI Express Link width: 16X

```

Well, I've been putting off upgrading the kernel.  I guess I can go ahead and do it now.....!

---

### Post by Vindicate86 on 2008-06-30
> **RomeReactor said:**
> Vindicate86: Your current display setup is not allowing you to enable Compiz; this might be due to having VIA or SiS integrated video, or having an ATI or nVidia card, but without enabling their restricted drivers in 'System->Administration->Hardware Drivers'. What video card do you have? Run this to find out:
```
lspci -nn | grep VGA
```
and post the output.

01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8800 GT [10de:0611] (rev a2)

Found the Hardware Drivers thinger as well. Thanks

---

### Post by RomeReactor on 2008-06-30
> **Malibyte said:**
> Well, I've been putting off upgrading the kernel.  I guess I can go ahead and do it now.....!

Seems you upgraded from either Dapper or Gutsy; all the xorg.conf files I've seen on fresh installs are mostly empty, only referring to the video card as a "Configured Device". If you're going to install a new kernel, make sure you also install its restricted modules.

---

