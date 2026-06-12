---
title: "Trouble making screen resolution change persistent"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by SurfaceThought on 2011-12-28
Hello All,

I am brand new to Ubuntu and so far it has been exciting as well as sometimes a frustrating learning experience. I happen to have Intel integrated graphics and apparently Ubuntu is not super friendly with Intel integrated graphics. 

I have been able to change to screen resolution to my native screen resolution by using the following XRandR commands:

```
xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1280x768_60.00
xrandr --output VGA1 --mode 1280x768_60.00
```

In order to make these changes persistent I have copied them into the /etc/gdb/gdbinit file. I restarted the computer, and I received a bunch of error messages saying that the OS could not make the screen resolution work. I copy and pasted the commands one at a time into the Terminal to make sure that the code that I had left in the gdbinit file was good. I copied the first line 

```
xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
```

and it executed fine. I entered the next line in 

```
xrandr --addmode VGA1 1280x768_60.00
```

And not only did it execute, but upon entering it the screen automatically re-sized to the correct resolution. The is strange to me because it is like the OS new that it was supposed to be in resolution mode ¨280x768_60.00¨, but the mode did not add correctly from the gdbinit file. I cannot figure out why it would work when I entered it into the terminal but it did not work when it was executed from the gdbinit file.

Has anyone wrestled with this problem? Any help is greatly appreciated.

--Evan

---

### Post by jtarin on 2011-12-28
Intel integrated graphics work just fine with Ubuntu. Normally any modeline settings are used in the "/etc/X11/xorg.conf" file. Do you have such a file? You also need to ensure you have the correct driver installed for your graphics chip.

Sample File Monitor Section:/etc/X11/xorg.conf
```
Section "Monitor"
Identifier "VGA"
# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
# 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
Modeline "1280x768_60.00" 80.14 1280 1344 1480 1680 768 769 772 795 -HSync +Vsync
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
Option "PreferredMode" "1024x768_60.00"
EndSection
Section "Monitor"
Identifier "LVDS"
Modeline "1280x768_60.00" 80.14 1280 1344 1480 1680 768 769 772 795 -HSync +Vsync
Modeline "1024x600_60.00" 48.96 1024 1064 1168 1312 600 601 604 622 -HSync +Vsync
Option "PreferredMode" "1280x768_60.00"
EndSection
Section "Device"
Identifier "Intel 945 GM"
Driver "intel"
Option "AccelMethod" "xaa"
EndSection
Section "Screen"
Identifier "Primary Screen"
Device "Intel 945 GM"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1440x900" "1280x768" "1280x1024" "1024x768" "640x480"
Virtual 1440 1792
EndSubSection
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Primary Screen"
EndSection
```

---

### Post by SurfaceThought on 2011-12-28
Thanks for the reply Jtarin!

First of all, I have no xorg.conf file. In fact, as far as I can tell, I have no ¨X11¨ folder in my /etc directory. In the research I have read, I have seen people recommend creating a xorg.conf file, however I was a little bit confused because I have no X11 folder. Does this mean that I need to create this folder as well? Additionally,  I think I would need a command in order to figure out what my monitors ¨name¨ is. I inherited it from my Grandfather and I have no idea what the model name is, so in your xorg.conf file, I don know what I would need to put where yours says ¨Intel 945 GM¨. I know it is a Dell and that is it.

As for the driver issue, I have not installed any drivers. The research I have done seems to imply that proprietary drivers tend to be unstable and possibly more trouble then they are worth. Most of the forums I have seen seem to recommend that Ubuntu should be smart enough to handle the graphics hardware after the necessary tweaking. I wouldn´t be surprised if this would fix the problem, however, as I am dual-booting this system with Windows 7 and windows was unable to recognize the proper screen resolution until I installed the drivers disk that came with the Desktop kit.

Do you recommend installing the driver? If so where do I find it, and how would I do it? I haven´t the slightest clue...

Again, thank you for your help.

--Evan

---

### Post by jtarin on 2011-12-28
First you will have to determine your chip.Use the command ```
lspci
```

---

### Post by SurfaceThought on 2012-01-02
Thanks for the help!

However, this problem is now a non problem, as I decided to install a friends old Nvidia 8800 GT into my PC. Now Ubuntu looks greater than ever, and I do not need to mess with loading any drivers.

---

