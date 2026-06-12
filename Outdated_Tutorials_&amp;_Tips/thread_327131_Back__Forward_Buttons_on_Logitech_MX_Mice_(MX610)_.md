---
title: "Back / Forward Buttons on Logitech MX Mice (MX610) - The Quick &amp; Easy Guide"
date: 2006-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by kogber on 2006-12-28
This guide will get your back /forward mouse buttons working in Firefox.  If you are looking for more functionality, I have made [this guide]("http://ubuntuforums.org/showthread.php?t=332256"), which uses the evdev driver and xbindkeys for mapping buttons and includes info about the mx610 indicator lights.

**Preface**
Thanks to all of the Ubuntu forum posts that help me figure Stuff out.
New linux user notice: You will be editing the xorg.conf file.  If something with this file goes wrong when you reboot, Ubuntu will not load correctly, and you will need to revert to a backup of xorg.conf from a command line.  Instructions for backing up xorg.conf will follow in this guide. 

[SIZE="5"]**The Quick & Easy Guide**[/SIZE]

**1. Backup your xorg.conf file**

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.good     #(think: Copy Source Destination)
```


now you have a good version (xorg.conf.good) of the file to fall back on if something goes wrong.   If, after rebooting, you wind up at a text prompt, type in your username and pass.  Then type: [COLOR="DarkRed"]
Write this down! [/COLOR]
```

sudo cp /etc/X11/xorg.conf.good /etc/X11/xorg.conf
startx  # this command will load Xorg (the GUI)

``` 

**2. Edit your xorg.conf file**
Open up your xorg.conf file in a text editor from a console command:

```
sudo gedit /etc/X11/xorg.conf
```  
(replace gedit with kate in kubuntu)

find the section that looks like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

Then edit it like so:

```
Section "InputDevice"
	Identifier "Configured Mouse"
 	Driver "mouse"
 	option "CorePointer"
 	option "Emulate3Buttons" "no"
 	option "Device" "/dev/input/mice"
 	option "Protocol" "ExplorerPS/2"
 	option "ZAxisMapping" "4 5"
**      option "ButtonMapping" "1 2 3 6 7"**
  	option "Resolution" "800"
EndSection
```

This will map your back (6) and forward (7) buttons!  ( Also try 8 & 9 if 6 & 7 does not work for your mouse )

**3. Save and Reboot**
Now save the file, and restart the computer.  [COLOR="DarkRed"]Remember: if the xorg.conf file is not edited properly (ie typos) you will need to revert to the backup as explained above.[/COLOR]

[SIZE="3"]
Additional Information and Links[/SIZE]

If your mouse is not the MX610, and the 6 7 mapping does not work for your mouse, you can run the xev utility in the console to see what buttons correspond to back and forward.

To get the back/forward buttons working in other applications, see  [HOWTO: Configuring Logitech mice in Ubuntu 6.06: New Guide]("http://ubuntuforums.org/showthread.php?t=219894") , Section 2: Side buttons and Nautilus, Epiphany, Konqueror, etc

---

### Post by trav5 on 2007-01-04
This works fine in Firefox for my Logitech lx 7 but in nautilus it scrolls side to side. I copied your xorg section exactly. Any thoughts on getting fow/back working in nautilus? And should I remove the backup of xorg?```
rm /etc/X11/xorg.conf.good
```right?

---

### Post by Skidpad on 2007-01-04
First of all, Thank You for the help!     =D>  Not having my fwd/back buttons working on my MX610 mouse has been a big deal since I installed Ubuntu last weekend; everything now functions correctly in Firefox...I may tackle the Nautilus & side scroll functions next.  

For those who are interested, here is my xorg.conf file; I added the **line** as shown, everything else as-is. 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		  "mouse"
	Option		"CorePointer"
	Option		"Device"		        "/dev/input/mice"
	Option		"Protocol"		        "ExplorerPS/2"
	Option		"ZAxisMapping"		 "4 5"
        **Option     "ButtonMapping"         "1 2 3 6 7" **
	Option		"Emulate3Buttons"     "true"

---

### Post by kogber on 2007-01-05
Skidpad & trav5,

Since posting this howto, I have gotten everything on the mouse working except the horizontal scroll.  This includes the email and IM indicator lights.  I am going to post another Quick & Easy howto that includes info about getting the back/forward working in other apps (as opposed to a link here to someone else's howto), as well as the indicator lights stuff.  I am learning as much as I can about the various details of linux I/O before I post this next one.  I will post what I know asap.  Stay tuned, it will be up later today.

trav - it is always a good idea to keep that working xorg.conf backup, Just In Case.

---

### Post by trav5 on 2007-01-05
Now see the need to keep the backup. I was trying someone else's how to last night and had to use it. Something strange happened after redoing your xorg conf. I dont think it is related because it happens during bios screen and first part of os startup for both edgy and m$2k. My screen resolution is not right. It is like it is set 800 instead of 1024. It is fine once os loads. From searching the forums I think it might be the video card. The only thing that seems weird is it happened after manually entering the option "Resolution" "800" line to the mouse config. Still should not effect the bios screen.

---

### Post by trav5 on 2007-01-05
Sorry meant to post xorg.conf```
tux@tux-laptop:~$ cat /etc/X11/xorg.conf
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
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "ButtonMapping"         "1 2 3 6 7"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by kogber on 2007-01-05
trav5, are you sure you put that "Resolution" "800" line into the *Mouse* Config section?  Any changes to the vid card resolution before linux or win2k loads probably means you changed a setting in your laptop BIOS or the video card firmware.  Let's take this to a new thread and keep this one relevant.

---

### Post by trav5 on 2007-01-05
> **kogber said:**
>  Let's take this to a new thread and keep this one relevant.

I started a new thread in hardware and laptops.

---

### Post by kogber on 2007-01-08
[New Guide]("http://ubuntuforums.org/showthread.php?t=332256") is now posted.  It uses xbindkeys so backwards and forwards should work in Epiphany, Konqueror, etc - any app that supports the standard "Alt + Left/Right" for navigation.

---

### Post by reabralop on 2007-01-17
I was able to successfully get my back and forward buttons working but I have another button that now functions as a back button as well. My two extra buttons are for page up and page down (above and below the scroll wheel). The page down stills does his job but the page up is now "back".

My question is what are the number's meaning in the code above. Basically i need to know what to change to get the functionality back without loosing other buttons.

---

### Post by kogber on 2007-01-18
reabralop,

I am going to guess you have a mx510 series?  Are you using a usb or ps/2 connection?

First, an explanation of the numbers:

option "ZAxisMapping" "4 5" maps button 4 to the scroll up action, and button 5 to scroll down.

The ButtonMapping line maps physical button numbers to logical buttons/events in this order (left click, middle click, right click, left, right):
```
option "ButtonMapping" "1 2 3 6 7"
```


This guide is a quick "hack" since it uses the PS/2 protocol, so you unfortunately can't add more mappings to this ButtonMapping line to simply add the page up/down buttons (from what I understand).

First, I would suggest you try adding the following line to the mouse's InputDevice section(don't forget to backup the xorg.conf):
```
   Option "Buttons"      "10" 
```

This might fix the problem, if it is a case of overlapping.

If that doesn't work, I would suggest that you run the xev utility in a console (just type "xev" in a console, and ctrl+C to exit ) to see what button number each mouse button corresponds to. 

You might have to switch to the evdev usb driver to get all of your mouse buttons working.    I would suggest searching the forum for other mentions of your exact mouse model to see if there is an easy solution for you.  You can try my or someone else's evdev guide.

---

### Post by robertpolson on 2007-01-19
Excellent guide. I got my mouse buttons working.

---

### Post by Omegatron on 2007-02-28
Thanks.  This works on a Logitech MediaPlay mouse to get back and forward in Firefox, which makes life so much easier while trying to search for solutions to all my other Linux problems.  :-)

I tried other guides and X wouldn't start.  Sigh.  I hate editing text files.  Why can't this just be part of Ubuntu?  Why can't there just be a package to download that fixes this for us?

---

### Post by Velmar on 2007-10-13
Just a short note from this new user...

Make sure you have the line

```
Option          "Protocol"              "ExplorerPS/2"
```

in there, my original xorg.conf read

```
Option		"Protocol"	"ImPS/2"
```

instead.
Because of that, it did not work with my old Logitech MouseMan Optical. Changing that line did the trick, though.

Hope that helps.

Vel.

---

