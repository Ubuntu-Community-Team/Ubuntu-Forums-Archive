---
title: "Resolution Problem"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by orix on 2008-05-24
After the installation of Edgy 6.10 I have a problem with the resolution not being able to change from anything besides 800x600, so I have a problem with  not being able to see the bottom of some of the screens, and see very little in the screens.  I'm running a AMD Semprom 3000+ processor with a nVidia GeForce 4 MX graphics on a Dell SE198WF moniter. Any help would be great.

---

### Post by diablo75 on 2008-05-24
In terminal, type:

```
sudo gedit /etc/X11/xorg.conf
```

In the file when it opens, replace the monitor section with this stuff:

```
Section "Monitor"
Identifier "DELL SE198WF"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1440x900"
Horizsync 31.5-56.0
Vertrefresh 56.0 - 65.0
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
modeline "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
modeline "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
Gamma 1.0
EndSection
```

And the Screen section too:

```
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Integrated Graphics Controller"
Monitor "DELL SE198WF"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1440 900
Modes "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
EndSubSection
EndSection
```

Then save and restart the computer.

---

### Post by Enthralled on 2008-05-24
You can also try:

```
sudo nvidia-xconfig
```

If you are using proprietary nVidia video card drivers.

---

### Post by orix on 2008-05-26
That fixed that, but the Problem I'm having now is that the windows are Maxed out and I can't see the top of them to unmax and the top of the prompt for the terminal is also off the top of the moniter.  Is there anything I can do about this new problem?

---

### Post by mips on 2008-05-26
Specifying the correct sync ranges for your monitor might help. These you will find in your monitors hardware specs.

Edit: Oops, sorry did not see you aready answered my question.

---

