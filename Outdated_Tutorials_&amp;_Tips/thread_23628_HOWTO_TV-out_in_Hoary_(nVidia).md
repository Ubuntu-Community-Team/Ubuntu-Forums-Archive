---
title: "HOWTO: TV-out in Hoary (nVidia?)"
date: 2005-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Promethe on 2005-04-03
My first HOWTO, so don't shout at me, if there is anything wrong :)
Let me know, if it's working on ATIs card too

Some parts borrowed from Official Gentoo HOWTOs.

Becouse I want to use TV-out only sometimes, eg. to watch movie, listen to music, play in DOOM, or show my little sister kids movie, in this time doing something on my lappy, I had to set up separate screens. So, get up and go work :]

At first, you had to made this in term:
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
It will make backup of your x.org config file.
Now, apt-get nvtv by this:
```
$ sudo apt-get install nvtv
``` 
Next thing which you need to do is edit your xconf file.
```
$ sudo gedit /etc/X11/xorg.conf
```
First thing, which we will change in conf file, will be adding TV as next monitor and changing name of default monitor. Seek for **Monitor** section, and change monitor identifier to:
```
Identifier "Monitor[0]" #CRT 
```
Now, under this section, add following:
```
 Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 60 
    VertRefresh 30-150 
 EndSection
``` 
If you need, change *HorizSync* and *VertRefresh*, but this values should work fine on most new TVs.
Second thing, which we will change in config file, will be adding TV-output as next device and changing name of default device. Seek for **Device** section, and change monitor identifier to:
```
   Identifier      "Device[0]" 
```
In the same section add:
```
screen 0
```.
Now, under this section, add following:
```
Section "Device" 
   Driver          "nvidia" 
   Identifier      "Device[1]" 
   Screen 1 
   Option          "TVOutFormat" "Composite" #or S-VIDEO etc 
   Option          "TVStandard" "PAL-G" #or NTSC etc 
   Option          "ConnectedMonitor" "Monitor[1]" 
   BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

```
If you are in country which don't use PAL, change it to your TV standard. 
Now, seek for Screen section, and change Identifier, Monitor and Screen to following:
```
   Identifier  "Screen[0]" 
   Device      "Device[0]" 
   Monitor     "Monitor[0]" 

```
Under this add:
```
Section "Screen" 
   Device "Device[1]" 
   Identifier "Screen[1]" 
   Monitor "Monitor[1]" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 24 
               Modes "1024x768" 
       EndSubSection    
EndSection
```
And change/add to your config file serverlayout:
```
Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Mouse1" "CorePointer" 
   InputDevice "Keyboard1" "CoreKeyboard" 
EndSection
```
Remember to check name of your mouse and keyboard, and change it names. You can find names of input devices in **Input device** section as following:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
```
Identifier is name of device. If name of your input device is diffrent, change Mouse1 or Keyboard1 from above server layout code to your needs.
Now save xorg.conf.
At now, we will add small bash feature, which will let us to run players on second screen easly.
Do following in terminal:
```
$ sudo gedit /etc/bash.bashrc
```
Add following section on end:
```
tv()
{
  if [ "$1" == "" ]; then
    echo "usage: tv program name"
  else
    DISPLAY=:0.1 $1
  fi
}
```
And you will be able to run e.g. Totem on second display by typing in terminal (or ALT+F2 and checked "Run in terminal"):
```
$ tv totem movie.avi
```

Nice feature for Kubuntu users, which will allow them to run movies from context menu. If somebody know trick like this for GNOME, let me know.
Add this entry to:
```
~/.kde/share/apps/konqueror/servicemenus/nameofyourchoice.desktop
``` 
```
[Desktop Entry]
Actions=PlayOnTV
Encoding=UTF-8
ServiceTypes=video/*

[Desktop Action PlayOnTV]
Exec=mplayer -display localhost:1 %F
Name=Play this movie on TV
Icon=yast_tv
```
**Before you ask!** Check twice:
[list]
[*]did you changed names of all devices, screens and monitors in xorg.conf?
[*]did you rebooted Xs (by CTRL+ALT+Backspace)
[*]did you ended script in bash.rc by } ?
[*]did you close all sections in xorg.conf?
[*]did you installed nvtv?
[/list]

Have a nice day!

---

### Post by bihe on 2005-04-03
really cool howto. i will use it for my dvr box in the living room

---

### Post by Bo Rosén on 2005-04-03
Great initiative, well done.
One thing though, I don't think nvtv works will all nvidia cards.

---

### Post by Klin'Targ on 2005-04-07
[QUOTE=Bo Rosén]Great initiative, well done.
One thing though, I don't think nvtv works will all nvidia cards.[/QUOTE]
This is true, and my card is one of them (Geforce 420 GO). I got tv-out working via an alternate method though. Simply add this to the Device section of your xorg.conf file:
```
Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TVOutFormat" "COMPOSITE"
Option "TVStandard" "NTSC-M"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "60"
Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384"
```
You can set MetaModes, TVStandard and TVOutFormat to whatever is appropriate to your setup.
The way this works is if you have a tv plugged in when the x server starts, it will clone your main screen, if you don't it will ignore this section. So, if you want to watch something on a tv, just connect the cable and restart the x server. Arguably this is not as elegant as the nvtv solution, but it is less complex and seems to work on my hardware at least.

---

### Post by Promethe on 2005-04-08
Klin - above solution let's you create two diffrent, independent from each other X sessions - so you can play DOOM 3 on one, and on second you can watch newest SG-1  O:) 
Your solution lets only clone desktop...

---

### Post by RedDwarf on 2005-04-08
If you want to play Doom3 and watch SG-1 on new cards (without nvtv nor TwinView):

```
Section "Monitor"
    Identifier "monitor1"
    VendorName "LG"
    HorizSync 30-71
    VertRefresh 50-160
EndSection

Section "Monitor"
    Identifier "monitor2"
    VendorName "Philips"
    HorizSync 30-40
    VertRefresh 50
    DisplaySize 412 310
    ModeLine "720x576/50p" 27 720 744 800 864 576 581 583 625 #27.0 MHz, 31.2 kHz, 50.0 Hz
    Modeline "800x600/50p" 31.60 800 824 968 1000 600 602 603 632 #31.6 MHz, 31.6 kHz, 50.0 Hz
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia"
    BoardName "NVIDIA GeForce FX5200"
    Driver "nvidia"
    Option "DPMS"
    Option "NoLogo" "true"
    Option "RenderAccel" "true"
    BusID  "PCI:1:0:0"
    Option "ConnectedMonitor" "CRT"
    Option "HWCursor" "On"
    Option "NvAGP" "2"
    Screen 0
EndSection

Section "Device"
    Identifier "device2"
    VendorName "nVidia"
    BoardName "NVIDIA GeForce FX5200"
    Driver "nvidia"    
    Option "NoLogo" "true"
    Option "RenderAccel" "true"
    BusID  "PCI:1:0:0"
    Option "ConnectedMonitor" "TV"
    Option "TVStandard" "PAL-B"
    Option "TVOutFormat" "SVIDEO"
    Option "IgnoreEDID" "true"
    Option "HWCursor" "On"
    Option "NvAGP" "2"
    Screen 1
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Virtual 1024 768
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Virtual 1024 768
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Virtual 1024 768
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Virtual 1024 768
    EndSubsection
EndSection

Section "Screen"
    Identifier "screen2"
    Device "device2"
    Monitor "monitor2"
    DefaultColorDepth 24
EndSection

Section "ServerLayout"
    Identifier "layout0"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    Screen 0 "screen1"
    Screen 1 "screen2" rightOf "screen1"
EndSection
``` 

Note this is MY x.org, there are extra options not needed and I use a PAL 50Hz TV (1024 is supported, but I still have to find a 1024x768 50Hz modeline that is accepted).

But this is explained better on the readme of nVidia drivers. Basically you must create two "Screen", "Device" and "Monitor" and use that 'Screen 1 "screen2" rightOf "screen1"' on "ServerLayout".
In "Device" is VERY IMPORTANT to put "BusID" and "Screen".

---

### Post by chronos on 2005-04-15
Thanks for the nice howto, I think I got it working. Is it somehow possible to switch completely to the tv screen, so that I could use mouse and everything there? The tv-script works with totem at least, but it's not too convenient when you have to use keyboard shortcuts and stuff...

edit: some typos

---

### Post by dermotti on 2005-04-15
Wow i cant wait to try this at home

---

### Post by yarc on 2005-04-15
Is there any way to disable mouse-switching-thingy.  So it doesent swith screen when moving the mousecursor to the edge of the screen.

---

### Post by chronos on 2005-04-15
[QUOTE=yarc]Is there any way to disable mouse-switching-thingy.  So it doesent swith screen when moving the mousecursor to the edge of the screen.[/QUOTE]
Hehe, thanks for answering my question... :grin: I didn't notice that ](*,)

---

### Post by Rollerbob on 2005-04-15
I recently installed Hoary on a Thinkpad T21 and I'd like to connect it to my TV using S-Video. It has an S3 savage card which is capable of TV out but I'd like to configure it to output at PAL resolution. Is something like this available for older video cards that aren't Nvidia?

---

### Post by RastaMahata on 2005-04-15
wow, I wish I had a tv near my pc :(

but first, I'll save for the car, then the laptop, then the tv...


I think I'll have to wait 3 years :P

---

### Post by artnay on 2005-04-16
People using GNOME and MPlayer, this is for you. With this you can simply start a movie in screen 1, which I use for my projector. 

1. Open your favorite editor and add the next lines:

# !/bin/sh
DISPLAY=:0.1 /usr/local/bin/gmplayer -fs "$*"

2. Save the document and give a name for it (eg. gmplayer.conf), then close the editor.

3. Now open Nautilus File Browser and go into movies directory. 

4. Click the movie file with the right button of your mouse.

5. Choose "Open with", then choose "Open with other application".

6. Select "Use a custom command" and then type "sh /where/ever/you/saved/gmplayer.conf". Replace /where/... with the path where you saved gmplayer.conf. Then press "Open".

GMPlayer should now start in screen 1. The script assumes you have gmplayer executable in your /usr/local/bin directory and rights to use that file. Next time you should see the script listed on "Other Application" menu. This is pretty simple but at least it works and makes life a bit easier.  :roll:

---

### Post by michealm on 2005-04-16
If i post my conf. can some one edit it for me as Ive tried several times with no success

---

### Post by vrunt on 2005-04-16
Excellent.
Now, is there a way to get TV in?

---

### Post by michealm on 2005-04-17
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"A70S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A70S"
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

Can someone edit this so i can use my TV out on my FX 5200
TV is NTSC

Thx

---

### Post by Sandy Malteser on 2005-04-17
Hi,

I#m having some problems getting my kubuntu to display on my tv. when i boot up the computer i can see everything on my tv aswell as on my monitor until i get to kdm. my monitor displays kdm as it should my tv just starts showing all kinds of colored lines. any sugestions. ooh yeah my graphics card is NVidea GeForce4 MX 440 AGP 8x the tv(pal) is connceted to the computer with a svideo cable.

---

### Post by michealm on 2005-04-19
so is anyone going to try and help or is this just going to become a dead thread? ](*,)

---

### Post by Promethe on 2005-04-19
Heffa nice day :]

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Keyboard1"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Mouse1"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
        Identifier      "Device[0]" 
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen 0
EndSection

Section "Device" 
   Driver          "nvidia" 
   Identifier      "Device[1]" 
   Screen 1 
   Option          "TVOutFormat" "Composite" #or S-VIDEO etc 
   Option          "TVStandard" "NTSC" #or NTSC etc 
   Option          "ConnectedMonitor" "Monitor[1]" 
   BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
EndSection

 Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 60 
    VertRefresh 30-150 
 EndSection

Section "Screen"
   Identifier  "Screen[0]" 
   Device      "Device[0]" 
   Monitor     "Monitor[0]" 
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

Section "Screen" 
   Device "Device[1]" 
   Identifier "Screen[1]" 
   Monitor "Monitor[1]" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 24 
               Modes "1024x768" 
       EndSubSection    
EndSection

Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Mouse1" "CorePointer" 
   InputDevice "Keyboard1" "CoreKeyboard" 
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by stoffe on 2005-04-19
Hiya. I followed this fine HOWTO, and after some re- and false starts, I've got it working... kinda. I have picture on the TV, and it looks quite good - apart from the fact that it is always starting about 1/5 down from the top of the screen, and about as much is disappearing under the bottom. No amount of tweaking seems to be able to remedy this.

I think it somehow might be due to the fact that it is a 16:9 TV and my card does not seem to want to run any such mode, no matter what syncs I set. I haven't been able to gather the real syncs, but both yours and the ones in the nvidia README does work - although in the xorg log it only lists diverse 4:3 formats as possible, and trying to set any other is promptly ignored.

I've also tried to set the screen to relative positions, but that has no effect on where the screen is placed. And for some reason my TV does not allow me to go to any kind of 4:3 mode or so, or at least I can't find that button. ;) It is a Samsung CX-6840N according to the back btw, no manual and google does not really turn up anything.

Is there anything, I mean anything that could help in this case? I mean, everything just works so nice and then this last thing...  :roll: 

The syncs that do produce an image are:

    HorizSync 50 
    VertRefresh 30-150 

from this HOWTO, and

     HorizSync 30-50
     VertRefresh 60

from nvidia README

They give slightly different allowed modes, but none that works.

At the very least, is it possible to offset the screen somehow? I have no idea if that would actually work, but it would be worth a shot. That's what I wanted to try with "Relative" instead of "RightOf" but it had no effect.

Really hope someone recognizes this problem and have solved it. :)

---

### Post by blitze on 2005-04-20
Be Wary though with DVI outputs and TV out.  FPD are treated as the second screen by the Nvidia drivers.  Still it works well and oneday someone either Nvidia or Gnome will sortout the screen order issue.  Why we can't allocate which we'd like to use as primary god only knows but at the moment we can't.   :-|

---

### Post by ykpaiha on 2005-04-20
Thanks to the poster.
For the 1st time i could do:
Watch a movie on the TV in full screen
And an other one on my crt computer....(just I use 1 sound card and both goes in the same chanel...sadness)
(for newby like me)
Do not forget to have for each output:
screen, device and monitor
1for the tv, one for the crt.

Bravo

---

### Post by martin.rolin on 2005-04-21
I have managed to get dualview with a cloned desktop on my tv. Now i would like to have video overlay so that I dont have to stretch the moviewindow when i want to se movies on the tv. 

i cant run in fullscreen because my crt-desktop has 1152x864 and the tv 1024x768.

Does anyone know how to solve my problem?

---

### Post by mrk on 2005-04-21
would be very nice if I just could make it work :-(
I changed my xorg.conf as suggested, but:
-when x starts, my tv shows no signal (blue screen, just as when the pc is off)
-when I try to launch some app with the script I get a "couldn't find 0.1 screen"...
ps -A gives me nvtvd up and working, and the hardware too is ok since using nvtv I can see some output in my, but not in that cool way (two separate screens:-))
any suggestion?
thanks

my xorg.conf:

```
Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Keyboard1"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "it"
EndSection

Section "InputDevice"
        Identifier      "Mouse1"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        #Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Identifier      "Device[0]"
        Driver          "nvidia"
        Screen          0
        BusID           "PCI:1:0:0"
EndSection

Section "Device"
        Driver          "nvidia"
        Identifier      "Device[1]"
        Screen          1
        Option          "TVOutFormat" "Composite"
        Option          "TVStandard" "PAL-B"
        Option          "ConnectedMonitor" "Monitor[1]"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Monitor[0]"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Monitor"
        Identifier      "Monitor[1]"
        HorizSync       60
        VertRefresh     30-150
EndSection

Section "Screen"
        Identifier      "Screen[0]"
        Device          "Device[0]"
        Monitor         "Monitor[0]"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Device          "Device[1]"
        Identifier      "Screen[1]"
        Monitor         "Monitor[1]"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Simple Layout"
        Screen 0        "Screen[0]"
        Screen 1        "Screen[1]" RightOf "Screen[0]"
        InputDevice     "Keyboard1" "CoreKeyboard"
        InputDevice     "Mouse1" "CorePointer"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by iluciv on 2005-04-24
I have the same problem as stoffe (I was wondering if you found a fix or work around )
It works but is only black and white a the screen size is way too large on the tv. 
I was wondering if there is any way of telling if nvtv is working (is it a module?) 
I haven't tried Red Dwarfs method yet. I would like to get this working cause its just what I want to do with the dual display. 

the card is a ti 4200 4x 
I'm using a svideo to av socket adapter on an LG 51cm tv 
The xorg.conf on ubuntu 5.04 is edited properly 

I hope people still look at these posts

---

### Post by stoffe on 2005-04-24
[QUOTE=iluciv]I have the same problem as stoffe (I was wondering if you found a fix or work around )[/QUOTE]

No, sorry I haven't. Still subscribed to this thread in case someone comes up with something... I really, really hope so. :)

[QUOTE=iluciv]It works but is only black and white a the screen size is way too large on the tv.[/QUOTE]

At least for the " only black and white" part it might be because you aren't using all the cables you need. When I first tried TV out way back, I had to buy an extra composite cable to use side-by-side with the S-Video one. I don't recall why, but it has to do with the card/chipset, not OS or software (if it is the same for you).

I have all the colors I expect, but like I said, my screen is offset real bad.

[QUOTE=iluciv]I was wondering if there is any way of telling if nvtv is working (is it a module?)[/QUOTE]

[FONT=Courier New]ps -ef | grep nvtvd[/FONT]

Should show a running process. It is a service, can be started/stopped via [FONT=Courier New]/etc/init.d/nvtv[/FONT] but should be running by default. (I do miss the extra command [FONT=Courier New]status[/FONT] that was available on Gentoo).
 
[QUOTE=iluciv]I hope people still look at these posts[/QUOTE]

Me too. Really would like this to work. And to get those windows using bastards off my back about yet another thing I can do as good or better. ;-)

---

### Post by stoffe on 2005-04-25
Just wanted to add that I've now tried to connect the same setup to a 4:3 TV and it works perfectly, so it is definitely something to do with the 16:9 format. Any ideas at all on how I could remedy this?

Oh, and I had to modify the "tv" function slightly for it to work as advertised, change:```
DISPLAY=:0.1 $1
```to```
DISPLAY=:0.1 "$@"
``` - dunno if that is totally correct, but it worked for me.

---

### Post by elasticwings on 2005-04-28
Hello, I'm having alot of trouble trying to get my tv out working.  I only want the tv as the display, but I can't seem to find why it isn't working?  Here is what is in my xorg.conf
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
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

Section "Device"
        Identifier      "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        #Option         "DPMS"
        HorizSync       30-50
        VertRefresh     60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        Option "TVStandard" "NTSC-M"
        Option "ConnectedMonitor" "TV"
        Option "TVOutFormat" "SVIDEO"
        #SubSection "Display"
        #       Depth           1
        #       Modes           "1024x768" "800x600" "640x480"
        #EndSubSection
        #SubSection "Display"
        #       Depth           4
        #       Modes           "1024x768" "800x600" "640x480"
        #EndSubSection
        #SubSection "Display"
        #       Depth           8
        #       Modes           "1024x768" "800x600" "640x480"
        #EndSubSection
        #SubSection "Display"
        #       Depth           15
        #       Modes           "1024x768" "800x600" "640x480"
        #EndSubSection
        #SubSection "Display"
        #       Depth           16
        #       Modes           "1024x768" "800x600" "640x480"
        #EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "640x480"
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

---

### Post by elasticwings on 2005-04-28
I found some stuff I did wrong, but I still haven't fixed the problem.  Here is an update of my xorg.conf file.


```
Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
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

Section "Device"
Identifier "NVIDIA S-Video TV out"
Driver "nvidia"
VendorName "NVIDIA"
BoardName "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
#BusID           "PCI:1:0:0"
Option "ConnectedMonitor" "TV"
Option "TVStandard" "NTSC-M"
Option "TVOutFormat" "SVIDEO"
Option "DigitalVibrance" "255"
Option "TVOverScan" "1.0"
Option "RenderAccel" "true"
Option "NoLogo" "true"
EndSection

Section "Monitor"
        Identifier      "tv"
        VendorName      "RCA"
        HorizSync       30-50
        VertRefresh     60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA S-Video TV out"
        Monitor         "tv"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "640x480"
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

---

### Post by elasticwings on 2005-04-28
I finally got it working.  Not the way, I was intending to with the xorg.conf file, but I got it kicking with nvtv.

---

### Post by abbot on 2005-05-06
Im trying to get this to work with a Voodoo 3 card.  i see the nvtv and atitvout packages, but nothing for Voodoo cards.  can anyone give me a clue?

---

### Post by trivialpackets on 2005-05-08
[QUOTE=abbot]Im trying to get this to work with a Voodoo 3 card.  i see the nvtv and atitvout packages, but nothing for Voodoo cards.  can anyone give me a clue?[/QUOTE]
 Does this configure it to allow for the dragging of windows from my notebook to my monitor?  This is what I'd really like as it's useful in debugging my code to be able to see multiple parts of the code at once without trying to squeeze it all onto one screen.  I actually like that feature on windows, what isi t hydravision?  In any case, if anyone knows, let mme know, and I'll dow hat this said, and find out for myself.  Thanks all.

---

### Post by bahumbug on 2005-05-09
OK, i spent some time on this and got it to work:
i have a tv connected to my nVidia TI 4600 via s-video, with NTSC-M display, here's my xorg.conf maybe some of you can just change some values and have it working on your comp

You probably don't have to worry about the top part, just from Section "Device" down is the important part:

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"device1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" "true"
	Screen 		0
EndSection

Section "Device"
    	Identifier 	"device2"
    	Driver 		"nvidia"    
    	Option 		"RenderAccel" "true"
   	BusID  		"PCI:1:0:0"
   	Option 		"TVStandard" "NTSC-M"
   	Option 		"TVOutFormat" "SVIDEO"
	#Option 		"ConnectedMonitor" "TV"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-85
EndSection

Section "Monitor"
	Identifier	"monitor2"
	HorizSync	30-75
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
   	Identifier 	"screen2"
    	Device 		"device2"
    	Monitor 	"monitor2"
    	DefaultDepth 	24
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Layout"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen 		0 "screen1"
	Screen 		1 "screen2" RightOf "screen1"
EndSection

```

device1 is for my computer monitor and device2 is for my TV, same thing with monitor1 and monitor2 and screen1 and screen2.  in "ServerLayout" i made it so that "screen2" (the TV) is to the right of "screen1" (my monitor).  like someone mentioned before, you basically have to have two separate statements(device, screen, monitor) for each display you have.  hope this helps as i had a frustrating time with it.

PEACE

---

### Post by Kev0r on 2005-05-15
Hi there, this is all very nice, but what if you wanna clone ur screen on the TV. While booting my Tv-out works. When GDM hits the deck, it switches off...

So my question: how can i just get my tv to clone my normal screen! Not all those fancy Left/Right stuff as it doesn't work nicely (that worked btw).

---

### Post by Ziff on 2005-05-25
Can somebody please configure my X so i can use TV-out i tried but everything just  crashed :P
My tv is PAL and i have a 6600GT
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"103025"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"103025"
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

---

### Post by Sonic-NKT on 2005-05-30
got it working... did it exactly like in the tutorial on page 1 and it works.. but when i shut down the xserver (kill it or just want to shut down my pc) it hangs up..
reset is the only thing that helps.. does anyone have an idea?
i have a Geforce 4 4200.

---

### Post by Sonic-NKT on 2005-05-31
BUMP...
cant someone help me? its really annoying to check the HDD every single start :(
should i post anything ? log files or something.. Please
Thanks"

---

### Post by GastonV on 2005-06-15
Hello Klin'Targ,
I am working with Fedora Core 3 and a nVIDIA Fx5200 Video Card.
I have tried with this in my Screen Section :
[gastonv@pandora1 ~]$ cat /etc/X11/xorg.conf
...
Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        Option "TwinView" "true"
        Option "TwinViewOrientation" "Clone"
        Option "TVOutFormat" "SVIDEO"
        Option "TVStandard" "PAL-B"
        Option "SecondMonitorHorizSync" "30-50"
        Option "SecondMonitorVertRefresh" "60"
        Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384"
EndSection

Booting up My Computer shows very good and corrct the colored GRUB-Screen and The Linux Login Text Procedure.
After that I see different colored screens, red, bue and green and at the end a black screen with red lines.
Opening an application gives a blinking colored block ...
Logging out gives at the end again a correct logout text.
Please Klin'Targ, can you or someone else help me?
Many thanks in advance,
Gaston Verhulst - Belgium.

---

### Post by Arktis on 2005-07-01
Here is a working config for a **three** display setup. :D

Uses:

-2 Nvidia Cards; an FX 5200 (AGP), and a GeForce4 MX 4000 (PCI).
-The normal outputs from both cards and the s-video out from the agp card.
-**NO twinview**
-[b]NO nvtv
[/b] -3D Acceleration on all 3 displays.
-unfortunately, no xinerama (can't use it with 3d acceleration enabled ](*,), which I cannot live without), meaning each screen is it's own separate compartment but you can still move the mouse between each and view them all simultaneously.

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	FontPath "unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
		# paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
	  SubSection "extmod"
			Option "omit xfree86-dga"
	  EndSubSection
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
		Identifier	  "Configured Mouse"
		Driver		  "mouse"
		Option		  "CorePointer"
	 Option		 "Device"			 "/dev/input/mice"
	 Option		 "Protocol"			 "ExplorerPS/2"
	 Option		 "Buttons"			 "7"
	 Option		 "ZAxisMapping"		 "6 7"
	 Option		 "Resolution"		 "100"
EndSection

Section "Device"
	Identifier	"NVIDIA FX 5200 128 MB AGP"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		 "ConnectedMonitor"	"CRT-0"
	Option 		"UseInternalAGPGART"	"no"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Screen		0
EndSection

Section "Device"
	Identifier	"SVIDEO AGP"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"ConnectedMonitor"	"TV-0"
Option		 "TVOutFormat"		"SVIDEO"
    Option		  "TVStandard"		"NTSC-M"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Screen		1
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce4 MX 4000 64 MB PCI"
	Driver		"nvidia"
	BusID		"PCI:1:10:0"
	Option		 "ConnectedMonitor"	"LCD-0"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
#	Screen		0
EndSection

#Section "Device"
#	Identifier	"SVIDEO PCI"
#	Driver		"nvidia"
#	BusID		"PCI:1:10:0"
#	Option		"ConnectedMonitor"	"TV-0"
# Option		 "TVOutFormat"		"SVIDEO"
# Option		 "TVStandard"		"NTSC-M"
#	Option		"VideoOverlay"		"on"
#	Option		"OpenGLOverlay"		"off"
#	Screen		1
#EndSection

Section "Monitor"
	Identifier	"CRT-0"
	Option		"DPMS"
	HorizSync	31-62
	VertRefresh	55-90
EndSection

Section "Monitor"
	Identifier	"TV-0"
#	Option		"DPMS"
	HorizSync	60
	VertRefresh	30-150
EndSection

Section "Monitor"
	Identifier	"LCD-0"
	Option		"DPMS"
	HorizSync	31.25-80
	VertRefresh	56-85
EndSection

Section "Screen"
	Identifier	"Right"
	Device		"NVIDIA FX 5200 128 MB AGP"
	Monitor		"CRT-0"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Television"
	Device		"SVIDEO AGP"
	Monitor		"TV-0"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Left"
	Device		"NVIDIA GeForce4 MX 4000 64 MB PCI"
	Monitor		"LCD-0"
	DefaultDepth	16
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
	Screen		0 "Right"
	Screen		1 "Left" LeftOf "Right"
	Screen		2 "Television" LeftOf "Left"
	Option		"Xinerama" "off"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

If I had another tv or svideo capable monitor, this could be slightly edited to allow for 4 displays.  It's not perfect, since I'm not really experienced with this sort of thing, so if anyone has suggestions on how to improve it, please do tell.

---

### Post by izmaelis on 2005-07-29
Thank you for a great how to. It worked fine just after I went step by step through it.

---

### Post by Svartvit on 2005-07-30
Reviving this thread to ask for some help. I get "(totem:12149): Gtk-WARNING **: cannot open display:" when trying to run "tv totem <film>". Skimmed through the thread without finding any help, and I've reconfigured xorg.conf three times and ending up getting the same result.

Here's my xorg.conf:
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
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
	Identifier	"Device[0]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
  	Driver          "nvidia" 
  	Identifier      "Device[1]" 
  	Screen 1 
  	Option          "TVOutFormat" "Composite" #or S-VIDEO etc 
 	Option          "TVStandard" "PAL-G" #or NTSC etc 
  	Option          "ConnectedMonitor" "Monitor[1]" 
  	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
EndSection

Section "Monitor" 
   	 Identifier "Monitor[1]" #TV 
  	 HorizSync 50 
  	 VertRefresh 30-150 
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
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

Section "Screen" 
   Device "Device[1]" 
   Identifier "Screen[1]" 
   Monitor "Monitor[1]" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 24 
               Modes "1024x768" 
       EndSubSection    
EndSection

Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Mouse1" "CorePointer" 
   InputDevice "Keyboard1" "CoreKeyboard" 
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Does anyone know where the glitch could be?

---

### Post by BobLot on 2005-08-03
[QUOTE=Sonic-NKT]got it working... did it exactly like in the tutorial on page 1 and it works.. but when i shut down the xserver (kill it or just want to shut down my pc) it hangs up..
reset is the only thing that helps.. does anyone have an idea?
i have a Geforce 4 4200.[/QUOTE]

sorry for reviving this thread, but I have the same problem with the same video card. Does anybody know of a solution?

I'll post my xorg.conf
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"dri"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"NVIDIA GeForce Ti 4200"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	Option		"RenderAccel"
	Option		"Twinview" "true"
	Option 		"TwinViewOrientation" "Clone"
	Option 		"TVStandard"  "PAL-B"
	Option 		"SecondMonitorHorizSync" "30-50"
	Option 		"SecondMonitorVertRefresh" "60"
	Option 		"MetaModes" "1024x768,1024x768;  512x384,512x384"
EndSection

Section "Monitor"
	Identifier	"Philips 107B"
	Option		"DPMS"
	Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"NVIDIA GeForce Ti 4200"
	Monitor		"Philips 107B"
	DefaultDepth	24
		SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Twinview"
	Screen	 	"CRT"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "dri"
	Mode 0666
EndSection

```

---

### Post by tommy_haaland on 2005-08-12
[QUOTE=Klin'Targ]This is true, and my card is one of them (Geforce 420 GO). I got tv-out working via an alternate method though. Simply add this to the Device section of your xorg.conf file:
```
Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TVOutFormat" "COMPOSITE"
Option "TVStandard" "NTSC-M"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "60"
Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384"
```
You can set MetaModes, TVStandard and TVOutFormat to whatever is appropriate to your setup.
The way this works is if you have a tv plugged in when the x server starts, it will clone your main screen, if you don't it will ignore this section. So, if you want to watch something on a tv, just connect the cable and restart the x server. Arguably this is not as elegant as the nvtv solution, but it is less complex and seems to work on my hardware at least.[/QUOTE]

I tried this, but after I got a LCD computer screen, and using DVI, it all fucks up. Anyone know what I have to do to get this working?

---

### Post by drbizzaro on 2005-08-30
Aaaah, I got alot of help from this thread in getting tv-out to work, so thank you to everyone. Like some in the thread I had some problems with my 16:9 tv, though (the output being offset alot). 

Anyway I've found the solution to this in the Screen section set (if you have PAL, some other value if you have NTSC):

Modes "720x576Noscale"

Then in the Monitor section for the TV set:

DisplaySize     400 225

Hope it helps somebody.

---

### Post by coolclassic on 2005-09-02
[QUOTE=iluciv]
It works but is only black and white 

[/QUOTE]
Same problem but changing from s-video to composite solved it

---

### Post by jnk on 2005-09-04
I followed this howto when installing nvtv and configing my xorg.conf file.
But when I try to start VLC from console with output on my TV whit this command:
**vlc --vout x11 --x11-display :0.1 --fullscreen --no-wxwin-embed**
But the movie is played on my monitor and not on my TV and I get this error msg in console:
**[00000286] x11 video output error: cannot open display :0.1**
Don't know what to do... ;( I've have been trying things out for some hours now.
please help....

My xorg.conf file:
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
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
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Option		"NoLogo"
	Screen 0
EndSection

Section "Device"
	Identifier	"Device[1]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Option          "TVOutFormat" "S-VIDEO" #or Composite etc 
	Option          "TVStandard" "PAL-G" #or NTSC etc 
	Option          "ConnectedMonitor" "Monitor[1]" 
	Screen 1
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
EndSection

Section "Monitor" 
	Identifier	"Monitor[1]" #TV 
	HorizSync 50 
	VertRefresh 30-150 
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen[1]"
	Device		"Device[1]"
	Monitor		"Monitor[1]"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Simple Layout"
	Screen 0	"Screen[0]"
	Screen 1	"Screen[1]" RightOf "Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by dilerra on 2005-09-09
[QUOTE=blitze]Be Wary though with DVI outputs and TV out.  FPD are treated as the second screen by the Nvidia drivers.  Still it works well and oneday someone either Nvidia or Gnome will sortout the screen order issue.  Why we can't allocate which we'd like to use as primary god only knows but at the moment we can't.   :-|[/QUOTE]

I'd just thought I'd mention that I managed to get my setup with a DVI output to my flatscreen, and a composite output to my tv, to work. Previously, I had to use a CRT-connector to my flatscreen to be able to do this... but no any longer  :)

The "secret" is to use an option that tells the Device what kind of CONNECTIONS that are not accepted. My primary device, Device[0], should NOT be allowed to run on a CRT or COMPOSITE/S-VIDEO (TV that is) connection. This forces it to use my ordinary screen, situated at the computer itself, and does not blank it out like it does otherwise (with a DVI-connection).

I think the above makes it work in general (with DVI + TV connected), running each at whatever the desired resolution one could want.

Take a look at my attached xorg.conf if you would like something similar. Good luck!

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
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
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Logitech diNovo Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Logitech diNovo Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"9 10"
	Option		"Resolution"		"800"
EndSection

Section "Device"
	Identifier	"Device[0]"
	Screen		0
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"ConnectedMonitor"		"Monitor[0]"
	Option		"NoLogo"			"true"
	Option		"RenderAccel"			"true"
	Option		"IgnoreDisplayDevices"		"CRT, TV"
EndSection

Section "Device"
	Identifier	"Device[1]"
	Screen		1
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"ConnectedMonitor"		"Monitor[1]"
	Option		"NoLogo"			"true"
	Option		"RenderAccel"			"true"
	Option		"TVOutFormat"			"COMPOSITE"
	Option		"TVStandard"			"PAL-G"
EndSection

# This is Acer AL1721
Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

# This is my TV
Section "Monitor"
	Identifier	"Monitor[1]"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
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

Section "Screen"
	Identifier	"Screen[1]"
	Device		"Device[1]"
	Monitor		"Monitor[1]"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen[0]"
	Screen 1	"Screen[1]" LeftOf "Screen[0]"
	InputDevice	"Logitech diNovo Keyboard"
	InputDevice	"Logitech diNovo Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Kyral on 2005-09-09
Can someone screw with my XOrg.conf to get this working? I went through it but it wound up trying to output to the S-Video as default.

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	    FontPath	    "unix/:7100"				    # local font server
		# if the local font server has problems, we can fall back on these
		FontPath		"/usr/share/X11/fonts/misc"
		FontPath		"/usr/share/X11/fonts/cyrillic"
	    FontPath	    "/usr/share/X11/fonts/100dpi/:unscaled"
	    FontPath	    "/usr/share/X11/fonts/75dpi/:unscaled"
		FontPath		"/usr/share/X11/fonts/Type1"
		FontPath		"/usr/share/X11/fonts/CID"
		FontPath		"/usr/share/X11/fonts/100dpi"
		FontPath		"/usr/share/X11/fonts/75dpi"
		# paths to defoma fonts
	    FontPath	    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	    FontPath	    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
		Load	"GLcore"
		Load	"bitmap"
		Load	"dbe"
		Load	"ddc"
		Load	"extmod"
		Load	"freetype"
		Load	"glx"
		Load	"int10"
		Load	"record"
		Load	"type1"
		Load	"v4l"
		Load	"vbe"
EndSection

Section "InputDevice"
		Identifier	  "Generic Keyboard"
		Driver		  "kbd"
		Option		  "CoreKeyboard"
	    Option		  "XkbRules"	  "xorg"
	    Option		  "XkbModel"	  "pc104"
	    Option		  "XkbLayout"	 "us"
EndSection

Section "InputDevice"
		Identifier	  "Configured Mouse"
		Driver		  "mouse"
		Option		  "CorePointer"
	    Option		  "Device"			    "/dev/input/mice"
	    Option		  "Protocol"			  "ImPS/2"
	    Option		  "ZAxisMapping"		  "4 5"
EndSection

Section "Device"
		Identifier	  "NVIDIA Corporation NV34 [GeForce FX 5500]"
		Driver		  "nvidia"
		BusID		   "PCI:1:0:0"
EndSection

Section "Monitor"
		Identifier	  "CMC 17 AD"
		Option		  "DPMS"
EndSection

Section "Screen"
		Identifier	  "Default Screen"
	    Device		  "NVIDIA Corporation NV34 [GeForce FX 5500]"
		Monitor		 "CMC 17 AD"
		DefaultDepth	24
		SubSection "Display"
			    Depth		   1
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   4
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   8
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   15
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   16
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   24
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
EndSection

Section "ServerLayout"
		Identifier	  "Default Layout"
		Screen		  "Default Screen"
		InputDevice	 "Generic Keyboard"
		InputDevice	 "Configured Mouse"
EndSection

Section "DRI"
		Mode	0666
EndSection
``` 

Or should I try TwinView. I'm only gonna use this to output my anime to the TV sometimes

---

### Post by dilerra on 2005-09-10
[QUOTE=Promethe]

Nice feature for Kubuntu users, which will allow them to run movies from context menu. If somebody know trick like this for GNOME, let me know.
Add this entry to:
```
~/.kde/share/apps/konqueror/servicemenus/nameofyourchoice.desktop
``` 
```
[Desktop Entry]
Actions=PlayOnTV
Encoding=UTF-8
ServiceTypes=video/*

[Desktop Action PlayOnTV]
Exec=mplayer -display localhost:1 %F
Name=Play this movie on TV
Icon=yast_tv
```
[/QUOTE]

Hi again all,

I put together a really simple script that makes it possible to right-click a file in Nautilus and from there choose to play that file in whatever media player one could  want on the second monitor (in my case, my tv). Just follow the very easy instructions below...

1. Open a terminal
2. Run "sudo gedit" or another text editor of your choice. just make sure that you run it with sudo...
3. Create an empty document and paste what you find below...
```

#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
	DISPLAY=:0.1 vlc -f "$uri"
done

```
The important part here is **vlc -f**. This opens the vlc media player in fullscreen. You can change this to whatever media player you prefer.
4. Save this file as /home/YOURUSERNAME/.gnome2/nautilus-scripts/TheNameOfTheTextDisplayedInTheContextMenu
("TheNameOfTheTextDisplayedInTheContextMenu" can be replaced with the text you want to be displayed, like "View in fullscreen on TV"...).
5. Exit your editor
6. Go into the directory /home/YOURUSERNAME/.gnome2/nautilus-scripts/
7. Change permissions for the file like this: "sudo chmod +x *"
8. Exit the terminal

Now, if you open a Nautilus window, you will be able to right-click files and from the Scripts-tab choose your own TV-script...

Hope this makes sense to you guys. Good luck!

---

### Post by reet on 2005-09-14
Thank you so much for this helpful HowTo!

I have just switched from my old Radeon 8500 to an FX5200. I didn't need the 3d acceleration and wanted fanless so cheap card here I come. I tried and I tried and I just could not get anything to display on my TV with the Radeon card. After switching to the nvidia card, installing the drivers, and changing xorg.conf according to this HowTo a tear came to my eye when I saw the nvidia logo appear on my tv on my first try. The picture quality is just wonderful as well, I can't tell the difference in image quality between watching a movie on my computer and my dvd player.

Thanks. \\:D/

---

### Post by dbrodie on 2005-09-22
I just wated to day thanks! The tutorial worked great on my Geforece 420 MX. 

Well, it didn't work great to begin with... but one I plugged in the cable it worked great  :)

---

### Post by cazz on 2005-09-24
Hmm I must have done something wrong.
After I have edit xorg.conf and reboot the computer I can't see anyting on the monitor or TV :(

---

### Post by daller on 2005-09-26
Here is my xorg.conf ```
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

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
	Option		"XkbLayout"	"dk"
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
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"NoLogo" "true"
	Option 		"TwinView" "true"
	Option 		"TwinViewOrientation" "Clone"
	Option 		"TVOutFormat" "COMPOSITE"#	
	Option 		"TVStandard" "PAL-B"
	Option 		"SecondMonitorHorizSync" "30-50"
	Option 		"SecondMonitorVertRefresh" "60"
	Option 		"MetaModes" "1680x1050,1680x1050,1024x768,1024x768;800x600,800x600"
EndSection

Section "Monitor"
	Identifier	"Standard Sk&#230;rm"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
	Monitor		"Standard Sk&#230;rm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

``` When I restarted X, the resolution on my laptop is no longer 1680x1050 - but 800x600 !!! This is quite annoying! - does any of you know how to fix this?

---

### Post by werand on 2005-09-29
[QUOTE=dilerra]Hi again all,
I put together a really simple script that makes it possible to right-click a file in Nautilus and from there choose to play that file in whatever media player one could  want on the second monitor (in my case, my tv). Just follow the very easy instructions below...
1. Open a terminal
2. Run "sudo gedit" or another text editor of your choice. just make sure that you run it with sudo...
3. Create an empty document and paste what you find below...
```

#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
DISPLAY=:0.1 vlc -f "$uri"
done

```
The important part here is **vlc -f**. This opens the vlc media player in fullscreen. You can change this to whatever media player you prefer.
4. Save this file as /home/YOURUSERNAME/.gnome2/nautilus-scripts/TheNameOfTheTextDisplayedInTheContextMenu
("TheNameOfTheTextDisplayedInTheContextMenu" can be replaced with the text you want to be displayed, like "View in fullscreen on TV"...).
5. Exit your editor
6. Go into the directory /home/YOURUSERNAME/.gnome2/nautilus-scripts/
7. Change permissions for the file like this: "sudo chmod +x *"
8. Exit the terminal
Now, if you open a Nautilus window, you will be able to right-click files and from the Scripts-tab choose your own TV-script...
Hope this makes sense to you guys. Good luck![/QUOTE]
If you're like me and have some directories/filenames including spaces (like '/mnt/win/My Movies/movie.avi') the above script shall be adjusted to this:
```
#!/bin/bash
for uri in "$@"; do
DISPLAY=:0.1 totem --fullscreen "$uri"
done
```
(I use Totem as my media player but that doesn't matter)
/Anders

---

### Post by reet on 2005-09-30
Hello,
I have been using TV-out according to this tutorial for a few weeks now and it works just great. However I have 2 questions to ask:

1. Is it possible to make the screensave operate independantly of each display. For ex. if there is no activity on the tv for 10 mins engage the screensaver but not on the monitor?

2. Is it possible to send programs that are already open to the TV display? I haven't found out how to do this, and am having to close the program and re-open it on the TV. Slightly annoying.

Thanks to anyone who can help me with this.

---

### Post by Xanf on 2005-10-08
Hi friends!

Sorry for bumping this old thread up, but it seems to be the most appropriate place for my question.

I experimented a lot (whole today) with Xorg settings for the TV-OUT at Nvidia card (in fact - 2 cards, GEForceFX 5600 Go and old Geforce 200MX, but I need now to make working the below with the last one).

And got to the following point where I need someone's else help. So, let me describe in details:
1. There is no problem to make TV-OUT to work as it is - either as described above in the thread, or according to the Nvidia instructions. Clone or TwinView. For making either extended desktop (across 2 displays) or to be able to run different programs on different displays - it's all OK.
2. But, for the really smooth TV video output of DVDs or other movies - there is need that the combination "display/driver" of the xorg.conf, where the TV attached is initialized by nvidia driver as the FIRST. (as in fact and according to Nvidia's read.me - only the first initialzed display gets acceleration).
3. Neither of my attempts to make the TV primary display and CRT secondary one within one X server vere successful - it either not able to run it that way, or maybe a driver bug. Only if CRT is the first and TV is a second I get both to work. But I don't like the quality of movie on the TV then.
4. So finally I ended up with running two separated X servers: by default my PC starts with X server for only TV out - so I have to log in to Gnome looking at the TV, and then, from the terminal by ALT+CTL+F2 - I login again and run the command like "sudo X -ac -layout CRT :1" manually  - which gives me second X server.
5. I can switch between those two X servers by ALT+CTL+F7 or F8 and have the advantage that my mouse is not crossing the borders of any of those screens. :-)
6. But, in this situation - I watch movies on the X session which is connected to TV, have Gnome session there on the TV too and in parallel with movie - I run other applications on the CRT by commands like "DISPLAY=:1 gedit myfile.txt". But I miss Gnome on that second X server display...

So, my need and request for help is the following:
1. How to make Ubuntu to run both those X servers automatically on the boot time in specific order - so that X for TV is initiated first and X for CRT - second?
2. How then, after #1 is done - to make GDM to appear not on the X session 0, but on the X session 1 ?

This will leave me able to normally work with CRT (but having no acceleration on it - doesn't matter for me) and only when I need to watch a DVD or MPEG movie - to run manually (or with xine - I can do it automatically) the video player on X session 0 (with a command like DISPLAY=:0 totem movie1.avi).

I hope I clearly explaind the issue....

If needed - I can post also the xorg.conf here, but don't think it's needed for solving my issue.

---

### Post by Mitch on 2005-10-09
I think my request for help is sort of similar to Xanf's.  I got my TV working wonderfully (two different sessions), but now I am getting greedy.  I want things to work a little more elegantly if possible.  

Here are two things I'd like to change:

1.  I'd like to not have my mouse switch over to my TV.

-This seems like it would be easy for someone who knew what they were doing.  Maybe taking out the "leftOf" thing in the serverlayout?

2.  I'd like to be able to switch off my TV without changing my xorg.conf and rebooting.  

-I know I can turn off the power, but I'd just like to give my GPU a break.  If I can't easily shut off that X session the is there anyway to minimize what goes on in that screen, (i.e. removing the panels and background) that would be cool too.

---

### Post by mrguytx on 2005-10-11
I followed the How-To, and I do actually get my laptop screen up, Nvidia logo, but weird, once the desktop comes up, I can get a mouse CURSOR, but clicking does nothing.

I know I"m very close to getting this to work which will thrill my 3 year old daughter so she can watch video's while I still have my laptop.

I think it must be in the final "serverlayout" section (just a hunch)

if anyone can spot an error in this xorg.conf I'll owe ya a sixpack.

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

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
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Keyboard1"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Mouse1"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier      "Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		 0
EndSection

Section "Device" 
	Driver          "nvidia" 
	Identifier      "Device[1]" 
	Screen		 1 
	Option          "TVOutFormat" "S-VIDEO" #or S-VIDEO etc 
	Option          "TVStandard" "NTSC" #or NTSC etc 
	Option          "ConnectedMonitor" "Monitor[1]" 
	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier 	"Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Monitor" 
	Identifier 	"Monitor[1]" #TV 
	HorizSync 60 
	VertRefresh 30-150 
EndSection

Section "Screen"
	Identifier  "Screen[0]" 
	Device      "Device[0]" 
	Monitor     "Monitor[0]" 
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

Section "Screen" 
	Device "Device[1]" 
	Identifier "Screen[1]" 
	Monitor "Monitor[1]" 
	DefaultDepth 24 
        SubSection "Display" 
               Depth 24 
               Modes "1024x768" 
        EndSubSection    
EndSection

#Section "ServerLayout"
#	Identifier  "Default Layout"
#	Screen	    "Default Screen"
#	InputDevice "Generic Keyboard"
#	InputDevice "Configured Mouse"
#	InputDevice "Synaptics Touchpad"
#EndSection

Section	"ServerLayout"
	Identifier  "Simple Layout" 
	        Screen 0 "Screen[0]" 
	        Screen 1 "Screen[1]" RightOf "Screen[0]"
	InputDevice	"Keyboard1"
	InputDevice	"Mouse1"
#	InputDevice	"Synaptics Touchpad" 
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by tuke81 on 2005-10-11
Allright nice How-to thanks!

I'm using it as it is but have made few changes of my xorg.conf:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

# use -display :0.1 to use screen 1
section "ServerLayout"
    	Identifier "dual"
    	Screen 0 "Screen0" 0 0
    	Screen 1 "Screen1" LeftOf "Screen0"
    	InputDevice "Generic Keyboard"
    	InputDevice "Configured Mouse"
EndSection

In this configuration mine ubuntu starts normaly without twinview.
but if I wanted to use my TV, I must shutdown x.
It's pretty hard to find safety way to shutdown x, my way is to kill gdm
(it sometimes halt whole system) with command:

tuke@tuke:~$ sudo killall gdm

after that I can start x again with different layout with command:

tuke@tuke:~$ startx -- -layout dual

Is there any changes to force ubuntu start without gdm??

---

### Post by Mitch on 2005-10-11
MrGuyTX:  

I think I had the exact same problem.  In server Layout change RightOf to LeftOf  and tell me if that doesn't fix it.


Tuke81:

Thanks I think I'll use that configuration too.

---

### Post by tuke81 on 2005-10-11
[QUOTE=Mitch]MrGuyTX:  

I think I had the exact same problem.  In server Layout change RightOf to LeftOf  and tell me if that doesn't fix it.


Tuke81:

Thanks I think I'll use that configuration too.[/QUOTE]

LeftOf and RightOf means witch side you have your tv. Mine is left so I use 
LeftOf

---

### Post by mrguytx on 2005-10-11
[QUOTE=Mitch]MrGuyTX:  

I think I had the exact same problem.  In server Layout change RightOf to LeftOf  and tell me if that doesn't fix it.


Tuke81:

Thanks I think I'll use that configuration too.[/QUOTE]

Nope that didn't do it. However it did make GDM be invisible. I had a black screen but I could tell from the "ubuntu sound" (those little drums) that I could log in.
Logged in, get background, get gnome panels above and below, get mouse cursor but clicking does nothing. 

Man I can tell I'm "this close" to figuring this out but after a couple of days now, I may just leave it at using twinview. At least I can use the tv that way, but my laptop is stuck in 1024x768 mode and I really prefer 1400x1050.

Grrr.

Thanks for the tip though.

=G

---

### Post by tuke81 on 2005-10-11
mayby I wasnt so accurate of my question, with my xorg.conf has two diifferent serverlayouts. It need to modified little bit more than just that layout thing. Here is the main components how its works:

Section "Device"
    	Identifier "NVIDIA Corporation NV34 [GeForce FX 5500]"
    	Driver "nvidia"
    	Option "NoLogo"
    	BusID "PCI:1:0:0"
    	#Screen 0
EndSection

Section "Device"
    	Identifier "nvidia1"
    	Driver "nvidia"
    	BusID "PCI:1:0:0"
    	Option "NoLogo"
    	Screen 1
    	Option          "TVOutFormat" "Composite" #or S-VIDEO etc 
	Option          "TVStandard" "PAL-G" #or NTSC etc 
	Option          "ConnectedMonitor" "Monitor1" 
EndSection

Section "Monitor"
	Identifier	"901B"
	Option		"DPMS"
EndSection

Section "Monitor"
    	Identifier "Monitor1"
    	HorizSync 30-50
	VertRefresh 60
#    	Option "DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"901B"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
    	Identifier "Screen1"
    	Device "nvidia1"
    	Monitor "Monitor1"
    	DefaultDepth 24
    	SubSection "Display"
        Depth 	24
        Modes 	"1024x768" "832x624" "800x600"
    	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

# use -display :0.1 to use screen 1
section "ServerLayout"
    	Identifier "dual"
    	Screen 0 "Screen0" 0 0
    	Screen 1 "Screen1" LeftOf "Screen0"
    	InputDevice "Generic Keyboard"
    	InputDevice "Configured Mouse"
EndSection 

So Normal login it uses default layout, with only CRT is on. I get Twinview with entering command startx -- -layout dual, but what I wanted to do is start ubuntu without any gdm nor x-server, that I can login and use that layout what I need. Normaly it can be done by configuring inittab but some reason or other I cant get it work properly.:???: :confused:

---

### Post by inz on 2005-10-13
I have a working setup with two monitors running twinview. Basically I have one long desktop spanning these two monitors, I would like to add a TV display as well. Everything is connected to one Geforce 5900XT card. Has anyone done this? Could anyone provide me a sample config? I have tried a lot, but can't seem to get xorg to start up on all three displays at the same time. :(

To get one "seperate" desktop on the tv, do I need to add two "device" sections even though it is all connected to the same device? I feel confused.

---

### Post by hegex on 2005-10-14
Hello Earthlings!
Nice Thread. Helped me alot, but i have to make one question more.
Tv-out works fine but now nvidia-glx-config will not be enabled. It gives me this message :

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

.. What should i do?

---

### Post by mb2k on 2005-10-19
Excuse me, perhaps a stupid question, but does this work without having the Nvidia driver installed ? I`m running "nv" as driver...

Cause I have given up the try of installing the damn fu*** nvidia drivers ....

---

### Post by mrguytx on 2005-10-19
[QUOTE=mrguytx]Nope that didn't do it. However it did make GDM be invisible. I had a black screen but I could tell from the "ubuntu sound" (those little drums) that I could log in.
Logged in, get background, get gnome panels above and below, get mouse cursor but clicking does nothing. 

Man I can tell I'm "this close" to figuring this out but after a couple of days now, I may just leave it at using twinview. At least I can use the tv that way, but my laptop is stuck in 1024x768 mode and I really prefer 1400x1050.

Grrr.

Thanks for the tip though.

=G[/QUOTE]

SOLVED.
I posted the link on the fedorasolved site.

[http://fedorasolved.com/viewtopic.php?t=155](http://fedorasolved.com/viewtopic.php?t=155)

(but this is the xorg.conf on my ubuntu laptop so it works great)

---

### Post by _MiniMe_ on 2005-11-03
I found this thread some time ago and now tried to get the tv-out to work on my GeForce 6600.  I followed the instructions of RedDwarf (on the first side of this thread). I thaught that would give me two running X-servers, one on the monitor and one on the TV. But it doesn't seem to work correctly. I can change the resolution of the second monitor (=tv) with "System"->"Settings" but I get no picture an the tv. 

This is my xorg.conf:

```
#################### MONITOR ###########################
Section "Monitor"
	Identifier	"monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	HorizSync 30-40
	VertRefresh 50
	DisplaySize 412 310
	ModeLine "720x576/50p" 27 720 744 800 864 576 581 583 625 #27.0 MHz, 31.2 kHz, 50.0 Hz
	Modeline "800x600/50p" 31.60 800 824 968 1000 600 602 603 632 #31.6 MHz, 31.6 kHz, 50.0 Hz	
EndSection

################### DEVICE ############################
Section "Device"
	Identifier	"device0"
	BoardName 	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Option 		"NoLogo" "true"
	Option 		"ConnectedMonitor" "CRT"
	Screen 0
EndSection

Section "Device"
    	Identifier "device1"
	VendorName "nVidia"
	BoardName "NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver "nvidia"    
	Option "NoLogo" "true"
	BusID  "PCI:3:0:0"
	Option "ConnectedMonitor" "TV"
	Option "TVStandard" "PAL-B"
	Option "TVOutFormat" "COMPOSITE"
	Option "IgnoreEDID" "true"
	Screen 1
EndSection

################ SCREEN ################################
Section "Screen"
	Identifier	"screen0"
	Device		"device0"
	Monitor		"monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
EndSection

Section "ServerLayout"
	Identifier	"layout0"
	Screen 0	"screen0"
	Screen 1	"screen1" leftOf "screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

The Xorg.1.log in /var/log/ reports some errors, but that didn't help me solving the problem. Here are the reported errors:

```
(II) Primary Device is: PCI 03:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:3:0:0) found
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe9000000 - 0xe90001ff (0x200) MX[B]
	[6] -1	0	0xea085000 - 0xea08503f (0x40) MX[B]
	[7] -1	0	0xea084000 - 0xea0847ff (0x800) MX[B]
	[8] -1	0	0xea080000 - 0xea080fff (0x1000) MX[B]
	[9] -1	0	0xea000000 - 0xea07ffff (0x80000) MX[B]
	[10] -1	0	0xea086000 - 0xea086fff (0x1000) MX[B]
	[11] -1	0	0xea083000 - 0xea0830ff (0x100) MX[B]
	[12] -1	0	0xea082000 - 0xea082fff (0x1000) MX[B]
	[13] -1	0	0xea087000 - 0xea087fff (0x1000) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[21] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(EE) Screen 0 deleted because of no matching config section.
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.


```

It complains about a missing config section, but I can't find an error in the Xorg.conf. And then it says that screen 0 is deleted, but screen 0 is the one on my monitor??? I hope someone can help...

---

### Post by mrguytx on 2005-11-03
perhaps this will help you, though it's posted on a fedora site, it is an ubuntu xorg.conf, I know this because it's MINE, and I have tvout working here great, but not the same as this thread led me to..I had to tweak a bit...

compare the xorg.conf on this link, maybe it will help you, there are also instructions there, (mine)

[http://fedorasolved.com/viewtopic.php?t=157](http://fedorasolved.com/viewtopic.php?t=157)

good luck

---

### Post by _MiniMe_ on 2005-11-03
thx for the fast reply, but unfortunately it didn't help

the only differences between my xorg.conf and yours were the "TwinView" Option and the "Modes" section for screen1 (=tv). I changed that and it made everything worse. Now I can't change the resolution of the second screen (it doesn't exist in the menu) and the mousepointer doesn't go "out of the monitor" anymore. This two things worked before, although I couldn't see anything on my tv :( It was a good idea to ake a backup ;) 

I had the tvout working with Hoary and a GeForce 5700, but without two independant X-servers (was quite annoying to switch all the time). I really can't figure out what's wrong now... (I'm using breezy)

btw: I tried nvtv, but it reported a fatal error "no supported videocard found"

---

### Post by _MiniMe_ on 2005-11-03
Hey,

  it works now! I just had to change the outputformat to S-VIDEO. I knew that the card has a s-video-plug, but my tv can't display an s-video-signal properly (picture is b/w). With the GeForce 5700 it worked when I changed the format to COMPOSITE. Too bad the card is broken, now i have to buy a new cable (after buying a new card few days ago :( )

But I have another problem: when I start a movie with "DISPLAY=:0.1 xine movie", xine opens up on the tv, but doesn't start the movie (it doesn't load it). When I start it manually, it works. When I use the same syntax to start a movie on the monitor it works fine. Any idea what the problem is?

thx again for your help

btw: the error output in the xorg logfile still exists.... :???:

---

### Post by mcpish on 2005-11-17
I got almost everything working except overscan.

The image on my TV is a little underscanned so I followed the instructions according to the nvidia site 

> 
Option "TVOverScan" "Decimal value in the range 0.0 to 1.0"
   Valid values are in the range 0.0 through 1.0. Please see the article titled "Linux - Configuring TV-Out."

The "TVOverScan" option can be used to enable Overscan where
 supported.  Valid values are decimal values in the range 1.0 (which
 means overscan as much as possible: make the image as large as
 possible) and 0.0 (which means disable overscanning: make the image
 as small as possible).  Overscanning is disabled (0.0) by default.


So I put the line 
**Option "TVOverScan" "1.0"** in my xorg.conf file right under the other option settings in the file but it doesn't overscan the image.  However, if I use the 'nvidia-settings' GUI program in linux I CAN use the slider and it does fix the overscan, it just doesn't seem to save these settings after each reboot.  What is the proper command I'm supposed to use to set TV overscan in the xorg.conf file?

---

### Post by October on 2005-12-02
I'm still struggling with this!  I had it working peachy on Hoary with an FX5200 and recently upgraded to Breezy and a Leadtek GF4 ti4600 A250 Ultra, for gaming purposes!

After reading this thread and trying various bits and pieces of it this is what I have accomplished:

When I restarted X **my monitor goes to sleep and my tv out wakes up and I actually get to SEE the "nvidia" splash screen on the big screen and then it goes black**.  I hear the drums so I assume everything else is working fine.  I get no x server errors.  I used to run my old setup in "clone" and would be happy to get even that working...

Here is the xorg.conf that produced these results and that is the closest I've gotten so far.  Help?

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
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

Does ANYONE have Breezy tv-out working with a ti4600?

Thanks in advance!

---

### Post by LooGoo99 on 2005-12-04
[QUOTE=blitze]Be Wary though with DVI outputs and TV out.  FPD are treated as the second screen by the Nvidia drivers.  Still it works well and oneday someone either Nvidia or Gnome will sortout the screen order issue.  Why we can't allocate which we'd like to use as primary god only knows but at the moment we can't.   :-|[/QUOTE]

I'm well on my way getting this to work, but unfortunately X seems to think the TV is my primary display and I can't persuade him otherwise! So each time I need to login, the login display is on the primary screen (TV) only. The monitor is attached through the DVI output on my Nvidia FX5600.

Odd thing is: my monitor is at 1024x768. But according to my xorg.conf, it should be 1280x1024... X seems to be confusing my TV and monitor.

I've tried various options I found on the forums, but to no avail. Any suggestions are most welcome!

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
	Identifier		"Device[0]"
        Driver		"nvidia"
        BusID		"PCI:1:0:0"
        #Option 		"ConnectedMonitor" "Monitor[0]"
        Screen 0
EndSection

Section "Device" 
   Driver          	"nvidia" 
   Identifier      	"Device[1]" 
   Option          	"TVOutFormat" "S-VIDEO" #or S-VIDEO etc 
   Option          	"TVStandard" "PAL-G" #or NTSC etc 
   #Option       	"ConnectedMonitor" "Monitor[1]" 
   BusID           	"PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
   Screen 1 
EndSection

Section "Monitor"
	Identifier 		"Monitor[0]" #TFT
	Option		"DPMS"
	HorizSync		28-64
	VertRefresh	43-60
	Modeline		"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 60 
    VertRefresh 30-150 
 EndSection

Section "Screen"
	Identifier		"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen" 
   Device 		"Device[1]" 
   Identifier 	"Screen[1]" 
   Monitor 		"Monitor[1]" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 	24 
               Modes 	"1024x768" 
       EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
	Screen 0 "Screen[0]"
        Screen 1 "Screen[1]" LeftOf "Screen[0]"
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "CorePointer"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by mrguytx on 2005-12-04
[QUOTE=October]I'm still struggling with this!  I had it working peachy on Hoary with an FX5200 and recently upgraded to Breezy and a Leadtek GF4 ti4600 A250 Ultra, for gaming purposes!

After reading this thread and trying various bits and pieces of it this is what I have accomplished:

When I restarted X **my monitor goes to sleep and my tv out wakes up and I actually get to SEE the "nvidia" splash screen on the big screen and then it goes black**.  I hear the drums so I assume everything else is working fine.  I get no x server errors.  I used to run my old setup in "clone" and would be happy to get even that working...

Here is the xorg.conf that produced these results and that is the closest I've gotten so far.  Help?

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
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

Does ANYONE have Breezy tv-out working with a ti4600?

Thanks in advance![/QUOTE]


Look at the ServerLayout in the link I sent you, that seems to be your issue.

---

### Post by mrguytx on 2005-12-04
[QUOTE=LooGoo99]I'm well on my way getting this to work, but unfortunately X seems to think the TV is my primary display and I can't persuade him otherwise! So each time I need to login, the login display is on the primary screen (TV) only. The monitor is attached through the DVI output on my Nvidia FX5600.

Odd thing is: my monitor is at 1024x768. But according to my xorg.conf, it should be 1280x1024... X seems to be confusing my TV and monitor.

I've tried various options I found on the forums, but to no avail. Any suggestions are most welcome!

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
	Identifier		"Device[0]"
        Driver		"nvidia"
        BusID		"PCI:1:0:0"
        #Option 		"ConnectedMonitor" "Monitor[0]"
        Screen 0
EndSection

Section "Device" 
   Driver          	"nvidia" 
   Identifier      	"Device[1]" 
   Option          	"TVOutFormat" "S-VIDEO" #or S-VIDEO etc 
   Option          	"TVStandard" "PAL-G" #or NTSC etc 
   #Option       	"ConnectedMonitor" "Monitor[1]" 
   BusID           	"PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
   Screen 1 
EndSection

Section "Monitor"
	Identifier 		"Monitor[0]" #TFT
	Option		"DPMS"
	HorizSync		28-64
	VertRefresh	43-60
	Modeline		"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 60 
    VertRefresh 30-150 
 EndSection

Section "Screen"
	Identifier		"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen" 
   Device 		"Device[1]" 
   Identifier 	"Screen[1]" 
   Monitor 		"Monitor[1]" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 	24 
               Modes 	"1024x768" 
       EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
	Screen 0 "Screen[0]"
        Screen 1 "Screen[1]" LeftOf "Screen[0]"
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "CorePointer"
EndSection

Section "DRI"
	Mode	0666
EndSection
```[/QUOTE]

Try changing "LeftOf" to "RightOf" in your ServerLayout section, just a guess...

---

### Post by LooGoo99 on 2005-12-04
> Try changing "LeftOf" to "RightOf" in your ServerLayout section, just a guess...If only it were that simple :cool: Too bad, that wouldn't do it!

---

### Post by October on 2005-12-04
> 
Look at the ServerLayout in the link I sent you, that seems to be your issue.

Yeah, sorry, my bad.  I posted my backup xorg.conf by accident!  :oops: 

BELOW is the correct xorg.conf, again, it puts my monitor to sleep and I get to see the nvidia splash screen on my tv and then all I get is a black screen.  Help???

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
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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


Section "Monitor"
    Identifier "monitor1"
    VendorName "Viewsonic"
   # HorizSync 30-71
   # VertRefresh 50-160
EndSection

Section "Monitor"
    Identifier "monitor2"
    VendorName "Generic TV"
    HorizSync 30-50
    VertRefresh 60
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia"
    BoardName "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
    Driver "nvidia"
    Option "DPMS"
    Option "NoLogo" "false"
    Option "RenderAccel" "true"
    Option "Twinview" "true"
    Option "TwinViewOrientation" "Clone"
    BusID  "PCI:1:0:0"
    Option "ConnectedMonitor" "CRT"
    Option "HWCursor" "On"
    Option "NvAGP" "2"
    Screen 0
EndSection

Section "Device"
    Identifier "device2"
    VendorName "nVidia"
    BoardName "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
    Driver "nvidia"    
    Option "NoLogo" "false"
    Option "RenderAccel" "true"
    Option "Twinview" "true"
    Option "TwinViewOrientation" "Clone"
    BusID  "PCI:1:0:0"
    Option "ConnectedMonitor" "TV"
    Option "TVStandard" "NTSC-M"
    Option "TVOutFormat" "SVIDEO"
    Option "IgnoreEDID" "true"
    Option "HWCursor" "On"
    Option "NvAGP" "2"
    Screen 1
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Virtual 1024 768
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Virtual 1024 768
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Virtual 1024 768
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Virtual 1024 768
    EndSubsection
EndSection

Section "Screen"
    Identifier "screen2"
    Device "device2"
    Monitor "monitor2"
  DefaultColorDepth 24
EndSection

Section "ServerLayout"
    Identifier "layout0"
    InputDevice "Generic Keyboard" "CoreKeyboard"
    InputDevice "Configured Mouse" "CorePointer"
    Screen 0 "screen1"
    Screen 1 "screen2" LeftOf "screen1"
EndSection

```

Thanks in advance!

---

### Post by October on 2005-12-04
Ok, I've made a bit of progress, I think.  I adapted some of my xf86 config from a previous debian install that worked with my 5200FX and dropped the metamode resolution to "800x600,800x600".   I get a full desktop on the tv but  the monitor remains asleep.  Any clues?

Here is the xorg.conf that produced these results:

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
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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


Section "Monitor"
    Identifier "monitor1"
    VendorName "Viewsonic"
 HorizSync 30-71
 VertRefresh 50-160
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia"
    BoardName "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
    Driver "nvidia"
    Option "DPMS"
    Option "NoLogo" "false"
    #Option "RenderAccel" "true"
    Option "Twinview" 
    Option "TwinViewOrientation" "Clone"
    BusID  "PCI:1:0:0"
    Option "ConnectedMonitor" "crt, TV"
    Option "MetaModes" "800x600,800x600"
   Option "TVStandard"               "NTSC-M"
   Option "SecondMonitorHorizSync"   "30-50"
   Option "SecondMonitorVertRefresh" "60"
    Option "HWCursor" "On"
    #Option "NvAGP" "2"
    Screen 0
EndSection



Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Virtual 800 600
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Generic Keyboard" "CoreKeyboard"
    InputDevice "Configured Mouse" "CorePointer"
    Screen "screen1"
EndSection

```

---

### Post by mrguytx on 2005-12-04
[QUOTE=October]Ok, I've made a bit of progress, I think.  I adapted some of my xf86 config from a previous debian install that worked with my 5200FX and dropped the metamode resolution to "800x600,800x600".   I get a full desktop on the tv but  the monitor remains asleep.  Any clues?

Here is the xorg.conf that produced these results:

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
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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


Section "Monitor"
    Identifier "monitor1"
    VendorName "Viewsonic"
 HorizSync 30-71
 VertRefresh 50-160
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia"
    BoardName "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
    Driver "nvidia"
    Option "DPMS"
    Option "NoLogo" "false"
    #Option "RenderAccel" "true"
    Option "Twinview" 
    Option "TwinViewOrientation" "Clone"
    BusID  "PCI:1:0:0"
    Option "ConnectedMonitor" "crt, TV"
    Option "MetaModes" "800x600,800x600"
   Option "TVStandard"               "NTSC-M"
   Option "SecondMonitorHorizSync"   "30-50"
   Option "SecondMonitorVertRefresh" "60"
    Option "HWCursor" "On"
    #Option "NvAGP" "2"
    Screen 0
EndSection



Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Virtual 800 600
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Generic Keyboard" "CoreKeyboard"
    InputDevice "Configured Mouse" "CorePointer"
    Screen "screen1"
EndSection

```[/QUOTE]

again, you only have one screen defined in your ServerLayout section, please adjust accordingly, like this:

```
Section   "ServerLayout"
   Identifier  "Default Layout"
        Screen 0 "Screen[0]"
        Screen 1 "Screen[1]" LeftOf "Screen[0]"
   InputDevice   "Keyboard1"
   InputDevice   "Mouse1"
   InputDevice   "Synaptics Touchpad"
EndSection
```

---

### Post by October on 2005-12-04
SUCCESS!!!!!!!

I read LOTS of threads and modified my xorg.conf at least a dozen times.  Turned out that using the "ConnectedMonitor" option was a no-no and Xinerama also needs to be disabled.  Finally, while the card I am running (a GF4 ti4600 Ultra) is superior to my newer FX5200 for gaming, it seems incapable of doing twinview at 1024x768 so for now both my desktop and tv-out are at 800x600.  Below is my working xorg.conf in case anyone can benefit from it:

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
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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


Section "Monitor"
    Identifier "monitor1"
    VendorName "Viewsonic"
 HorizSync 30-71
 VertRefresh 50-160
# Sony Vaio C1(X,XS,VE,VN)?
# 1024x480 @ 85.6 Hz, 48 kHz hsync
ModeLine "1024x480" 65.00 1024 1032 1176 1344 480 488 494 563 -hsync -vsync

# TV fullscreen mode or DVD fullscreen output.
# 768x576 @ 79 Hz, 50 kHz hsync
ModeLine "768x576" 50.00 768 832 846 1000 576 590 595 630

# 768x576 @ 100 Hz, 61.6 kHz hsync
ModeLine "768x576" 63.07 768 800 960 1024 576 578 590 616
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia"
    BoardName "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
    Driver "nvidia"
    #Option "DPMS"
    Option "NoLogo" "false"
     Option "Xinerama" "off"
    #Option "RenderAccel" "true"
    Option "Twinview" "true"
    Option "TwinViewOrientation" "Clone"
    #Option "ConnectedMonitor" "CRT-0, TV-0"
    Option "MetaModes" "800x600,800x600"
   Option "TVStandard"               "NTSC-M"
   Option "SecondMonitorHorizSync"   "30-50"
   Option "SecondMonitorVertRefresh" "60"
    Option "HWCursor" "On"
    #Option "NvAGP" "2"
     BusID  "PCI:1:0:0"
    Screen 0
EndSection



Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Virtual 800 600 
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Virtual 800 600
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Virtual 800 600
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Generic Keyboard" "CoreKeyboard"
    InputDevice "Configured Mouse" "CorePointer"
    Screen "screen1"
EndSection

```

---

### Post by LooGoo99 on 2005-12-08
SOLVED :KS 

My problem (the TV was my primary device instead of my monitor) had something to do with the ConnectedMonitor option. I had to define this option right. This site was helpful: [http://www.gmpf.de/index.php/NVidia:TV-OUT](http://www.gmpf.de/index.php/NVidia:TV-OUT)

---

### Post by iyiguncevik on 2007-06-29
I made it working with both scenario's: with 2 screens and with TwinView. 

In TwinView Clone mode, there's a big disadvantage that when I play a movie full screen both monitors are playing the movie.

With 2 screens, I have some other problem. It works fine unless I use Beryl. When Beryl is running, I couldn't manage to start an application (mplayer, totem, ...) in TV screen. DISPLAY=:0.1 stuff doesn't return any errors, but nothing happens on TV screen neither. I only see my beautiful wallpaper :)

Is there anyone who could manage working with 2 screens with Beryl or Compiz?

Iyigun

---

### Post by o.besner on 2008-02-01
Just wanted to say thanks for the tutorial (It works even on Gutsy)

I have an HP dv9xxx laptop, and the nVidia 6150 tv out works like a charm now.

---

