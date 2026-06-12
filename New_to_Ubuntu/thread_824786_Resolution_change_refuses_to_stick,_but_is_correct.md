---
title: "Resolution change refuses to stick, but is correct at login screen"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by PeteMason01 on 2008-06-10
So I'm starting to pull my hair out. :(

My setup is such:  I've got a laptop that is 'docked' to a monitor and keyboard and essentially never goes anywhere.  I'm trying to use the monitor as the only display, and not use the laptop monitor at all.  All is rosy at the login screen and everything is being displayed at the correct resolution (1680x1050).  However, as soon as I login, the monitor will revert to the laptop display's native resolution (1440x900) even though it is on the correct (external) monitor.

I've tried changing the settings using nvidia-settings as admin, but as soon as I shutdown/logout/restart X-server it just reverts back to what it was.  I can change the settings once I'm logged in without any issues.  For reference it *is* detecting the external monitor correctly/listing it with the correct name and resolutions.  The way it is currently set is with the laptop screen disabled (which it stays, even after reboot).

I've also tried using the Applications->Other->Screens & Graphics but that just seems to have bigger problems (such as shifting the entire desktop 4 inches to the right on the screen) and won't detect the external monitor correctly (it suggests odd refresh rates like 51 and 52, which I'm pretty sure aren't right).

I've taken a look at xorg.conf but can't seem to make heads nor tails of it.  I've also looked at some other forum posts, and have tried a load of suggestions including making xorg.conf unwritable, but all to no avail.

If anyone has any suggestions, they'd be greatly appreciated.  I'm inches away from permanently switching from Windows and this is the only major annoyance still standing in my way.

Finally, I'm using Ubuntu 8.04.

Cheers

Pete Mason


Below is the important looking part from my xorg.conf:

> Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L226W"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
**I deleted a few more resolutions here, it just continues down to 800x600**
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6600"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1680x1050@60 +0+0; CRT: nvidia-auto-select +0+0; CRT: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by PeteMason01 on 2008-06-10
OK, I think a little more fanangaling and I actually got it to stick.

I switched over to 'TwinView' in the nvidia settings and set the laptop display resolution to 'off'.  I've restarted X a few times and logged out and it seems to stick, so I'm not going to tinker and more and I'll just hope to hell that it stays.

Pete Mason

---

### Post by wolfen69 on 2008-06-10
in the future, use ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Rabreu on 2011-09-20
> **PeteMason01 said:**
> OK, I think a little more fanangaling and I actually got it to stick.

I switched over to 'TwinView' in the nvidia settings and set the laptop display resolution to 'off'.  I've restarted X a few times and logged out and it seems to stick, so I'm not going to tinker and more and I'll just hope to hell that it stays.

Pete Mason

Thank you very much. I had the exact same problem and your solution appears to work here as well.

---

### Post by realzippy on 2011-09-20
[:)]("http://www.google.com/imgres?q=zombie&start=234&num=10&hl=en&client=ubuntu&hs=Lo8&channel=fs&biw=1366&bih=574&tbm=isch&tbnid=c7M3qdHJZrvyaM:&imgrefurl=http://www.goodreads.com/book/show/535441.The_Zombie_Survival_Guide&docid=zZXCnnkf2s2t2M&itg=1&w=705&h=222&ei=yAR5TvGOCsqOswbUmpjRDw&zoom=1&chk=sbg")

---

### Post by Rabreu on 2011-09-20
I found another solution on another forum.
Delete the file ~/.config/monitors.xml. It's useless if you are using nvidia proprietary driver

---

### Post by skinnny on 2012-03-20
> **Rabreu said:**
> I found another solution on another forum.
Delete the file ~/.config/monitors.xml. It's useless if you are using nvidia proprietary driver

Cheers mate, this worked for me!

---

