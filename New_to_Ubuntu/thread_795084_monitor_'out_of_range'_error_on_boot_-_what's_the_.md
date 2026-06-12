---
title: "monitor 'out of range' error on boot - what's the cause?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by guildofghostwriters on 2008-05-15
Occasionally when I boot, the monitor displays its own 'out of range' message with vertical and horizontal values. It doesn't happen every time I boot and I've always been able to get round it by alt-ctrl-backspace to the login screen and logging in (I have it set to log in automatically seeing as I'm the only person who uses this pc) - so far, it's always booted in without the out of range error after that.

The first time it happened, last weekend, I had been experimenting with different compiz settings and gdesklet so I purge removed gdesklets and got rid of all the flashier compiz stuff and it didn't happen for a few days. The only other things that have changed have been installing the gartoons icons through system/preference/appearance, normal updates and I've installed conky. Trying to solve it, I discovered that aticonfig (following a failed attempt to set up dual head) seemed to be applying the settings for my secondary monitor to my primary monitor but I've corrected this and the out of range thing still happens.

Any ideas please?

I don't know if this helps, but here's my xorg.conf:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "uk"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by cmnorton on 2008-05-15
I get this when the splash screen is up, booting and shutting down. It goes away, when the full-fledged desktop gets displayed. I am running a Thinkpad T61p through a KVM switch to an Acer AL 1914 monitor. I'm using the vesa driver, because the monitor won't work with the NVIDIA driver.

The monitor does not seem to mind.

If you are getting this at another time, then you need some xconfig help.

---

### Post by timandjulz on 2008-05-15
I get the same thing after monitor goes black for power savings (which won't disable for some reason).  When the monitor comes back up it either gives the same out of range error or the screen is radically messed up (pixels are shifted... looks like it is displaying 1680x1050 on 1024x768)

Actually, there are three possibilities:
1) out of range error
2) screen shifted so I can't read it
3) X defaults to lowest resolution (320x200) while the desktop still thinks it is as 1680x1050.

Work arounds are:
1) ctrl-alt-backspace, but that kills my running apps
2) Add "Screen Resolution" on the panel and memorize keystrokes to reset the screen.
3) Sometimes hotkeys like ctrl-alt-backspace get disabled.  In this case I have to reboot, possibly causing corruptions.

I am running a Sceptre 20" X20WG-NAG 1680x1024, ATI Radeon X300

---

### Post by guildofghostwriters on 2008-05-16
Well, in the absence of replies, I tried setting the vertical and horizontal refresh rates and just one screen resolution in xorg.conf to see if that helped. The first time I rebooted, the screen was somehow set to a completely different res that my monitor shouldn't support. I manually changed the res and rebooted and it all seemed to be fine.

Later I came back from walking the dog and it wouldn't boot at all. It kept stalling, the output saying something about being unable to receive a return value from the avahi-daemon. I couldn't safemode into a terminal either and trying to fix xserver from the boot menu options didn't solve it either. I made various attempts to fix it from the Live CD and to restore a backup I made using this thread [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) but none of them worked so I just gave up and installed from scratch (again! I've resorted to this several times - luckily I have things like music, work, images on an external hd).

It looks like nobody has been able to think up a solution while all that was going on but I'd still be interested to discover what caused it, and what caused the avahi-daemon problem, so I know what to avoid in future.

---

### Post by philinux on 2008-05-16
Install and run startupmanager from synaptic, one option is to set the boot option display resolution and colour depth. Here's a screenshot of mine. I had this problem in gutsy but hardy did not cause a problem. I use this to set the "show messages at startup". It's a nice gui and saves tinkering in terminal. 
(I like the cli for some things just not this)

---

### Post by guildofghostwriters on 2008-05-16
Was this to help my out of range thing or the splash screen problem? Since I reinstalled I haven't had any trouble and to be perfectly honest I don't want to fiddle with too much because incessant fiddling just keeps leading me to situations where I have to reinstall and start all over again. I suppose nearly 20 years of windows had got me to a place where I generally knew how to tinker and fiddle without lousing it all up and now with linux I'm back at year zero and at the bottom of the learning curve, to cluster a load of cliches. But I'll keep your suggestion in mind if it does start to happen again - thanks.

---

### Post by philinux on 2008-05-16
> **guildofghostwriters said:**
> Was this to help my out of range thing or the splash screen problem? Since I reinstalled I haven't had any trouble and to be perfectly honest I don't want to fiddle with too much because incessant fiddling just keeps leading me to situations where I have to reinstall and start all over again. I suppose nearly 20 years of windows had got me to a place where I generally knew how to tinker and fiddle without lousing it all up and now with linux I'm back at year zero and at the bottom of the learning curve, to cluster a load of cliches. But I'll keep your suggestion in mind if it does start to happen again - thanks.
Both works a treat.

---

### Post by guildofghostwriters on 2008-05-17
Well, touching wood worked wonders - I just had my first out of range since I reinstalled so I've followed your advice, installed and run startupmanager. Once again, touching wood this works! I'll let you know if the problem persists.

---

### Post by guildofghostwriters on 2008-05-18
AH B*~*~R! It's happened again. However, I think I may have worked out why. I can't be 100% certain but I believe this may happen when I start - as I normally do - with the monitor switched off. I guess that means that the monitor can't be queried for its capabilities during the boot. Will experiment and see.

---

