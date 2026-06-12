---
title: "[SOLVED] Desktop cube: friend or foe?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by SeanLor on 2008-06-10
Greetings, oh wise ones;

So, I'm just getting started with the wonderful world of Linux, and seem to be taking two steps forward & one step back. I had the desktop cube working, but now I can't enable 'normal' or 'extra' visual effects, and it makes me sad. :confused: Compiz check says:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```


Any suggestions? I'm really unfamiliar with the workings of Ubuntu, so step by step help in moron-friendly lingo would be grand. Thanks!

---

### Post by Epidemic_HardyBoy on 2008-06-10
Uhh. I dont know if this will work, seeing as I am as new as you.

buuuut..

System -> administration -> Hardware Drivers

Then uncheck the box if checked, then recheck it.

or just check it if unchecked, thats what happened to me once and that fixxed it.

---

### Post by SeanLor on 2008-06-10
Unfortunately the only hardware driver that shows up is for my wireless card. Even when the cube was working, said driver didn't show up for my checking/unchecking pleasure. Thanks for giving 'er a shot, though!

---

### Post by Nepherte on 2008-06-10
Don't worry about the video driver not popping up in the hardware restricted driver manager. That is only the case if you have a nvidia/ati card.

---

### Post by exile on 2008-06-10
what does your xorg.conf say (/etc/X11/xorg.conf) say for the Device and Module sections? Are any of the compiz effects working?

Have you tried enabling the Cube in Advanced Desktop Effects Settings?

---

### Post by SunnyRabbiera on 2008-06-10
The cube is fancy though its not really needed...
the standard virtual desktop manager should do, unless you are into the wow factor.

---

### Post by philinux on 2008-06-10
System >Prefs>Advanced desktop Settings.

Have you got this menu item?

---

### Post by Golem XIV on 2008-06-10
Intel's 965 chipset is supported out-of-the-box in Hardy and no restricted drivers are necessary or available.

I have the same chipset and everything is working fine.  You say Compiz was working fine before, which probably means that you did something that caused the problem.  Did you play with the xorg.conf file?

You can also try to
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see if it helps.

---

### Post by BDNiner on 2008-06-10
If you could post your /etc/X11/xorg.conf file i could see what is wrong. Intel cards are supported by default so there is probably a wrong setting.

---

### Post by SeanLor on 2008-06-10
Okay, so responding in order: 

Nepherte - cool, I was concerned as to why others had their video drivers showing up but mine was shy. Good to know that's no big deal, thx.

Exile - my xorg.conf is below, and yup, I've got the cube checked off in the adv. display settings. It was working very well, and then I monkeyed around with things to try & get videos to play on my TV (s-video, works great now), and I solved one problem but created another. And nope, one of the compiz effects are working.

[CODE] Section "InputDevice"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection /[CODE]


SunnyRabbiera - Yonder cube isn't necessary at all, but it's darn enjoyable. Like beer, y'know? You can live without it, but why? ;^)

Philinux - Yup, I sure do have yonder menu item, and all the fun settings I had when the cube worked are still checked off-cube gears, caps, 3D windows, etc. That's why I'm bloody perlexed by this whole thing; I know my comp can make it go, it just doesn't want to right now, for whatever reason.

Thanks for the responses, everyone! Let me know if I can provide any more specific info for you. Cheers!

---

### Post by philinux on 2008-06-10
Open a terminal then 

metacity --replace

Then

compiz --replace

Try the cube etc.

Post back any output.

---

### Post by SeanLor on 2008-06-10
Metacity --replace didn't spit out any text at me, but compiz --replace said:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by wPwLUi3N on 2008-06-10
I was never very comfortable with cube and other special effects. I think it requires much more work to be done on them. I recommend staying with original, they are slick enough for me at least.

---

### Post by philinux on 2008-06-10
[http://ubuntuforums.org/showthread.php?t=709672](http://ubuntuforums.org/showthread.php?t=709672)

check out post 3 & 19

---

### Post by SeanLor on 2008-06-10
Hrm...still no dice. I wish I had a bit more know-how, so as to more effectively communicate why that didn't help, but all I've got is "nope." Here's the text from my terminal after following the suggestions on posts 3 & 19:


seanuary@DellBot:~$ gksudo gedit /usr/bin/compiz
seanuary@DellBot:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
seanuary@DellBot:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
seanuary@DellBot:~$ SKIP_CHECKS=yes compiz --replace ccp &
Checking for Xgl: [1] 27360
seanuary@DellBot:~$ not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by SeanLor on 2008-06-12
Hmmm...seem to have hit a wall here. What's frustrating is the fact that all of Ubuntu's fancy effects DID work, and now they won't. Argh, says I.

---

### Post by Golem XIV on 2008-06-12
> **SeanLor said:**
> It was working very well, and then I monkeyed around with things to try & get videos to play on my TV (s-video, works great now), and I solved one problem but created another. And nope, one of the compiz effects are working.

It would be useful if you could tell us what you did to get the S-Video working, seeing that it's likely you screwed up Compiz getting it to work.

---

### Post by BDNiner on 2008-06-12
Looking at your xorg.conf file it seems like the inofrmation in the "Monitor" and "Screen" sections is missing. I have an Nvidia card so i could not tell you what should be in those sections. Also from the errors in post 15 it seems like xgl is not enabled. I have a section at the end of my xorg.conf file that reads
```

Section "Module"
        Load     "glx"
EndSection

```

But it is an Nvidia card not an Intel.

---

### Post by SeanLor on 2008-06-12
Good point, I suppose 'monkeyed around' isn't too specific! I searched 'nvidia' in Synaptic, and changed/added different packages in the hopes of getting the visual effects to work. (Not the best plan, without knowing what I was doing, I know.)  Not sure if it helps, but the packages I've got installed (once again after searching Nvidia) are as follows:

jockey-common
jockey-gtk
linux-restricted-modules-2.6.24-16-generic
linux-restricted-modules-2.6.24-18-generic
nvidia-glx-new
nvidia-kernel-common
nvidia-settings
smartdimmer
xserver-xorg-video-nv

I can get to & change the advanced desktop effects menu, but when I try to change Preferences-->Appearance-->Visual Effects to Normal or Extra it says 'desktop effects could not be enabled.' I hope this helps, if there's any more specific info that I can pass on, feel free & ask. Thanks!

---

### Post by BDNiner on 2008-06-12
I would not install any packages intended for Nvidia cards, they will not help you in this situation. I have an old dell laptop with an intel video card and i am looking up the settings for the xorg file now.

---

### Post by SeanLor on 2008-06-12
Awesome, thanks. Should I uninstall the nvidia packages, then? Is it possible that they've interfered? And other than re-installing Ubuntu, is there any way to roll the system back to a certain point, like the system restore function in Windows?

---

### Post by Golem XIV on 2008-06-12
> **SeanLor said:**
> Good point, I suppose 'monkeyed around' isn't too specific! I searched 'nvidia' in Synaptic, and changed/added different packages in the hopes of getting the visual effects to work. (Not the best plan, without knowing what I was doing, I know.)  Not sure if it helps, but the packages I've got installed (once again after searching Nvidia) are as follows:

jockey-common
jockey-gtk
linux-restricted-modules-2.6.24-16-generic
linux-restricted-modules-2.6.24-18-generic
nvidia-glx-new
nvidia-kernel-common
nvidia-settings
smartdimmer
xserver-xorg-video-nv

I can get to & change the advanced desktop effects menu, but when I try to change Preferences-->Appearance-->Visual Effects to Normal or Extra it says 'desktop effects could not be enabled.' I hope this helps, if there's any more specific info that I can pass on, feel free & ask. Thanks!

If you have an Intel graphics card, why did you install nvidia drivers?  Do you have an additional nvidia card in your system (the Intel 965 is usually included in the motherboard's chipset, so it is possible to have 2 video cards at the same time)?

If you don't have an additional nvidia card get rid of all the nvidia drivers, including xserver-xorg-video-nv

If you do have an additional nvidia card, I would suggest first that you disable the onboard Intel video and then get rid of the xserver-xorg-video-nv.  This is the open source driver that does not support 3D and therefore Compiz.

---

### Post by BDNiner on 2008-06-12
did you try and resetup your video card using?
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by FrostDust on 2008-06-12
> **SunnyRabbiera said:**
> The cube is fancy though its not really needed...
the standard virtual desktop manager should do, unless you are into the wow factor.
The main benefit I've had in using the cube, over Metacity's multiple desktop usage, is that I can see all the windows I have open in other desktops, and not forget I have other things happening. In Metacity, I'd often forget I had other programs running on another desktop, even though the taskbar icon showed I had something there.

---

### Post by SeanLor on 2008-06-12
W00000000T!!! Thanks so much, folks, I'm back in business.

---

