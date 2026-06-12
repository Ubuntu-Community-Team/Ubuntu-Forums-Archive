---
title: "Resolution"
date: 2010-01-22
forum: Philippine Team
---

### Post by stupidchunk on 2010-01-22
I know this has been asked a lot of times but I'm still having a hard time figuring it out.

I have the nvidia drivers installed but Hardware Settings won't show the resolution my monitor usually runs at. It stops at 800x600 but it can reach up to 1280x1024. I tried configuring xorg.conf but to no avail. Everytime I add the modes subsection in xorg.conf and save it, it still doesn't show up when i recheck it. My monitor is a Likom L506E7N.

Hopefully these will help:

This is what I get when I run cat /etc/X11/xorg.conf

> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


This is what I get when I run sudo ddcprobe

> vbe: VESA 3.0 detected.
oem: NVidia
vendor: NVidia Corporation
product: NV11 Board Chip Rev B2
memory: 65536kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 80x60 (text)
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
edid: 
edid: 1 0
id: 1080
eisa: LKM1080
serial: 0000219f
manufacture: 38 2003
input: sync on green, analog signal.
screensize: 28 21
gamma: 2.800000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@75 Hz (VESA)
timing: 800x600@56 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@60 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 640x480@85
ctiming: 800x600@85
dtiming: 640x350@70
dtiming: 640x400@70
dtiming: 640x400@76
dtiming: 640x400@85


Thanks.

---

### Post by upbeatfury@yahoo.com on 2010-01-22
What type of NVIDIA card you have?, and did you install the nvidia driver for linux via nvidia.com?

---

### Post by stupidchunk on 2010-01-22
How would I know which nvidia card I have? I installed it via Hardware Drivers. It says there that it's version 96.

---

### Post by upbeatfury@yahoo.com on 2010-01-22
nvidia website currently on maintenance. so try to download the drivers for nvidia after a little bit and have that install in your system and see if your going to have nvidia manager so you can change up to 1280x1024.

---

### Post by stupidchunk on 2010-01-22
The UK site is working. How would I know which version to download? Thanks.

---

### Post by upbeatfury@yahoo.com on 2010-01-22
What nvidia card do you have?

---

### Post by upbeatfury@yahoo.com on 2010-01-22
And are you using 32bit or 64 bit linux?

---

### Post by loell on 2010-01-22
the problem lies mostly at the monitor's refresh rate, have you downloaded your drivers via **system menu**--> **Administration** --> **Hardware drivers** yet? it's probably the best route.

---

### Post by stupidchunk on 2010-01-22
> **loell said:**
> the problem lies mostly at the monitor's refresh rate, have you downloaded your drivers via **system menu**--> **Administration** --> **Hardware drivers** yet? it's probably the best route.

Yeah, that's what I did. Another thing, I set my resolution at 800x600 but everytime I reboot it goes back to 640x480. What should I do about my refresh rate? I'm having a hard time finding out my horizsync and vertrefresh kasi di naman kilala yung brand ng monitor ko. I read using ddcprobe will show it but in the log I posted earlier, I don't think naka-indicate yung horizsync and vertrefresh. Wala kasi yung 'monitorrange' which shows them.

---

### Post by loell on 2010-01-22
execute **nvidia-settings** in super user mode, in **X Server Display Comnfiguration** just lower the refresh rate. do trial and error from their on, to get the right rate.

---

### Post by stupidchunk on 2010-01-22
That worked for saving my settings everytime I reboot but the options for higher resolutions still do not show up.

---

### Post by loell on 2010-01-23
what are the available resolutions in there?

---

### Post by aljoriz on 2010-01-23
this assumes that you have install the nvidia driver.  

at the terminal type:
sudo rm /etc/X11/xorg.conf
then:
gksu nvida-settings
(write password)
go to X server display configuration adjust to the desired  resolution (i.e.1024x768) >APPLY>SAVE TO XCONFIG

Now write this on the save X box:
/etc/X11/xorg.conf

press save and you are done ... found this on the web upd8 blog.  Hope  this helped someone

---

### Post by stupidchunk on 2010-01-23
> **loell said:**
> what are the available resolutions in there?


Here are the resolutions listed:

832x624
800x600
720x450
720x400
680x384
640x480
640x400
640x350
576x432
512x384
416x312

There's actually a lot more but the lowest is 320x175

Here's my xorg.conf

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LKM"
    HorizSync       31.0 - 56.0
    VertRefresh     56.0 - 85.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768_60 +0+0; 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    Modes       "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection


---

### Post by stupidchunk on 2010-01-23
> **aljoriz said:**
> this assumes that you have install the nvidia driver.  

at the terminal type:
sudo rm /etc/X11/xorg.conf
then:
gksu nvida-settings
(write password)
go to X server display configuration adjust to the desired  resolution (i.e.1024x768) >APPLY>SAVE TO XCONFIG

Now write this on the save X box:
/etc/X11/xorg.conf

press save and you are done ... found this on the web upd8 blog.  Hope  this helped someone

rm will delete xorg.conf, right? I don't wanna delete in fear that something bad might happen but I followed the steps after that.

I got this error though: Failed to parse existing X config file '/etc/X11/xorg.conf'!

And in the terminal it said: VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Monitor "Configured Monitor" referenced by Screen "Default Screen".

---

### Post by loell on 2010-01-23
hmm, strange, there should be higher resolutions on the list.

try backing up xorg.conf  **sudo cp etc/X11/xorg.conf etc/X11/xorg.conf.backup **, then delete it, start nvidia-settings, see if there will be higher resolutions for your chooosing.

---

### Post by stupidchunk on 2010-01-23
Nope. Ganon pa din. Pero yung Modes part sa xorg.conf nawala after ko gawin yan. 

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LKM"
    HorizSync       31.0 - 56.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768_70 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768_70 +0+0; 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

