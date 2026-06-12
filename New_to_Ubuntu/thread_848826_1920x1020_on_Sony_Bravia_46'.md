---
title: "1920x1020 on Sony Bravia 46'"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Vicario3 on 2008-07-03
I'm kinda new to the linux OS. Been with Winblows to long, glad I found ubuntu distro.

Anyways straight to my question. Hopefully someone will help me.


When I switch my resolution to 1920x1020, using nvidia-settings the screen is way to big.

I was wondering if there is anything I can do to my xorg.config file to fix this or adjust my screen with 1920x1020 resolution.

Video card: 7600gt   Driver Version: I'm using the nvidia-glx-new 169.xxxx

[PHP]
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       15.0 - 50.0
    VertRefresh     58.0 - 62.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"

 # 
    Identifier     "monitor2"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:5:0:0"
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"

 # 
    Identifier     "device2"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

Section "Screen"

 # 
    Identifier     "screen2"
    Device         "device2"
    Monitor        "monitor2"
    DefaultDepth    24
EndSection


[/PHP]

---

### Post by AnarkistNZ on 2008-07-03
Just a thought, would it not be smarter to run at the native resolution of your tv?

If it's 720p, then run 1280x720
It it's 1080p, then run 1920×1080

---

### Post by ZabiGG on 2008-07-03
Hi there...

What do you mean when you say your screen is way too big? If you mean that the image is clipped and you are missing some portions of the display, I just wrote about that [here]("http://ubuntuforums.org/showthread.php?t=848822")

If it's the case, you're not alone... there are hundreds of unresolved posts about this issue all over the linux and nvidia forums :(

Nvidia cards don't like HDTV, but the (rest of the) image quality is very, very nice... lol

Cheers,

Z.

---

### Post by Vicario3 on 2008-07-03
> 
Just a thought, would it not be smarter to run at the native resolution of your tv?

If it's 720p, then run 1280x720
It it's 1080p, then run 1920×1080


The native resolution from nvidia-settings is reading 1280x720_60(1)<720p

for some reason this is wrong. On my windows xp system, I had my 7600gt connected to this tv using DVI/HDMI connector. It correctly read my native resolution of 1920x1080 and fit my screen fine using 1920x1080.

So, right now I am running native resolution. 1280x720 "720p" which doesn't use all of my tv. Which sucks... I would like to use all of my tv.

Would installing updated drivers not in the ubuntu respo possibly help?

> 
Hi there...

What do you mean when you say your screen is way too big? If you mean that the image is clipped and you are missing some portions of the display, I just wrote about that here

If it's the case, you're not alone... there are hundreds of unresolved posts about this issue all over the linux and nvidia forums

Nvidia cards don't like HDTV, but the (rest of the) image quality is very, very nice... lol

Cheers,

Z.
_____


Yes, and your options of resolutions are almost exactly the same as mine.

When you figure this out "I understand that it might be possible to correct the overscan and lacking resolutions problem"

Please help me ahha.

---

### Post by ZabiGG on 2008-07-03
Let's agree to keep each other posted ;)

---

### Post by ZabiGG on 2008-07-06
Hi there,

Still haven't found a real solution, but at least I've found a workaround to make the overscan manageable. Just link to the abovementioned post.

Hope this helps,

Z.

---

