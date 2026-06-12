---
title: "ATI Radeon 7500 Wrong Resolution Dual Monitor with HDMI"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by tbone3421 on 2012-09-22
I'm having trouble with a second monitor in a fresh installation of  12.04LTS.  I'm on a desktop with an ATI Radeon 7500 and I have two  identical LG monitors that each support 1920x1080.   The second monitor  is connected with HDMI and seems to work fine at resolutions less than  1920x1080.  The DVI monitor is working correctly at 1920x1080.  I've  been trying to follow various posts on these forums, installing  fglrx and the updated version as well.  I've also set the resolution  for both monitors in the Catalyst Control Center as well as in the  Ubuntu Displays setting, and everything is set to 1920x1080.  Am I missing a modeline or something?  Can anyone tell me why the monitor works for everything except this  resolution? I'm pretty stuck at this point.   Thanks so much in advance  for any advice at all.

Perhaps I have installed the drivers incorrectly, or in the wrong order? 

Additionally,  fglrxinfo yields the following:
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7500 Series
OpenGL version string: 4.2.11627 Compatibility Profile Context

A copy of my /etc/X11/xorg.conf file is pasted here:

Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "0-DFP5"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "1920 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "0-DFP6"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "ATI radeon 6870"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[1]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP5" "0-DFP5"
        Option      "Monitor-DFP6" "0-DFP6"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3840 1920
                                                                  1,1           Top


The xrandr command yields:

 xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 3840 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+   50.0     59.9     30.0     25.0     30.0  
   1776x1000      50.0     59.9     25.0     30.0  
   1680x1050      50.0     60.0  
   1400x1050      50.0     60.0  
   1600x900       50.0     60.0  
   1360x1024      50.0     60.0  
   1280x1024      50.0     75.0     60.0  
   1440x900       50.0     60.0  
   1280x960       50.0     75.0     60.0  
   1152x864       50.0     59.9     75.0  
   1280x768       50.0     75.0     60.0  
   1280x720       60.0     50.0     59.9  
   1024x768       50.0     75.0     60.0  
   1152x648       50.0     59.9  
   800x600        50.0     75.0     60.3     56.2  
   720x480        50.0     60.0     59.9  
   640x480        50.0     75.0     60.0     59.9  
DFP6 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      59.9*+
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       75.0     60.0  
   1152x864       59.9     75.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3     56.2  
   640x480        75.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)


Any advice at all is greatly appreciated, pretty stumped on this one.

---

### Post by QIII on 2012-09-22
Did you copy your entire xorg.conf correctly?

```
Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3840 1920
                1,1           Top

```is odd.  The Section and SubSection are not matched with EndSubSection and EndSection

```
Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3840 1920
                1,1           Top
        EndSubSection
EndSection

```Take a look at that again.

Not that that's all that may be wrong here, but I'm checking out the rest.

Here's mine, by way of example

```

Section "Monitor"
    Identifier   "0-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP4"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "61"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3840 1920
        Depth     24
    EndSubSection
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP3" "0-DFP3"
    Option        "Monitor-DFP4" "0-DFP4"
    BusID       "PCI:1:0:0"
EndSection

```

---

### Post by tbone3421 on 2012-09-22
> **QIII said:**
> Did you copy your entire xorg.conf correctly?

```
Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3840 1920
                1,1           Top

```is odd.  The Section and SubSection are not matched with EndSubSection and EndSection

```
Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3840 1920
                1,1           Top
        EndSubSection
EndSection

```Take a look at that again.

Not that that's all that may be wrong here, but I'm checking out the rest.

I must have messed up the copy/paste somehow.  So embarrassing!  Here is the current version:

Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "0-DFP5"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "1920 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "0-DFP6"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "ATI radeon 6870"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[1]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP5" "0-DFP5"
        Option      "Monitor-DFP6" "0-DFP6"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3840 1920
                Depth     24
        EndSubSection
EndSection

---

### Post by QIII on 2012-09-22
Do you have Xinerama on?

---

### Post by tbone3421 on 2012-09-22
> **QIII said:**
> Do you have Xinerama on?

In Catalyst Control Center the Xinerama box is grayed out because I "currently have only one desktop enabled".  Not sure what this means.  I do not desire cloned monitors, but rather a big single desktop that spans both monitors, which is what I have now except the second monitor's resolution is wacky.  Even though its set to 1920x1080, it appears significantly smaller than that, not filling up the entire monitor.

---

### Post by QIII on 2012-09-22
Ack.  Yeah.  Xinerama wouldn't be available, then.

Which driver do you have and how did you install it?

---

### Post by tbone3421 on 2012-09-22
> **QIII said:**
> Ack.  Yeah.  Xinerama wouldn't be available, then.

Which driver do you have and how did you install it?

I've been trying different drivers.  How can I determine which one is currently in use?

---

### Post by tbone3421 on 2012-09-22
> **QIII said:**
> Ack.  Yeah.  Xinerama wouldn't be available, then.

Which driver do you have and how did you install it?

jockey-text -l
xorg:fglrx_updates - ATI/AMD proprietary FGLRX graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
kmod:wl - Broadcom STA wireless driver (Proprietary, Enabled, In use) [auto-install]
xorg:fglrx - ATI/AMD proprietary FGLRX graphics driver (Proprietary, Enabled, In use)


I believe I installed this from Synaptic, which is 'supposed' to remove conflicting items.

---

### Post by QIII on 2012-09-22
Let's get back to that in a minute.  I'm going to have you cat something, but it'll return a lot of info and I'll have to tell you where to look.  I want to check something before we go into all that.

First...

Open CCC.

Under "Display Manager", click each of your monitors.  On the "Adjustments" tab, make sure each of them has "Use display for scaling" checked and Graphics processor scaling is set to "Scale image to full panel size"

Edited:  Removed some text in case someone follows this.  Solution below.

---

### Post by tbone3421 on 2012-09-22
> **QIII said:**
> Let's get back to that in a minute.  I'm going to have you cat something, but it'll return a lot of info and I'll have to tell you where to look.  I want to check something before we go into all that.

First...

Open CCC.

Under "Display Manager", click each of your monitors.  On the "Adjustments" tab, make sure each of them has "Use display for scaling" checked and Graphics processor scaling is set to "Scale image to full panel size"

EDIT:  OK, hold the boat!  A couple of things.  Let me have a moment to type.  Be right back.

Confirmed that those items are indeed checked.

---

### Post by tbone3421 on 2012-09-22
> **tbone3421 said:**
> Confirmed that those items are indeed checked.

Oddly enough though, under Display Manager it is listing one monitor as Digital Monitor (2) and the other problematic monitor as DTV(1).  Not sure if that is meaningful.

---

### Post by tbone3421 on 2012-09-22
FIXED IT!!!!   The problem is the sliding bar in the Scaling Options somehow defaulted to a non-zero percentage.  By changing it to zero, the image fits the screen.   Thank you very much for helping me sort through this mess.

---

### Post by QIII on 2012-09-22
Good!

Never mind about reinstalling then!

The fglrx-updates package is a pain, and using the GUI "Additional drivers" install method often results in oddities.

Glad it worked out.

Now, I accept my fees in cash in non-sequential, unmarked, small denomination US currency deposited by courier in my Swiss bank account ...

;)

---

### Post by NikTh on 2012-09-22
> **QIII said:**
> 
Now, I accept my fees in cash in non-sequential, unmarked, small denomination US currency deposited by courier in my Swiss bank account ...

:lolflag:

---

