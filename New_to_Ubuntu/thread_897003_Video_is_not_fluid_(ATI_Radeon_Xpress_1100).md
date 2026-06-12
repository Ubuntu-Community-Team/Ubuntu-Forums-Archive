---
title: "Video is not fluid (ATI Radeon Xpress 1100)"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by joey_breizh on 2008-08-21
Hi,

I just switched from Windows Vista to Ubuntu (so I'm very new to Linux) and I was surprised to find that video in VLC is not fluid, especially when there's fast motion. It only happens if I play a video full screen, if I leave it to its original size it looks fine. 

I didn't use to do that under Windows with the same PC, so I'm thinking there's something I need to tweak in my video settings to make it right, but I have no clue what or where to start. Someone on the VLC forums mentioned something about video acceleration but in Ubuntu I don't know how or where to check if that's running or how to make sure I have the right drivers installed.

Like I put in the title line, my graphic card is an ATI Radeon Xpress 1100.

Thanks for your help! :)

---

### Post by Thingymebob on 2008-08-21
make sure youre running the ATI drivers
type **fglrxinfo** into a terminal
if the vendor is not ATI then:

open a terminal and enter
```

sudo apt-get install linux-restricted-modules-generic retricted-manager xorg-driver-fglrx

depmod -a

```

then edit xorg.conf
```

gksudo gedit /etc/X11/xorg.conf
```
find the section that reads something like
```

    SECTION "Device"
            Identifier "ati.........

```

add the following before **that** EndSection
```
Driver "fglrx"
```

Last one:
```

sudo aticonfig --initial -f
```

restart and you should be done do the first step again to confirm.

---

### Post by joey_breizh on 2008-08-21
Thank you! Vendor is indeed ATI, I get this when I enter fglrxinfo in a terminal:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

Now how do I check the drivers are up to date?

---

### Post by Thingymebob on 2008-08-22
goto system > administration > hardware drivers
if the *ati accelerated graphics driver* box is checked then your system will automatically be keeping them up to date

Adding the following in your xorg.conf may improve things (gksudo gedit /etc/X11/xorg.conf) - add to the same section that has the line Driver "fglrx"

first backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```

	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"

```
restart the X -server with ctrl+alt+backspace

then try each of the following 1 at a time restarting X after adding each one
```

Option      "AccelMethod"          "EXA"
Option      "MigrationHeuristic"   "greedy"
Option      "DRI"                  "true"
Option	    "TexturedVideo"	   "on"
Option      "UseFastTLS"           "0"
Option      "BlockSignalsOnLock"   "on"
Option	    "KernelModuleParm"     "locked-userpages=0"
Option      "ForceGenericCPU"      "off"

```

if X won't start after adding any of the above or other problems appear then remove the line you just added or restore the original with
```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

---

### Post by joey_breizh on 2008-08-22
Thank you! The box is checked so I wanted to try editing the xorg.conf.

But when I type the command in the terminal and it opens my xorg.conf, the file appears empty, and it won't let me save the file if I type anything in it... is there something ridiculously simple I'm missing?

---

### Post by Thingymebob on 2008-08-22
Linux is case sensitive make sure you're typing the path exactly as 
/etc/X11/xorg.conf
(capital X in X11(eleven))

You need to open it as root with - gksudo gedit /etc/X11/xorg.conf

---

### Post by joey_breizh on 2008-08-22
I was typing in double L instead of eleven, so that wasn't going to work... I've tried the first two and I get no video (but still audio) if I do that, so I went back and erased them and now I'm going to try the rest. I'll keep you posted.

---

### Post by joey_breizh on 2008-08-22
Looks like 

Option      "AccelMethod"          "EXA"

fixed the problem! Thank you so much.

---

### Post by joey_breizh on 2008-08-23
Weird - the image quality is back to being not good even though I haven't touched the xorg.conf again. It's like after the first time I reset the server, it looks fine, but if I shut down the computer and then turn it back on, it's back to looking crappy when in full screen...

---

