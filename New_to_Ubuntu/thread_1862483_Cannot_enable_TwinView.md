---
title: "Cannot enable TwinView"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by mopalia on 2011-10-16
Running Oneric, with a Samsung Synchmaster 1280x1024 as O, and Asus VH242H as 1.  When I try to enable Twinview, I get the message
"Failed to set MetaMode (1) 'DFP-0: nvidia-auto-select @1280x1024 +0+0, CRT-1: nvidia-auto-select @1920x1080 +1280+0' (Mode 3200x1080, id: 50) on X screen 0."  The X Configuration file says 
# Removed Option "TwinView" "0" 
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0" 
    Identifier     "Screen0" 
    Device         "Device0" 
    Monitor        "Monitor0" 
    DefaultDepth    24 
    Option         "TwinView" "1" 
    Option         "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1280+0" 
    SubSection     "Display" 
        Depth       24 
    EndSubSection 
EndSection

The Samsung works fine, but the Asus just gives a blank white screen.  How can I fix this?  Thanks.

---

### Post by papibe on 2011-10-16
Hi mopalia, there's a two different ways to go with this problem, depending if you have [Optimus]("http://www.nvidia.com/object/optimus_technology.html") or not.

Could you post the result of this command?
```
$ lspci -nn | grep -i vga
```
Regards.

---

### Post by mopalia on 2011-10-16
01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9500 GT] [10de:0640] (rev a1)

Sorry, miscopied before.

---

### Post by papibe on 2011-10-16
I have the exact same card!

Let's make sure you are using the card (the driver) before trying to configure Twinview.

First, just in case, backup your X configuration file:
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then, recreate the configuration file using this:
```
$ sudo nvidia-xconfig
```
Then restart your machine, and post the result of this command:
```
$ grep -i nvidia /var/log/Xorg.0.log
```
Tell us how it goes.
Regards.

---

### Post by mopalia on 2011-10-16
17.256] (II) Module glx: vendor="NVIDIA Corporation"
[    17.256] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:14:51 PDT 2011
[    17.257] (II) LoadModule: "nvidia"
[    17.258] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.258] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.258] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:57:12 PDT 2011
[    17.258] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.260] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.260] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.260] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    17.260] (==) NVIDIA(0): RGB weight 888
[    17.260] (==) NVIDIA(0): Default visual is TrueColor
[    17.260] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.260] (**) NVIDIA(0): Option "TwinView" "0"
[    17.260] (**) NVIDIA(0): Option "MetaModes" "DFP: nvidia-auto-select +0+0"
[    18.694] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc ASUS VH242H (CRT-1)) does
[    18.694] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[    18.764] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    18.764] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    18.765] (II) NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
[    18.765] (--) NVIDIA(0): Memory: 1048576 kBytes
[    18.765] (--) NVIDIA(0): VideoBIOS: 62.94.72.00.00
[    18.765] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    18.765] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    18.765] (--) NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0
[    18.765] (--) NVIDIA(0):     Ancor Communications Inc ASUS VH242H (CRT-1)
[    18.765] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
[    18.765] (--) NVIDIA(0): Ancor Communications Inc ASUS VH242H (CRT-1): 400.0 MHz
[    18.765] (--) NVIDIA(0):     maximum pixel clock
[    18.765] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    18.765] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    18.767] (II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
[    18.767] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[    18.767] (**) NVIDIA(0):     enabled on all display devices.
[    18.836] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    18.836] (II) NVIDIA(0): Validated modes:
[    18.836] (II) NVIDIA(0):     "DFP:nvidia-auto-select+0+0"
[    18.836] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    18.860] (--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
[    18.861] (--) NVIDIA(0):     option
[    18.861] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    18.861] (==) NVIDIA(1): RGB weight 888
[    18.861] (==) NVIDIA(1): Default visual is TrueColor
[    18.861] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    18.861] (**) NVIDIA(1): Option "TwinView" "1"
[    18.861] (**) NVIDIA(1): Option "MetaModes" "CRT: nvidia-auto-select +0+0"
[    18.861] (II) NVIDIA(1): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
[    18.861] (--) NVIDIA(1): Memory: 1048576 kBytes
[    18.861] (--) NVIDIA(1): VideoBIOS: 62.94.72.00.00
[    18.861] (II) NVIDIA(1): Detected PCI Express Link width: 16X
[    18.861] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    18.861] (--) NVIDIA(1): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0
[    18.861] (--) NVIDIA(1):     Ancor Communications Inc ASUS VH242H (CRT-1)
[    18.861] (--) NVIDIA(1):     Samsung SyncMaster (DFP-0)
[    18.861] (--) NVIDIA(1): Ancor Communications Inc ASUS VH242H (CRT-1): 400.0 MHz
[    18.861] (--) NVIDIA(1):     maximum pixel clock
[    18.861] (--) NVIDIA(1): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    18.861] (--) NVIDIA(1): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    18.862] (**) NVIDIA(1): TwinView enabled
[    18.862] (II) NVIDIA(1): Display Device found referenced in MetaMode: CRT-1
[    18.862] (WW) NVIDIA(1): TwinView requested, but only 1 display devices found.
[    18.862] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID has been
[    18.862] (**) NVIDIA(1):     enabled on all display devices.
[    18.881] (II) NVIDIA(1): Assigned Display Device: CRT-1
[    18.881] (II) NVIDIA(1): Validated modes:
[    18.881] (II) NVIDIA(1):     "CRT:nvidia-auto-select+0+0"
[    18.881] (II) NVIDIA(1): Virtual screen size determined to be 1920 x 1080
[    18.884] (--) NVIDIA(1): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    18.884] (--) NVIDIA(1):     option
[    18.885] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    18.889] (II) NVIDIA(0): Setting mode "DFP:nvidia-auto-select+0+0"
[    18.970] (==) NVIDIA(0): Disabling shared memory pixmaps
[    18.970] (==) NVIDIA(0): Backing store disabled
[    18.970] (==) NVIDIA(0): Silken mouse enabled
[    18.970] (**) NVIDIA(0): DPMS enabled
[    18.971] (II) NVIDIA(0): [DRI2] Setup complete
[    18.975] (II) NVIDIA(1): Setting mode "CRT:nvidia-auto-select+0+0"
[    19.106] (==) NVIDIA(1): Disabling shared memory pixmaps
[    19.106] (==) NVIDIA(1): Backing store disabled
[    19.106] (==) NVIDIA(1): Silken mouse enabled
[    19.106] (**) NVIDIA(1): DPMS enabled
[    19.107] (II) NVIDIA(1): [DRI2] Setup complete

Still a white screen. Restart?

---

### Post by papibe on 2011-10-16
White screen? Not good.

Could post the entire log (/var/log/Xorg.0.log)?
Use [http://paste.ubuntu.com/]("http://paste.ubuntu.com/") to paste it, and then post the link.

Regards.

---

### Post by mopalia on 2011-10-16
Hey, wait - IT WORKS!!!  Thank you  a thousand times.  You are a virtual God.  

(want to talk about my sound problems now?)

Thanks again.

---

### Post by mopalia on 2011-10-16
Oh, rats.  It opened a few documents and pictures, still with the white background.  Then when I closed them, it went back to a green screen (my usual background) and the menus disappeared.  The cursor still travels to the monitor, but it changes to an X on the Asus.  Back where I started 2 days ago. :(

---

### Post by papibe on 2011-10-16
Sorry to hear that, but it looks like we are getting closer.

Let's take a look at the complete log, it may be some clues there.

Regards.

---

### Post by mopalia on 2011-10-16
I'm having some trouble getting the log - never done this one before. 
 sudo /var/log/Xorg.0.log  gets a command not found response, so I'm obviously doing something wrong.

---

### Post by papibe on 2011-10-16
Try this:
```
$ cat /var/log/Xorg.0.log
```
Regards.

---

### Post by mopalia on 2011-10-16
Sorry for the delay, got called AFK.  [http://paste.ubuntu.com/710443/](http://paste.ubuntu.com/710443/)  That's a lot of stuff!  Thanks for the introduction to the pastebin.  I'm learning . . .

---

### Post by papibe on 2011-10-16
Did you tried to set Twinview manually?

I would do it using the 'Nvidia X Server Settings'. To do it run this:
```
$ gksudo nvidia-settings
```
Configure your monitors there. When you are happy with the configuration, save the settings. To do that select 'X Server Display Configuration' from the left, and from the right 'Save to X Configuration File'.

Then restart to machine to see that settings are sticking

My guess is that the other monitor is a HDTV connected via a VGA cable? The monitors are so different that maybe 'Separate X Screen' could be a good option (instead of Twinview). BTW, that's what I'm using in my PC with a Dell Monitor and a Sony HDTV.

Tell us how it goes.
Regards.

---

### Post by mopalia on 2011-10-16
Yes, several times.  When I select TwinView and either hit apply or save the config, I get the error message that I started this thread with - still happens.  When I try the Separate X setting, I get "The current setting cannot be complete due to one or more of the following reasons:", followed by a list including location has changed, location type has changed, color depth has changed, X screen has been removed or added, and Xinerama has been enabled/disabled.  
I have the "apply what is possible" option - should I try that, or is this a lost cause?
Thanks again for your very valued support.

---

### Post by mopalia on 2011-10-17
Well,that was interesting.  It flipped the desktop to the Asus monitor, but even though the icons are there,nothing responds to the mouse.  It's a dead desktop.  And the Samsung is black and doesn't respond to anything once it has booted up.  I tried using the gksudo nividia-settings command from root (after booting back up) but it just tells me that it cannot open display.  So now I have no monitor working in Ubuntu.

---

