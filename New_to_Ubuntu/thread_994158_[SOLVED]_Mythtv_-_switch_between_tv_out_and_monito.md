---
title: "[SOLVED] Mythtv - switch between tv out and monitor"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Hospadar on 2008-11-26
EDIT AGAIN:

Figured it out, instead of ```
sudo nvidia-settings
``` I did ```
sudo nvidia-settings -c :0.0
``` to control the primary X screen.

***************
EDIT:
My bad, I'm trying to do this over ssh, which is probably the problem, because I suspect nvidia-settings is looking at my current (remote) xserver.

Is there a way to tell nvidia-settings which x-server I want it to configure so I can manage it remotely?

****************
Hi,
I've had mythbuntu installed for a while, and I just re-installed with 8.10

I'm wondering if there is a way to switch between tv-out and a monitor.  I enabled tv-out in the setup and it works fine, but now and then I'd like to plug in a monitor to do some things.

My first thought was to use nvidia-settings, but that complains that I'm not using nvidia drivers (which is not the case):
```
luke@luke-tron:~$ lsmod | grep nvidia
nvidia               6900560  38 
i2c_core               31892  9 tuner_simple,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,v4l2_common,tveeprom,nvidia
agpgart                42184  2 nvidia,intel_agp

```

I didn't see anything in mythbuntu-control-centre to this effect.  If anyone knows how to toggle this (or convince nvidia-settings that I am in fact using their driver) please do let me know

also here's xorg.conf:
```
luke@luke-tron:~$ cat /etc/X11/xorg.conf

Section "Module"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "1"
    #Option         "UseDisplayDevice" "TV"
    Option          "ConnectedMonitor"      "TV"
    Option         "TVOutFormat" "COMPOSITE"
    Option         "TVStandard" "NTSC-M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x480" "800x600" "640x480"
    EndSubSection
EndSection

```

---

