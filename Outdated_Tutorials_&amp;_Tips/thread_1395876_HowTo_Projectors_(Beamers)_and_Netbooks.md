---
title: "HowTo: Projectors (Beamers) and Netbooks"
date: 2010-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Ares Drake on 2010-02-01
This how-to is based on [_a German wiki_]("http://wiki.ubuntuusers.de/RandR"), the man page of randr and some own experiments. It addresses some projector detection and configuration problems in Karmic:


I just upgraded a first generation Atom netbook from Jaunty to Karmic. It has the ordinary Intel GMA950 integrated graphics,
lspci | -grep VGA gave me:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
```

Using a projector on the external VGA port was no problem and worked "out-of-the-box" in Jaunty, though both the internal display (native resolution 1024x600) and the projector (native resolution 1024x768) would only display at a resolution of 800x600 in mirrored mode, so the picture quality wasn't the best. But at least the projectors were reliably detected and auto-configured.

After the upgrade, more often than not the projectors were not detected at all and showed "no signal" at their VGA inputs. I don't know if it is because some of these projectors are rather old and maybe don't send any information of what resolutions they are capable so auto-configure fails or because of regressions in Intel's drivers not detecting them properly or because of something entirely different.

As the projector output wasn't working reliably out of the box, I googled around a bit and came to the following solution, witch I'd like to share here: I use scripts to manually set the display modes via randr. The following ONLY sets the projector as a clone of the internal screen, for desktop enlargement you would have to make different scripts.


[SIZE="4"]**Step by step guide:**[/SIZE]

**1. First, edit your /etc/X11/xorg.conf**
[INDENT](e.g. with ALT+F2 -> gksu gedit /etc/X11/xorg.conf) and add the following lines in the screen section:

```
SubSection "Display"
        Virtual    1024 768
EndSubSection
```

Afterwards, you xorg probably looks like this:
```

#comment lines are removed
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
	        Virtual    1024 768
	EndSubSection

EndSection
```

This is necessary to have the option of using resolutions larger than 1024x600 up to 1024x768 even if the projector is not connected and detected at the start of the xserver. If you want resolutions greater 1024x768 replace that value with e.g. 1920x1080 for home cinema projectors.
[/INDENT]



**2. Use one or more of the following scripts:**
[INDENT]The following scripts can be used to set the desired video output. You can use only one or multiple scripts depending on situations and your preferences. I think they are pretty much self explanatory. Just copy+paste them to a new file, name that somescript.sh and place it in a convenient place like /home/yourusername/scripts. Make them executable with 
```
chmod +x /home/yourusername/*.sh
```
and finally you can make application menu shortcuts or desktop shortcuts to them for easy access. 


Script 1: Sets VGA output to 1024x768 (native resolution for most projectors) and sets internal display to scale the same image to 1024x600. I mostly use this script, it gives me crystal sharp projector images at native resolution and I still have the ability to see the whole picture on the netbook, though it looks a little weired there because of the scaling.
```
#!/bin/bash
# ~/Scripts/1024scale.sh
# change display settings to clone mode, 1024x768 pix for VGA (projector) and scales it to the resolution of 1024x600  of the internal display
xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768
xrandr --fb 1024x768
xrandr --output VGA1 --mode 1024x768
xrandr --fb 1024x768 --output LVDS1 --mode 1024x600 --scale 1x1.28 --panning 0x0
```


Script 2: Sets VGA output to 1024x768 (native resolution for most projectors) and sets internal display to off
```
#!/bin/bash
# ~/Scripts/1024off.sh
# Sets VGA output to 1024x768 (native resolution for most projectors) and sets internal display to off
xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768
xrandr --fb 1024x768 --output VGA1 --mode 1024x768
xrandr --output LVDS1 --off
```


Script 3: Sets VGA output to 1024x768 (native resolution for most projectors) and sets internal display to diplay an 1024x600 part of it with panning. 
```
#!/bin/bash
# ~/Scripts/1024scale.sh
# sets VGA output to 1024x768 and sets internal display to diplay an 1024x600 part of it with panning. 
xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768
xrandr --output VGA1 --mode 1024x768
xrandr --fb 1024x768 --output LVDS1 --mode 1024x600 --panning 0x768 --scale 1x1

```

Script 4: Change display settings to clone mode, 800x600 pix for VGA (projector) and  internal display. This is my fallback option.

```
#!/bin/bash
# ~/Scripts/800clone.sh
# change display settings to clone mode, 800x600 pix for VGA and  projector
xrandr --output VGA1 --off
xrandr --output LVDS1 --off
xrandr --fb 800x600 
xrandr --output VGA1 --mode 800x600 --rate 60
xrandr --output LVDS1 --mode 800x600 --same-as VGA1 --auto --scale 1x1 --panning 0x0
```[/INDENT]

I hope this will be useful to some and may save a couple presentations from technical problems :-)

---

### Post by wieman01 on 2010-02-01
Wunderbar!

---

### Post by myszka on 2010-02-01
Great tutorial!

In my case (Jaunty Netbook Remix and EeePC 901) pressing Fn-F5 key (switch display) generates (out of the box):
1. Two head configuration
2. VGA+LVCD (800x600 mode) in parallel
3. Only VGA (native beamer/monitor resolution)
4. Only LVCD

And this is enough (for me) in most situations.

But your solution for panning or scaling on lcd looks very interesting :-)

Once again, thanks!

---

### Post by Ares Drake on 2010-02-02
> **myszka said:**
> In my case (Jaunty Netbook Remix and EeePC 901) pressing Fn-F5 key (switch display) generates (out of the box):
1. Two head configuration
2. VGA+LVCD (800x600 mode) in parallel
3. Only VGA (native beamer/monitor resolution)
4. Only LVCD

And this is enough (for me) in most situations.


Yeah, on Jaunty my Asus EEE1005HE (with eeetray installed) behaved the same way. Just after the dist-upgrade the detection of projectors was no longer reliable. Fn+F5 just said: "External monitor not detected". I could have lived with 800x600 as well, that seems to be the highest common resolution the two display devices announce as being capable of, as displayed by
```
radr
```
witch is probably why it gets selected for parallel (clone) mode by auto-detection. However as auto-detection didn't work reliably, I was forced to dig for manual settings anyway and once I found out how to manually set the modes, adding scaling or panning was a no-brainer :)

---

### Post by msmoore on 2010-03-14
Hello,
 

 I have an Acer Apire One Zg5 AOA 150-1049 and it's running Ubuntu 9.10.  When I plug it into the Infocus Projector, the screen goes blank, or flickers and the computer crashes.  I've searched the net for info, but nothing seems just like my computer (for instance the answer above)__
 

 

 My video card info is:
 -display:0              
        description: VGA compatible controller  
        product: Mobile 945GME Express Integrated Graphics Controller  
        vendor: Intel Corporation  
        physical id: 2  
        bus info: pci@0000:00:02.0  
        version: 03  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list rom  
        configuration: driver=i915 latency=0  
        resources: irq:16 memory:58480000-584fffff ioport:60c0(size=8) memory:40000000-4fffffff(prefetchable) memory:58500000-5853ffff  
   *-display:1 UNCLAIMED  
        description: Display controller  
        product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller  
        vendor: Intel Corporation  
        physical id: 2.1  
        bus info: pci@0000:00:02.1  
        version: 03  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: latency=0  
        resources: memory:58400000-5847ffff  
 

 So the Infocus projector says my computer  stats are such when plugged in:
 resolutions 1024x768
 verticial refresh 59.8 HZ
 horizontal refresh is 48.20 kHz
 

 The config file on X11 is called XvMCConfig
 

 The display gui in Ubuntu says I have  
 1024x600 for 16:9
 640X480 for 4:3
 It crashes when I choose either
 

 Hope someone can help me.
 

 Thanks
 

 
I was hoping to have find a simpler answer than the above.  I tried to look for THAT config and I don't have it.

---

### Post by lavezarez on 2010-03-17
Thanks, Ares! Your guide helped me get the projector working finally :D

I modified your scripts into just two:
1. Enabling VGA output for projector @ 1024 x 768, and having the laptop LCD have the same res:
```
#!/bin/bash
# ~/Scripts/1024scale.sh
# change display settings to clone mode, 1024x768 pix for VGA (projector) and scales it to the resolution of 1024x600  of the internal display
xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768
xrandr --fb 1024x768
xrandr --output VGA1 --mode 1024x768
xrandr --fb 1024x768 --output LVDS1 --mode 1024x768 --scale 1x1 --panning 0x0
```2. Disabling the VGA output, and restoring the laptop's LCD to 1280 x 800 res:
```
#!/bin/bash
# ~/Scripts/1024off.sh
# Sets Internal display output to 1280x800 (native resolution for my Lenovo G400) 
# and sets VGA output to off
xrandr --output VGA1 --off
xrandr --fb 1280x800 --output LVDS1 --mode 1280x800 --auto
```

---

### Post by TomBrooklyn on 2011-05-24
What is a beamer?

---

### Post by wieman01 on 2011-05-24
> **TomBrooklyn said:**
> What is a beamer?
A projector... "beamer" is the German word for "projector". Don't ask me why Germans call a projector "beamer" (not a car!) and a cell phone "handy". :-)

---

