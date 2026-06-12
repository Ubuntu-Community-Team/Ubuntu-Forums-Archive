---
title: "Losing 1024x768 resolution when nvidia drivers are installed"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by mabari99 on 2012-03-09
I'm new to ubuntu and converted an old window box dell dimension 4600  with 1G memory and an 80G hard drive. Also it has an Nvidia GEFORCE  Fx5200 card. I managed to install 10.04, and stepped my way up to 11.10.  Unfortunately, I have not been able to use the NVIDIA drivers, either  proprietary or open source, and so I can't get to really see what Unity  really can do. After literally days of experimenting and having to  re-install twice, I have now settled on Gnome Classic, which I have  tweaked to my satisfaction, and I have actually got the cube working,  which I love. I have discovered that the etc/X11/xorg.conf file does not  exist in this environment, so I'm assuming that somehow the OS knows  what the hardware is and allows Compiz to interact with the Gnome  fallback. Unfortunately Gnome won't run, shows gobbledegook and Ubuntu  (which I believe is Unity) does not work properly without the Nvidia  drivers. However, if I install ANY of the drivers, I lose the resolution  which drops down to 800x600 from 1024x768 and no matter what I try, I  can't get it back. I believe that my hardware should be able to work  with the other, later shells, but I would really love someone  knowledgeable to confirm this and tell me exactly how to install the  drivers without blowing up my resolution. Thanks for all your help!

---

### Post by Grenage on 2012-03-09
Greetings.

You have a couple of choices here, you can try and set the correct resolution using [xrandr]("https://wiki.archlinux.org/index.php/Xrandr"), or we can put in an xorg.conf (will get used if present).  I lean towards the latter, other lean towards the former.  If you can reply with your monitor make/model, that will help.

---

### Post by mabari99 on 2012-03-09
I'm using a vga cable to connect me to a samsung 19" HD LCD TV. I would prefer to use the xorg.conf file too, but I'm really gunshy about loading up any of the nvidia drivers. Please give me instructions how to get back the configuration I have, if something goes wrong, at least I know things work in Gnome Classic.

---

### Post by mabari99 on 2012-03-10
bump

---

### Post by dekom on 2012-03-10
When you installed the nvidia driver, did you check nvidia-settings to see if the driver is reading your card information correctly?

Otherwise, this may be a case of the driver no longer supporting your card.

Also, you can let nvidia-settings generate a xorg.conf file for you, and I believe that configuration will be loaded, despite xserver's auto-detect.

---

### Post by Bobhuber on 2012-03-10
> **mabari99 said:**
> I'm using a vga cable to connect me to a samsung 19" HD LCD TV. I would prefer to use the xorg.conf file too, but I'm really gunshy about loading up any of the nvidia drivers. Please give me instructions how to get back the configuration I have, if something goes wrong, at least I know things work in Gnome Classic.
You will most likely have to create the xorg.conf file before installing the drivers from nvidia's site. Just tell the installer not to update the file (it will ask). Specify the resolution for your card 1024X768 and the monitor type as CRT in the xorg.conf. 
Back up the system if your concerned about torching something.
Heres MY config using just my TV for a monitor . YOU WILL HAVE TO CHANGE IT TO MATCH YOUR SYSTEM
```
Section "Module"
    Load           "extmod"
    SubSection     "extmod"
        Option         "omit DPMS"
    EndSubSection
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "VIZ VL420M"
    HorizSync       31.0 - 70.0
    VertRefresh     50.0 - 77.0
    
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by mabari99 on 2012-03-10
Tried this, but did not work. Tried many other options in xorg.conf, but got the dreaded 'Mode not Supported' message. Pressed ctrl alt f1 keys, got to login, logged in and dumped xorg.conf file. Rebooted. Came back up but in 800x600. Removed xvidia drivers. Now I can boot every time, but it has lost the 1024x768 resolution. What is it the system is reading to keep the lower resolution when there are no nvidia drivers and no xorg.conf file. Anyone give me a clue about this. And many thanks to you guys who have taken the trouble to reply.

---

### Post by mabari99 on 2012-03-12
I have tried everything I can, loading each driver in turn, removing them. I have learned the hard way that I have to remove the xorg.conf file when I activate any of the drivers, or it will cause the system to not boot, and I have to then get to a root screen and remove the xorg.conf. The worst scenario was when I couldn't even do that so I had to run ubuntu from a cd and mount the hard drive on the computer in write mode and then go and remove the xorg.conf file. I have found that if I remove the drivers and the xorg.conf file, I get the proper resolution, but of course no compiz settings work. If I leave the driver activated but no xorg.conf file, I get back the compiz settings, but the resolution is 800x600 and is almost impossible to work with. So there we have it, I need some total genius in writing xorg.conf files to show me what I can put into it that will fix the boot and resolution problems. Are you out there, my genius friend, I need you now!!!

---

### Post by Grenage on 2012-03-12
Hello again, and sorry for the delayed reply (weekends are always busy).

I don't suppose you have the model number of that TV?

---

### Post by mabari99 on 2012-03-12
I hope this is what you mean:

From the label on the back of the TV:

Model Number:  LN19A330J1D

My eyes aren't so good now, it's possible the 1's are l's and the 0 is O, but I think not.

---

### Post by Grenage on 2012-03-12
Ok, assuming that you've installed the proprietary driver (additional hardware), try this as an xorg.conf:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Samsung"
	ModelName "LN19A330J1D"
	HorizSync 31 - 80
	VertRefresh 60 - 75
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "Nvidia Fx5200"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1440x900"
	EndSubSection
EndSection
```

The native resolution of the TV seems to be 1440x900 with PC use, according to the manual; I've put in some rough numbers for the frequency ranges, but added a modeline for the native resolution.

If anything goes wrong, you should be able to restore normal operation by deleting the config file.

---

### Post by mabari99 on 2012-03-12
Found this brilliant thread:
[Ubuntu Forums]("http://ubuntuforums.org/archive/index.php") > [The Ubuntu Forum Community]("http://ubuntuforums.org/archive/index.php/f-130.html") > [Main Support Categories]("http://ubuntuforums.org/archive/index.php/f-327.html") > [Desktop Environments]("http://ubuntuforums.org/archive/index.php/f-329.html") > [SOLVED] Stuck in low res after Nvidia driver install (Ubuntu 10.10)

Thank you so much Anthonyvo

Based on what he said in his post, I modified my xorg.conf and this is what I came up with:

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Samsung"
        ModelName      "LN19A330J1D"
        HorizSync       31.0 - 61.0
        VertRefresh     50.0 - 90.0
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "CRT: 1024x768 +0+0"
        #Option         "metamodes" "1024x768 +0+0"
        SubSection "Display"
                Depth       24
        EndSubSection
EndSection

Section "Module"
        Load           "extmod"
        Load           "glx"
        SubSection "extmod"
                Option         "omit DPMS"
        EndSubSection
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "keyboard"
EndSection

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
        # generated from default
EndSection

Section "Device"
        Identifier     "Device0"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce XF 5200"
        Option "IgnoreEDID" "1"
        Option "NoDDC"
        Option  "NoLogo"        "True"
EndSection

I'm pretty sure it was the IgnoreEDID that did it, as it was not working properly and I have found lots of google results for this.

Anyway, I now have the correct resolution AND the compiz settings, at least on Gnome Classic. When I use Ubuntu on login, I get the correct resolution, but when I click the desktop wall icon, I only get 1 desktop, not 4. I figured that I would change compiz settings and remove the desktop cube and replace with desktop wall. But every time I try to change a setting in Compiz Manager, the program closes without accepting changes. Ah well! I guess you take it bit by bit with Linux. Looks like this could be another bug, so I'll mark this one solved and open another for compiz.

Many thanks to all who helped me.

---

