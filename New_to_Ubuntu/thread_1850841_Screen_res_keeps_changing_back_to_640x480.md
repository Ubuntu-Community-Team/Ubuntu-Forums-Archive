---
title: "Screen res keeps changing back to 640x480"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by psylencer on 2011-09-27
Hi,  I have a older TV screen : Sharp LC32AF3X

It's stated native screen res (as stated by sharp) is 960 x 540 px 

When I run xrandr it tells me the max resolution is 720x576 and the current resolution is 640x480.  When i change the display settings to anything other than Auto, the screen reverts back to 640x480 auto upon restart. 

Basically I cant make the screen res changes permanent.  I have tried changing the settings in both Nvidia-settings and the applications>settings>display option and every time I restart they are both set back to "Auto 640x480".

Can someone please point me in the right direction?

Also no matter what I do I cant get the desktop to fill my screen. any tips?

Thanks in advance.

---

### Post by realzippy on 2011-09-27
Show content of your xorg.conf file...

```
cat /etc/X11/xorg.conf
```

---

### Post by pndragon on 2011-09-27
The desktop I'm using now does not have nvidia but the previous one did and it had much the same problem.

The thing about nvidia-settings is that it can change your screen size but it won't save the configuration unless you have opened it as the superuser. The best way is from the command-line:

```
sudo nvidia-settings
```

---

### Post by psylencer on 2011-09-27
xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Extensions"
	Option	"Composite"	"on"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"DPI"	"100x100"
	Option	"NoLogo"	"1"
	Option         "TripleBuffer" "True"
EndSection

BTW using ubuntu 11.04

OK will give it a try.  BTW, I tried 1920x1080 which is available and what I would prefer, the screen seems to accept the input res even though its native res is much lower but doesn't resize the desktop.  What im left with is a really small desktop in the middle of the screen.  Any suggestions?

---

### Post by psylencer on 2011-09-27
ok tried running sudo nvidia-settings - no change - screen res keeps changing back to auto upon reboot.

Any other suggestions?

---

### Post by realzippy on 2011-09-28
You cannot run any larger resolution than 960x540,this is your panel's native.
You do not get that resolution offered in nvidia-settings?

---

### Post by Immolatus on 2011-09-28
you need to edit xorg.conf to include the desired resolution. or you might need to generate your own as ubuntu's handling is less straight forward for the last two distributions. xorg.conf goes in xorg.conf.d you can force compatible resolutions there. try the xorg wiki for howto.

---

### Post by Grenage on 2011-09-28
Just for fun, see if this config works; it's sparse, as I don't have much info.  It should be enough:

Backup the old config:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Make a new one, paste the info in, and save:
```
gksu gedit /etc/X11/xorg.conf
```

```
Section "Monitor"
   Identifier "Monitor0"
Modeline "960x540_60.00"   40.75  960 992 1088 1216  540 543 548 562 -hsync +vsync
EndSection

Section "Device"
   Identifier    "Device0"
   Driver        "nvidia"
   Option        "NoLogo"	"1"
   Option        "TripleBuffer" "True"
EndSection

Section "Screen"
   Identifier    "Screen0"
   Device        "Device0"
   Monitor       "Monitor0"
   DefaultDepth  24
   SubSection    "Display"
      Depth      24
      Modes      "960x540"
   EndSubSection
EndSection

Section "Extensions"
   Option	 "Composite"   "on"
EndSection
```
Once done, you can restart X, or restart the PC.  If it didn't turn out well, you can simply delete the new conf from the command line.

---

### Post by psylencer on 2011-09-29
> **realzippy said:**
> You cannot run any larger resolution than 960x540,this is your panel's native.
You do not get that resolution offered in nvidia-settings?

No - not there.  Strangely the screen accept 1080i input, however this creates a very small box in the middle of the screen.  THe higher the res - the smaller the box appears.

---

### Post by psylencer on 2011-09-29
> **Grenage said:**
> Just for fun, see if this config works; it's sparse, as I don't have much info.  It should be enough:

Backup the old config:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Make a new one, paste the info in, and save:
```
gksu gedit /etc/X11/xorg.conf
```

```
Section "Monitor"
   Identifier "Monitor0"
Modeline "960x540_60.00"   40.75  960 992 1088 1216  540 543 548 562 -hsync +vsync
EndSection

Section "Device"
   Identifier    "Device0"
   Driver        "nvidia"
   Option        "NoLogo"	"1"
   Option        "TripleBuffer" "True"
EndSection

Section "Screen"
   Identifier    "Screen0"
   Device        "Device0"
   Monitor       "Monitor0"
   DefaultDepth  24
   SubSection    "Display"
      Depth      24
      Modes      "960x540"
   EndSubSection
EndSection

Section "Extensions"
   Option	 "Composite"   "on"
EndSection
```
Once done, you can restart X, or restart the PC.  If it didn't turn out well, you can simply delete the new conf from the command line.

Will try and get back to you - although was thinking about changing the frequency to 50hz as that's what TVs run on in Aus.

---

