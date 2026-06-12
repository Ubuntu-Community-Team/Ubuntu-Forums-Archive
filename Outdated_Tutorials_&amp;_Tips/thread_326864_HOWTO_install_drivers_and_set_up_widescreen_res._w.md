---
title: "HOWTO: install drivers and set up widescreen res. with Intel 945 vga card and Ubuntu"
date: 2006-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by J.Vega on 2006-12-28
I searched the internet for two whole days in order to get together the information needed to install the drivers for my Intel 945GM graphics card in my laptop, and so I thought I should post a guide just for the case somebody else has the same problem ;)

**This guide has been written by my own and has only been tested on my Fujitsu Siemens Amilo Pi1505 laptop with Ubuntu, so I cannot guarantee that it works always.** (although I don't know why it shouldn't work on other laptops with the same vga card :mrgreen: )
The guide has 2 parts. 1. Install the drivers. 2. Set up the resolution
The second part doesn't depend on the first, so you can do the second part even if you didn't do the first part, and also if you have another graphics card.

[COLOR="Red"]**If you intend to install the latest 64bit version of Ubuntu edgy:**[/COLOR]
Don't follow this guide. I've recently installed 64 bit Ubuntu and the driver was already installed. I just had to add the videoram section in the xorg.conf file. Search this guide to see how to do this.

**_1. Install the drivers._**
There's an explanation on how to install the drivers at
[http://yogharp.wordpress.com/2006/12/19/ubuntu-edgy-on-intel-945gm-graphics-wide-screen-lcd-notebooks/](http://yogharp.wordpress.com/2006/12/19/ubuntu-edgy-on-intel-945gm-graphics-wide-screen-lcd-notebooks/)
I followed the guide there (and the instructions following are based on the guide there), but the author says that the widescreen resolution will work immediately after installing the drivers, which was not true for my laptop.

-download the driver package for SuSE Linux from
[http://downloadmirror.intel.com/df-support/9726/eng/dri-Intel-3.4.3006-20051209.i386.rpm](http://downloadmirror.intel.com/df-support/9726/eng/dri-Intel-3.4.3006-20051209.i386.rpm)

-install the alien package from the Ubuntu CD/DVD or from the web via the Synaptic Package Manager

-as su (or via sudo), do ```
alien dri-Intel-3.4.3006-20051209.i386.rpm
```
what you get is a converted .deb-package, which can be easily installed with dpkg

-install the package: again, as su, do ```
dpkg -i dri-Intel-3.4.3006-20051209.i386.deb
```

-the drivers are now installed, so all you have to do now is to put them into the xorg.conf file:
as su, edit ```
/etc/X11/xorg.conf
```, and search for the ```
[device]
```-section, where your graphics card is described. now change the ```
Driver
``` from ```
vesa
``` to ```
i810
```

[COLOR="Red"]**Hint:**[/COLOR] On my laptop, which is able to give the vga card up to 128MB of memory as video RAM, Ubuntu only gives 12MB away (you can see this in /var/log/Xorg.0.log). To give the vga card its 128MB memory, add this line to the end of the "Device"-section where you changed the driver:
```
VideoRam        131072
```
Now if you reboot and look at the /var/log/Xorg.0.log file, you should see something like:
```
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(**) I810(0): VideoRAM: 131072 kByte
[...]
(--) I810(0): Maximum frambuffer space: 130904 kByte
```

That's it, you finished installing the drivers! Reboot or just restart the X server (logout and Ctrl-Alt-Backspace) to check if it works.
If it doesn't work or if you wanna undo everything you just did, do the following:
as su, do dpkg -r dri-Intel
as su, change the Driver in the device-section of your /etc/X11/xorg.conf file back to vesa (or whatever was there before you changed it to i810) and remove the videoram line

**_2. Set the widescreen resolution_**
There's a tool called 915resolution, which hacks the vga BIOS to change the available resolutions. The changes are only temporary (until you reboot) and so there's no risk of messing up your card.

[COLOR="Red"]**News:**[/COLOR] I've noticed, that there is a 915resolution package in the synaptics package manager (at least if you have all available sources activated, like universe and multiverse). Thus, you don't need to download 915resolution by yourself. You can just install it with apt-get or the synaptics package manager.

-download 915resolution for Debian:
[http://www.freshnet.org/debian/hoary/915resolution_0.5-2_i386.deb](http://www.freshnet.org/debian/hoary/915resolution_0.5-2_i386.deb)

-as su, do ```
dpkg -i 915resolution_0.5-2_i386.deb
```
you now have 915resolution installed

-again, as su, do ```
915resolution -l
``` to list the modes of your graphics card

-choose a mode (i recommend the highest resolution, since your laptop screen will probably be unable to use that resolution at all) and set the resolution to the resolution of your choice with ```
915resolution <mode> <width> <height>
```, for example ```
915resolution 54 1280 800
``` to set mode 54 to 1280x800

-now that your vga card has the mode (for this session), you need to tell X that your monitor supports that mode, too. So you have to add a "Modeline" to your /etc/X11/xorg.conf file.

-generate a Modeline for the desired resolution and frequency, for example with the program xorg-edit, or somehow else.
If you use xorg-edit, don't edit your xorg.conf with it! It just messes everything up by setting your keyboard layout to ```
us
``` and such things! just generate the modeline and quit without saving!

-insert the Modeline into your /etc/X11/xorg.conf file:
as su, edit ```
/etc/X11/xorg.conf
```
in your ```
[Monitor]
``` section, add the Modeline to the end of the section. My Monitor section, for example, looks like this now:

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Modeline "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync
EndSection
```

-basically, you're done. The problem is, that after a reboot, your video BIOS is resetted, and you have to execute 915resolution again. Fortunately, 915resolution provides startup scripts (in /etc/rc*.d). Unfortunately, they are at the wrong place there.
So, if you want 915resolution to be executed each time you boot Ubuntu and BEFORE gdm is started, you have to do as follows:

-first, remove the old scripts from the rc*.d directories:
as su, do ```
update-rc.d 915resolution remove
```
then, insert the scripts before gdm:
usually, Ubuntu goes to runlevel 2 and gdm is started by ```
/etc/rc2.d/S13gdm
```
so if you want 915resolution to start before gdm:
as su, do ```
update-rc.d 915resolution defaults 12
```
you can check if you've done it correctly by looking into ```
/etc/rc2.d
```
if there's a file called ```
S12915resolution
```, everything is fine. If not, go through the steps again and try to find the problem

-now the last thing you have to do is to tell the script what resolution to add to the video BIOS:
as su, edit ```
/etc/default/915resolution
``` and insert the values you want 915resolution to set.

The next time you start your laptop, you should have the desired resolution.

Oh, and while we're at it:
**If you boot without a splash screen (so if you have the text scrolling while Ubuntu boots up:**
you may want to set the vga mode to a useful value in grub's menu.lst
as su, edit ```
/boot/grub/menu.lst
```
and in the first line starting with ```
kernel     /boot/vmlinuz........
```, append:
```
vga=771
```
This makes the text look nice, but it doesn't work with a splash screen! (at least it didn't work for me, but I hate the splash screen anyway :mrgreen: )


**Beware! I am new to Ubuntu and I'm no Linux expert, so if you have problems, I might not be able to help you!** Feel free to ask, though.

---

### Post by Robotra on 2006-12-29
Thank you so much!  This worked perfectly, and started up as soon as I booted.  I love not having a smudgy display anymore.  :D

---

### Post by J.Vega on 2007-01-06
I added a small piece of text for the ones that don't use a splash screen while booting and want the text to be displayed as nice as possible ;)

---

### Post by encompass on 2007-01-07
I have everything setup the way you have said... but I don't think I can log out and back in again without losing the resolution.
It keeps jumping back to my old resolution 1024x768 when I logout or jump to the console and back again.
I understand the resolution with the console and back, no wide screen is supported in console mode so the resolutions could get scrambled.
But what about the login screen.  Is there a way to have it run a resolution script to reset it when ever my session is closed.  Or perhaps when I press cntrl alt backspace I could configure that to run the script and then start gdm again.  Hmmm...
Any ideas on that?
Have you noticed your resolution changes after logging out?

---

### Post by uterrorista on 2007-01-08
```
Go to the folder where u put the rpm file then do the alien :D :
#sudo alien dri-Intel-3.4.3006-20051209.i386.rpm
```
gives the error:
```
qaz@blue:~/Desktop$ sudo alien dri-Intel-3.4.3006-20051209.i386.rpm
sudo: alien: command not found

```
what's the problem ??? :-k

---

### Post by iGama on 2007-01-08
You need to install alien

sudo apt-get install alien

---

### Post by uterrorista on 2007-01-08
Thanks... it's my first day !! :p 
already installed!

another problem:
```
Go to the folder where u put the rpm file then do the alien :D :
#sudo alien dri-Intel-3.4.3006-20051209.i386.rpm
```
this ouput:
```
qaz@blue:~/Desktop$ sudo alien dri-Intel-3.4.3006-20051209.i386.rpm
Warning: Skipping conversion of scripts in package dri-Intel: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
dri-intel_3.4.3006-20051210_i386.deb generated

```
then:
```
qaz@blue:~/Desktop$ sudo dpkg -i dri-Intel-3.4.3006-20051209.i386.deb
dpkg: erro processando dri-Intel-3.4.3006-20051209.i386.deb (--install):
 não pode aceder ao arquivo: Arquivo ou diretório inexistente
Foram encontrados erros enquanto processava:
 dri-Intel-3.4.3006-20051209.i386.deb
qaz@blue:~/Desktop$ 

```

"Skipping conversion of scripts in package dri-Intel: postinst prerm" ???
what's the problem?

---

### Post by J.Vega on 2007-01-09
encompass: sorry, but I can't reconstruct the problem. When I log out and or kill the X server, my resolution remains unchanged. Are you sure you have 915resolution and not the old 815resolution? Do you run 915resolution via the scripts in rc*.d? and do they have the correct number? (i.e. 12, so at least 1 before gdm in Ubuntu edgy)
I can't find a reason why your X behaves like that...
Or does your VGA card reset the BIOS when you change the tty or log out?
Maybe you can try
sudo 915resolution -l
to see if the modes were resettet during the logout/console switch

uterrorista:
if my Spanish hasn't completely left me, it says that it can't find the file dri-intel.....deb
make sure it's there (in the directory you're in), and maybe try this alien --scripts it suggested.
I suppose something went wrong during the "alienation" and the .deb file wasn't created at all.

---

### Post by nyvalbanat on 2007-01-09
It seems like you're just typing the wrong .deb filename. You can try command completion using the Tab key - type "sudo dpkg -i dri<Tab>" and it should complete the filename for you if it's in that directory.

Good luck!
-Val

---

### Post by uterrorista on 2007-01-09
i already solved the problem. i followed other tutorial. **thanks** anyway

---

### Post by Wilb on 2007-01-09
Are you sure you need to do all of the above? I've got the exact same laptop as you, and after a clean Edgy install all I have to do is install the 915resolution package and all is sorted!

---

### Post by J.Vega on 2007-01-09
You don't need to do all of the above if you just want to set the resolution. But installing the new drivers increases performance significantly, especially since otherwise Ubuntu uses the standard vesa drivers.
If you just want to use your laptop for some office work or anything like that, you're fine with installing 915resolution only. But if you want to do more vga-card-intesive things (play games, use 3d apps, etc.), you're better off installing the Intel drivers.
I can play Starcraft with wine, for example, which was not possible before installing the right drivers ;)

---

### Post by encompass on 2007-01-09
> **J.Vega said:**
> encompass: sorry, but I can't reconstruct the problem. When I log out and or kill the X server, my resolution remains unchanged. Are you sure you have 915resolution and not the old 815resolution? Do you run 915resolution via the scripts in rc*.d? and do they have the correct number? (i.e. 12, so at least 1 before gdm in Ubuntu edgy)
I can't find a reason why your X behaves like that...
Or does your VGA card reset the BIOS when you change the tty or log out?
Maybe you can try
sudo 915resolution -l
to see if the modes were resettet during the logout/console switch


I will try that.... I also notice that I can't change from one res to another.  Of course if I don't restart the Xserver I am fine... but if I resize the screen and then change it back to 1440 900 on the same session of gnome it won't go higher again.  It jsut stays the same but make it "scrollable"  I have to move my mouse to the bottom right for a while before it scrolls to show my trash bin.  Get the idea?  I have seen it when ever the res on a laptop is beyode that of it's screen capabilities.

---

### Post by J.Vega on 2007-01-10
I got the idea, but unfortunatley I don't know how to solve that problem. It seems to me like you X is kinda messed up.
Maybe you could have a look at the /etc/X11/xorg.conf file to see if there's something wrong in you monitor section.

---

### Post by encompass on 2007-01-10
> **J.Vega said:**
> I got the idea, but unfortunatley I don't know how to solve that problem. It seems to me like you X is kinda messed up.
Maybe you could have a look at the /etc/X11/xorg.conf file to see if there's something wrong in you monitor section.

Can you throw me your xorg?  I would love to compare it...

---

### Post by J.Vega on 2007-01-10
sure, here's mine
i've changed the name of the graphics adapter just for fun, there's no need to do so, too, it already worked before ;)

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
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
        Modeline "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
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

---

### Post by philc on 2007-01-28
+1 this tutorial!

I tried to get widescreen working with Breezy and my Siemens Amilo which uses the Intel 855GM chipset. I gave up after a week of frustrated trying.

Decided it was time to give Edgy a chance, hoping that the widescreen issue would be fixed "out of the box." It wasn't but, after taking a deep breath, I dived into the forums again.

Using this HOWTO and 915resolution I now have Ubuntu in glorious 1280x800 resolution.

Thank you! :D

---

### Post by italoraony on 2007-02-14
THANK YOU VERY MUCH!!!!!

I don't have a smudgy screen any more!! :lolflag: :lolflag:

---

### Post by J.Vega on 2007-02-15
glad I could help :mrgreen:

I added a piece of text to allow your Intel 945GM to access 128MB of the system RAM as video RAM. This should improve performance in games and other graphic-intensive apps.
I wasn't able to test if games really run visibly faster now, but everything seems like the vga card now really has 128MB of video RAM.

You can safely add the line to your xorg.conf file after following the whole guide. There's no need to do this at any specific point of time. Just add the line and restart (I'm not sure if restarting the X server is enough).

---

### Post by timothyp on 2007-02-15
Hi,
I'm trying to connect my intel graphcis card to my HDTV which has a PC connector.

It states it can do 
1280x1024@60Hz  Horizontal Refresh: 63.98  Vertical Refresh 60.2
The book also says:   H: 31-69  V:59-86

Currently no matter what I do,
I get an image (unless I set H and V sync so I have to comment those lines out),
which is clear and everything, but a very low resolution, it is a wide screen resolution though because nothing seems stretched and I get a full screen image.

The graphical tools say 640x480, but I doubt it.
Anyway I have the following xorg.conf, and please note the tv has a D-sub 15-pin connetor for pc.

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "be"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation 945G Integrated Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Panasonic"
#Option "DPMS"
HorizSync 63.98
VertRefresh 60.02
Modeline "1280x1024@60" 115.38 1280 1312 1744 1776 1024 1045 1055 1076
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 945G Integrated Graphics Controller"
Monitor "Panasonic"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

Section "ServerLayout"
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

```

What am I doing wrong?

---

### Post by J.Vega on 2007-02-15
First thing I noticed in your xorg.conf:
Your modeline is titled "1280x800@60", but your Screen-Section only says "1280x1024". I think that you need to change the names to match each other.

You could try to use xrandr to change the resolution on your HDTV. If this doesn't work, it may be that you need a second "Screen"-section for your HDTV. There  you need a line to tell X.org that this screen is connected by the vga out. I don't exactly know how to write a second "Screen"-section, but you might be able to find something with google.

---

### Post by timothyp on 2007-02-15
It seems I got it working, I'll try and post my xorg.conf tommorow,
perhaps it might help others.

Everything works great now, except for Elephants Dream HD version.
You know the free open source movie....

That one crashes with whatever application I want to use.
Playing dvd's or other movies works just fine.

---

### Post by headphase on 2007-02-15
I installed both the intel and 915 resoultion and I still only have 1024x768 as an option what gives? :confused:

How do I save the xorgs?  I tried gedit but it said I don't have permission.

---

### Post by J.Vega on 2007-02-16
You **need** the modeline in the xorg.conf to enable the widescreen resolution (having the i810 driver selected is quite useful, too). Otherwise your graphics card says it supports it, but your screen doesn't.
You need to edit the files as root. If you wanna use gedit, you have to execute
```
sudo gedit
```
or
```
sudo gedit /etc/X11/xorg.conf
```
for example. Since the xorg.conf is a system configuration file, you can't edit it as a normal user.

---

### Post by headphase on 2007-02-16
Look at my edited xorg.  Can you find anything overriding my resolution?
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
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam        131072
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
        Modeline "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
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

---

### Post by J.Vega on 2007-02-16
With that xorg.conf, you should be able to use the 1280x800 resolution. If it still doesn't work, you can take a look at the output of
```
sudo 915resolution -l
```
to see if 915resolution really enabled the 1280x800 resolution.
If everything seems correct, try changing the resolution with ```
xrandr -s 1280x800
```.

---

### Post by headphase on 2007-02-16
Here is my output
```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x800, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x800, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x800, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```

---

### Post by headphase on 2007-02-16
Here's a look at my xorg.0.log:
```
(WW) I810(0): config file hsync range 45.7143-50.5263kHz not within DDC hsync ranges.
(II) I810(0): Generic Monitor: Using hsync range of 45.71-50.53 kHz
(II) I810(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(II) I810(0): Not using mode "1280x800" (no mode of this name)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0):  Built-in mode "1024x768"
(--) I810(0): Display dimensions: (300, 190) mm
(--) I810(0): DPI set to (86, 102)
```
Notice the mode is not setting.

Here's a glance of what is ouputed from the mode part of xorg.0.log:
```
*Mode: 54 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00076a3
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 58 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
```
Not what you would expect if you run 915resolution 54 1280 800.:(

---

### Post by headphase on 2007-02-16
Got it!  I finally got the first post directions down.  Thanks a bunch!

---

### Post by J.Vega on 2007-02-17
May I ask what exactly was wrong? :mrgreen:

---

### Post by loko on 2007-02-17
i read this thread and now i wonder myself.

i also have intel 945GM Chipset in Notebook (Asus W5F) which has an Intel 950 grapic-chip.

i  think you also use edgy. i just installed edgy, without i915, without tweaking something and my resolution ist 1280x800 out of the box.

how could this be?

---

### Post by czechrm on 2007-02-17
2 questions - 1) could someone clarify the creating of the Modeline for the monitor? and 2) I have a Toshiba with the 950 chip - is the 915resolution still gonna work?  I have the 1280x800 resolution but i can't see the whole screen (it scrolls up and down and side to side)!!  HELP PLEASE!!  I have been working on this for a week solid now...

---

### Post by headphase on 2007-02-17
> **J.Vega said:**
> May I ask what exactly was wrong? :mrgreen:

915 was after gdm.:redface:

---

### Post by J.Vega on 2007-02-18
loko: I also recently reinstalled Ubuntu (since I now use the 64 bit version) and the resolution was correct out of the box, too. It seems that the i810 driver has been installed with one of the x.org driver packages (check synaptics to see the specific package) and that with this driver, the resolution gets set correctly.
If everything is working correctly, you can ignore this guide safely (setting the videoram might be helpful, though).
I don't exactly know if this issue is solved by installing a more recent download of Ubuntu, but if the problem is there, this guide should help.

czechrm: 1.: For the modeline, you can use a calculator like one of these:
[http://umc.sourceforge.net/](http://umc.sourceforge.net/)
or
[http://zaph.com/Modeline/](http://zaph.com/Modeline/)    (online calculator, but requires more knowledge)

There is no "universal modeline" for all monitors. You can try one of those written in the xorg.conf files posted here, but I recommend calculating your own.


2.: I think that 915resolution should work for your laptop. Feel free to test it, you can't damage anything by using it, since the changes to the video BIOS are only temporary.

---

### Post by headphase on 2007-02-24
> **J.Vega said:**
> glad I could help :mrgreen:

I added a piece of text to allow your Intel 945GM to access 128MB of the system RAM as video RAM. This should improve performance in games and other graphic-intensive apps.
I wasn't able to test if games really run visibly faster now, but everything seems like the vga card now really has 128MB of video RAM.

You can safely add the line to your xorg.conf file after following the whole guide. There's no need to do this at any specific point of time. Just add the line and restart (I'm not sure if restarting the X server is enough).

Can you tell me where and what you added this to?  I am in dual monitor mode so I can't simply cut and paste.

---

### Post by J.Vega on 2007-02-24
You have to add it to the "Device"-Section in your xorg.conf
My "Device"-Section now looks like this:
```
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        131072
EndSection
```
I think you should be able to copy&paste this line, since you don't have 2 "Device"-Sections, do you? (I haven't tried dual monitor mode yet, so I don't know much about it)

---

### Post by abgpt on 2007-02-26
> **J.Vega said:**
> sure, here's mine
i've changed the name of the graphics adapter just for fun, there's no need to do so, too, it already worked before ;)

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#


```

Great, thanks a lot for this Xorg Conf. This works perfectly for me.

---

### Post by Dambrosio on 2007-03-04
I followed the two steps:
```
sudo alien dri-Intel-3.4.3006-20051209.i386.rpm
```
and
```
dpkg -i dri-Intel-3.4.3006-20051209.i386.deb
```
the first problem is after i execute the first command the .deb file created has a lock on the icon and it is named dri-Intel-3.4.3006-20051210_i386.deb instead of dri-Intel-3.4.3006-20051209_i386.deb.
Then when i try and depackage the file i get a few error in the terminal
> error processing dri-Intel-3.4.3006-20051209_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing 
dri-Intel-3.4.3006-20051209_i386.deb
so i double click the .deb file on the computer and install via package installer. It starts to install and then i get the following error message:
> Selecting previously deselected package dri-intel.
(Reading database ... 88864 files and directories currently installed.)
Unpacking dri-intel (from .../dri-intel_3.4.3006-20051210_i386.deb) ... 
Setting up dri-intel (3.4.3006-20051210) ...

ERROR: AGPGART module did not compile
./install.sh: line 1583: ./testgart: no such file or directory

ERROR: AGPGART module did not compile

ERROR: Kernel modules did not compile
cp: cannot start `drm/i915.ko': No such file or directory
Failed to install file /lib.modules/2.6.17-10-generic/kernel/driver/char/drm/i915.ko
cp: cannot stat `agpgart-2.0/intel-agp.ko': No such file or directory
Failed to install file /lib/modules/2.6.17-10-generic/kernel/driver/char/agp/intel-agp.ko
The installation of one or more files failed

You will need to reboot for the changes to take effect,
as we were unable to unload the current kernel modules.

I have no idea what to do from here.
Thank you,
Dan

---

### Post by jeenuv on 2007-03-05
Hi,

I read this post wit much expectation. Mine is a DELL Inspiron 6400 with intel 945GM card. I followed what ever you wrote. But mine didn't work, apart from the fact that my resoluton got reduced (It was initially 1024x768 on wide screen that didn't look good, and it became, 800x600)!

I reverted the changes made to /etc/X11/xorg.conf and /etc/defaults/915resolution and then all were reset to the initial and I got my old resolution back. But I admit that I wrote the mode line and the related configuration wrong (infact I just copy-paste what ever you wrote in the post). How can i determine the correct modeline for my system? Perhaps that would solve the issue.

I really want my wide screen display working! Please help!

Thanks
Jeenu V

---

### Post by J.Vega on 2007-03-05
Dambrosio: Try deleting your old rpm and deb files and then start over those steps. Be sure to do the dpgk -i part as superuser (e.g. via the sudo command)
The lock icon on the file is just because you created the file as root and thus cannot access it as a normal user. If it still fails, I also don't know what to do exactly. Maybe there are some packages missing or something like that.


jeenuv: If you browse this thread, you should find a post of mine, where I posted 2 modeline calculators. You could try using one of them. Since I have a FSC laptop and you have a DELL one, it is possible that my screen differs from yours and that you need an other modeline. Check if there are any differences between our screens that you may need to consider.
I don't recommend blindly following the guide, since I can only describe what I did for my screen to work. Try to understand what in particular I was doing there and if maybe there is something you have to change for your screen which is not the same as what I did.

---

### Post by Dambrosio on 2007-03-07
I tried to re-do the steps and the same thing happened. Is there some other advice that anyone has? Or is there another Thread on how to install the Intel 945 video card. Im running off of the vesa xorg configuration and my screen/resolution looks horrible.
Thanks,
Dan

---

### Post by J.Vega on 2007-03-08
The only other guide I know is the one posted at the beginning of the howto (the one that I followed). But it's basically the same as mine. You could try that, though.

---

### Post by fastpakr on 2007-04-23
I'm beginning to feel like I'm losing my mind...  Just installed 7.04 on a Dell Latitude D620 with a 945.  No problem adding alien and creating the .deb.  I added the modeline to xorg.conf and created the mode in 915resolution with no problem.  However, I still can't get anything above 1024x768 to show up when I try to change resolution.  When I reboot, I still see the correct mode when I run 915resolution -l.  Opening the xorg.0.log shows some interesting things, though...
(I) I810(0): DDCModelFromDetailedTiming: 1280x800 Warning: We only handle seperate sync.
(I) I810(0): Printing DDC gathered Modlines:
(I) I810(0): Modeline * 1280x800" 71.11 1280 1328 1360 1440 800 803 809 823 -hsync -vsync
(I) I810(0): Modeline * 1280x800" 59.26 1280 1328 1360 1440 800 803 809 823 -hsync -vsync

The above modelines are different from what I have in xorg.conf, which is:
Modeline "1440x900" 108.84 1440 1472 1880 1912 900 918 927 946

Also, further on in the log I see:
(I) I810(0): Not using mode "1440x900" (no mode of this name)

Why is it that it can't find the mode, even though it's in xorg.conf and in the 915resolution settings?

Help, I'm pretty lost at this point.  Thanks!

---

### Post by timothyp on 2007-04-23
I'm not sure if it will help you but it helped with my problem (on TV)
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

As only finding the correct modeline actually worked

---

### Post by the8thstar on 2007-04-29
Do you know how to activate 3D rendering on a 945M chipset?

---

### Post by timothyp on 2007-04-29
I have no idea sorry, never needed it as I only use it for my MythTV frontend

---

### Post by eltorodeoro on 2007-05-04
just wanted to say thanks to J.Vega for a great how-to.  I've got a Dell Latitude D620 w/ Intel 945GM that this tutorial worked fantastically on (Feisty).  I've not tried anything fancy with it like Beryl, but the 1280X800 resolution works great, and that's all I needed.

Thanks!

---

### Post by Lumo on 2007-09-29
I have followed the instructions but it won't reboot with 'vesa' changed to 'i810' - it says that it cannot find any other reference to i810.

What am I doing wrong? I have ubuntu 7.04

---

### Post by zavizionov on 2007-10-12
[http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html](http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html)

---

### Post by Lumo on 2007-10-15
> **zavizionov said:**
> [http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html](http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html)

Thank you!

It now works with full colour depth.

Just got to fix the random crashing, touchpad and sound now.

---

### Post by jk0man on 2008-11-23
Hey, this could be excelent howto, but what now? Ubuntu 8.10 is not using xorg.conf but .fdi XML files. Do anyone have any suggestions how to do it here?

---

### Post by bearsomg on 2010-01-18
I had the same exact problem a while ago, but I fixed it. Read my post [http://ubuntuforums.org/showthread.php?t=1251234](http://ubuntuforums.org/showthread.php?t=1251234)




It wasn't made for Intel cards, but it works for any configuration. Read my last post on the first page.

---

