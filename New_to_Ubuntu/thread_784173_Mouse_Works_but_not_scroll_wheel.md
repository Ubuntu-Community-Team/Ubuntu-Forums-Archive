---
title: "Mouse Works but not scroll wheel"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by wandman on 2008-05-06
Hi guys,

I am totally new to Linux, I have installed xubuntu 8.04 and it seems to be working fine except I cannot get my mouse scroll wheel to function. I am using a standard infra red ps2 mouse with two buttons and a scroll wheel that you can also click.

My laptop also has a trackpad. It is working fine, could there be a conflict?

Any advice would be appreciated.

---

### Post by wandman on 2008-05-07
Uh oh,

I found a tutorial that told me to edit the xorg.conf to look like this:

```
Section "InputDevice" 
    Identifier   "Configured Mouse" 
    Driver       "mouse" 
    Option       "CorePointer" 
    Option       "Device" "/dev/input/mice" 
    Option       "Protocol" "ExplorerPS/2" 
    Option       "Buttons" "5" 
    Option       "ZAxisMapping" "4 5" 
EndSection
```

Now my mouse isn't recognised and my trackpad doesn't work. I really am stuck now as I don't know any keyboard shortcuts to even begin to fix it.

---

### Post by tyroeternal on 2008-05-07
I think that what you needed to do was simply add these two lines into the section for your mouse that was already in your xorg.conf file:
> Option       "Buttons" "5"
Option       "ZAxisMapping" "4 5" 

If you simply added that whole section I would try removing it again, and just adding those two lines.  Hopefully you made a backup of your xorg.conf file before you modified it! (This is a GOOD practice to get into).

If you are comfortable enough with the command line, after you login just press *Ctrl + Alt + F2*.  This will drop you to a command line :D.  Now to edit your xorg.conf file you will want to type:
```
sudo nano /etc/X11/xorg.conf
```
Make your changes to the file as neccessary and then hit ```
Ctrl + x
``` to save and close the program.

If you did, in fact, make a backup file of your xorg.conf then get to the command line like I showed you and type:
```
sudo mv [location of backup] /etc/X11/xorg.conf
```

Hopefully one of these routes will work for you!  After you've made the changes you can just type in:
```
exit
```
to log out, and then hit *Ctrl + Alt + F7* and that should bring you back to your normal world.

Before the new settings take effect you need to restart X... in gnome you can just press ```
Ctrl + Alt + Backspace
```.  I'm not sure about xfce, so instead of logging out of the command line and going back to xfce you can type:
```
sudo shutdown -r now
```
to restart the computer.

Let me know how it goes!

---

### Post by wandman on 2008-05-08
Thanks tyroeternal,

That all seems to make sense but when I type in sudo nano /etc/X11/xorg.conf at the command line I see the editor but it loks like the file is blank (or it has created a blank file for me to start writing). I foolishly didn't make a backup of my xorg.conf file.

I am surprised that it is blank as all I did was accept the changes when I closed mousepad when I edited the file in the first place.

Any ideas?

---

### Post by tyroeternal on 2008-05-08
Well, to generate a new xorg.conf from scratch you just have run a few more commands :D.

**Step 1**: Get to the command line again, like I showed you with *Ctrl + Alt+ F2*.

**Step 2**: Stop XDM (this is for xfce... gnome uses gdm, kde uses kdm). I Belive this should help with autodetecting hardware.```
sudo /etc/init.d/xdm stop
```

**Step 3**: Reconfigure xorg.  This is going to require answering some questions, but it should not be too difficult :). ```
sudo dpkg-reconfigure xserver-xorg
```

**Step 4**: Start up XDM ```
sudo /etc/init.d/xdm start
```

**Step 5**: Restart X / Restart the computer and therefore restart X.  (I'm not completely sure that this needs to be done since xdm was started and stopped, but its probably good policy to make sure)

Hopefully I didn't miss anything important because I am no expert at everything. Lemme know how it goes!

---

### Post by wandman on 2008-05-08
Thanks tyroeternal I managed to get the mouse and trackpad working again!

The problem I have now is that even though I have edited the xorg.conf file to have this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Buttons" "5"
	Option		"ZAxisMapping" "4 5"
EndSection
```

But the scroll wheel does not work. I can click the wheel and it acts just like a left click at the moment. CLicking and holding doesn't allow me to scroll either.

We're getting there slowly but surely. Thanks for your patience tyroeternal.

---

### Post by tyroeternal on 2008-05-08
HAHA, indeed, slow and steady.

Well, before we do anything lets backup our xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.orig.conf
```
Look back up at the previous post to see how to restore it should things go bad.

If the mouse connects with PS/2 it should look like this...
```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Protocol" "IMPS/2"
Option "Device" "/dev/input/mice"
Option "CorePointer" 
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "no"
EndSection

```
Note that instead of *ExplorerPS/2* which was used earlier you put in *IMPS/2*.  Also noteworthy: make sure that your touchpad section includes:```
Option "SendCoreEvents" "true"
```
This should make sure that both your mouse and touchpad can be used.

If this doesn't work out for you, please post your whole xorg.conf and we will see where to go next... but hopefully all goes smoothly!

---

### Post by wandman on 2008-05-09
I made the changes, the mouse still works as does the touchpad but still no scroll wheel. here is my xorg.conf file

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol" "IMPS/2"
	Option		"Device" "/dev/input/mice"
	Option		"Corepointer"
	Option		"Buttons" "5"
	Option		"ZAxisMapping" "4 5"
	Option		"Emulate3Buttons" "no"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"800x600@60"	"1024x768@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by tyroeternal on 2008-05-09
Hmm... It definitely appears to be as it should.  We will continue poking it with sticks until it works, though.

I searched around for scroll wheels not working and found a post that might help.  They suggested this layout, and said that for some reason the button numbers switched for them around the upgrade to ubuntu edgy:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol" "IMPS/2"
	Option		"Device" "/dev/input/mice"
	Option		"Corepointer"
	Option		"ZAxisMapping" "6 7"
	Option		"Emulate3Buttons" "yes"
EndSection
```

I suppose its worth a try!

---

### Post by wandman on 2008-05-10
Oh dear, I'm afraid that didn't work either.

I even tried adding back in the ```
Option  "Buttons" "5" 
```option and even tried 7 for the value as well.

I tried plugging in another mouse (USB) and the scroll wheel doesn't work for that either. I know that the scroll wheel does work on my PS2 mouse as I tried it on my XP system no problem.

Is it a lost cause? The strange thing is that since you started helping me the scroll wheel does work as a button, just not as the scroll function.

---

### Post by tyroeternal on 2008-05-13
I'm not sure what else can be done for it, but that doesn't mean you have to give up hope.  I would recommend posting in the hardware section of the forums, giving them the mouse's section of your xorg.conf, and see if anyone else can point you in the right direction.  Best of luck!

---

### Post by wandman on 2008-05-15
Thanks tyroeternal for all your help. I'll try the hardware section but I learned a lot following your steps.

Thanks again!

---

