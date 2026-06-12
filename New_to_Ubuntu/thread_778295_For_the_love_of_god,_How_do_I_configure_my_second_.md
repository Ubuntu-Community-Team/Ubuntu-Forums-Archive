---
title: "For the love of god, How do I configure my second monitor!?!!"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by leotemp on 2008-05-01
I have been through a dozen xorg.cong tutorial pages and tried every combo of unbelievable complex BS in the book and I still cant up the rez on my second monitor in twinview I am so frustrated right now and nobody seems to have an answer. Isnt there a gui or some sane way of doing what amounts to something every commercial OS does out of the box?

---

### Post by tamoneya on 2008-05-02
if you have an nvidia graphics card like I do you can try ```
sudo apt-get install nvidia-settings
sudo nvidia-settings
```
This will launch a GUI which will allow you to configure with twin view

---

### Post by blazercist on 2008-05-02
Step 1: calm down
Step 2: You have to tell us which video card you have.
Step 3: You have to tell us if you are using Compiz
Step 4: You have to tell us your monitor resolutions.
Step 5: You have to paste your xorg.conf

---

### Post by leotemp on 2008-05-02
sorry, ive been at this forever, I have nvidia settings installed but it doesnt have any rez for the second monitor aside from 640x480

VIDEO CARD: Nvidia Geforce 8800GTS 512

COMPIZ: I have compiz installed but im not sure if its running, right now i have desktop effects disabled.

Monitor 1 rez: 1680x1050
Monitor 2 rez: 1280x1024


XORG:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Monitor"
	Identifier	"Gateway Monitor"
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Monitor		"Gateway Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by MaindotC on 2008-05-02
Thank you - now can you tell us what troubleshooting steps you've already tried so we don't ask you to do repeat things?

---

### Post by leotemp on 2008-05-02
Ive tried editing the xorg to different specs found online and clicked on everything in nvidia settings in every combo possible (i think) but aside from wild thrashing I dont even know where I would begin to trouble shoot.

---

### Post by tamoneya on 2008-05-02
I have 8600 GTS which is similar enough to what you have.  Try the nvidia-settings suggestion in my earlier post.

---

### Post by leotemp on 2008-05-02
I have but like i said, it doesn't provide any resolution options for my second monitor. After enabling twinview the only options are 320x240 and 640x480

---

### Post by MaindotC on 2008-05-02
Ok, did you try rebooting with the 2nd monitor attached or did you add the 2nd monitor after you booted the machine?

---

### Post by leotemp on 2008-05-02
its been attached since before installation.

---

### Post by gandaran on 2008-05-02
just a dumb question
did you try using the screens and graphics gui?

---

### Post by leotemp on 2008-05-02
I have tried the screen resolution UI and the NVIDIA settings UI. The screen resolution UI doesn't appear to allow me to manipulate the second monitor in any way. The NVIDIA settings show the second monitor but has no options whatsoever unless i enable Twinview, after enabling Twinview my only option for increasing the resolution is 320x240 and 640x480. FYI when i enable Twinview the monitor does activate but is at 640x480. I have also disabled dekstop background effects just in case, still no love :(

---

### Post by gandaran on 2008-05-02
> **leotemp said:**
> I have tried the screen resolution UI and the NVIDIA settings UI. The screen resolution UI doesn't appear to allow me to manipulate the second monitor in any way. The NVIDIA settings show the second monitor but has no options whatsoever unless i enable Twinview, after enabling Twinview my only option for increasing the resolution is 320x240 and 640x480. FYI when i enable Twinview the monitor does activate but is at 640x480. I have also disabled dekstop background effects just in case, still no love :(

okay, did you really use the screen and graphics gui? I'm not talking about the screen resolution gui.
on screen and graphics gui, if you have a second monitor plugged in it'll show up and you can make some changes.   
by the way scr/graphics only show up in the menus of hardy 8.04 if you enable it using the system » preferences » main menu

---

### Post by GavinZac on 2008-05-02
or from the command line:

sudo displayconfig-gtk

---

