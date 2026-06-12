---
title: "Nvidia driver black screen after 8.04 update"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by jtclicker on 2008-04-30
Since upgrading to 8.04 I get a back screen and the monitor goes off when I reboot after installing the nvidia driver. I'm using a geforce M8440 agpX. My config file after repairing the x server is
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
	Option		"Emulate3Buttons"	"true"
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
	Ide

And the config that fails is
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"CPD-G420"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"CPD-G420"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1920x1440"	"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

Any ideas?? Everything worked fine on Gutsy

---

### Post by hermes0710 on 2008-04-30
Try removing this line:
Busid "PCI:1:0:0"

---

### Post by jtclicker on 2008-04-30
Thanks. I'm a bit of a newbie. Do I do this by modifying by using sudo nautilus, then opening from there, or do I do this by when I get the black screen at reboot from the terminal - if so , how?? Sorry for this but I'm on a learning curve

---

### Post by philyook on 2008-04-30
I also get this black screen from time to time.  It's usually not the whole screen that goes black, just the most recently opened window.

---

### Post by jesterfred on 2008-04-30
From a terminal you can us the following command:

```
sudo nano /etc/X11/xorg.conf
```

Nano is a simple text editor.  You will be able to remove the offending line with it.

---

### Post by jtclicker on 2008-04-30
with mine the whole monitor goes off line at boot

---

### Post by pedro_orange on 2008-04-30
> **jtclicker said:**
> Thanks. I'm a bit of a newbie. Do I do this by modifying by using sudo nautilus, then opening from there, or do I do this by when I get the black screen at reboot from the terminal - if so , how?? Sorry for this but I'm on a learning curve

From the terminal you can edit your file as follows:

```
sudo nano -w /etc/X11/xorg.conf
```

If you're editing /etc/X11/zorg.conf that is.

---

### Post by hermes0710 on 2008-04-30
> **jtclicker said:**
> Thanks. I'm a bit of a newbie. Do I do this by modifying by using sudo nautilus, then opening from there, or do I do this by when I get the black screen at reboot from the terminal - if so , how?? Sorry for this but I'm on a learning curve

Either way:

From GUI:

Open a terminal: (<alt>+F2 and type "gnome-terminal").
In the terminal execute: ```
sudo gedit /etc/X11/xorg.conf
```
Remove the line and save the file, exit and reboot.

From Console:

   Execute: 
     ```
sudo vim /etc/X11/xorg.conf
```
    Go to the line and press two times the "d" letter. Then, holding down the <shift> button press two times the "z" letter in order to save the file and exit the editor. (In case vim is not installed in your system you can do the same thing replacing "vim" with "vi" in the above command.

---

### Post by jtclicker on 2008-04-30
OK, done that, now get this (after having to auto repair the X server a couple of times) which still doesn't work
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by pedro_orange on 2008-04-30
Did you upgrade to 8.04 from the previous version of Ubuntu? Or is it a fresh install?

How did you install the drivers on your machine before you upgraded?

Doing a:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Will automatically sort your xorg.conf file out; just follow the instructions and hit return on defaults if you have no idea.

Other than that:

- You can try a fresh install of 8.04 on a test partition
- Manually downloading the nvidia driver from terminal. (wget etc)

---

### Post by jtclicker on 2008-04-30
It is an upgrade. I installed the drivers on the previous version by activating restricted drivers, then just 'enabling' the nvidia driver. I'll try your suggestion

---

### Post by jtclicker on 2008-04-30
Thanks but that seems to only do what the auto xserver command does on the recovery boot up and gives me a conf without the nvidia driver

---

### Post by jtclicker on 2008-04-30
any ideas anyone?? I'm guessing that the driver isn't being pointed at  the card, but dunno how to fix it

---

