---
title: "Power Outage Now Screen Resolution is Messed Up"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by x000111 on 2013-09-02
I've been looking into this for a while now and can't find anything newer than 2010 and dealing with xorg.conf... so it's all outdated as far as I can understand. The power in my house went out yesterday while my computer was on. When I rebooted my screen resolution won't auto detect past 1024x768. In the settings menu, the highest resolution is 1360x768 (not right for my monitor) but when I choose it it just goes to 1024x768 again.

When I change the settings under the nVidia server settings manager, it changes but still, 1360x768 is lower resolution than I had before. My monitor supports 1440x900.. I'm not sure that I had exactly that before. All I know is that I had a higher resolution than 1360x768 and it worked fine for me.

I'm really not sure what output would be useful... all that comes to mind is the following. Any direction or solution will be greatly appreciated.

```

uname -a
Linux xanStation 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:46:08 UTC 2013 i686 athlon i686 GNU/Linux

```

Here is a little info from nvidia-smi:

NVIDIA-SMI 4.304.88   Driver Version: 304.88
GeForce 7300 GT

I've tried running `dpkg-reconfigure xserver-xorg` and ` dpkg-reconfigure-xserver-xorg-video-all` with no success.

---

### Post by whitesmith on 2013-09-02
What does Systems Settings->Appearance give you?

---

### Post by x000111 on 2013-09-02
It just gives me options for the theme, as usual. Should I be looking for something specific?

I've also just removed all of my nVidia drivers just to see what would happened since after running `nvidia-xconfig` made it so I could only have a 640x800 resolution. Now I'm back to square one, with only 1027x768.

---

### Post by x000111 on 2013-09-02
After messing around with xrandr I was able to get the old resolution back (without nvidia drivers installed still). Could someone tell me how to add this to the xorg.conf in Ubuntu 13.04? I tried creating the file below but after rebooting, my screen went back to 1024x768.

FILE: /usr/share/X11/xorg.conf.d/10-monitor.conf
NOTE: The Modeline was produced by `cvt` and worked perfectly when implemented with `xrandr`.
```

Section "Monitor"
  Identifier "Monitor0"
  Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection
Section "Screen"
  Identifier "Screen0"
  Device "VGA-1"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1440x900_60.00" "1024x768"
  EndSubSection
EndSection



```

---

