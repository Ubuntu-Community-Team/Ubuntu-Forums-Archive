---
title: "Small Resolution"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Wotcher on 2008-04-24
I'm tired of the small screen resolution that I have while using Ubuntu. The largest I have available to me is 1024x768. My screen is capable of going higher than that since I also use this screen for Windows XP.

How do I get it to go higher? The other day I found a thread on this issue, but I didn't really understand it (newbie here!) and now I can't find it. So, please, if anyone would like to help me fix this, please reoly. Thanks! :)

Wotcher

---

### Post by overdrank on 2008-04-24
> **Wotcher said:**
> I'm tired of the small screen resolution that I have while using Ubuntu. The largest I have available to me is 1024x768. My screen is capable of going higher than that since I also use this screen for Windows XP.

How do I get it to go higher? The other day I found a thread on this issue, but I didn't really understand it (newbie here!) and now I can't find it. So, please, if anyone would like to help me fix this, please reoly. Thanks! :)

Wotcher

Ok what version of Ubuntu are you using, Feisty, Gusty, Hardy? What is the model of your graphics card?

---

### Post by billgoldberg on 2008-04-24
> **Wotcher said:**
> I'm tired of the small screen resolution that I have while using Ubuntu. The largest I have available to me is 1024x768. My screen is capable of going higher than that since I also use this screen for Windows XP.

How do I get it to go higher? The other day I found a thread on this issue, but I didn't really understand it (newbie here!) and now I can't find it. So, please, if anyone would like to help me fix this, please reoly. Thanks! :)

Wotcher

Either install your graphics card using "restricted drivers" in "system -> administration" or add some resolutions in your xorg.conf file.

I believe hardy has a gui tool for that, not in gutsy.

---

### Post by Wotcher on 2008-04-24
> **overdrank said:**
> Ok what version of Ubuntu are you using, Feisty, Gusty, Hardy? What is the model of your graphics card?

Hi, I'm using Gutsty. I went to System > Administration > Screens and Graphics. And it says that my Graphic card is "Intel 845."

---

### Post by Wotcher on 2008-04-24
> **billgoldberg said:**
> Either install your graphics card using "restricted drivers" in "system -> administration" or add some resolutions in your xorg.conf file.

I believe hardy has a gui tool for that, not in gutsy.

I tried going to the restricted drivers and it says that I don't have any hardware that needs restricted drivers.

I have no idea how what a xorg.conf file is (I'm a noob! sorry :p )

---

### Post by overdrank on 2008-04-24
> **Wotcher said:**
> Hi, I'm using Gutsty. I went to System > Administration > Screens and Graphics. And it says that my Graphic card is "Intel 845."

HI and I would suggest using synaptic manger to locate and install the 915 resolution.Then restart x with the alt, ctrl, backspace bar all at the same time. This has helped other and to view your xorg you can use this command in the terminal ```
cat /etc/X11/xorg.conf
```This will allow you to see what resolution are set in your xorg.

---

### Post by Wotcher on 2008-04-24
> **overdrank said:**
> HI and I would suggest using synaptic manger to locate and install the 915 resolution.Then restart x with the alt, ctrl, backspace bar all at the same time. This has helped other and to view your xorg you can use this command in the terminal ```
cat /etc/X11/xorg.conf
```This will allow you to see what resolution are set in your xorg.

Ok, so I've opened the Synaptic Package Manager and I found the 915 resolution program. So all I have to do is check mark it and then it'll install? And what's this about restarting x?

Wotcher

---

### Post by overdrank on 2008-04-24
> **Wotcher said:**
> Ok, so I've opened the Synaptic Package Manager and I found the 915 resolution program. So all I have to do is check mark it and then it'll install? And what's this about restarting x?

Wotcher

Yes you can either restart x or the system.

---

### Post by spec-chum on 2008-04-24
> **Wotcher said:**
> Ok, so I've opened the Synaptic Package Manager and I found the 915 resolution program. So all I have to do is check mark it and then it'll install? And what's this about restarting x?

Wotcher

CTRL + ALT + Backspace restarts the X server.  Unlike Windows the GUI in Linux is separate from the operating system.  You can run Ubuntu or any other Linux without a GUI.

The graphical interface is provided by X-Windows which runs on your operating system.  If you make any changes to the configuration of that (by installing that 915 resolution program for example) you can apply them by restarting X.  You don't have to restart the whole operating system.

---

### Post by Wotcher on 2008-04-25
> **spec-chum said:**
> CTRL + ALT + Backspace restarts the X server.  Unlike Windows the GUI in Linux is separate from the operating system.  You can run Ubuntu or any other Linux without a GUI.

The graphical interface is provided by X-Windows which runs on your operating system.  If you make any changes to the configuration of that (by installing that 915 resolution program for example) you can apply them by restarting X.  You don't have to restart the whole operating system.

Ok, I've installed 915 resolution from the Synaptic Manager and I restarted X.

I've gone to the Screen Resolution preferences and it only shows the three sizes that I already have, the largest being 1024x768.

Did I do something wrong? How is this supposed to work?

Wotcher

---

### Post by Wotcher on 2008-04-26
> **Wotcher said:**
> Ok, I've installed 915 resolution from the Synaptic Manager and I restarted X.

I've gone to the Screen Resolution preferences and it only shows the three sizes that I already have, the largest being 1024x768.

Did I do something wrong? How is this supposed to work?

Wotcher

It's been at least 13 hours since I posted this... can anyone help at all?

Wotcher

---

### Post by overdrank on 2008-04-26
> **Wotcher said:**
> It's been at least 13 hours since I posted this... can anyone help at all?

Wotcher

Ok and you have no other option in screens and graphics? If you could post the output of this command ```
cat /etc/X11/xorg.conf
```

---

### Post by Wotcher on 2008-04-26
> **overdrank said:**
> Ok and you have no other option in screens and graphics? If you could post the output of this command ```
cat /etc/X11/xorg.conf
```

Thank you for responding.

When I go to the Screen Resolution preferences, I only get the three original resolutions, 1024x768 being the largest.

Here's what I get when I type that prompt into Terminal:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Gateway EV73"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Gateway EV73"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Thank you very much for your help. (Someone mentioned that Hardy comes with a GUI tool that supposedly fixes this problem... I haven't found anything; was s/he mistaken?)

Wotcher

---

### Post by natrixgli on 2008-04-26
First, what is the resolution you use in Windows?

what happens if you do this in a terminal:

1) Backup xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

2) Edit xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```

Change this:

```
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

```

to this:

```
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

```

Save, and restart X (CTRL + ALT + Backspace)


Can you then go to System > Preferences > Screen Resolution and select 1280x1024? If this works, then simply add your desired resolution to the 'Modes" section.


Cheers,

-n8

---

### Post by Wotcher on 2008-04-26
> **natrixgli said:**
> First, what is the resolution you use in Windows?

what happens if you do this in a terminal:

1) Backup xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

2) Edit xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```

Change this:

```
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

```

to this:

```
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

```

Save, and restart X (CTRL + ALT + Backspace)


Can you then go to System > Preferences > Screen Resolution and select 1280x1024? If this works, then simply add your desired resolution to the 'Modes" section.


Cheers,

-n8

The resolution I prefer in Windows is 1152x864 (the highest my screen goes in Windows is 1280x1024).

Ok, I've never done anything like that in Terminal. I'll give it a shot.

When you ask if it works, then simply add your desired resolution to the Modes section, isn't that what the steps you showed me do? Is what you showed me just a trial to see if the option shows up and then I have to actually add it to something?

Wotcher

---

### Post by natrixgli on 2008-04-26
> **Wotcher said:**
>  Is what you showed me just a trial to see if the option shows up and then I have to actually add it to something?

Wotcher


Based on what I saw in your xorg.conf I figured 1280x1024 would be the max resolution supported by your monitor. (which I gather is a 17" Gateway Non-widescreen monitor...)

You should be able to replace "1280x1024" with your preferred resolution, so long as your monitor supports it. Also you can get rid of some of the resolutions you don't use if you like. 

Most of this actually won't be done on the command line, it will be done in a text editor. It'll be easier than it looks.


Best of luck,

-n8

---

### Post by Wotcher on 2008-04-26
> **natrixgli said:**
> Based on what I saw in your xorg.conf I figured 1280x1024 would be the max resolution supported by your monitor. (which I gather is a 17" Gateway Non-widescreen monitor...)

You should be able to replace "1280x1024" with your preferred resolution, so long as your monitor supports it. Also you can get rid of some of the resolutions you don't use if you like. 

Most of this actually won't be done on the command line, it will be done in a text editor. It'll be easier than it looks.


Best of luck,

-n8

Ok, thank you very much, I'll try it out right now.

Wotcher

---

### Post by Wotcher on 2008-04-26
> **Wotcher said:**
> Ok, thank you very much, I'll try it out right now.

Wotcher

Didn't work. I still only have 1024 as the highest resolution.

>>Update: I tried to do it again, only this time, instead of putting in 1152x864, I put in 1280x1024, and it worked! So I have a bigger resolution now! Thank you for all your help. :-)

Wotcher

---

