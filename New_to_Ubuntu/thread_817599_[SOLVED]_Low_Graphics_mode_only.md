---
title: "[SOLVED] Low Graphics mode only"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Sirchristopher on 2008-06-03
I was trying to get my SVIDEO working and changed my 'Screens and Graphics' settings.  Now, not only my SVIDEO doesn't work, but when I log in I am given a prompt that says I am running in low graphics mode and it asks me to configure my display.  I don't know what to do from there.  Please help.

---

### Post by unutbu on 2008-06-03
Please post 

```
ls -l /etc/X11/xorg*
```

---

### Post by Sirchristopher on 2008-06-03
-rw-r--r-- 1 root root 2318 2008-06-03 19:28 /etc/X11/xorg.conf
-rw-r--r-- 1 root root 3551 2008-06-02 23:43 /etc/X11/xorg.conf.1
-rw-r--r-- 1 root root 4057 2008-06-02 23:44 /etc/X11/xorg.conf.2
-rw-r--r-- 1 root root 2318 2008-06-03 18:12 /etc/X11/xorg.conf.3
-rw-r--r-- 1 root root 2228 2008-06-03 19:28 /etc/X11/xorg.conf.4
-rw-r--r-- 1 root root 1272 2008-06-03 19:31 /etc/X11/xorg.conf.failsafe
-rw-r--r-- 1 root root 1272 2008-06-03 19:10 /etc/X11/xorg.conf.failsafe.1
-rw-r--r-- 1 root root 1272 2008-06-03 19:30 /etc/X11/xorg.conf.failsafe.2
-rw-r--r-- 1 root root 2311 2008-06-03 19:30 /etc/X11/xorg.conf.failsafe.3
-rw-r--r-- 1 root root 2746 2008-06-03 19:30 /etc/X11/xorg.conf.failsafe.bak

---

### Post by philinux on 2008-06-03
> **Sirchristopher said:**
> I was trying to get my SVIDEO working and changed my 'Screens and Graphics' settings.  Now, not only my SVIDEO doesn't work, but when I log in I am given a prompt that says I am running in low graphics mode and it asks me to configure my display.  I don't know what to do from there.  Please help.

If you're using hardy and nvidia screens and graphics can bork your driver.

Try
sudo nvidia-xconfig then

gksudo nvidia-settings

---

### Post by Sirchristopher on 2008-06-03
I'm running Hardy, but I have an Intel graphics card.

---

### Post by Sirchristopher on 2008-06-03
bump

---

### Post by unutbu on 2008-06-03
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.5
sudo cp xorg.conf.1 xorg.conf
```
Log out of your X session. Press Ctrl-Alt-Backspace to restart the X server.

If that does not work, post
```
cat /etc/X11/xorg.conf
```

---

### Post by Sirchristopher on 2008-06-03
Thanks for the tip, unfortunatly it did not work.  Here is what I got when I ran the last command you said...

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by unutbu on 2008-06-03
Try 
```
gksudo displayconfig-gtk
```

If that does not work, post

```
cat /var/log/Xorg.0.log
```

---

### Post by Sirchristopher on 2008-06-03
Thank you very much!  'gksudo displayconfig-gtk' did it.

If I may ask...  What did that command do?

---

### Post by unutbu on 2008-06-03
```
gksudo displayconfig-gtk
sudo dpkg-reconfigure -phigh xserver-xorg
gnome-display-properties
```

Each of these commands allows you to choose your driver and your resolution. I learned of them by lurking the forums. I do not know the internals of how they work. Sorry.

---

### Post by Sirchristopher on 2008-06-04
That's ok.  Thank you for the help.

---

