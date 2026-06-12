---
title: "VGA mode not supported"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by evil_urna on 2008-08-23
I have a nvidia fx5500 card. I have been having this problem pretty much since the upgrade to hardy. When I boot up the system for some reason it goes to a refresh rate that my monitor cannot handle. It only seems to occur on the ubuntu loading screen and, more frustratingly, on pretty much any game that has a fmv. For example Diablo II. I can play the game just fine but I cannot see any of the opening videos.

I fixed this before by adding a modeline to my xconfig for the res and refresh rate that I wanted. but since hardy that does not work anymore. The nivida xserver settings seems to be in battle with ubuntu's display settings dialog, from what I can tell. If i set it to 1024X768 at 60hz in the nvidia panel it just changes back to "auto" refresh when I close it and go back. 

Any help would be greatly appreciated

---

### Post by nitro_n2o on 2008-08-23
it might be the case that hardy have updated the nvidia driver and i think you nvidia driver should be the nvidia-glx-legacy, which works better with FX cards series ... 

check if you have the latest driver "nvidia-glx-new" and try downgrading the driver and see if that works

Just a suggestion, I'm not sure if it'll work or if it'll break any other thing

---

### Post by evil_urna on 2008-08-24
> **nitro_n2o said:**
> it might be the case that hardy have updated the nvidia driver and i think you nvidia driver should be the nvidia-glx-legacy, which works better with FX cards series ... 

check if you have the latest driver "nvidia-glx-new" and try downgrading the driver and see if that works

Just a suggestion, I'm not sure if it'll work or if it'll break any other thing

I tried installing via the package manager. I am not sure if that was wrong or not but it did not work. It broke the drivers a similar error as if I try to upgrade the drivers from the updates window. Whenever there is a update that involves video drivers I have to go back and manually install drivers. It is quite frustrating

---

### Post by glennric on 2008-08-24
The FX series cards are still supported by the nvidia-glx-new package.  Those are the ones you should use, not the legacy.  Do you have a "vga=???" line on the kernel line of /boot/grub/menu.lst?  Try removing or changing that.

It is also worth pointing out that mode lines in the xorg.conf file still work if your xorg.conf file is set up right.  You might also try running "sudo dpkg-reconfigure xserver-xorg" to get back to a default xorg.conf.

---

### Post by evil_urna on 2008-08-24
> **glennric said:**
> The FX series cards are still supported by the nvidia-glx-new package.  Those are the ones you should use, not the legacy.  Do you have a "vga=???" line on the kernel line of /boot/grub/menu.lst?  Try removing or changing that.

It is also worth pointing out that mode lines in the xorg.conf file still work if your xorg.conf file is set up right.  You might also try running "sudo dpkg-reconfigure xserver-xorg" to get back to a default xorg.conf.

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1c55bf9e-ed63-42f7-810e-746a372ee10d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1c55bf9e-ed63-42f7-810e-746a372ee10d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1c55bf9e-ed63-42f7-810e-746a372ee10d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1c55bf9e-ed63-42f7-810e-746a372ee10d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
this is the menu.list file  Also I tried reseting the xorg and all it did was break x :(

---

### Post by cwsnyder on 2008-08-24
To recover to the default X mode, select the recovery mode on GRUB.

There are a couple of places to point to modes into the xorg.conf.  Section "Monitor" has the listing for refresh rates, Horizontal and Vertical frequencies, etc.  Section "Screen", Subsection "Display" includes a line called Virtual which lists the default, or login display mode, then a line Modes which lists some of the modes your monitor can display, the first mode of which should match the Virtual line to correctly display the login screen.

Hope this helps.

cwsnyder

---

### Post by evil_urna on 2008-08-24
> **cwsnyder said:**
> To recover to the default X mode, select the recovery mode on GRUB.

There are a couple of places to point to modes into the xorg.conf.  Section "Monitor" has the listing for refresh rates, Horizontal and Vertical frequencies, etc.  Section "Screen", Subsection "Display" includes a line called Virtual which lists the default, or login display mode, then a line Modes which lists some of the modes your monitor can display, the first mode of which should match the Virtual line to correctly display the login screen.

Hope this helps.

cwsnyder

well i tried all of that to no avail. and now Diablo II has no video what so ever. but that is unrelated. I was ******* about in the wine reg on that one :)

---

### Post by evil_urna on 2008-08-24
> **evil_urna said:**
> well i tried all of that to no avail. and now Diablo II has no video what so ever. but that is unrelated. I was ******* about in the wine reg on that one :)

could this problem be caused by a faulty moniter? I tried my spare and it is working fine. any ideas

---

### Post by evil_urna on 2008-08-24
> **evil_urna said:**
> could this problem be caused by a faulty moniter? I tried my spare and it is working fine. any ideas

I should add that my old monitor is **** and I would very much rather not use it. I am rather attached to my LCD

---

### Post by zamadatix on 2008-08-24
if one monitor works with the grpahics card and one doesnt and you sa there both the same it looks like your stuck. (your monitor is still betetr than most ;) )

---

### Post by evil_urna on 2008-08-24
> **zamadatix said:**
> if one monitor works with the grpahics card and one doesnt and you sa there both the same it looks like your stuck. (your monitor is still betetr than most ;) )

well it works yea but it is a 15" CRT that is as old as john mccain. The crappy part is that I had it working before. I am going to post my xconfig file. is there anything out of order in this?

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Thu Jun  5 00:10:21 PDT 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
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
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    ModeLine       "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by evil_urna on 2008-08-24
> **evil_urna said:**
> well it works yea but it is a 15" CRT that is as old as john mccain. The crappy part is that I had it working before. I am going to post my xconfig file. is there anything out of order in this?

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Thu Jun  5 00:10:21 PDT 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
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
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    ModeLine       "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I reset from GRUB and that made Diablo 2 work but only in 2d mode. not really sure whats going on there but it is still failing out boot. on logout it is switching to 64x60 hz not sure why

---

