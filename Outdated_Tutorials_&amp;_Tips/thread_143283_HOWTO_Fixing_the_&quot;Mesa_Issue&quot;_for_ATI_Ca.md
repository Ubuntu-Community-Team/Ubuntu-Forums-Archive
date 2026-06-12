---
title: "HOWTO: Fixing the &quot;Mesa Issue&quot; for ATI Cards"
date: 2006-03-12
forum: Outdated Tutorials &amp; Tips
---

### Post by escape on 2006-03-12
**Updated 10/21/2006.**

**Note: Not quite applicable to Edgy yet; ie I haven't gotten fglrx working in edgy yet. If you have, please post your card and what you did! In the interim, a better guide is [here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Ubuntu_6.04_.28Dapper_Drake.29").**


**_The HOWTO Itself_**

First, update your package database.
```
sudo apt-get update
```
Now, as mentioned in the original thread, remove the fglrx driver and restricted modules if you have them installed. If you're not sure, you can do these commands anyway; it will just tell you it's not installed.```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
```Your xorg file must also be set to be ati, not fglrx now, or else X won't start. To do this, open up /etc/X11/xorg.conf in your favorite text editor with root priveledges, in my case $>sudo emacs -nw /etc/X11/xorg.conf and under the section marked "Device", make sure you have Driver listed as "ati" and not "fglrx". 
Reboot.

Now, ***first install the restricted modules, then install the fglrx driver.*** It may also help to install other things related to fglrx; I also have xserver-xorg-driver-ati installed. fglrx-control is useful but not necessary (meaning I have fglrx working properly without fglrx-control installed).```
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
```Go back into your text editor with /etc/X11/xorg.conf, and rechange Driver under "Device" from "ati" to "fglrx". 
Reboot.

Use fglrxinfo (or, if you're running Xgl with the gdm hack (ie running everything on screen 1 in stead of screen 0), do fglrxinfo -display :1.0) should now give something like```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5695 (8.23.7)
```Note: Don't worry about the "Generic" part. If this didn't work, before you go to troubleshooting, double check you have fglrx in Xorg and try  ```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```.


**_Troubleshooting/WTF section_**
In general, ```
strace fglrxinfo 2>&1 | less
sudo dmesg | grep fgrlx
```might help you figure out what's up. Note that these solutions were contributed by people with a mix of Breezy and Dapper, they might not work on both or either. These solutions are listed in relative order of difficulty, from easiest to hardest.

**0. Problem: It doesn't work, but I was paying attention during the install and noticed that certain commands gave error messages as they executed. **
Solution: Post the error message *from the install* here. Meaning, not the output of fglrxinfo, which is obviously broken, but the errors that occurred when installing packages, etc. We can hopefully try to help you with those errors. Sometimes they might be "failed to remove directory: not empty" types of errors; if you have balls, and don't care too much for your system, try simply removing manually what the install says it cannot remove. As you can see below, a lot of linking goes on, so automatic removals and cleanups don't always work. Obviously though, the rm command can be as fatal as it is useful, so be careful. Do post here if you don't know what to do. 

**1. Problem: fglrx randomly stopped working**
Solution: You probably just updated (to a new kernel). You need the restricted modules (and probably the headers as well) for your new kernel. Repeat the process above, with appropriate kernel version, etc. You can avoid this by installing linux-kernel-[3,6]86 and restricted modules with -[3,6]86 as well (instead of linux-kernel-$(uname -r))


**2. Problem: fglrx isn't finding files it needs, ie things are not linked properly**
Solution: First check if this is an issue for you.Use ```
cd /usr/lib/
ls -la | grep libGL
``` to check links. Make sure the link from /usr/lib/libGL.so.1 goes to /usr/lib/libGL.so.1.2 (fglrx) instead of something else (Mesa). Also make sure the link from /usr/lib/libGLU.so.1 points to /usr/lib/libGLU.so.1.3.x.  If they don't, you can probably make the links manually. Try ```
man ln
```for info on making sym links. Also check ```
cd /usr/lib/
ls -la | grep dri
```  has /usr/lib/dri linking to  to /usr/lib/xorg/modules/dri. If it doesn't, try ```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```Disclaimer: from experience I know that messing around with links can REALLY mess things up if you sudo ln -s over a file that already exists. Be SURE you understand the syntax of ln and that you are not linking over a file that already exists; if you think you have to back, that file up first. You can (almost) always recover from accidents involving linking components of X badly by going into recovery mode and undoing what you've done.

**3. Problem: It's not the links, I think its the fglrx driver**
Fix: Start doing the steps from the main way again but install this instead of xorg-driver-fglrx. Or, failing that, try them both. One or the other seems more logical though. Get them here:
```
http://enemy-territory.co.il/Linux/fglrx-6-8-0_8.23.7-2_i386.deb
```
From the directory the file downloaded from, do
```
sudo dpkg -i fglrx_6_8_0-8.23.7-2.i386.deb
```
To install the drivers. Now make sure your /etc/X11/xorg.conf has "fglrx" instead of "ati" under the Driver section of "Device", and reboot. These drivers are probably outdated by now though, you might want to try googling or posting to find out what are the latest ones. They change often. 

**4. Problem: DRI is messed up**
Solution: To first figure out if DRI is the problem, look for common culprits: errors in your xorg log (usually its /var/log/Xorg.9[3,4].log or something similar in that directoyr) regarding DRI, DRI is not enabled in your /etc/X11/xorg.conf file (it should be a section at the bottom of the file), there is not DRI in your /usr/X11R6/lib/modules directory, "$>strace fglrxinfo 2>&1 | less | grep DRI" gives you errors regarding DRI, etc.
Solution: Add or enable DRI in your /etc/X11/xorg.conf; ask in this thread or post if you don't know how. Using similar techniques to alt solution #1, try linking DRI to where it needs to be if it does not exist in /usr/X11R6/lib/modules. Do this with```
cd /usr/X11R6/lib/modules/
sudo ln -s ../../../lib/dri
``` Alternately you could try```
sudo ln -s /usr/lib/xorg/modules/dri /usr/X11R6/lib/modules/dri
```Check to see what's missing where before you start blindly linking. 

**5. Problem: Not sure still/basic driver issues with fglrx**
Solution: Go [here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Ubuntu_6.04_.28Dapper_Drake.29"), choose your distro, and go to Method 2.

**6. Problem: Nothing fixed my problem**
Solution: Post about it here. Try to include as much info as possible. Please don't post your Xorg log over four separate posts, attach it as a file.

I will try to do as much as I can with helping others troubleshoot this issue, but I'm not exactly an expert. Also, so many people have helped contribute to this that I can't begin to list everyone. Thank you guys.

---

### Post by knalle on 2006-03-12
thanks! great sutff!

---

### Post by whatever on 2006-03-12
i had to create a symlink to get accelerated opengl:
```
sudo ln -s /usr/lib/dri/ /usr/lib/xorg/modules/dri
```

---

### Post by karolbe on 2006-03-12
[QUOTE=whatever]i had to create a symlink to get accelerated opengl:
```
sudo ln -s /usr/lib/dri/ /usr/lib/xorg/modules/dri
```[/QUOTE]

This worked for me, too. THANKS!

---

### Post by Melvil on 2006-03-12
Great, works like a charm!

But now I have to use "fglrxinfo -display :1.0" to check for the driver because I'm still using the "1=Standard" hack in gdm.conf. Is this still necessary with the new drivers?

---

### Post by nim901 on 2006-03-12
> sudo apt-get remove xorg-fglrx-driver
its xorg-driver-fglrx :cool:

oh, BTW, it wont work for me :\
here is my xorg.log
[http://paste.ubuntu-nl.org/10075](http://paste.ubuntu-nl.org/10075)

---

### Post by senning on 2006-03-12
It's not working for me either.  fglrxinfo gives me:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

My xorg.conf looks like 
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"AccelMethod" 		"EXA"
	Option		"AGPMode" 		"4"
	Option		"EnablePageFlip" 	"true"
	Option		"DDCMode"
	Option		"RenderAccel"		"true"
	Option		"SubPixelOrder"		"NONE"
#	Option		"backingstore"		"true"
#	Option		"AllowGLXWithComposite"	"true"
EndSection

Section "Monitor"
	Identifier	"L1511S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Monitor		"L1511S"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

### Post by nim901 on 2006-03-12
fglrxinfo gives me this
```
Error: unable to open display :0
```
:-#

---

### Post by Melvil on 2006-03-12
If you have Xgl running with the 1=Standard hack, make sure you enter "fglrxinfo -display :1.0"

---

### Post by nim901 on 2006-03-12
uh.. :-# 
but still .. 
```
fglrxinfo -display :1.0
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
:-?

---

### Post by Melvil on 2006-03-12
Yeah that's crap.
Make sure you you have "fglrx" in your /etc/X11/xorg.conf instead of "ati" in the driver section and check /var/log/Xorg.0.log and "dmesg | grep fglrx" for any errors

---

### Post by nim901 on 2006-03-12
```
 
$ dmesg | grep fglrx
[4294706.550000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294706.552000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[4294706.552000] [fglrx] module loaded - fglrx 8.23.7 [Mar  6 2006] on minor 0
[4294722.708000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294722.708000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294722.708000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294722.708000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[4294722.709000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294722.718000] [fglrx] free  AGP = 118222848
[4294722.719000] [fglrx] max   AGP = 118222848
[4294722.719000] [fglrx] free  LFB = 122679296
[4294722.719000] [fglrx] max   LFB = 122679296
[4294722.719000] [fglrx] free  Inv = 0
[4294722.719000] [fglrx] max   Inv = 0
[4294722.719000] [fglrx] total Inv = 0
[4294722.719000] [fglrx] total TIM = 0
[4294722.719000] [fglrx] total FB  = 0
[4294722.719000] [fglrx] total AGP = 32768


```
is it ok?
and Xorg logs are @ [http://paste.ubuntu-nl.org/10075](http://paste.ubuntu-nl.org/10075)

---

### Post by Melvil on 2006-03-12
That looks okay, I get nearly the same output, though mine runs fine with the Ati driver. I never had problems with the mesa driver so you might want to wait for someone who experienced the same problems, sorry.

---

### Post by nim901 on 2006-03-12
lets hope that someone will know how to solve it :eek:

---

### Post by senning on 2006-03-12
I took out the composite extension from xorg.conf and it works fine now.  Yay PlanetPenguin Racer!  (Though I'm pretty sure I'm pretty bad at it).

Check near the bottom of /var/log/Xorg.0.log.  If it says something like 
```

(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
Then maybe it'll work for you.

---

### Post by nim901 on 2006-03-12
> I took out the composite extension from xorg.conf 
how?

>  Check near the bottom of /var/log/Xorg.0.log.  If it says something like 
dont have any thing like that

---

### Post by recover82 on 2006-03-12
/*
 * edit : see my next post 
 * i'm a friggin idiot.  ive been at work for 18 hours
 */

---

### Post by nim901 on 2006-03-12
```
Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection
```
i dont have any thing like that :-?

---

### Post by recover82 on 2006-03-12
do you have anything in your xorg.conf that looks like the following?

Section "Extensions"
    Option "Composite" "true"
EndSection

---

### Post by nim901 on 2006-03-12
nop
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us,il"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
    Driver        "fglrx"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "PS576"
    Option        "DPMS"
    HorizSync    30-60
    VertRefresh    60-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
    Monitor        "PS576"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "DRI"
    Mode    0666
EndSection


```

---

### Post by shuttleworthwannabe on 2006-03-12
jeco's post in another thread is what I did and it worked: here the link:
===
n dapper:
SHOULD WORK FOR ANY FGLRX COMPATIBLE CARD
once dapper is installed boot into recovery mode.

"sudo apt-get install xorg-driver-fglrx linux-686" (or other architechure k7,am64-generic, etc..)
"sudo aticonfig --initial"

now reboot "sudo shutdown -r now"

People get wrapped up in big howto's when theres only 2 commands to get it working..
(once its working later run "sudo aticonfig --ovt=Xv" to set video overlay on)
===
Link: [http://www.ubuntuforums.org/showthread.php?t=142427]("http://www.ubuntuforums.org/showthread.php?t=142427")

---

### Post by nim901 on 2006-03-12
but i did it ... and it ain`t working

---

### Post by scpike on 2006-03-12
neither method worked for me, ati X300

---

### Post by nim901 on 2006-03-12
ok, now it works!!!
every one, do like this-
```
 sudo apt-get remove xorg-fglrx-driver
sudo apt-get remove linux-restricted-modules-$(uname -r) 
``` after reboot -
```
 sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx 
``` and then download this file (10 mb)
```
https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/fglrx_6_8_0-8.23.7-1.i386.rpm
``` then - 
```
alien fglrx_6_8_0-8.23.7-1.i386.rpm
sudo dpkg -i fglrx_6_8_0-8.23.7-1.i386.deb
``` 

reboot
after reboot - 
```
sudo dpkg-reconfigure xserver-xorg
``` select fglrx
reboot X (ctrl+alt+backspace)
H_A_V_E F_U_N!!! \\:D/\\:D/\\:D/\\:D/\\:D/ (credit to me :P)

---

### Post by escape on 2006-03-12
Glad to hear this worked for you. I'll add it to the first post as a little tidbit. What did you have previously set up? Ie, did you have Xgl, or compositing? What video card do you have? Maybe the extra info will help others.

---

### Post by nim901 on 2006-03-12
i have xgl + compiz (i used the ati guide)
kernel 2.6.15-18
what more info do you need?
and btw, ive update the guide^^ and i`m uploading the deb pkg so you will just need to install it :-D

---

### Post by escape on 2006-03-12
[QUOTE=scpike]neither method worked for me, ati X300[/QUOTE]

Can you post your xorg.conf? Some extra info would help.

---

### Post by escape on 2006-03-12
[QUOTE=nim901]i have xgl + compiz (i used the ati guide)
kernel 2.6.15-18
what more info do you need?
and btw, ive update the guide^^ and i`m uploading the deb pkg so you will just need to install it :-D[/QUOTE]

Alright, thanks!

---

### Post by nim901 on 2006-03-12
yep
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us,il"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "PS576"
        HorizSync    30.0 - 60.0
        VertRefresh  60.0 - 75.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
        Monitor    "PS576"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

---

### Post by escape on 2006-03-12
[QUOTE=nim901]yep
[/QUOTE]

Err, I meant scpike's xorg, since he's still having problems :D . While I'm at it though, what's the -phigh option do for dpkg-reconfigure?

---

### Post by nim901 on 2006-03-12
umm, here is the deb link ```
http://enemy-territory.co.il/Linux/fglrx-6-8-0_8.23.7-2_i386.deb
```
and 
>  Err, I meant scpike's xorg, since he's still having problems :grin: . While I'm at it though, what's the -phigh option do for dpkg-reconfigure?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by escape on 2006-03-12
[QUOTE=nim901]umm, here is the deb link ```
http://enemy-territory.co.il/Linux/fglrx-6-8-0_8.23.7-2_i386.deb
```
and 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```[/QUOTE]

Will just try it out then.. also updating main page. Also, are you an ET fan? So a fun game..

---

### Post by jecos on 2006-03-12
If your still having only mesa make sure your not using a 9100 IGP, cause they aren't officiall supported under 3D. [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.23.7.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.23.7.html)

---

### Post by scpike on 2006-03-12
ok heres the xorg.conf

> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "EmulateWheel" "true"
	Option	    "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 70.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection




its been working fine until the new kernel

---

### Post by escape on 2006-03-12
[QUOTE=scpike]ok heres the xorg.conf
its been working fine until the new kernel[/QUOTE]

Are you **positive** you have the restricted modules installed for your new kernel, and you installed them before (re)installing xorg-driver-fglrx?

It might also be something with having two graphics cards listed under xorg.conf, but that's going into territory I'm unfamiliar with.

---

### Post by scpike on 2006-03-12
i followed the guide on the first page exactly, what do the new debs do differently?

---

### Post by escape on 2006-03-12
[QUOTE=scpike]i followed the guide on the first page exactly, what do the new debs do differently?[/QUOTE]

I think the deb is basically what you can get from the ATI site for fglrx drivers; I was under the impression that what was in synaptic should do fine, but it may be what you need to get it working. 

If you're only running a single monitor, maybe also try ```
l
dpkg-reconfigure xserver-xorg
``` to get a clean xorg.conf file.

Again, I'm not an expert or anything, maybe one of the others in this thread can help out, or try the original thread.

---

### Post by scpike on 2006-03-12
i tried it again with the new debs, no go

ill try the whole thing fresh and see what happens.

any other ideas? 

does installing the dev version of the driver do anything?

---

### Post by escape on 2006-03-12
[QUOTE=scpike]i tried it again with the new debs, no go

ill try the whole thing fresh and see what happens.

any other ideas? 

does installing the dev version of the driver do anything?[/QUOTE]

I don't have the dev version installed, and it works. The dev is probably useful for other things though. If what I said above doesn't work, then I'm completely out of ideas. Sorry.

---

### Post by jecos on 2006-03-12
[QUOTE=escape]I think the deb is basically what you can get from the ATI site for fglrx drivers; I was under the impression that what was in synaptic should do fine, but it may be what you need to get it working. 

If you're only running a single monitor, maybe also try ```
aticonfig --initial
dpkg-reconfigure xserver-xorg
``` to get a clean xorg.conf file.

Again, I'm not an expert or anything, maybe one of the others in this thread can help out, or try the original thread.[/QUOTE]

"aticonfig --initial" modifies the xorg.conf and adds to the existing lines.  
"dpkg-reconfigure xserver-xorg" creates xorg.conf from scratch.

---

### Post by escape on 2006-03-13
[QUOTE=jecos]"aticonfig --initial" modifies the xorg.conf and adds to the existing lines.  
"dpkg-reconfigure xserver-xorg" creates xorg.conf from scratch.[/QUOTE]

Right, kind of redundant there, sorry. Still learning this stuff.

---

### Post by nim901 on 2006-03-13
[quote=scpike]
any other ideas? 
[/quote] have you tried my deb?
if you dont, first remove all fglrx stuff reboot and then tray that

---

### Post by Trel on 2006-03-13
I would like to note to any laptop users that removing the restricted linux modules may kill your wireless ethernet connection so have a wired one ready before doing this.

Also I've yet to get this to work. I'll try a bit later.

---

### Post by erimar77 on 2006-03-13
I just wanted to say the first portion of this thread worked wonderfully for me.  Especially after a couple days of banging my head on the desk trying to figure this out..

---

### Post by escape on 2006-03-13
It seems like there's two groups of people here - one group is missing something that's preventing them from getting the howto to work, while the other group has it, and the howto is working for them. If it's not the deb for the fglrx driver posted on the first page, then I'm not really sure what it could be though.

---

### Post by nim901 on 2006-03-13
ummm, yeah, thats wird 
try use ati.com script

---

### Post by cvrefugee on 2006-03-13
I followed Method 1 & 2 from [here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Ubuntu_6.04_.28Dapper_Drake.29") but I still have the "Mesa Issue".  My full Xorg.0.log is attached, but I think this part shows my problem:

```

(II) fglrx(0): [drm] DRM interface version 1.2
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8c90000
(II) fglrx(0): [drm] mapped SAREA 0xf8c90000 to 0xb7651000
(II) fglrx(0): [drm] framebuffer handle = 0xe8000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: radeon
(II) fglrx(0):     Version: 1.19.0
(II) fglrx(0):     Date: 20050911
(II) fglrx(0):     Desc: ATI Radeon
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8c90000 at 0xb7651000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

---

### Post by mindwarp on 2006-03-14
I have the exact same error as posted above.  This really needs to be solved asap, I mean if they are taking 6 extra weeks for dapper to get polish, how about getting one of the biggest manufacturers of videos cards products working?

That being said, next time I won't make the mistake of buying any product with ATI inside.

---

### Post by cvrefugee on 2006-03-14
That's weird, now it works all of a sudden...all I did was reboot.

---

### Post by nim901 on 2006-03-14
well .. dah .. you must do rebot else the fglrx model wont load, lol :)

---

### Post by wangdang on 2006-03-14
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


here's a [link to my xorg log]("http://www.legnemark.se/Xorg.0.log.txt")

I need help, my poor xwindows is sooo slow.

---

### Post by mindwarp on 2006-03-14
Reboot after last stepped fixed it.  First time I have had these drivers actually working.

---

### Post by escape on 2006-03-14
[QUOTE=wangdang]display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


here's a [link to my xorg log]("http://www.legnemark.se/Xorg.0.log.txt")

I need help, my poor xwindows is sooo slow.[/QUOTE]

What's your xorg.conf? There's also a HUGE section in your log involving trying to access a device using fglrx and failing... probably what's causing the issue. Don't know how to fix it though.

---

### Post by dharapvj on 2006-03-16
Hi,
I have Dell inspiron 9300 with ATI Radeon X300 card. I am facing issue in Dapper since flight 3.

I followed the steps given in 1st page of this thread + additions from second page as given by nim901.
I still have issue with Mesa thing..

Here is my Xorg.log snippet and xorg.conf snippet

```
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```


```
Section "Device"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
#	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
EndSection

```
Both of them are attached also here.

Any help?
My output of fglrxinfo is as follows:
```
vj@DgD:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Pls help,
Vijay
[ATTACH]7123[/ATTACH]

[ATTACH]7124[/ATTACH]

---

### Post by Heavy_Master on 2006-03-16
Many thanks, it works for me! :)

---

### Post by escape on 2006-03-16
[QUOTE=dharapvj]Hi,
I have Dell inspiron 9300 with ATI Radeon X300 card. I am facing issue in Dapper since flight 3.

I followed the steps given in 1st page of this thread + additions from second page as given by nim901.
I still have issue with Mesa thing..
```
Section "Device"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection
Section "ServerLayout"
	Identifier     "Default Layout"
[COLOR="Red"]	Screen      0  "Default Screen" 0 0[/COLOR]
#	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
EndSection

```
Pls help,
Vijay
[/QUOTE]

Vijay, here's a couple of things I think might not be helping you in your xorg - first, you have three screen listings, they all seem to be the same though. It might be confusing fglrx? Also, what I have in red above - I don't think the 0's are needed (espeically if you get rid of the extra "Screen" entries). Try fixing these things with sudo dpkg-reconfigure xserver-xorg, which will rewrite your xorg .conf file.

---

### Post by unf on 2006-03-16
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Ubuntu_6.04_.28Dapper_Drake.29]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Ubuntu_6.04_.28Dapper_Drake.29")

You should try Method 2 this when you are doing "sudo modprobe fglxr" and it gets fatal error. 


hmmp.. my problem solved with this. 

sudo apt-get install module-assistant 
sudo module-assistant build, install fglrx

reboot

I dont really know what I am doing so be carefull :) :) \\:D/

---

### Post by r00tzz on 2006-03-17
Does this work with Radeon Xpress 200M?? My computer hangs after setarting X with DRI and fglrx driver. Log shows nothing (at least for me).

Here's the files:
[ATTACH]7199[/ATTACH]
[ATTACH]7200[/ATTACH]

I did an update from brezzy to dapper.

Also this message shows when I call glxinfo: Error: couldn't find RGB GLX visual

---

### Post by escape on 2006-03-17
[QUOTE=r00tzz]Does this work with Radeon Xpress 200M?? My computer hangs after setarting X with DRI and fglrx driver. Log shows nothing (at least for me).

Here's the files:
[ATTACH]7199[/ATTACH]
[ATTACH]7200[/ATTACH]

I did an update from brezzy to dapper.

Also this message shows when I call glxinfo: Error: couldn't find RGB GLX visual[/QUOTE]

Are you running Xgl? I got that error when trying to run an Xgl server instead of Xorg.

---

### Post by ap9er on 2006-03-18
Hey guys,

When doing sudo aticonfig --initial I'm getting
"Parse error on line 318 of section Monitor in file xorg.conf
The VertRefresh keyword must be followed by a list of numbers or ranges." 

Having looked around I can't find a fix for the problem.
My xorg.conf is as follows:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	128000
EndSection

Section "Monitor"
	Identifier	"Philips 170B"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh     56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP"
	Monitor		"Philips 170B"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```


Anyone help?
Thanks in advance.

---

### Post by escape on 2006-03-18
[QUOTE=ap9er]Hey guys,

When doing sudo aticonfig --initial I'm getting
"Parse error on line 318 of section Monitor in file xorg.conf
The VertRefresh keyword must be followed by a list of numbers or ranges." 
Having looked around I can't find a fix for the problem.
Anyone help?
Thanks in advance.[/QUOTE]

Strange, because it looks fine (but line 318 wtf?); try retyping the line in there. Failing that run sudo dpkg-reconfigure xserver-xorg to regenerate your xorg file, then try sudo aticonfig --initial again.

---

### Post by eMuNiX on 2006-03-18
Despite hours of reading howtos and wiki's I still can't get Compiz/XGL to work with my ATI9600.  I know that it should work, I have full OpenGL 3D working already, as I have tried the Kororaa liveCD and it definately works there.  As soon as I try to do anything I either lose 3D and go back to Mesa or I lose X completely.....off to try yet more things as I have new resolve after playing with the liveCD.

glxinfo gives:-
```
emunix@linux:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5695 (8.23.7)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None

```

---

### Post by r00tzz on 2006-03-18
[QUOTE=escape]Are you running Xgl? I got that error when trying to run an Xgl server instead of Xorg.[/QUOTE]


Hummm started the installation according to [How To: "Simple" Install Xgl/compiz for Dapper, ATI, Gnome]("http://www.ubuntuforums.org/showthread.php?t=131253")... never finish:oops: ..

Will try removing everything and starting over.

---

### Post by r00tzz on 2006-03-18
[QUOTE=r00tzz]Hummm started the installation according to [How To: "Simple" Install Xgl/compiz for Dapper, ATI, Gnome]("http://www.ubuntuforums.org/showthread.php?t=131253")... never finish:oops: ..

Will try removing everything and starting over.[/QUOTE]


Quoting myself... solved the problem by giving UMA some memory... Have to enable UMA+SidePort to fglrx work... Now I have 3D!!!\\:D/  

Thanks everyone!!

---

### Post by jvolkman on 2006-03-19
Well, I finally figured out my problem after hours of scratching my head.  I have a laptop and a desktop, buth with ATI video cards, both running Dapper, and both running the latest version of fglrx (from the Dapper repos).  GL worked on the laptop but not the desktop, even though the Xorg log file looked almost identical for both systems (DRI initialization successfull!).

I did "strace fglrxinfo" and found this gem:
```
open("/usr/X11R6/lib/modules/dri/fglrx_dri.so", O_RDONLY) = -1 ENOENT (No such file or directory)
```

It was looking for fglrx_dri.so in the non-existent directory /usr/X11R6/lib/modules/dri.  I had already made a link from /usr/lib/xorg/modules/dri to /usr/lib/dri, so i issued the following command:

```
sudo ln -s /usr/lib/xorg/modules/dri /usr/X11R6/lib/modules/dri
```

Alternatively, you could do:
```
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/dri
```

That did it.  I didn't even have to restart X.

Hope this helps someone

---

### Post by jvolkman on 2006-03-19
Upon additional investigation, I found that the file /etc/X11/Xsession.d/10fglrx was pointing things to the wrong path for the fglrx DRI driver.  Simply removing that file made opengl apps point to /usr/lib/dri/fglrx_dri.so

---

### Post by dolny on 2006-03-20
I followed the howto, then followed jvolkman hints and it works :) Thanks!

---

### Post by pwner4once on 2006-03-21
just as a side note. i installed the xorg server and got my 3d acceleration working. but stuff like xine starts playing video in another window other than the original one because they default use the OpenGLOverlay feature.  this was caused by the VideoOverlay. u can check that by using "xvinfo"

so i had to add

        Option "VideoOverlay"   "on"
        Option "OpenGLOverlay"  "off"
to the Device section in order to get it to work.

---

### Post by Nightwish on 2006-03-21
now i'm annoyed...
```

(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled

``` 
and yet, i only have mesa. i'm convinced something is borked for now. none of the things here seem to work.

edit: actually, the only thing missing is trying to recreate the xorg.conf file. but i'm too bored now.

---

### Post by Toxicity999 on 2006-03-25
Well... I'm having issues... it worked originally... Fine infact. After a fglrx update it all reverted back to mesa, so I thought, no problem I'll repeat this from memory, I did it fine and all. But... in having to use the 'ATi' driver settings midway through I found that the ati drivers leave the screen completely unreadable! I tried running through the same things in the command line but needless to say issues issues issues.

---

### Post by TB2 on 2006-03-26
Using Dapper Drake Flight 5 on a Desktop Radeon 9600pro, trying to install Xgl/Compiz...

Tried everything, and still get the Mesa output for "fglrxinfo -display :1.0", tried the manual way, tried the linux-686 thing, tried symlinks, everything I found. I dont get errors in /var/log/Xorg.0.log but there's a section looking strange to me:> ...
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
...
...beginning at card1 going up to card254. Is that normal?

I'm getting really frustrated with this stuff... ](*,)

---

### Post by massivevoid on 2006-03-26
Mine shows the same thing, but I don't thing it is something to worry about. My fglrx loaded fine, just to add. 

I think that card0 is your video card and it does a check through card1-card254, then back to card0. So, does it checking to see what card install? Is that right?

Strange that it goes through 254. :-k 

Though, this thread is very useful and should be sticky to the top. :)

---

### Post by TB2 on 2006-03-26
Well, if fglrx works, then I think thats a scan, too. 254 is quite near to 256,a nd because it starts at 0, 255 would be the highest position. maybe that last one isn't scanned beacuse it is used for something else...

Anyway... fglrx won't work -.-

---

### Post by shamrock_uk on 2006-03-26
Well, just in case this helps someone else:

I've been butting my head against ATI for about two years with the drivers working/not working on an ad-hoc basis. 

They always work for me on a fresh install. A kernel upgrade always breaks them, even when the requisite restricted modules are also upgraded. 

I'd followed this walkthrough until I was blue in the face, but then suddenly it worked. The only difference - I had noticed there was a new kernel available. Selecting *it*, along with the restricted modules, rebooting into the new kernel and then installing the stock xorg-driver-fglrx from the repos got it working :)

I'm not about to break my system to test this, but perhaps if you're at your wits end, consider a kernel which hasn't been anywhere near your system before and try that.

---

### Post by so0le on 2006-03-27
Not working in my Radeon 9600XT, tried the first method in this howto -> same result.

Tried to do the second method, it gaves me errors like this:

```

(Reading database ... 74478 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.23.7-2_i386.deb) ...
dpkg: error processing fglrx-6-8-0_8.23.7-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libfglrx_gamma.so.1.0', which is also in package xorg-driver-fglrx
dpkg-deb: subprocess paste killed by signal (Katkennut putki)
Errors were encountered while processing:
 fglrx-6-8-0_8.23.7-2_i386.deb

```

"Katkennut putki" is finnish, it means like "Cutted pipe" or "Broken pipe". My card worked fine at Windows.

And, here's the rest of the info:

$ fglrxinfo:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
[/edit]

xorg.conf:
[edit]
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fi"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Radeon 9600XT"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "L1715S"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Radeon 9600XT"
        Monitor         "L1715S"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

$ dmesg | grep fglrx:
```

[4294712.435000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294712.451000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294712.451000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294766.541000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294766.541000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294766.541000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294766.541000] [fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
[4294766.542000] [fglrx:firegl_unlock] *ERROR* Process 7424 using kernel context 0

```

/var/log/Xorg.0.log:
```

drmOpenDevice: node name is /dev/dri/card175
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card176
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card177
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card178
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card179
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card180
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card181
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card182
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card183
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card184
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card185
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card186
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card187
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card188
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card189
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card190
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card191
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card192
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card193
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card194
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card195
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card196
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card197
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card198
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card199
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card200
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card201
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card202
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card203
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card204
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card205
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card206
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card207
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card208
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card209
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card210
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card211
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card212
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card213
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card214
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card215
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card216
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card217
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card218
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card219
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card220
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card221
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card222
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card223
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card224
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card225
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card226
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card227
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card228
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card229
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card230
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card231
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card232
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card233
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card234
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card235
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card236
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card237
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card238
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card239
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card240
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card241
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card242
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card243
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card244
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card245
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card246
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card247
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card248
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card249
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card250
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card251
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card252
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card253
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8b40000
(II) fglrx(0): [drm] mapped SAREA 0xf8b40000 to 0xb7aeb000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfeaf0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8b40000 at 0xb7aeb000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "Protocol" "ImPS/2"
(**) Mouse1: Device: "/dev/input/mice"
(**) Mouse1: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Mouse1: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Mouse1: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Mouse1: ZAxisMapping: buttons 4 and 5
(**) Mouse1: Buttons: 5
(**) Option "CoreKeyboard"
(**) Keyboard1: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard1: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xfree86"
(**) Keyboard1: XkbRules: "xfree86"
(**) Option "XkbModel" "pc101"
(**) Keyboard1: XkbModel: "pc101"
(**) Option "XkbLayout" "fi"
(**) Keyboard1: XkbLayout: "fi"
(**) Option "CustomKeycodes" "off"
(**) Keyboard1: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Keyboard1" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Mouse1" (type: MOUSE)
(II) Mouse1: ps2EnableDataReporting: succeeded
(II) 3rd Button detected: disabling emulate3Button

```

---

### Post by gurjit on 2006-04-08
Hello everyone, guess what; i cant get fglrx to work properly. Ive tried so many HowTo's but nothing helps. So i thought i might aswell try another just incase i get lucky. So here is my information.

[B]AMD ATHALON 1.3GHz
ATI RADEON 9200SE
512 RAM[/B]


[COLOR="Red"]**XORG.CONF**[/COLOR]

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"CPD-210GS"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Monitor		"CPD-210GS"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


```




[COLOR="Red"]**dmesg | grep fglrx**[/COLOR]

> gurjit@Ubuntu:~$ dmesg | grep fglrx
[4294694.233000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294694.241000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294694.241000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294722.107000] [fglrx:firegl_unlock] *ERROR* Process 6665 using kernel context 0
gurjit@Ubuntu:~$


If you need any more information please done hesitate to ask. ( IM GOING TO PASTE THE Xorg.0.log file over the next few posts)

---

### Post by gurjit on 2006-04-08
Here is my Xorg.0.log fire PART 1:

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux Ubuntu 2.6.12-10-k7 #1 Sat Mar 11 16:59:38 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-k7 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:59:38 UTC 2006 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  8 02:01:07 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "CPD-210GS"
(**) |   |-->Device "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3205 card 1043,8118 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1106,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1043,80a1 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1043,80a1 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1043,80b0 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ff rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5964 card 148c,2073 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x5964) rev 1, Mem @ 0xd0000000/28, 0xe5000000/16, I/O @ 0xc000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[1] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[5] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[6] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[1] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[5] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[6] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.22.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9200 SE (RV280 5964),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9550 (M12 4E56), RADEON 9500 (R300 4144),
	RADEON 9600 TX (R300 4146), FireGL Z1 (R300 4147),
	RADEON 9700 PRO (R300 4E44), RADEON 9500 PRO/9700 (R300 4E45),
	RADEON 9600 TX (R300 4E46), FireGL X1 (R300 4E47),
	RADEON 9800 SE (R350 4148), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9800 PRO (R350 4E48),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), MOBILITY RADEON X300 (M22 5460),
	MOBILITY RADEON X600 (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	RADEON X800 XL (R430 554D), RADEON X800 (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), MOBILITY RADEON X700 XL,
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.22.5
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.22g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb  7 2006 19:32:18
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.22.1-driver-lnx-244115
(--) Chipset RADEON 9200 SE (RV280 5964) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8210658
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9200 SE (RV280 5964)" (Chipset = 0x5964)
(--) fglrx(0): (PciSubVendor = 0x148c, PciSubDevice = 0x2073)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe5000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9200
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V280
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/X11R6/lib/modules/linux/libdrm.a
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SNY  Model: 1070  Serial#: 4070243
(II) fglrx(0): Year: 1999  Week: 31
(II) fglrx(0): EDID Version: 1.1
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 24
(II) fglrx(0): Gamma: 2.50
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.600
(II) fglrx(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 720x400@88Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@87Hz (interlaced)
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Serial No: 4070243
(II) fglrx(0): Ranges: V min: 48  V max: 120 Hz, H min: 30  H max: 70 kHz,
(II) fglrx(0): Monitor name: CPD-210GS
(II) fglrx(0): Monitor name: 
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 200/165MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 40 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.77  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.68  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.18  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
```

---

### Post by gurjit on 2006-04-08
```

(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.41  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  150 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  150 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  120 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  120 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  100 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  100 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (330, 240) mm
(--) fglrx(0): DPI set to (98, 108)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.22.5
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000b
(==) fglrx(0): cpuSpeedMHz: 0x00000514
(==) fglrx(0): OpenGL ClientDriverName: "atiogl_a_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe5000000 - 0xe500ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[8] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xd0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xd0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card15
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card16
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card17
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card18
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card19
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card20
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card21
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card22
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card23
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card24
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card25
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card26
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card27
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card28
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card29
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card30
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card31
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card32
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card33
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card34
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card35
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card36
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card37
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card38
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card39
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card40
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card41
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card42
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card43
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card44
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card45
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card46
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card47
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card48
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card49
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card50
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card51
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card52
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card53
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card54
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card55
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card56
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card57
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card58
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card59
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card60
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card61
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card62
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card63
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card64
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

---

### Post by gurjit on 2006-04-08
```

drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card65
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card66
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card67
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card68
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card69
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card70
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card71
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card72
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card73
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card74
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card75
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card76
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card77
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card78
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card79
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card80
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card81
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card82
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card83
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card84
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card85
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card86
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card87
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card88
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card89
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card90
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card91
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card92
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card93
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card94
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card95
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card96
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card97
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card98
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card99
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card100
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card101
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card102
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card103
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card104
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card105
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card106
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card107
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card108
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card109
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card110
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card111
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card112
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card113
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card114
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card115
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card116
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card117
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card118
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card119
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card120
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card121
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card122
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card123
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card124
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card125
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card126
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card127
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card128
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card129
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card130
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card131
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card132
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card133
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card134
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card135
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card136
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card137
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card138
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card139
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card140
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card141
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card142
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card143
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card144
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card145
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card146
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card147
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card148
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card149
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card150
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card151
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card152
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card153
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card154
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card155
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card156
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card157
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card158
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card159
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card160
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card161
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card162
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card163
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card164
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card165
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card166
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card167
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card168
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card169
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card170
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card171
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card172
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card173
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card174
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card175
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card176
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card177
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

---

### Post by gurjit on 2006-04-08
```

drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card178
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card179
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card180
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card181
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card182
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card183
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card184
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card185
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card186
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card187
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card188
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card189
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card190
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card191
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card192
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card193
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card194
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card195
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card196
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card197
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card198
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card199
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card200
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card201
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card202
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card203
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card204
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card205
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card206
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card207
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card208
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card209
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card210
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card211
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card212
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card213
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card214
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card215
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card216
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card217
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card218
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card219
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card220
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card221
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card222
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card223
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card224
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card225
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card226
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card227
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card228
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card229
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card230
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card231
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card232
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card233
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card234
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card235
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card236
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card237
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card238
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card239
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card240
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card241
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card242
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card243
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card244
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card245
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card246
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card247
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card248
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card249
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card250
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card251
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card252
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card253
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xe0c61000
(II) fglrx(0): [drm] mapped SAREA 0xe0c61000 to 0xb7aaf000
(II) fglrx(0): [drm] framebuffer handle = 0xd0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0c61000 at 0xb7aaf000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

```

OK THATS THE END OF IT. If you need any more info please dont hesitate to ask.

---

### Post by escape on 2006-04-10
[QUOTE=gurjit]OK THATS THE END OF IT. If you need any more info please dont hesitate to ask.[/QUOTE]

In general, for such a large file, you might want to upload it as an attachment. I don't know if anyone would want to actually look through all of that and decipher if for you. Can you give us some more, easier information to work with - are you using the latest drivers? Are you pulling the drivers from the repository?

---

### Post by sha_man on 2006-04-15
i have the exact same problem and nothing helped :( 
Maybe it's because of the 686-Kernel?

My xorg.conf is


```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ch"
	Option		"XkbVariant"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"P19-2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 XT (RV350 NJ)"
	Monitor		"P19-2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

should I also post my xorg.0.log?

---

### Post by escape on 2006-04-15
[QUOTE=sha_man]i have the exact same problem and nothing helped :( 
Maybe it's because of the 686-Kernel?

My xorg.conf is


```
xorg
```

should I also post my xorg.0.log?[/QUOTE]

I know fglrx does work on the 686 kernel, but maybe its conflicting with something specific on your computer. You could try a 386 and see if it fixes it... probably won't though.

I won't stop you from posting your xorg log, but I personally don't really know how to fix issues or errors that I can spot it in.

---

### Post by sha_man on 2006-04-17
ok here it is (joined). Now if somebody could fix this ati thing, i would really apreciate!

Thanks

---

### Post by sha_man on 2006-04-17
somebody could tell me how to **remove completely** every trace and links etc... of the fglrx drivers? I have installed those from ubuntu repo. & even those from ati ( "sudo ./ati-driver-installer-8.24.8-x86.run" I did). 

So I could try again....
Thanks :)

and: this is the output of *dmesg | grep fglrx *:

```
[4294691.105000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294691.134000] [fglrx] Maximum main memory to use for locked dma buffers: 681 MBytes.
[4294691.134000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294710.942000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4294710.943000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294710.943000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294710.943000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294710.943000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[4294710.946000] [fglrx:firegl_unlock] *ERROR* Process 7902 using kernel context 0
[4295353.443000] [fglrx] module unloaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4295369.009000] [fglrx] Maximum main memory to use for locked dma buffers: 681 MBytes.
[4295369.009000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4295369.010000] [fglrx] module unloaded - fglrx 8.16.20 [Aug 16 2005] on minor 0

```

EDIT: here my fglrx-install.log (german):

```

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.12-10-686«
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_init':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8175: Warnung: »pm_register« ist veraltet (deklariert bei include/linux/pm.h:106)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_cleanup':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8185: Warnung: »pm_unregister_all« ist veraltet (deklariert bei include/linux/pm.h:116)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6079: Warnung: »ati_gart_base« definiert, aber nicht verwendet
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:581: Warnung: »inter_module_put« ist veraltet (deklariert bei include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:583: Warnung: »inter_module_unregister« ist veraltet (deklariert bei include/linux/module.h:565)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:603: Warnung: »inter_module_register« ist veraltet (deklariert bei include/linux/module.h:564)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:634: Warnung: »inter_module_put« ist veraltet (deklariert bei include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3592: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3593: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3594: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3595: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3596: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3597: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3598: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3599: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3601: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3611: Warnung: Funktionsdeklaration ist kein Prototyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `test_inter_module_interface':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3677: Warnung: »inter_module_put« ist veraltet (deklariert bei include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3683: Warnung: »inter_module_put« ist veraltet (deklariert bei include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_allocate_memory_phys_list':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3941: Warnung: Verarbeiten des Argumentes 3 von Zeiger auf Funktion erzeugt Ganzzahl von Zeiger ohne Typkonvertierung
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_bind_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3980: Warnung: Verarbeiten des Argumentes 1 von Zeiger auf Funktion von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_unbind_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3993: Warnung: Verarbeiten des Argumentes 1 von Zeiger auf Funktion von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2256: Warnung: »deferred_flush« definiert, aber nicht verwendet
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.12-10-686«
build succeeded with return value 0
 compiling fglrx_agp.ko module
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/lib/modules/fglrx/build_mod/firegl_agpgart modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.12-10-686«
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/backend.o
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c: In function `agp_backend_initialize':
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:191: Warnung: Verarbeiten des Argumentes 1 von Zeiger auf Funktion erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c: In function `agp_backend_cleanup':
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:216: Warnung: Verarbeiten des Argumentes 1 von »__ke_phys_to_virt« erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:216: Warnung: Verarbeiten des Argumentes 1 von Zeiger auf Funktion erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c: At top level:
/lib/modules/fglrx/build_mod/firegl_agpgart/backend.c:294: Warnung: »agp_init« definiert, aber nicht verwendet
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/generic.o
In Datei, eingefügt von /lib/modules/fglrx/build_mod/firegl_agpgart/agp.h:32,
                    von /lib/modules/fglrx/build_mod/firegl_agpgart/generic.c:43:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.h:759:1: Warnung: "PCI_DEVICE_ID_INTEL_ICH7_1" redefined
In Datei, eingefügt von include/linux/pci.h:452,
                    von /lib/modules/fglrx/build_mod/firegl_agpgart/generic.c:34:
include/linux/pci_ids.h:2439:1: Warnung: this is the location of the previous definition
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/isoch.o
In Datei, eingefügt von /lib/modules/fglrx/build_mod/firegl_agpgart/agp.h:32,
                    von /lib/modules/fglrx/build_mod/firegl_agpgart/isoch.c:10:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.h:759:1: Warnung: "PCI_DEVICE_ID_INTEL_ICH7_1" redefined
In Datei, eingefügt von include/linux/pci.h:452,
                    von /lib/modules/fglrx/build_mod/firegl_agpgart/isoch.c:6:
include/linux/pci_ids.h:2439:1: Warnung: this is the location of the previous definition
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.o
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `intel_i810_cleanup':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:158: Warnung: Verarbeiten des Argumentes 1 von »__ke_iounmap« streicht Qualifizierer von Zeiger-Zieltypen
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `i8xx_alloc_pages':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:174: Warnung: »page« könnte in dieser Funktion uninitialisiert bleiben
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `intel_i810_free_by_type':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:348: Warnung: Verarbeiten des Argumentes 1 von »__ke_phys_to_virt« erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:348: Warnung: Verarbeiten des Argumentes 1 von »i8xx_destroy_pages« erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:351: Warnung: Verarbeiten des Argumentes 1 von »__ke_phys_to_virt« erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:351: Warnung: Verarbeiten des Argumentes 1 von Zeiger auf Funktion erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:354: Warnung: implizite Deklaration der Funktion »kfree«
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `intel_i830_cleanup':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:564: Warnung: Verarbeiten des Argumentes 1 von »__ke_iounmap« streicht Qualifizierer von Zeiger-Zieltypen
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `intel_i915_cleanup':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:670: Warnung: Verarbeiten des Argumentes 1 von »__ke_iounmap« streicht Qualifizierer von Zeiger-Zieltypen
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:671: Warnung: Verarbeiten des Argumentes 1 von »__ke_iounmap« streicht Qualifizierer von Zeiger-Zieltypen
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `find_i830':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1526: Warnung: Zuweisung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1528: Warnung: Zuweisung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `agp_intel_probe':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1697: Warnung: implizite Deklaration der Funktion »pci_assign_resource«
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `agp_intel_remove':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1734: Warnung: Verarbeiten des Argumentes 1 von »__ke_pci_get_drvdata« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `agp_intel_resume':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1742: Warnung: Verarbeiten des Argumentes 1 von »__ke_pci_get_drvdata« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: At top level:
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1814: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1815: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `fgl_agp_intel_init':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1827: Warnung: Verarbeiten des Argumentes 1 von »__fgl_pci_module_init« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c: In function `fgl_agp_intel_cleanup':
/lib/modules/fglrx/build_mod/firegl_agpgart/intel-agp.c:1834: Warnung: Verarbeiten des Argumentes 1 von »__fgl_pci_unregister_driver« von inkompatiblem Zeigertyp
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.o
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: In function `agp_ali_probe':
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:303: Warnung: Verarbeiten des Argumentes 1 von »__ke_pci_find_capability« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:331: Warnung: Verarbeiten des Argumentes 1 von »__ke_pci_read_config_byte« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:363: Warnung: Verarbeiten des Argumentes 1 von »__ke_pci_read_config_dword« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:367: Warnung: Verarbeiten des Argumentes 1 von »__ke_pci_set_drvdata« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: In function `agp_ali_remove':
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:373: Warnung: Verarbeiten des Argumentes 1 von »__ke_pci_get_drvdata« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: At top level:
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:396: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:397: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: In function `fgl_agp_ali_init':
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:403: Warnung: Verarbeiten des Argumentes 1 von »__fgl_pci_module_init« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c: In function `fgl_agp_ali_cleanup':
/lib/modules/fglrx/build_mod/firegl_agpgart/ali-agp.c:408: Warnung: Verarbeiten des Argumentes 1 von »__fgl_pci_unregister_driver« von inkompatiblem Zeigertyp
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.o
In Datei, eingefügt von /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:113:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.h:759:1: Warnung: "PCI_DEVICE_ID_INTEL_ICH7_1" redefined
In Datei, eingefügt von include/linux/pci.h:452,
                    von /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:74:
include/linux/pci_ids.h:2439:1: Warnung: this is the location of the previous definition
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function `__ke_phys_to_virt':
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:660: Warnung: Verarbeiten des Argumentes 1 von »phys_to_virt« erzeugt Ganzzahl von Zeiger ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:660: Warnung: return erzeugt Ganzzahl von Zeiger ohne Typkonvertierung
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function `__ke_verify_area':
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:1123: Warnung: »verify_area« ist veraltet (deklariert bei include/asm/uaccess.h:105)
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function `__ke_get_vm_phys_addr':
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:1362: Warnung: Verarbeiten des Argumentes 1 von »pmd_offset« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: In function `__ke_vm_phys_addr_str':
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:1818: Warnung: Verarbeiten des Argumentes 1 von »pmd_offset« von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c: At top level:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:333: Warnung: »firegl_stub_list« definiert, aber nicht verwendet
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_wrap.c:1475: Warnung: »deferred_flush« definiert, aber nicht verwendet
  CC [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.o
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c:2:1: Warnung: "/*" within comment
In Datei, eingefügt von /lib/modules/fglrx/build_mod/firegl_agpgart/agp.h:32,
                    von /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c:28:
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.h:759:1: Warnung: "PCI_DEVICE_ID_INTEL_ICH7_1" redefined
In Datei, eingefügt von include/linux/pci.h:452,
                    von /lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c:17:
include/linux/pci_ids.h:2439:1: Warnung: this is the location of the previous definition
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c: In function `firegl_agp_init':
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c:301: Warnung: »inter_module_register« ist veraltet (deklariert bei include/linux/module.h:564)
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c:302: Warnung: »inter_module_register« ist veraltet (deklariert bei include/linux/module.h:564)
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c: In function `firegl_agp_exit':
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c:327: Warnung: »inter_module_unregister« ist veraltet (deklariert bei include/linux/module.h:565)
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c:328: Warnung: »inter_module_unregister« ist veraltet (deklariert bei include/linux/module.h:565)
/lib/modules/fglrx/build_mod/firegl_agpgart/firegl_agp.c:332: Warnung: »inter_module_put« ist veraltet (deklariert bei include/linux/module.h:568)
  LD [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/fglrx_agp.o
  Building modules, stage 2.
  MODPOST
  CC      /lib/modules/fglrx/build_mod/firegl_agpgart/fglrx_agp.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/firegl_agpgart/fglrx_agp.ko
make[1]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.12-10-686«
AGPGART build succeeded with return value 0
 finished compiling for fglrx_agp
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel modules
done.
```

---

### Post by escape on 2006-04-17
[QUOTE=sha_man]somebody could tell me how to **remove completely** every trace and links etc... of the fglrx drivers? I have installed those from ubuntu repo. & even those from ati ( "sudo ./ati-driver-installer-8.24.8-x86.run" I did). [/QUOTE]

Try ```
sudo dpkg -l | grep fglrx
``` and remove these packages with ```
sudo dpkg --purge <package>
```. This will get rid of the ubuntu deb's.

For the ati driver, maybe try ```
sudo apt-get reinstall xserver-xorg-driver-ati xserver-xorg
```. Someone might want to double check that last one for me. That should overwrite the ATI thing you downloaded with the basic driver from the repository.

---

### Post by sha_man on 2006-04-17
Thanks!
With the "ATI" drivers I meant I had installed those from the ATI *site*, so that they are still the fglrx, but just the newest (here is how installed them: [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.24.8_drivers_in_Breezy_Badger](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.24.8_drivers_in_Breezy_Badger))

---

### Post by Mr Fat Bat on 2006-04-17
I've pretty much exhausted all of the ideas in this forum and found though google and I still can't get fglrx working!  

I have it working at home but nothing can get it working at work on an ATI Radeon x300 and a Dell 1907fp monitor!

---

### Post by escape on 2006-04-17
[QUOTE=Mr Fat Bat]I've pretty much exhausted all of the ideas in this forum and found though google and I still can't get fglrx working!  

I have it working at home but nothing can get it working at work on an ATI Radeon x300 and a Dell 1907fp monitor![/QUOTE]

Could be something with other hardware, because fglrx definitely works with some X300's (mine). Try the latest version from ATI, it came out a few days ago, don't know that it's in the repositories yet.

---

### Post by mjziegle on 2006-04-18
0-254 and a value for the sign of the value

---

### Post by mjziegle on 2006-04-18
0-254 is 255 values
1 value is reserved for the sign

it's 256 or 8-bit

Mine does the same thing.  I think this is if you have multiple cards in your system it searchs over all possible card values.  I doubt this is a bug.


-Matt

[QUOTE=massivevoid]Mine shows the same thing, but I don't thing it is something to worry about. My fglrx loaded fine, just to add. 

I think that card0 is your video card and it does a check through card1-card254, then back to card0. So, does it checking to see what card install? Is that right?

Strange that it goes through 254. :-k 

Though, this thread is very useful and should be sticky to the top. :)[/QUOTE]

---

### Post by sha_man on 2006-04-18
That is a part of my Xorg.0.log:

```
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf0b97000
(II) fglrx(0): [drm] mapped SAREA 0xf0b97000 to 0xb7b4c000
(II) fglrx(0): [drm] framebuffer handle = 0xd0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xe5000000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf0b97000 at 0xb7b4c000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ch"
(**) Generic Keyboard: XkbLayout: "ch"
(**) Option "XkbVariant" "de"
(**) Generic Keyboard: XkbVariant: "de"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

```

Please help :-|

---

### Post by escape on 2006-04-19
[QUOTE=mjziegle]0-254 is 255 values
1 value is reserved for the sign
it's 256 or 8-bit
Mine does the same thing.  I think this is if you have multiple cards in your system it searchs over all possible card values.  I doubt this is a bug.
-Matt[/QUOTE]

Assuming the architecture uses two's complement then yes it should go from -255 to 254 (or just 0 to 254).

---

### Post by xlyz on 2006-04-22
[quote=jvolkman]It was looking for fglrx_dri.so in the non-existent directory /usr/X11R6/lib/modules/dri.  I had already made a link from /usr/lib/xorg/modules/dri to /usr/lib/dri, so i issued the following command:

```
sudo ln -s /usr/lib/xorg/modules/dri /usr/X11R6/lib/modules/dri
``` 
Alternatively, you could do:
```
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/dri
``` 
That did it.  I didn't even have to restart X.

Hope this helps someone[/quote] 
It did :D

---

### Post by dawg on 2006-04-23
just installed new kernel in dapper beta and my fglrx went to hell.  i had used this very same how to and got it to work earlier before changing kernels now whenever i try anything heres what i get

mario@linbox:~$ sudo apt-get install linux-restricted-modules-$(uname -r)
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-restricted-modules-2.6.16-ck3

any ideas as to what i can do to fix this?

by the way the only reason i installed the new kernel was because of issues with cedega and it running games super slow.

---

### Post by brianfinley on 2006-04-25
I had the same issue, and did this:

```
strace fglrxinfo 2>&1 | less
```

And saw this:

```
open("/usr/X11R6/lib/modules/dri//fglrx_dri.so", O_RDONLY) = -1 ENOENT (No such file or directory)
```

So I did this:
```

locate fglrx_dri.so

```

Which produced this as output: "/usr/lib/dri/fglrx_dri.so".  So then I did this:
```

cd /usr/X11R6/lib/modules/
sudo ln -s ../../../lib/dri

```

And now, when I run fglrxinfo I get this:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FireGL V3200 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5755 (8.24.8)

```

And, glxgears runs fast, etc.  Fixed!

---

### Post by f3tus on 2006-04-30
I tried method 3 but fglrxinfo still outputs ```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

Here's the image of ATI control panel.
[[IMG]http://img86.imageshack.us/img86/2808/cpanel0ob.th.png[/IMG]](http://img86.imageshack.us/my.php?image=cpanel0ob.png)

Also, ```
ls -la | grep libGL
``` shows nothing. I am 100% my xorg.conf is as it should be, I also had no errors while installing.

---

### Post by LinuxAndBeer on 2006-04-30
Thanks that tutorial was excellent !

---

### Post by vtp on 2006-05-05
After many idea in the forum the last 2 days with no luck then I follow brianfinley method it work! Thank brianfinley.
Here was my ordeal. I've got Xgl-compiz running fine on my Dell inspiron 9200 with Intel 1.8G Pentium M, 1G mem and ATI mobil 9700. By adding these repo to my /etc/apt/sources.list
[LIST]
[*]## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)

[*]deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
[*]deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
[*]#reggaemanu xgl mesa
[*]deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
[/LIST]

Then doing the update following with dist-upgrade to current 2.6.15-21-386 kernel. Every thing work fine. 
But my problem start when the auto update kick-in some how the update break my system. X crashed, GDM wouldn't run I have to remove fglrx driver then reverse back to ati to get X and GDM running but painfully slow. I have check dmesg,Xorg.0.log for any error but everything seems to work fine. I still got mesa instead of ATi on fglrxinfo until I follow brianfinley method. 
So the moral of the story is: be very carefully with the auto update especially relate to the driver it might do more harm than good!

---

### Post by kingi89 on 2006-05-08
And now I've tried almost everything (including this thread) but still:
fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
Xorg.0.log:
```
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x8000 at 0xb7ed6000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```
Full Xorg.0.log: [http://orisrk.homelinux.com/jako/Xorg.0.log.txt](http://orisrk.homelinux.com/jako/Xorg.0.log.txt)
Full xorg.conf: [http://orisrk.homelinux.com/jako/xorg.conf.txt](http://orisrk.homelinux.com/jako/xorg.conf.txt)
Any ideas?

---

### Post by Pancake on 2006-05-10
I figured I'd just say I had the same mesa issue after upgrading to the dapper beta yesterday.

At first X didn't work at all, the log said something about how the fglrx module didn't exist.

I fixed this by editing my xorg.conf file, and following the guide at the beginning of this topic.  This got it to the point where I could set the driver as fglrx in xorg.conf, but fglrxinfo would still display tons of mesa crap.

then I tried what brianfinley said:

```

cd /usr/X11R6/lib/modules/
sudo ln -s ../../../lib/dri

```

now the fglrxinfo command outputs:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5755 (8.24.8)



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5755 (8.24.8)

```

I assume this means it's using the fglrx driver's, but i'm not sure.  Whatever it is, it seems to run 3d stuff.

---

### Post by darrenm on 2006-05-12
Thank you everyone for giving me lots to try, unfortunately none of these would work for me as I was doing something very silly.

I had previously installed the driver and got it working via the help of this site:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I had followed the ATi Dapper build instructions which included blacklisting the fglrx module from /etc/default/linux-restricted-modules-common

Of course I had forgotten all about this and when I suddenly remembered and took it out again all I had to do was ```
sudo /etc/init.d/gdm restart
``` and I am now cooking on fglrx gas.

:D

---

### Post by arunsub on 2006-05-15
I did as per the instructions and it worked. The problem is, when I type fglrxinfo, I get the following:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.5755 (8.24.8)

It's saying generic instead of my card name (X1600 mobility radeon). Does anybody know why?

---

### Post by Bulltitan on 2006-05-21
I have 7 days using ubuntu and in the 7th day after only 2 installs i've found some piece of guide like this wich i started to love since the first minute it worked. Now for all the new people reading this just follow the instructions, i have been trough xandros 2.0, mandrake 9, xandros 3.0 and ubuntu 5.10 has been the most stable and easy to setup version of linux i have ever seen, i even tryed skyos these (guys are doing a great job also).
Really thanks a lot escape and all the others adding info to this thread, that's the way linux will be known and used by common people, by helping each other.:-D
Ho by the way i'm writing this post from ubuntu thanks to another nice help given here about adsl usb modems.
If you need help just ask!

---

### Post by Mau on 2006-05-23
For Breezy: If you followed these steps and got your card to configure correctly, but your resolution isn't what you want, you can force it to be your desired resolution by running:```
$ sudo dpkg-reconfigure xserver-xorg
``` Select the fglrx driver, and then uncheck all the screen resolutions except the desired one.

I was stuck at 1024x768, and I wanted to get to 1600x1200.  This got me there.

---

### Post by dejitarob on 2006-05-23
[QUOTE=jvolkman]Well, I finally figured out my problem after hours of scratching my head.  I have a laptop and a desktop, buth with ATI video cards, both running Dapper, and both running the latest version of fglrx (from the Dapper repos).  GL worked on the laptop but not the desktop, even though the Xorg log file looked almost identical for both systems (DRI initialization successfull!).

I did "strace fglrxinfo" and found this gem:
```
open("/usr/X11R6/lib/modules/dri/fglrx_dri.so", O_RDONLY) = -1 ENOENT (No such file or directory)
```

It was looking for fglrx_dri.so in the non-existent directory /usr/X11R6/lib/modules/dri.  I had already made a link from /usr/lib/xorg/modules/dri to /usr/lib/dri, so i issued the following command:

```
sudo ln -s /usr/lib/xorg/modules/dri /usr/X11R6/lib/modules/dri
```

Alternatively, you could do:
```
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/dri
```

That did it.  I didn't even have to restart X.

Hope this helps someone[/QUOTE]

Thanks, this worked for me. I thought this wouldn't help me at first glance because I had already tried it but it was just the instructions for fixing the  symbolic link in the first post were incorrect. I have [filed a bug]("https://launchpad.net/distros/ubuntu/+source/xorg-driver-fglrx/+bug/46239") for this.

---

### Post by phorque on 2006-05-24
Goddamnit this gets annoying. I have to reinstall linux-restricted-modules and fglrx every time there is a kernel update and then restart my xserver for acceleration to work.

Shouldn't something trigger synaptic, or the update manager, to do this automatically so that I don't have to sit here like a n00b wondering why my machine has gotten so slow until I have the sense to type "fglrxinfo" and see "mesa" instead of "ATI"?

Sucks to be going strong, then update, and max out your CPU just by watching a movie fullscreen. :neutral: It's not like I can't fix it, but it gets me every time!

---

### Post by funkenstein on 2006-05-24
thanks, putting the restricted modules in first fixed it for me on 64bit dapper

---

### Post by FuzzyFiz on 2006-05-24
```
onder@Fuzzy:~$ sudo apt-get remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 26.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 159612 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversio ns/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibm esa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
onder@Fuzzy:~$ sudo apt-get remove linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
Package linux-restricted-modules-2.6.15-23-686 is not installed, so not removed
The following packages will be REMOVED
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 26.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 159612 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
onder@Fuzzy:~$ strace fglrxinfo
strace: fglrxinfo: command not found
onder@Fuzzy:~$

```

This my last trials,
First I had mesa issue,
now when &#305; type fglrxinfo it doesn't show anything at all.
I tried the way at the beginnig of the thread but it did't worked. You can check the error.
Help please....
Thanks

---

### Post by escape on 2006-05-24
Update: cleaned up original post a lot and added in more suggestions posted here.

---

### Post by Colonel Kilkenny on 2006-05-24
FuzzyFiz:
First remove restricted-modules (sudo aptitude remove linux-restricted-modules-*YOURKERNELVERSION*)
then change fglrx to ati in Xorg.conf.
Reboot.
Then sudo dpkg-divert &#8211;rename &#8211;remove /usr/lib/libGL.so.1.2 and sudo dpkg --force-all --purge xorg-driver-fglrx
After those you can just install them back  in order:
sudo aptitude install linux-restricted-modules-*YOURKERNELVERSION*
sudo aptitude install xorg-driver-fglrx

edit. and after all this you can edit your xorg.conf back to "fglrx" and restart X with ctrl-alt-backspace.

---

### Post by FuzzyFiz on 2006-05-24
thanks Kilkenny 
I can't move on after these commands, can you explain them alittle bit.
Then sudo dpkg-divert –rename –remove /usr/lib/libGL.so.1.2 and sudo dpkg --force-all --purge xorg-driver-fglrx
After those you can just install them back in order:
sudo aptitude install linux-restricted-modules-*YOURKERNELVERSION*
sudo aptitude install xorg-driver-fglrx
Thanks

---

### Post by FuzzyFiz on 2006-05-24
and after first command I get this
Writing extended state information... Error!
E: I wasn't able to locate file for the xorg-driver-fglrx package. This might mean you need to m anually fix this package.
E: Couldn't lock list directory..are you root?

---

### Post by studio on 2006-05-25
Hi.
After lots of reboots and installations i mananged to fglrx with combination of this link: [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide) and Escape's first post.
First i tried the wiki's method 1. The mesa issue.
Then Escape's method. No mesa but renderer string was Generic, there was no ati's control panel and sudo aticonfig --initial didn't work at all.
Then i tried wiki's method 2. No matter what the mesa issue.
But with method 2 i had made two .deb packages that i think helped (don't ask me how, i'm newbie in Ubuntu), fglrx-control and fglrx-sources.
So:
1. Make sure that you have the universe and multiverse repositories enabled.
2. code= sudo apt-get update
3. wiki's method 2. It will not work so:
4. Escape's method, ***BUT*** after the second installation and ***BEFORE*** reboot don't gedit xorg.config. Make
code= sudo dpkg-reconfigure xserver-xorg #select the "fglrx" module
then reboot.

My video card: Ati Radeon 9600XT with dual screen and tv-out support in ati's control panel :D 

p.s sorry for my english. not my native language.

---

### Post by likeatim on 2006-05-25
[QUOTE=Colonel Kilkenny]Then sudo dpkg-divert &#8211;rename &#8211;remove /usr/lib/libGL.so.1.2 and sudo dpkg --force-all --purge xorg-driver-fglrx
[/QUOTE]
when I do that, I get a 
```
Removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/fglrx/libGL.so.1.2.xlibmesa', not allowed
```

---

### Post by Colonel Kilkenny on 2006-05-25
Sorry Fuzzyfiz and likeatim, I don't know what's the problem. Did you boot your computer with ati in use instead of fglrx?

---

### Post by likeatim on 2006-05-25
[QUOTE=Colonel Kilkenny]Sorry Fuzzyfiz and likeatim, I don't know what's the problem. Did you boot your computer with ati in use instead of fglrx?[/QUOTE]
I think I did.
But now after installing the newest ATI fglrx, I can't even remove the driver because of the issue described above.... This grafix business in Linux is just plain bull***....

---

### Post by FuzzyFiz on 2006-05-25
I tried also, I can't remove the error is like likeatim's one.Plus know I can't remove the ati driver release 24. Synaptic always gives an error.Are there any one heard about a problem like this ?

---

### Post by tommohawk on 2006-05-26
Hi guys, this thread has been excellent value look....

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

All this on an extremely difficult to configure laptop!

However, every time the system updates itself, the fglrx driver reverts to using MESA - and it is really slooooooow when that happens.  I can get it working again simply by re-installing xorg-driver-fglrx without even having to restart X but this is a real pain.

Anyone got any ideas on how to stop this happening?

---

### Post by Cavalierski on 2006-05-27
[QUOTE=FuzzyFiz]I tried also, I can't remove the error is like likeatim's one.Plus know I can't remove the ati driver release 24. Synaptic always gives an error.Are there any one heard about a problem like this ?[/QUOTE]

Ok, here you go. I also face the issue and now after several try My box is fixed :) 

```
sudo rm /var/lib/dpkg/info/xorg-driver-fglrx.postrm
sudo dpkg --purge xorg-driver-fglrx
sudo aptitude update
sudo aptitude install xorg-driver-fglrx
```

Hope this helps.

---

### Post by FuzzyFiz on 2006-05-28
Cavalierski , I did yours and it worked just fine thank you. I didn't waiting for reply, kind a hopeless.
After all escape's revised solution works too double check , nice effort guys =D>

---

### Post by Cavalierski on 2006-05-28
[QUOTE=FuzzyFiz]Cavalierski , I did yours and it worked just fine thank you. I didn't waiting for reply, kind a hopeless.
After all escape's revised solution works too double check , nice effort guys =D>[/QUOTE]

I'm glad that it works.  And It's good of you to keep patient and keep interest on this subject to find out the way. Probably if I were you, I couldn't wait for more than 1 day :p 

In my case, my radeon9000pro with h/w enhancement (not ATI proprietary) didn't work after several try and I'm back to "ati" driver. That's enough for me as I'm using ubuntu as a programming environment. ;)

When I got time, I'll try to figure out, but so far I'm bussy playing with my daughters...

---

### Post by Norckon on 2006-05-29
Hi all!

Checking out this forum and Compiz.net for a couple of days now trying to get Xgl + compiz to work. Unfortunately I can't get it working, because of OpenGL running on Mesa Project.
I'm running a custom build kernel 2.6.16.18 on Kubuntu Dapper fully upgraded with fglrx 2.0.5814 (8.25.18).

I'm trying to get Compiz working on KDE, using .xsession as follows:
```

#!/bin/bash

Xgl :1 +bs -br -fullscreen -ac -accel xv:pbuffer -accel xgl:pbuffer &

sleep 2

DISPLAY=:1

LD_LIBRARY_PATH=/opt/mesa gnome-window-decorator &
LD_LIBRARY_PATH=/opt/mesa compiz --display :1 --replace gconf &

exec startkde

```

Running the compiz line in a xterm return GLX_EXT_jadda_jadda missing, of course because of mesa. Replacing LD_LIBRARY_PATH by LD_PRELOAD doesn't make a difference. I can't start Xgl from kdmrc's ServerCmd: it won't get to the login screen, I just see a black screen with a mousecursor and that's it.

I didn't have the /opt/mesa or any libGL diversions. After some searching I found out /usr/lib/FGL.renamed.libGL.so.1.2 must be the old mesa lib. Uninstalling fglrx confirms this file being placed back. So I copied it to /opt/mesa.

strace fglrxinfo gives me some messages about file not found:
```

access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
above line x10 or something
open("/etc/drirc", O_RDONLY)            = -1 ENOENT (No such file or directory)
open("/home/norckon/.drirc", O_RDONLY)  = -1 ENOENT (No such file or directory)

```
I don't now wether this is normal. In Xorg fglrxinfo returns the normal ATI 8.25.18 stuff, in Xgl it's Mesa Project.

I checked all symlinks, everything in /usr/lib is ok (pointing to fglrx) and I created /usr/lib/xorg/modules/dri and /usr/X11R6/lib/modules/dri to /usr/lib/dri.

My xorg.conf is like this:
```

ection "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        #Load   "extmod" #crashes X, blank screen
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "Device"
        Identifier  "ATI Technologies Radeon X1600 SIL"
        Driver      "fglrx"
        Option      "backingstore" "on"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "KernelModuleParm" "locked-userpages=1" #0=slooow
EndSection

Section "DRI"
        Mode         0666
EndSection

```

Could it have something to do with the extmod module, which I can't load because X crashes with it?
Or perhaps the files fglrxinfo doesn't find?
Or.. something else? Really despered right now.

Thanks in advance!

---

### Post by frodon on 2006-06-21
Moved to the Tips & Trick section as requested.

escape, let me know if you wish to change the tag/title of the thread.

---

### Post by ashrack on 2006-06-21
[QUOTE=frodon]Moved to the Tips & Trick section as requested.

escape, let me know if you wish to change the tag/title of the thread.[/QUOTE]
thank U for hearing my request to move this thread here

---

### Post by bohboh on 2006-06-21
This worked for me (Eventually). Thanks

Upon getting it to work, my update manager wants to install alsorts of stuff which relate to mesa, 

gnome-session (i assume is ok to upgrade)
libgl1-mesa
libgl1-mesa-dev
libgl1-mesa-dri
libglu1-mesa
libwnck-common
libwnck18
mesa-common-dev
xserver-xorg-driver-i810

Having done the fglrx update which broke my system, should i update them? what will happen? what should i do to try and stop any updates from breaking this again?

I have locked my fxlgr components in synaptic. Will that be enough?

---

### Post by ashrack on 2006-06-21
I dont thing those things could be a problem so its safe to install this stuff,
Since it only relates to MESA which U dont use anymore if U have ATI properly set up and I810 driver which U are not using

---

### Post by Silverdisc on 2006-06-21
Hi everyone!!

First I want to thnks everybody here because without they, we were still with all these frustrating problems and kicking a bit our beloved cpu's....

Second I want to tell my case or "what i've do to solve that f***ng mesa and weird screen problem"

I enter the bios, pressed F10 (i guess) and set all options by whole on default settings...and that's it!! all worked like charm, no more mesa problems.. no more weird freezing screen like "unplugging the card-on-hot" or something like...7

I bless that would solve that imposible problem, and prey for the others that not :confused: =D> 

P.D. I'm from Spain, please, apologize my bad spelling and grammar, i'm so sorry...

---

### Post by pksings on 2006-06-22
I still get ...

fglrxinfo -display :0.0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

furthermore in my Xorg.0.log I get ...

(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.25.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.25g1
(II) ATI Proprietary Linux Driver Build Date: May 18 2006 09:54:44
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.25.1-driver-lnx-268237
(--) Chipset MOBILITY RADEON 9000 (M9 4C66) found


(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

I have tried "modprobe dri" but no such module exists.
modrobe drm installs that module but fglrx doesn't seem to care.

I'm stumped...

PK

---

### Post by ashrack on 2006-06-22
do U have DRI linked like the guide says and everything else properly set up and have U rebooted the machine??

---

### Post by herot on 2006-06-23
fglrx is working now due to the howto... 
(Radeon 9000 Pro; 2400fps in glxgears; Neverwinter Nights runs great!!)

anywayz, im about to change over my kernel to k7 (im on the 386 kernel now)... is there anything i need to do or CAN do to prevent this from breaking or will i have to go through the howto again to fix it once i upgrade?

---

### Post by bohboh on 2006-06-23
I changed mine from 386 to k7 and it went well, surprisingly easy.

Remember to download the header files for k7 as well.

I am not sure if you have to go through the pain of getting 3d accell to work, mine was broken anyway and so had to regardless.

---

### Post by Albi on 2006-06-24
I'm getting this message:

> albi@albi-desktop:~$ sudo apt-get remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  fglrx-control fglrx-kernel-2.6.15-25-386 xorg-driver-fglrx
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 27.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 102825 files and directories currently installed.)
Removing fglrx-control ...
Removing fglrx-kernel-2.6.15-25-386 ...
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)


And when I try to go on anyway, my fglrxinfo doesn't work...

---

### Post by bohboh on 2006-06-24
I got that message also, i renamed /usr/lib/libGL.so.1 to /usr/lib/libGL.so.1.old.

---

### Post by escape on 2006-06-25
Thank you, whoever moved this to the HOWTO's forum.

---

### Post by nmsmith on 2006-06-26
This worked for me last week, but today I got "mesa" back when I booted. I repeated the steps again in the howto and now have lovely compiz again!

I am guessing that the problem is to do with the built in system updates. How can I prevent fglrx from being wiped?

---

### Post by escape on 2006-06-26
[QUOTE=nmsmith]This worked for me last week, but today I got "mesa" back when I booted. I repeated the steps again in the howto and now have lovely compiz again!

I am guessing that the problem is to do with the built in system updates. How can I prevent fglrx from being wiped?[/QUOTE]

You likely updated your kernel. When you update your kernel, it doesn't automatically update the restricted modules if you had them installed. Even if it did, I'm not sure if xorg-driver-fglrx could manage the kernel upgrade.

---

### Post by Dimas on 2006-07-04
The howto doesn't work for me :-( I reinstalled fglrx driver, restricted modules... and:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

It happened when I updated ati drivers from saveas repository I think. Or when I updated the mesa libraries... I don't know :(

I think there's something wrong here:

```
$ ls -alis /usr/lib/fglrx/
total 452
390818   4 drwxr-xr-x   2 root root   4096 2006-07-04 20:31 .
340038  40 drwxr-xr-x 164 root root  40960 2006-07-04 20:31 ..
388609 408 -rw-r--r--   1 root root 410880 2006-06-28 21:21 libGL.so.1.2.xlibmesa
388610   0 lrwxrwxrwx   1 root root     12 2006-07-03 22:20 libGL.so.1.xlibmesa -> libGL.so.1.2
```

```
$ ls -alis /usr/lib/ | grep libGL
341234     0 lrwxrwxrwx   1 root root       16 2006-06-02 19:08 libGLEW.so.1.3 -> libGLEW.so.1.3.1
341235   208 -rw-r--r--   1 root root   205204 2005-11-30 21:47 libGLEW.so.1.3.1
340409     0 lrwxrwxrwx   1 root root       12 2006-07-03 22:21 libGL.so.1 -> libGL.so.1.2
340404   632 -rwxr-xr-x   1 root root   642476 2006-06-26 21:48 libGL.so.1.2
342733     0 lrwxrwxrwx   1 root root       20 2006-07-03 22:21 libGLU.so.1 -> libGLU.so.1.3.060500
342720   476 -rw-r--r--   1 root root   483308 2006-06-28 21:21 libGLU.so.1.3.060500
```

Anyone can help? Thx!

---

### Post by darrenm on 2006-07-04
[QUOTE=Dimas]The howto doesn't work for me :-( I reinstalled fglrx driver, restricted modules... and:

Anyone can help? Thx![/QUOTE]
When you ```
sudo modprobe fglrx
``` what happens?
If you can modprobe it then what does ```
/var/log/Xorg.0.log
``` say after you ```
sudo /etc/init.d/gdm restart
```?

---

### Post by Dimas on 2006-07-04
[QUOTE=darrenm]When you sudo modprobe fglrx what happens?[/QUOTE]
Nothing ?
[QUOTE=darrenm]If you can modprobe it then what does /var/log/Xorg.0.log say after you sudo /etc/init.d/gdm restart?[/QUOTE]

I filtered this:

```
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.25.18
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x4000 at 0xb720d000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```
```

(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.26.18
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
```

```
II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.26.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.26g1                           
(II) ATI Proprietary Linux Driver Build Date: Jun 22 2006 12:50:04
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.26.1-driver-lnx-275228
```

```
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.26.18
	ABI class: X.Org Server Extension, version 0.2
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
```

---

### Post by darrenm on 2006-07-04
[QUOTE=Dimas]Nothing ?


I filtered this:

```
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.25.18
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
[/QUOTE]
aha. I'm no Ubuntu / Debian expert but all my problems with this have been to do with running a different kernel version to the module. Looks to me like yours is the same.

Try [code]sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install linux-restricted-modules-$(uname -r)
``` then check
```
ls -alt /usr/src
``` and check linux is a symlink to your current kernel version.
Then if you still have problems maybe
```
sudo apt-get remove xorg-driver-fglrx && sudo apt-get install xorg-driver-fglrx
```

---

### Post by d3x7r0 on 2006-07-05
I finnaly figured out why my fglrx wasn't working and it was the kernel to blame :D

I haven't tried it yet but searching google for my chipset (VIA PT880 Ultra) I found out that agpgart only started supporting my chipset in version 2.6.17... since ubuntu is still using 2.6.16 I wouldn't be able to use my agp card with 3D aceleration... I'm gonna try to compile a new kernel now and see if it solves my problems :)

---

### Post by darrenm on 2006-07-05
[QUOTE=d3x7r0]I finnaly figured out why my fglrx wasn't working and it was the kernel to blame :D

I haven't tried it yet but searching google for my chipset (VIA PT880 Ultra) I found out that agpgart only started supporting my chipset in version 2.6.17... since ubuntu is still using 2.6.16 I wouldn't be able to use my agp card with 3D aceleration... I'm gonna try to compile a new kernel now and see if it solves my problems :)[/QUOTE]
Good luck with that but this line 
[code] (WW) fglrx(0): Kernel Module version does *not* match driver. [\code] 
says different?

---

### Post by dualtone on 2006-07-05
Hi everyone
I ***still*** can't get DRI working with my Radeon Mobility M300 (X300) ](*,)
I'm running Dapper and have tried everything I've seen (great work, btw, to all those who've put in so much effort over this).

Perhaps someone will be able to figure out my problem from my Xorg.0.log and xorg.conf? (Both in the attached ZIP file -- *'configs.zip'*)

**Thanks in advance for any and all help/suggestions!!!** :-D
You can email me [EMAIL="mr_matt_eaves@yahoo.co.uk"]**HERE**[/EMAIL]

---

### Post by Dimas on 2006-07-05
[QUOTE=darrenm]Good luck with that but this line 
[code] (WW) fglrx(0): Kernel Module version does *not* match driver. [\code] 
says different?[/QUOTE]

This goes to me? I reviewed your lines in your last post and all links are ok. And reinstalling restricted modules and xorg-driver-fglrx not solved my problem.

I view two posible causes:

**1) Kernel fglrx Module is 8.25, and the driver I've installed is the 8.26.**
(*(WW) fglrx(0): Kernel Module version does *not* match driver.*)
I tried:
- If I downgrade to 8.25 driver all goes fine. But when I update to 8.26 it doesn't match with kernel module version and I don't have acceleration.
- I tried to disable kernel fglrx module, but when I reboot I don't have acceleration.
Solution?
- Downgrade to 8.25 driver.. but for xgl sux.
- Update kernel fglrx module to 8.26. _BOT HOW??_ :(

**2) Driver is compiled for x.org 6.8.99.8 but I've 7.0**
If that's the problem, Why other people with dapper can run 8.26 drivers? :/

Can anyone help with **1)** ?
I attached Xorg.0.log and xorg.conf

---

### Post by d3x7r0 on 2006-07-05
[QUOTE=darrenm]Good luck with that but this line 
[code] (WW) fglrx(0): Kernel Module version does *not* match driver. [\code] 
says different?[/QUOTE]

Was that for me? :roll: 

Well I tried to compile and everything went smooth, even smoother than compiling 2.6.16 BUT the kernel module gives an error about a missing "makefile.lib.c" and doesn't compile so no go... :( I've read in the web that some other project had the exact same error message in this kernel but they provided a patch to fix and with fglrx beeing closed source I don't think it's possible to get one without ati releasing a new version of the driver...

So no 3D for me untill ati fixes this issue :(

PS: I suggest that everyone having problems like mine (where everything went fine but it still didn't work) take a look at your chipset and make sure agpgart supports it since it looks like the one built into the ati driver only works in kernels from the 2.4.x series...

---

### Post by d3x7r0 on 2006-07-05
[QUOTE=Dimas]This goes to me? I reviewed your lines in your last post and all links are ok. And reinstalling restricted modules and xorg-driver-fglrx not solved my problem.

I view two posible causes:

**1) Kernel fglrx Module is 8.25, and the driver I've installed is the 8.26.**
(*(WW) fglrx(0): Kernel Module version does *not* match driver.*)
I tried:
- If I downgrade to 8.25 driver all goes fine. But when I update to 8.26 it doesn't match with kernel module version and I don't have acceleration.
- I tried to disable kernel fglrx module, but when I reboot I don't have acceleration.
Solution?
- Downgrade to 8.25 driver.. but for xgl sux.
- Update kernel fglrx module to 8.26. _BOT HOW??_ :(

**2) Driver is compiled for x.org 6.8.99.8 but I've 7.0**
If that's the problem, Why other people with dapper can run 8.26 drivers? :/

Can anyone help with **1)** ?
I attached Xorg.0.log and xorg.conf[/QUOTE]

Try looking at this tutorial:
[ [multimedia] Ubuntu 6.06 - Howto: Fglrx 8.26.18 Driver Install (works With Xpress Series Cards Now!)](ttp://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx)

It might help you to figure out how to update the kernel module :)

---

### Post by Dimas on 2006-07-05
[QUOTE=d3x7r0]Try looking at this tutorial:
[ [multimedia] Ubuntu 6.06 - Howto: Fglrx 8.26.18 Driver Install (works With Xpress Series Cards Now!)](ttp://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx)

It might help you to figure out how to update the kernel module :)[/QUOTE]
Thanks but... indeed this guide has been the one that has taken me to the present situation ;-)

Looks like
"sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb" and
"sudo module-assistant prepare,update"
"sudo module-assistant build,install fglrx"
"sudo depmod"
would do the kernel module update .. but not :(

---

### Post by darrenm on 2006-07-05
[QUOTE=d3x7r0]Was that for me? :roll: [/QUOTE]
sorry yes, got confused.

---

### Post by Dimas on 2006-07-05
Did you know if are correct these sections of my xorg.conf correct for 8.26 property drivers and ati 9700 ? I tried to enable/disable *Load "dri"* but the *[drm] failed to load kernel module "fglrx"* is there...

```
Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "DRI"
	Mode         0666
EndSection
```

Looks like the problem is DRI:

```
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

---

### Post by andnobodyslept on 2006-07-06
Some quick basic questions.
First off I have an old video card (ATI Rage Mobility M3 AGP 2x). I've been looking around for a few days trying to get the DRI enabled, and I can't even tell if the current drivers support 3D acceleration.
If the current drivers do support my card then I need to know how to figure out if I have them and how to enable DRI, right now I'm getting the dreaded 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
 Here's my xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks

---

### Post by dualtone on 2006-07-06
When I use the command *sudo dmesg | grep fglrx* I get:

```
 [17179616.704000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179616.704000] fglrx: Unknown symbol agp_bind_memory
[17179616.704000] fglrx: Unknown symbol agp_enable
[17179616.704000] fglrx: Unknown symbol agp_backend_acquire
[17179616.704000] fglrx: Unknown symbol agp_free_memory
[17179616.704000] fglrx: Unknown symbol agp_allocate_memory
[17179616.704000] fglrx: Unknown symbol agp_unbind_memory
[17179616.704000] fglrx: Unknown symbol agp_copy_info
[17179616.704000] fglrx: Unknown symbol agp_backend_release
[17179619.340000] fglrx: Unknown symbol agp_bind_memory
[17179619.340000] fglrx: Unknown symbol agp_enable
[17179619.340000] fglrx: Unknown symbol agp_backend_acquire
[17179619.340000] fglrx: Unknown symbol agp_free_memory
[17179619.340000] fglrx: Unknown symbol agp_allocate_memory
[17179619.340000] fglrx: Unknown symbol agp_unbind_memory
[17179619.340000] fglrx: Unknown symbol agp_copy_info
[17179619.340000] fglrx: Unknown symbol agp_backend_release
```

As, my card is PCI Express rather than AGP, I wonder if all this is significant? If so what can I do about it? Everything works fine except DRI (which I really need). Thoughts?
:-D **Thanks!** :-D

---

### Post by kizz on 2006-07-07
I did the guide at page 1, but still I have the Mesa driver activated. 

I got ati 9800 Pro, here is my xorg.conf


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
        Load  "GLcore"
        Load  "glx"
        Load  "dri"
        Load  "extmod"
        SubSection "extmod"
        Option "omit xfree86-dga" 

EndSubSection

EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        Option "UseInternalAGPGART" "no"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
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

Section "DRI"
	Mode         0666
EndSection



Do anyone see what my problem is?


EDIT: My xorg.conf file is maybe infected by this guide: [http://www.ubuntu.si/dokuwiki/doku.php?id=instaliranje_gonilikov_za_ati-jeve_karticei](http://www.ubuntu.si/dokuwiki/doku.php?id=instaliranje_gonilikov_za_ati-jeve_karticei)
(if you can't see the guide, search for ati.jeve, and press the link)

---

### Post by Ftpmaster on 2006-07-08
> **kizz said:**
> I did the guide at page 1, but still I have the Mesa driver activated. 

I got ati 9800 Pro, here is my xorg.conf


i have the same card and this worked for me
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2")

-edit-
to be precise , i used only "sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper"

---

### Post by Alpha1Dash1 on 2006-07-12
Hi all, I think I may have stumbled accross the reason why the fix on page 1 of this thread works fine for some & not for others...

Initially I followed the instructions detailed in this howto:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") 

to install the drivers from ati.com for my x800pro. Then I found I had the "Mesa Issue" so tried the solution suggested on page 1. It didn't work, but I noticed that at 2 points the varions commands reported error messages along the lines of: "rmdir : failed to remove folder ./<x>/<y>- not empty" (sorry this was late last night, & I can't remember the exact messages). So, fearing nothing, went through the procedure again, but this time, when I saw the error message went & took the folders out by hand & then re-ran the command. This time the solution worked perfectly.

**NOTE** : This is meant as information only. I took this rash action because it didn't matter if I lost everything - I only installed it last Friday and so had nothing much to loose. **[COLOR="Red"]I strongly recommend that until someone who knows what they are doing (like escape) verifies it as safe you don't try it at home.     [/COLOR]**

---

### Post by Landser on 2006-07-12
The fglrx drivers hate me, they just NEVER work for me... I install them
and everything looks fine & all until:

```
fglrxinfo
```

```
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT

```

... I was like "what the hell?"

This is a radeon 9250, the xorg.conf is fine as well as the log file.

Man... Time to fix all this mess and return back to Mesa, that's the only driver that I can get DRI & 3D acceleration with, even though it's slow..

So.. What do you guys recommend?, should I stick with my Mesa drivers since they work with DRI & 3D or should I *still* try to get the cursed fglrx driver to work?.

---

### Post by philipacamaniac on 2006-07-12
Someone help me!! In hoary and breezy, my ATI Radeon 9700 Pro worked fine. I'm pretty sure I had it working in Dapper, but I've upgraded my computer, and so I reinstalled Dapper. Ever since then, I can't get any DRI, and mesa is the only 3D accel that will work. I've tried almost every solution I can find on these forums and Google, including several different ATI driver versions (including the latest), the supplied xorg-driver-fglrx, as well as the various remove/reinstall methods. Nothing has provided 3D acceleration.

I'm getting several errors, mainly related to AGP.

My hardware:
ASUS motherboard with VIA chipset
ATI Radeon 9700 Pro
Intel P4 3Ghz
2GB RAM

Here is the output of fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

``` 
Here is the output of dmesg |grep agp && dmesg |grep fglrx
```
[17179611.740000] Linux agpgart interface v0.101 (c) Dave Jones
[17179611.744000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179611.744000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[17179611.744000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179631.316000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[17179631.316000] [fglrx:firegl_unlock] *ERROR* Process 4580 using kernel context 0
``` 
I've attached my xorg.conf, as well as a condensed version of my Xorg.0.log (file size constraints of the forum).

As you can see, it seems that agp doesn't initialize because of:
```
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
``` which in turn causes DRI to fail, which in turn disable direct 3D rendering.

I've also tried different AGP aperture sizes with no success. I tried blacklisting agpgart and/or via_agp, but that has no affect, because modprobing fglrx seems to always load agpgart.

PLEASE HELP!

EDIT: I just read in an earlier post in this thread that the VIA PT880 Ultra chipset wasn't added until Linux 2.6.17.  That sucks big time!

---

### Post by kizz on 2006-07-17
> **Ftpmaster said:**
> i have the same card and this worked for me
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2")

-edit-
to be precise , i used only "sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper"

I did that code you send, but I have everything installed. Nothing new is installed. I have tried [http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+mesa+issue](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+mesa+issue) 
this link and done everything, but still mesa affects the shit. Here is my xorg.conf , see if someone can find a problem please :)

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by escape on 2006-07-17
> **Alpha1Dash1 said:**
> t didn't work, but I noticed that at 2 points the varions commands reported error messages along the lines of: "rmdir : failed to remove folder ./<x>/<y>- not empty" (sorry this was late last night, & I can't remember the exact messages). So, fearing nothing, went through the procedure again, but this time, when I saw the error message went & took the folders out by hand & then re-ran the command. This time the solution worked perfectly.


I've actually done this (use the rm command) to fix similar problems with other things;  it's actually quite useful. You do, however, have to be careful about it. I've added this to the front page because I think it is a useful thing to keep in mind. Also, I am definitely by no means an expert on this whole thing. In the end, the "rm solution" is usually tried despite warning because people are so desperate to fix their problem.

---

### Post by cptjaben on 2006-07-25
After following the original howto without succes i tried the method that worked for nim901, which can be found [here]("http://ubuntuforums.org/showthread.php?t=143283&page=3&highlight=ati+driver") (page 3 of this thread). after completing the steps i ran fglrxinfo and i got this:

[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsShader
[fglrx] API ERROR: could not register entrypoint for GetShaderiv
[fglrx] API ERROR: could not register entrypoint for GetShaderInfoLog
[fglrx] API ERROR: could not register entrypoint for IsProgram
[fglrx] API ERROR: could not register entrypoint for GetProgramiv
[fglrx] API ERROR: could not register entrypoint for GetProgramInfoLog
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparate
[fglrx] API ERROR: could not register entrypoint for StencilMaskSeparate
[fglrx] API ERROR: could not register entrypoint for BlendEquationSeparate
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT
[fglrx] API ERROR: could not register entrypoint for BlendFuncSeparate
[fglrx] API ERROR: could not register entrypoint for FogCoordf
[fglrx] API ERROR: could not register entrypoint for FogCoordfv
[fglrx] API ERROR: could not register entrypoint for FogCoordd
[fglrx] API ERROR: could not register entrypoint for FogCoorddv
[fglrx] API ERROR: could not register entrypoint for FogCoordPointer
[fglrx] API ERROR: could not register entrypoint for MultiDrawArrays
[fglrx] API ERROR: could not register entrypoint for MultiDrawElements
[fglrx] API ERROR: could not register entrypoint for PointParameterf
[fglrx] API ERROR: could not register entrypoint for PointParameterfv
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3f
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3d
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3b
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3s
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3i
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3ub
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3us
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3ui
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3fv
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3dv
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3bv
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3sv
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3iv
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3ubv
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3usv
[fglrx] API ERROR: could not register entrypoint for SecondaryColor3uiv
[fglrx] API ERROR: could not register entrypoint for SecondaryColorPointer
[fglrx] API ERROR: could not register entrypoint for WindowPos2d
[fglrx] API ERROR: could not register entrypoint for WindowPos2f
[fglrx] API ERROR: could not register entrypoint for WindowPos2i
[fglrx] API ERROR: could not register entrypoint for WindowPos2s
[fglrx] API ERROR: could not register entrypoint for WindowPos2iv
[fglrx] API ERROR: could not register entrypoint for WindowPos2sv
[fglrx] API ERROR: could not register entrypoint for WindowPos2fv
[fglrx] API ERROR: could not register entrypoint for WindowPos2dv
[fglrx] API ERROR: could not register entrypoint for WindowPos3i
[fglrx] API ERROR: could not register entrypoint for WindowPos3s
[fglrx] API ERROR: could not register entrypoint for WindowPos3f
[fglrx] API ERROR: could not register entrypoint for WindowPos3d
[fglrx] API ERROR: could not register entrypoint for WindowPos3iv
[fglrx] API ERROR: could not register entrypoint for WindowPos3sv
[fglrx] API ERROR: could not register entrypoint for WindowPos3fv
[fglrx] API ERROR: could not register entrypoint for WindowPos3dv
[fglrx] API ERROR: could not register entrypoint for GenQueries
[fglrx] API ERROR: could not register entrypoint for DeleteQueries
[fglrx] API ERROR: could not register entrypoint for IsQuery
[fglrx] API ERROR: could not register entrypoint for BeginQuery
[fglrx] API ERROR: could not register entrypoint for EndQuery
[fglrx] API ERROR: could not register entrypoint for GetQueryiv
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectiv
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuiv
[fglrx] API ERROR: could not register entrypoint for BindBuffer
[fglrx] API ERROR: could not register entrypoint for DeleteBuffers
[fglrx] API ERROR: could not register entrypoint for GenBuffers
[fglrx] API ERROR: could not register entrypoint for IsBuffer
[fglrx] API ERROR: could not register entrypoint for BufferData
[fglrx] API ERROR: could not register entrypoint for BufferSubData
[fglrx] API ERROR: could not register entrypoint for GetBufferSubData
[fglrx] API ERROR: could not register entrypoint for MapBuffer
[fglrx] API ERROR: could not register entrypoint for UnmapBuffer
[fglrx] API ERROR: could not register entrypoint for GetBufferParameteriv
[fglrx] API ERROR: could not register entrypoint for GetBufferPointerv
[fglrx] API ERROR: could not register entrypoint for DetachShader
[fglrx] API ERROR: could not register entrypoint for CreateShader
[fglrx] API ERROR: could not register entrypoint for ShaderSource
[fglrx] API ERROR: could not register entrypoint for CompileShader
[fglrx] API ERROR: could not register entrypoint for CreateProgram
[fglrx] API ERROR: could not register entrypoint for AttachShader
[fglrx] API ERROR: could not register entrypoint for DeleteShader
[fglrx] API ERROR: could not register entrypoint for DeleteProgram
[fglrx] API ERROR: could not register entrypoint for LinkProgram
[fglrx] API ERROR: could not register entrypoint for UseProgram
[fglrx] API ERROR: could not register entrypoint for ValidateProgram
[fglrx] API ERROR: could not register entrypoint for DrawBuffers
[fglrx] API ERROR: could not register entrypoint for GetAttachedShaders
[fglrx] API ERROR: could not register entrypoint for GetAttribLocation
[fglrx] API ERROR: could not register entrypoint for GetShaderSource


Does anyone know how this could be fixed or what it means?

Thanks much,
cptjaben

---

### Post by orangesims on 2006-07-26
n/m

---

### Post by cocoapunk on 2006-07-29
Hi all,

I've gotten most of the fglrx driver working, except one part.

Here are my fglrxinfo (debug on) and glxinfo
#:/var/log$ LIBGL_DEBUG=verbose fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
#:glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

As for xorg.conf, I used aticonfig --initial

Anyone have a clue to why DRI isn't working? 

thanks

---

### Post by brandon moore on 2006-07-31
i've racked my brain and read most of this thread, but i can't get it to work...  here's my stuff

/etc/X11/xorg.conf:
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768"
	EndSubSection
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

Section "DRI"
	Mode         0666
EndSection



this kicks back an error saying no screens are found.

> dmesg | grep fglrx

kicks back nothing.  it just goes back to a prompt.

any help?

---

### Post by rashkeev on 2006-07-31
Just a thought: the "mesa issue" kept popping up for me whenever I tried to install XGL. Every time my 3d libraries kept switching over to the mesa ones, and I could use this howto to set it back. Then I'd try again, lured by the promise of eye candy...

Anyone else have similar experience?

---

### Post by darrenm on 2006-07-31
> **rashkeev said:**
> Just a thought: the "mesa issue" kept popping up for me whenever I tried to install XGL. Every time my 3d libraries kept switching over to the mesa ones, and I could use this howto to set it back. Then I'd try again, lured by the promise of eye candy...

Anyone else have similar experience?

Nope, running fglrx here with Compiz with everything running great (except for Kino with poor frame rates, but thats a problem with XGL, not compiz)

Sorry thats not much help, trying to show theres light at the end of the tunnel...

However I did have loads of problems with the open-source driver, I had to go with the ATi provided binary driver installing as root and everything just worked.

---

### Post by Ftpmaster on 2006-08-02
well i have installed ubuntu 4-5 times by now and always custom compiled kernel, every time ive had mesa but always managed to get ati driver work for default kernel, but last 2 times it dint work for custom kernel, 
first i tried ati 8.26.18 driver but that dint work and then i tried the 
8.27.10 and it worked, so maybe it works for others too.
First try this howto with 8.27.10 driver.
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)
[https://www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run](https://www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run)

If this doesnt work u can try automatic install
sudo sh ati-driver-installer-8.27.10-x86.run
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

---

### Post by calvinthomas on 2006-08-09
My xorg.conf file is below, really frustrated because it was working and now nothing will get it working!


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 65.0
	VertRefresh  30.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
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

Section "DRI"
	Mode         0666
EndSection

And my log file is attached, had to zip it, it wouldn't let me add it as a txt file! Too big!

Calv

---

### Post by e00878 on 2006-08-17
disabling GDM help me fixing mesa issue

$sudo apt-get install xubuntu-desktop
$echo "false" | sudo tee /etc/X11/default-display-manager
$login:
$password:
$startx
$sudo shutdown -h now

---

### Post by darkly on 2006-08-21
I had a similar problem with my Mobility 9000.  Turned out the auto detect (which some post tell you to keep all the default selected values) was selecting ATI (which looked okay) instead of selecting fglrx.  A simple scroll-down during set-up fied all that. The following from URL below fixed the issue.  Google Earth now usable!

hxxps://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2

Install instructions for Ubuntu 5.04 (Hoary Hedgehog) and Ubuntu 5.10 (Breezy Badger)

   1. Install the kernel drivers. These drivers should be installed by default, but it's better to make sure they are installed. You need the package linux-$arch, where you replace $arch by the CPU architecture for the machine. This is 386 for Intel Pentium, 686 for Celeron, Pentium Pro, Pentium II, Pentium III, and Pentium 4 without Hyper-Threading. 686-smp for Pentium 4 with Hyper-Threading, or k7 or k7-smp for AMD athlon. On 64-bit systems, this may be amd64-generic, amd64-k8, amd64-k8-smp, or amd64-xeon.

      sudo apt-get install linux-686

   2. Install the xorg-driver-fglrx package:

      sudo apt-get install xorg-driver-fglrx

   3. Add fglrx to /etc/modules (optional, the advantages/drawbacks of this are: ......):

      echo fglrx | sudo tee -a /etc/modules

   4. Reconfigure Xserver:

      sudo dpkg-reconfigure xserver-xorg

      If ati is auto-selected at the video card selection screen, then go down to select fglrx. Leave other settings to their default value. Or, if you really know what you're doing, do the following instead:

      sudo sed -e 's/"ati"/"fglrx"/' -i /etc/X11/xorg.conf

   5. Restart your computer

---

### Post by luis146 on 2006-08-31
In my particular case, DRI wasn't working because DRM (the Kernel Direct Rendering Module) wasn't loaded. All I had to do was:

sudo modprobe drm

I also ran

sudo depmod -a

but I'm not even sure this is necessary - do I need to say I'm a newcomer to Linux? ;)

Anyway, after rebooting I finally got 3d acceleration instead of the Mesa indirect renderer. I hope this helps some of you still battling with the Mesa issue!

If this still doesn't solve your problem and you suspect DRI is the culprit, it  may be worth checking this troubleshooting guide:

[http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

Cheers

---

### Post by Tangent on 2006-09-01
> **Landser said:**
> The fglrx drivers hate me, they just NEVER work for me... I install them
and everything looks fine & all until:

```
fglrxinfo
```

```
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT

```

... I was like "what the hell?"

This is a radeon 9250, the xorg.conf is fine as well as the log file.

Man... Time to fix all this mess and return back to Mesa, that's the only driver that I can get DRI & 3D acceleration with, even though it's slow..

So.. What do you guys recommend?, should I stick with my Mesa drivers since they work with DRI & 3D or should I *still* try to get the cursed fglrx driver to work?.

Yeah, I had this problem too, with the exact  same video card. Anyway, this shows up for many of the RADEONs below 9500 with the newest version of the driver, but on the bright side, this error means you're close to done. You basically just need to roll back the libGL file, which you can download here: [http://files.covertprestige.info/important/libGL.so.1.2](http://files.covertprestige.info/important/libGL.so.1.2) . Download it to someplace and then use:
```
sudo cp libGL.so.1.2 /usr/lib/
```
And that should take care of it.

Also, don't give me credit for this, I got it from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29)
I would suggest that anyone having problems should check that page out, it's really very good.

---

### Post by CA_Warren on 2006-09-02
Hmm....This may be the same problem as everyone else is having, or a different one. It's hard to tell for me, because most people aren't describing the physical affects of their problems so much..

Here's what's happening with me: I *think* that every single online HowTo for this has worked for me getting fglrx installed and running - I've installed from the ATI .run file, from the apt repositories, from downloaded .deb files, and so on. I've followed Methods I and II in the other major Ubuntu Dapper fglrx Installation Guide, as well as this one, and they all lead to the same thing-

A restart, and a screen that A) Only takes up the left half of the monitor, though it's width varies by about an inch with the constant high-speed flickering it goes through, and B) is completely unreadable, much like a monitor set to too high of a resolution.

Yet it isn't set to too high of a resolution: The xorg.conf file specifies 1280x800, which is optimal for my monitor, and I've even tried reconfiguring X.org to perform at lower resolutions in case that was causing the issue. No avail.

Refresh rates shouldn't make much of a difference on an LCD screen, but I tried both 60 and 75 anyways. Still no avail.

Any ideas as to what might be causing this? I don't know how frequently dmesg and the xorg.0.log are refreshed, but dmesg after a reboot (since I can't read a thing in that mode) says nothing at all about fglrx, and the xorg.0.log doesn't seem to have much unusual either - I may not see something worth noting in it, however, so it is attached (this was the backup file when I rebooted - the normal file from when it tried to boot using fglrx as the display driver).

Thanks for any help or advice in advanced, I'd really like to get this working...just can't seem to figure out what's wrong.


SPECS:

Compaq Presario X1000
Intel Pentium-M 1.3GHz processor
15.4” WXGA screen (1280x800)
32MB ATI Mobility Radeon 9200
(I know - not the single most ideal setup for Graphics Acceleration anyways)

---

### Post by resolost on 2006-09-04
So heres the deal... last week I tried to get xgl and compiz workin on my computer... well long story short.. it didnt work... I thought that I had undone everything that I did to try to get it to work but apparently I have not because I cannot get the mesa information to go away... before I tried xgl and compiz everything worked fine... I have tried removing fglrx and reinstalling everyway I can find but always end up with the same result... I believe that I have something left over from my failed attempts to get xgl and compix working but have not been able to find what it is.. my information is as follows:

Pentium M
Mobility X700
xorg 7.0

fglrxinfo : 
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

cat /var/log/Xorg.0.log | grep WW :
```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

cat /var/log/Xorg.0.log | grep EE :
```
(EE) fglrx(0): Fail to initialize ASIC in kernel.
(EE) fglrx(0): Hardware already been locked.
```


Before my problems... my xorg.conf file worked fine so I am 99.9% sure it is not the problem but here it is anyway

cat /etc/X11/xorg.conf : 
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
    Identifier                          "ATI"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "(null)"
    Option "ScreenOverlap"              "0"
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=5653
    Screen 0
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

---

### Post by darrenm on 2006-09-04
Probably no help but I forgot to take /usr/bin/startcompiz from my session and it caused me no end of trouble. 

Check processes to ensure cgwd or gnome-window-decorator are not running.

I would also follow the binary install guide on the Ubuntu wiki e.g ```
fakeroot sh ati-driver-installer-8.28.8.run --buildpkg ubuntu/Dapper && sudo dpkg -i *.deb && sudo module-assistant prepare,update && sudo module-assistant build,install fglrx-kernel
```
if you haven't already.

---

### Post by resolost on 2006-09-04
I have already removed the startcompiz... ive looked through the processes and cgwd or gnome-window-decorator are not running... and ive done the binary  install twice already with no luck... thanks for trying though...

---

### Post by electrosoccertux on 2006-09-04
Well it said to post in here, so I'm posting in here.

I followed the guide for ATI-cards/Xgl/Compiz/32-bit over at compiz.net in their Howto section, however I seem to be stuck, for two reasons:
1). gconf-editor doesn't have any plugins for compiz besides fade. But I have the latest complete plugins package installed.
2). glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

And my xorg.conf has Load "DRI" so I should be set.

I followed the intall steps perfectly. I already had fglrx working fine accelerating all the open-gl apps/games, but my Xgl doesn't want to work. Any ideas what I should do? Thanks.

---

### Post by zazery on 2006-09-04
I'm running **Kubuntu LTS 6.06** and I've tried most of what was mentioned in this thread and in the official documentation and no such luck. I've tried to provide as much information as I can think of. Help is greatly appreciated.


I've got a **Radeon 9600 Pro** and I have a **dual screen** setup.
```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
```

The last thing I tried was [URL="
http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually"]method 2[/URL] of the official installation guide. This included downloading [B]ati-
driver-installer-8.26.18-x86.run[/B]. There were no errors reported the steps listed in the guide.

When I check dmesg to see if fglrx was loaded properly
```
dmesg | grep fglrx
[17179623.376000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179623.376000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179623.376000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0
```

When I type fglrxinfo I get the following:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

Dri is in my module section of my xorg.conf. It was also mentioned that 'drm' might be causing problems. When I 'sudo modprobe drm' it gives me the following error:
```
FATAL: Error inserting drm (/lib/modules/2.6.15-26-386/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
```

However, in my Xorg.0.log file it reports that DRM is loaded correctly.In my Xorg.0.log file it also says the following:
```
...

(==) fglrx(0): NoAccel = NO

...

(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!    *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available    *
(WW) fglrx(0): ***********************************

...

(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(WW) fglrx(1): ***********************************
(WW) fglrx(1): * DRI initialization disabled!    *
(WW) fglrx(1): * 2D acceleraton available (MMIO) *
(WW) fglrx(1): * no 3D acceleration available    *
(WW) fglrx(1): ***********************************
```

Here is my xorg.conf file:
[Click here for my xorg.conf file]("http://24.86.105.165/mesaissue/xorg.conf")

Here is my Xorg.0.log file:
[Click here for my Xorg.0.log file.]("http://24.86.105.165/mesaissue/Xorg.0.log")

Thanks!

---

### Post by joy uf on 2006-09-17
Hello,

i've been getting this error:
> (WW) fglrx(1): ***********************************
(WW) fglrx(1): * DRI initialization disabled!    *
(WW) fglrx(1): * 2D acceleraton available (MMIO) *
(WW) fglrx(1): * no 3D acceleration available    *
(WW) fglrx(1): ***********************************

I fixed it by adding this to the end of my xorg.conf:
> Section "Extensions"
        Option      "Composite" "Disable"
EndSection


After that, I did 
> sudo aticonfig --overlay-type=Xv 
and restartet my X Server.

I don't know what Composite is for, but at least now DRI loads and xine-check doesn't complain about Xv-Overlays.

HTH,
joy

---

### Post by darrenm on 2006-09-17
> **joy uf said:**
> Hello,

i've been getting this error:


I fixed it by adding this to the end of my xorg.conf:


After that, I did 

and restartet my X Server.

I don't know what Composite is for, but at least now DRI loads and xine-check doesn't complain about Xv-Overlays.

HTH,
joy

I assume you're on Edgy then?

---

### Post by joy uf on 2006-09-17
> **darrenm said:**
> I assume you're on Edgy then?

Yes, I am.

---

### Post by timetunnel on 2006-09-18
I had the "mesa issue" since kernel 2.6.15-24 and always booted into 2.6.15-23 if I needed the speed of the graphics card. I didn't try this howto here to fix the problem, because booting to 2.6.15-23 was fine for me. 

Today, security-updates of fglrx stuff and the kernel (to 2.6.15-27) were release, and suddenly the mesa issue is gone on my system (IBM Thinkpad R52 with an ATI X300). :D

---

### Post by mrbrdo on 2006-09-23
My contribution to the howto:
> Open a terminal and type:
```
glxinfo | grep OpenGL
```
Output should be similar to this (it's definetly not working if it mentions MESA):
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.2 (2.0.6011 (8.28.8))
```
NOTE: You might or might not have the first line. It does not matter if you do or do not.

In terminal, type:
```
glxinfo | grep direct
```
Output should say:
```
direct rendering: Yes
```
NOTE: If you are already using XGL (are logged into it), it will most probably say No. This is normal.

If the above commands don't display what they should, you can try following these steps (after doing each step, **reboot the machine** and see if it works yet):
1. In terminal, type "sudo nano -w /etc/X11/xorg.conf"
Under Section "Device", check that they all say Driver "fglrx". If they say "ati" or "radeon" or anything else, change it to "fglrx".
2. sudo nano -w /etc/X11/xorg.conf
My Section "Device" looks like this, see if you are missing any of the options:
```
Section "Device"
        Identifier  "ATI Card Name"
        BusID       "PCI:1:0:0"
[COLOR="Red"]        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
#        Option      "UseInternalAGPGART" "no" # check comments about[/COLOR] this line
EndSection
```
Uncomment the Option "UseInternalAGPGART" "no" line if you installed fglrx from Seveas repositories or ati.com. If you didn't or don't know, then leave it commented or don't add it.
3. On some cards it is necessary to disable Composite:
sudo nano -w /etc/X11/xorg.conf
At the very end add:
```
Section "Extensions"
   Option "Composite" "disable"
EndSection
```
4. Reboot after following the above steps.
5. If this still doesn't solve it, seek help on the forums. Provide the output of "dmesg | grep fglrx", "dmesg | grep agp", your /etc/X11/xorg.conf and your /var/log/Xorg.0.log

---

### Post by darrenm on 2006-09-24
Its not some cards that you have to disable composite on, its because Edgy uses xorg 7.1.1 which has composite enabled by default and ATi's binary driver won't currently support composite.

---

### Post by dawdler on 2006-10-31
I have an ATI X700 Pro and disabling the composite option solved my MESA issue on Edgy.  :) 

However, I am just curious to what the xorg composite option does?  :confused: 

Is the composite option referring to this compositing method...
[http://en.wikipedia.org/wiki/Alpha_compositing]("http://en.wikipedia.org/wiki/Alpha_compositing")
?

What sort of applications would I be able to tell if composite was on or off?

Thanks in advance,

---

### Post by medeshago on 2006-11-01
Everything was working in dapper. Upgraded to Edgy, and fglrx doesn't work.

nosotros@nosotros:~$ dmesg | grep fglrx
[17179616.256000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179616.260000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179616.260000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0

nosotros@nosotros:~$ dmesg | grep agp
[17179586.300000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.304000] agpgart: Detected VIA KM400/KM400A chipset
[17179586.312000] agpgart: AGP aperture is 128M @ 0xd8000000


xorg.conf and Xorg.0.log:
[ATTACH]18678[/ATTACH]

---

### Post by darrenm on 2006-11-01
> **dawdler said:**
> I have an ATI X700 Pro and disabling the composite option solved my MESA issue on Edgy.  :) 

However, I am just curious to what the xorg composite option does?  :confused: 

Is the composite option referring to this compositing method...
[http://en.wikipedia.org/wiki/Alpha_compositing]("http://en.wikipedia.org/wiki/Alpha_compositing")
?

What sort of applications would I be able to tell if composite was on or off?

Thanks in advance,
Composite is AKA AIGLX, the alternative to XGL. Xorg7.1 has compositing built in so with Beryl and a supported VGA card (e.g. not an ATi card with the fglrx driver) you can just install beryl, start it and you're done.

---

### Post by darrenm on 2006-11-01
> **medeshago said:**
> Everything was working in dapper. Upgraded to Edgy, and fglrx doesn't work.

nosotros@nosotros:~$ dmesg | grep fglrx
[17179616.256000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179616.260000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179616.260000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0

nosotros@nosotros:~$ dmesg | grep agp
[17179586.300000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.304000] agpgart: Detected VIA KM400/KM400A chipset
[17179586.312000] agpgart: AGP aperture is 128M @ 0xd8000000


xorg.conf and Xorg.0.log:
[ATTACH]18678[/ATTACH]


Heres the key ```
II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```
Same as the previous poster, the fglrx driver wont work with composite which is enabled by default in Edgy .

You need to add
```

Section "Extensions"
Option "Composite" "Disable"
EndSection

``` To the end of your xorg.conf file.

Edit : Just to be clear. Its ATi that won't support compositing, not the other way round. NVidia now have a driver that will work with composite but ATi have given no word about supporting it in their drivers.

---

### Post by dawdler on 2006-11-06
> **darrenm said:**
> Composite is AKA AIGLX, the alternative to XGL. Xorg7.1 has compositing built in so with Beryl and a supported VGA card (e.g. not an ATi card with the fglrx driver) you can just install beryl, start it and you're done.

So compositing is not a hardware/driver related mechanism, but rather an extension of the OpenGL specification.  However, the AIGLX directly accesses the video card ([http://en.wikipedia.org/wiki/AIGLX]("http://en.wikipedia.org/wiki/AIGLX")) so does that mean the AIGLX IS like a driver and sits in the kernel space, and so is that why you cannot run beryl with the fglrx driver b/c of driver conflicts?

I tip my hat to you darrenm.  Thanks.

---

### Post by darrenm on 2006-11-06
> **dawdler said:**
> So compositing is not a hardware/driver related mechanism, but rather an extension of the OpenGL specification.  However, the AIGLX directly accesses the video card ([http://en.wikipedia.org/wiki/AIGLX]("http://en.wikipedia.org/wiki/AIGLX")) so does that mean the AIGLX IS like a driver and sits in the kernel space, and so is that why you cannot run beryl with the fglrx driver b/c of driver conflicts?

I tip my hat to you darrenm.  Thanks.

Well I'm not sure about the terminology of if its a driver or not but as I understand it the reason it doesnt work is because ATi won't put the GLX_EXT_texture_from_pixmap extension in their drivers for some reason. If ATi were to write this extension it would work ok. But then perhaps they will need to re-write other sections to allow this to work with DRI.

---

### Post by lmandrake on 2006-11-06
I also have problems getting the 3D / DRI stuff working. I'm using an Asrock 939Dual VSTA Mainboard (ALI M1695 chipset) and a Radeon 9600XT.

I tried all the stuff I could find in this thread and the rest of the board; like blacklisting agp modules, disableing Composite, use internal and external agp etc. and now I'm running out of ideas. Does anybody have an idea for me? (Logs and config attached)

There is one open question: When I use the internal agp driver fglrx loads agpgart. Where can I see if this is the kernel driver or a ati driver?

---

### Post by darrenm on 2006-11-06
Why have you got DRI hashed out? The fglrx driver wont work without DRI.

---

### Post by lmandrake on 2006-11-06
Forget about that. Uncommenting DRI was the last thing I tried ... read it somewhere.

---

### Post by darrenm on 2006-11-06
Your log file also says that DRI is disabled. Can you try again with DRI enabled and then post the Xorg.log and xorg.conf files?
thanks

---

### Post by lmandrake on 2006-11-06
Enabling DRI again with the kernel agp did the job :) Strange thing is that I had the exact configuration running yesterday and there was 3D not working.

Thanks darrenm

---

### Post by darrenn on 2006-11-06
Great tips darrenm. Keep up the good work.

---

### Post by Darkfrost101 on 2006-11-06
Yay! I didnt get past the first step :)

However, im not sure if this is actually my fault :P

> 
root@jacob-laptop:/home/jacob# sudo apt-get update
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 4 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release.gpg [307B]
Hit [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release
Errhttp://mirror.ubuntulinux.nl dapper-seveas Release

Get: 5 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release [34.2kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release
Hit [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas/drivers Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get: 7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Packages
Fetched 34.6kB in 15s (2180B/s)
Reading package lists... Done
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
root@jacob-laptop:/home/jacob#


---

### Post by darrenm on 2006-11-06
Just import the Seveas GPG key. The website [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) tells you what to do.

But here it is anyway ```
wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
```

---

### Post by medeshago on 2006-11-11
Can't get it to work

nosotros@nosotros:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

nosotros@nosotros:~$ dmesg | grep fglrx
nosotros@nosotros:~$ dmesg | grep agp
[17179587.044000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.052000] agpgart: Detected VIA KM400/KM400A chipset
[17179587.060000] agpgart: AGP aperture is 128M @ 0xd8000000
nosotros@nosotros:~$ 


[ATTACH]19167[/ATTACH]

---

### Post by jaywhy13 on 2006-11-13
Ok... I think I've tried everything....

jay@s4b:/usr/lib/xorg/modules$ ll dri
lrwxrwxrwx 1 root root 12 2006-10-14 23:56 dri -> /usr/lib/dri


jay@s4b:/usr/lib/xorg/modules$ cat /etc/default/linux-restricted-modules-common
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="fglrx"




jay@s4b:/usr/lib/xorg/modules$ ls -la /usr/lib/ | grep libGL
-rwxr-xr-x   1 root root   642476 2006-08-18 13:54 FGL.renamed.libGL.so.1.2
lrwxrwxrwx   1 root root       27 2006-11-13 05:30 libGL.so -> /usr/lib/fglrx/libGL.so.1.2
lrwxrwxrwx   1 root root       12 2006-11-13 06:15 libGL.so.1 -> libGL.so.1.2
-rw-r--r--   1 root root   642552 2006-10-30 23:14 libGL.so.1.2
-rw-r--r--   1 root root   671844 2006-08-24 00:29 libGLU.a
lrwxrwxrwx   1 root root       11 2006-11-10 09:37 libGLU.so -> libGLU.so.1
lrwxrwxrwx   1 root root       20 2006-11-10 09:37 libGLU.so.1 -> libGLU.so.1.3.060501
-rw-r--r--   1 root root   483308 2006-08-24 00:29 libGLU.so.1.3.060501


jay@s4b:/usr/lib/xorg/modules$ ll /usr/X11R6/lib/modules/dri
lrwxrwxrwx 1 root root 16 2006-11-13 06:45 /usr/X11R6/lib/modules/dri -> ../../../lib/dri


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
fuse
fglrx



jay@s4b:/usr/lib/xorg/modules$ dpkg -l xorg-drver-fglrx
No packages found matching xorg-drver-fglrx.


jay@s4b:/usr/lib/xorg/modules$ dpkg -l linux-restricted-modules-$(uname -r)
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                         Version                                      Description
+++-============================================-============================================-========================================================================================================
ii  linux-restricted-modules-2.6.17-10-386       2.6.17.6-1                                   Non-free Linux 2.6.17 modules on 386



jay@s4b:/usr/lib/xorg/modules$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x81e17a0
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "MOBILITY RADEON X1400 (M54 7145)" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2002)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfdf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 37  vert.: 23
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.592 redY: 0.344   greenX: 0.319 greenY: 0.553
(II) fglrx(0): blueX: 0.159 blueY: 0.144   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 96.2 MHz   Image Size:  367 x 230 mm
(II) fglrx(0): h_active: 1440  h_sync: 1504  h_sync_end 1536 h_blank_end 1760 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 912 v_border: 0
(II) fglrx(0):  YD477171WX2
(II) fglrx(0):  &5@Im&#65533;
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 432/396MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 324/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 324/135MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   4. 392/252MHz @ 60Hz [enable sleep]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep, thermal diode mode]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1440x900 (pitch 0)
(**) fglrx(0): *Mode "1440x900": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"   96.21  1440 1504 1536 1760  900 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.21  1152 1504 1536 1760  864 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   96.21  1024 1504 1536 1760  768 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   96.21  800 1504 1536 1760  600 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   96.21  640 1504 1536 1760  480 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   96.21  1280 1504 1536 1760  720 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "720x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   96.21  720 1504 1536 1760  480 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   96.21  640 1504 1536 1760  432 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   96.21  640 1504 1536 1760  400 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   96.21  512 1504 1536 1760  384 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   96.21  400 1504 1536 1760  300 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   96.21  320 1504 1536 1760  240 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   96.21  320 1504 1536 1760  200 903 904 912 +hsync +vsync
(--) fglrx(0): Display dimensions: (370, 230) mm
(--) fglrx(0): DPI set to (98, 99)
(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)
(**) fglrx(0): *Mode "1440x900": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"   96.21  1440 1504 1536 1760  900 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.21  1152 1504 1536 1760  864 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   96.21  1024 1504 1536 1760  768 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   96.21  800 1504 1536 1760  600 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   96.21  640 1504 1536 1760  480 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   96.21  1280 1504 1536 1760  720 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "720x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   96.21  720 1504 1536 1760  480 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   96.21  640 1504 1536 1760  432 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   96.21  640 1504 1536 1760  400 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   96.21  512 1504 1536 1760  384 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   96.21  400 1504 1536 1760  300 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   96.21  320 1504 1536 1760  240 903 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   96.21  320 1504 1536 1760  200 903 904 912 +hsync +vsync
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x00000729
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xc0715000 (size=0x078cb000)
(II) fglrx(0): UMM area:     0xc0715000 (size=0x078cb000)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb78ff000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.29.6
(II) fglrx(0):     Date: Sep 19 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb78ff000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x07fe0000
(II) fglrx(0): Splitting WC range: base: 0xc0000000, size: 0x7fe0000
(II) fglrx(0): Splitting WC range: base: 0xc4000000, size: 0x3fe0000
(II) fglrx(0): Splitting WC range: base: 0xc6000000, size: 0x1fe0000
(II) fglrx(0): Splitting WC range: base: 0xc7000000, size: 0xfe0000
(II) fglrx(0): Splitting WC range: base: 0xc7800000, size: 0x7e0000
(II) fglrx(0): Splitting WC range: base: 0xc7c00000, size: 0x3e0000
(II) fglrx(0): Splitting WC range: base: 0xc7e00000, size: 0x1e0000
(II) fglrx(0): Splitting WC range: base: 0xc7f00000, size: 0xe0000
(II) fglrx(0): Splitting WC range: base: 0xc7f80000, size: 0x60000
(==) fglrx(0): Write-combining range (0xc7fc0000,0x20000)
(==) fglrx(0): Write-combining range (0xc7f80000,0x60000)
(==) fglrx(0): Write-combining range (0xc7f00000,0xe0000)
(==) fglrx(0): Write-combining range (0xc7e00000,0x1e0000)
(==) fglrx(0): Write-combining range (0xc7c00000,0x3e0000)
(==) fglrx(0): Write-combining range (0xc7800000,0x7e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc7000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc6000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc4000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc0000000,0x7fe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1472 x 7288
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support please upgrade to Xorg 6.9 or later and use Option "TexturedVideo".

---

### Post by baytuni on 2006-11-29
when I try to reinstall fglrx I get this error: 

```
sudo module-assistant install fglrx
Selecting previously deselected package fglrx-kernel-2.6.17-10-generic.
(Reading database ... 106030 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.17-10-generic (from .../fglrx-kernel-2.6.17-10-generic_8.31.5-1+2.6.17-10.33_i386.deb) ...
Setting up fglrx-kernel-2.6.17-10-generic (8.31.5-1+2.6.17-10.33) ...
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/agpgart.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/ali-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/amd-k7-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/amd64-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/ati-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/efficeon-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/intel-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/synclink.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/synclink_gt.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/synclinkmp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/tipar.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/tlclk.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/toshiba.ko is not an elf object
Segmentation fault (core dumped)

```

Why is that?

---

### Post by iammeagain on 2007-01-18
That did get mine to say ATI instead of mesa, but there are still lots of other problems, i have been trying for hours. At least its one step cloer.

---

### Post by brodiepearce on 2007-04-07
The fix on the first page doesn't work for me, the fglrxinfo output is exactly the same as it is before the process:

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

In my xorg.conf file there are also two sections listed as "Device":

```

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Driver      "vesa"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

You can see one lists it's driver as vesa, and the second as fglrx, I have been changing the driver name on the second "Device".  Should I be worried about the first one?

---

### Post by Fighter1405 on 2007-05-23
i just wanted to say thankyou so very very much. I have spent absolutely ages trying to get this to work and it finally does! Yes Thanks again

---

### Post by balthamaisteri on 2007-05-30
Damn, last night i found this thread and i got that mesa turn in to ati, and i was happy. Today when i started my computer it was back to mesa, and that thing doesn't work anymore :( 

why?... this pisses me off

edit:

if do :" sudo apt-get install --reinstall linux-restricted-modules-$(uname -r)" and then Ctrl + Alt +Del it works, but after restart it's gone again :/

I know this can work, i just cant remember how i did this last time, i never had this kind of problems.

---

### Post by Tumpster on 2007-08-09
So with that everything seems to be working for me. BUT if I update from here with the drivers from ati's website it goes back to the mesa problem. THe only way to fix it is to go back through all this all over again. I never had this problem. Is there some way to fix everything and have the latest drivers? I'd appreciate any help! :)

---

### Post by MaximB on 2007-08-13
This guide is a bit outdated as now we have Mesa 7.0.1 and Feisty Fawn.
can you please update this guide with all sources we will need ?

---

### Post by 1feistymedic on 2007-08-14
Yes...and if you could help me as well...my problem is below and I am using Feisty with a Radeon 7000 PCI card..

ok....here is the problem in a nutshell...

1) I have to use the radeon open source driver as shown in this thread:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

2) The binary one is not the one to use as shown in this thread:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

3) I did everything stated in the open source driver how-to

4) I enabled the PCI card in my BIOS

5) I can see the grub load....and then I see the Ubuntu banner with the orange line going from left to right

6) and then I get a blank screen

7) the only way I can get back to a regular screen is to reboot, go into bios, enable the on-board graphics card and disable the pci radeon card and connect the monitor to the onboard graphics card port

what am I doing wrong

9) here is my xorg.conf file:

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc101"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]"
Driver "i810"
BusID "PCI:0:1:0"
EndSection

Section "Device"
Identifier "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
Driver "ati"
BusID "PCI:1:8:0"
EndSection

Section "Monitor"
Identifier "A70"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]"
Monitor "A70"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
Monitor "A70"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Option "AIGLX" "true"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection


10) here is the output for the "glxinfo | grep vendor"

sean@desktop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
sean@desktop:~$

11) here is the output for: glxinfo | grep "direct rendering"

sean@desktop:~$ glxinfo | grep "direct rendering"
direct rendering: No
sean@desktop:~

12) here is LSPCI

sean@desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 DC-100 GMCH [Graphics Memory Controller Hub] (rev 02)
00:01.0 VGA compatible controller: Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller] (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801AB PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AB ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AB IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AB USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AB SMBus (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
01:08.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
01:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
01:0a.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 0
01:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
sean@desktop:~$

WHAT DO I DO NOW? HELP!!!!

---

### Post by rannsaicher on 2007-08-25
EDGY Upgrade from DApper

HW is  9600XT card - 3d working fine in dapper
Edgy upgrade and 3d direct render  stopped 
finally found the comments to add this

Section "Extensions"
   Option "Composite" "disable"
EndSection

to xorg.conf  because edgy uses new modules with compositing on and fglrx wont support compositing.

and were back in the air again.
Thanks guys

---

### Post by ressac on 2007-09-05
Hello i have  with AGP ...

this messeg from xorg log

> [agp] unable to acquire AGP, error "xf86_EINVAL" 

anybody khow how to fix AGP problem? :(

i tired to search and trying :( please help

---

### Post by trisct on 2007-09-13
One thing to look for is in the DRI section of the xorg.log, and see if you have any kind of ENOMEM message in there.  That would tell you the ATI renderer is unable to obtain enough AGP memory mapped.

I think the driver needs at least 32MB of AGP memory (set in your computers BIOS).  My renderer was stuck in MESA software mode until I upped the AGP memory for my ATI 9800 pro.  No more log errors, and the renderer gets set properly.

Now I just have to deal with system freezes when I actually use 3D stuff.  Sigh.

---

### Post by smacfarl on 2007-10-15
So it seems like you have two device sections and two screen sections.

I don't know if this will work, because I am still trying to get my own Radeon 7000 running with full 3d support, It does come up with 2d support.

I suggest eliminating the device and screen sections that contain

Identifier "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]"

and changing the PCI setting in your Radeon Device section

From 

BusID "PCI:1:8:0"

To 

BusID "PCI:1:0:0"

---

### Post by dayosh on 2007-12-02
My friend introduced me to Linux about a year ago.  I started using Feisty and was impressed with the layout.  I upgraded to Gutsy a couple of weeks ago, and then integrated DirectX 9.0c into Wine, and since then, I've been having difficulties.

My computer, quite simply, does not seem to want to believe me that it has an **ATI Radeon X1950 Pro** installed inside of it.  I've been receiving the "dreaded Mesa Error" that many others have been receiving, and cannot make it go away, no matter how many tutorials and forums I peruse.  I've also tried installing the fglrx drivers from multiple sources: Envy, ATI's site, synaptic, etc., and nothing seems to work as of yet.

Right below this post, I'm including all of the terminal commands I've entered, and the returns from those commands that I've received. ** It is important to note also that at one point, the "sudo aticonfig --init" command wiped my xorg.conf file a couple of times** (very frustrating).

I'm also going to include my ORIGINAL xorg.conf file that I had before messing around (Let's hear it for good ol' fashioned common sense! w00!) so that others may look upon it and supplement further advice (or pity, I'm not picky).  Thanks very much in advance!  :)

P.S., If any further info is needed, lemme know what, and I'll make an addendum to this post.  Thanks again!   :)

**Returns for Terminal Commands:**
```
$ fglrxinfo -display :0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

**Another return I've received:**
$ fglrxinfo -display :0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!


$ fglrxinfo -display :1
Error: unable to open display :1


$ lsmod | grep fglrx
fglrx                1481708  0 
agpgart                35016  2 fglrx,intel_agp


$ modinfo fglrx
filename:       /lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/fglrx.ko
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
srcversion:     B47D0E9E450B12FC0C62081
<Bunch of Aliases>
depends:        agpgart
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           firegl:charp


$ dpkg -l xorg-driver-fglrx
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xorg-driver-fg 7.1.0-8.37.6+2 Video driver for ATI graphics accelerators


$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
```



**Original xorg.conf file:**

---

### Post by seatownflyer on 2008-10-16
22 pages, yeesh.  if this has been posted already then I apologize, I do'nt feel like reading 22 pages.  Have you tried changing the AGP texture size in your bios?  That finally got my ati x1950 working and got rid of any lock ups or lingering mesa drivers.  I changed mine from 128 to 512.

---

