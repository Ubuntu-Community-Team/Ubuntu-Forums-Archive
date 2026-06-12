---
title: "HOWTO: TwinView"
date: 2005-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by sfink01 on 2005-11-03
I've created a HOWTO on TwinView for Ubuntu Breezy and it can be found at
[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)
it should work for Hoary also but hasn't been tested as of yet.

Enjoy!

---

### Post by poofyhairguy on 2005-11-03
Good guide. I like the line by line explanation. I would add its best to turn off the xinerama flag:

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

as said there. And you don't HAVE to turn render accel off. I can't live without it- its needed for xcompmgr.

---

### Post by UrbanSlayer on 2005-11-06
I would be very interested to see how your experience with 3 monitors goes.

While the nvidia drivers are far far better than the ATI ones, TwinView on Linux still doesnt support more than 2 screens, and that is damned, damned annoying.  Trying to set it up how I have it on XP means I have to use Xinerama, which is slow slow slow.

I'm waiting patiently for things to change, as this is the only thing stopping me from switching my main desktop to linux.

---

### Post by Mr_J_ on 2005-11-21
I tried and followed this to almost a T, but since I have PCI-E 6600GT I didn't put the "nvAGP" "2".
I read what it's supposed to do, and although it's not very descriptive I think it's for AGP cards for some reason. Go figure...:D 
Should I put it anyway?
I'm just wondering if it's going to damage anything if I do that.

Another thing.
Why does the acceleration has to be off?
Anyone know?

If there is another howto on doing this twinview thing I appreciated.
I searched, but to no help.

It's weird. I have two monitor outside of gdm, but inside I only have 1.
I go to console and I get another monitor.

---

### Post by sfink01 on 2005-11-23
You are right to leave out nvAGP, the module will handle your PCI card fine without it.

Render Accel "off" is just a starting point, for some cards it causes serious problems and hard lockups.  So once you get it going then try turning Render Accel on and see what happens.

What do you mean you have to go to the console and get another monitor?  Please explain in more detail.

Best,

Steve

---

### Post by Mr_J_ on 2005-11-24
If I do Ctrl+Alt+F1 for example. I get twinview working. I get the duplicate monitor actually working.
Basicly inside the console, but outside X I have this working.
In the getty consoles I have it working.

Sorry for repetition.

Another question.
If I want to get the monitor stretching across the 2 monitors. How would I do it?
It's with this same howto. Right?

---

### Post by sfink01 on 2005-11-24
Yes stretching the desktop across both monitors is included.  You can do it several ways.

You can put:
Option "NoTwinViewXineramaInfo"
into your Device section this will prevent the card from sending Xinerama info back to the Window Manager and give you a streched desktop.

Or

You can put:
Option "Xinerama" "On"
into your ServerLayout section and end up with the same result controlled by X.

Good Luck!

Steve

---

### Post by Mr_J_ on 2005-11-24
I think I had that already. Then I took it off.
I don't understand this anymore.

Got to get myself to understand all this because i thought
[COLOR="Sienna"]metamodes "1280x1024, 1280x1024;"[/COLOR]
told xorg to have 2 monitors at that resolution.
If [COLOR="Sienna"]NoTwinViewXineramaInfo[/COLOR] says it's stretched.
Isn't this conflictuous? (Hope it's spelled correctly.)

For all I know it's not a problem, and it's just my head playing tricks on me.

Maybe I should just read up on Xorg.conf to understand all this.
Got any good starting spots?

Wonder if I can have the two monitors and diferent resolutions in each.

What I really wanted was two independent monitors. Maybe using a key shortcut to switch between the two. I wanted them to show independent images in the two monitors. Now that would be a leg up on the OS business.
If anyone knows any way to do this please point it out to me, because that was my first intention to begin with.
Even If I have to login as if a diferent user in both, but I really wanted to have two independent monitors using the same login and desktops.

This is a dream, but if you could have the monitors extend when they are in the same desktop that my friends would be the sh*t.
Help a noobie dreamer out. Even if I have to switch window manager I'd be willing to do it.

---

### Post by poofyhairguy on 2005-11-24
[QUOTE=Mr_J_]
If I want to get the monitor stretching across the 2 monitors. How would I do it?
[/QUOTE]

Use the Xorg.conf I provide with in this thread:

[http://ubuntuforums.org/showthread.php?t=75527&highlight=xcompmgr](http://ubuntuforums.org/showthread.php?t=75527&highlight=xcompmgr)

---

### Post by poofyhairguy on 2005-11-24
[QUOTE=Mr_J_]
Maybe I should just read up on Xorg.conf to understand all this.
Got any good starting spots?[/QUOTE]

Search the Gentoo Wiki.

> Wonder if I can have the two monitors and diferent resolutions in each.

Yes you can. But you can't have them act as one desktop (aka be able to drag applications from one monitor to the next).

> 
What I really wanted was two independent monitors. Maybe using a key shortcut to switch between the two. I wanted them to show independent images in the two monitors. Now that would be a leg up on the OS business.
If anyone knows any way to do this please point it out to me, because that was my first intention to begin with.
Even If I have to login as if a diferent user in both, but I really wanted to have two independent monitors using the same login and desktops.

Ok. Tehre are two ways to do with with Nvidia:

1. Monitors of the same resolution act as if they are one desktop- desktop spanning. This is what I use - I like to drag applications from one monitor to the other.

2. Monitors of the same or different resolutions acting as their own desktop- almost as if each is its own computer. I think this is less useful, but its the only way to use two monitors with different resolutions at the same time.

---

### Post by qalimas on 2005-11-24
I got the spanning to work, but it's not exactly what I'm looking for.  what I want is to be able to maximize an app, but it only take up the monitor it's on, but still be able todrag other apps.  Also, the idea of my desktop image streching to over 3000 pixels long is horrid, it looks incredibly disorted :P

---

### Post by Mr_J_ on 2005-11-25
[http://pastebin.com/437760](http://pastebin.com/437760)

This is my Xorg.conf

I have gotten the two monitors to load in metacity, but as soon as I loggin the second monitor goes away.
[http://members.fortunecity.com/plastik3/15to21.htm#15%22](http://members.fortunecity.com/plastik3/15to21.htm#15%22)
My monitor is the SRC1502.
It's old 15'' monitor I had laying around doing nothing.

I'm not asking you to do it for me, but could you make sure I'm not reading this wrongly.

My second monitor can stand 1280x1024 right?
It's one of the resolutions it's suposed to support.

I have a couple more places I have to read yet, but the Gentoo seemed to be going all right.
Some quirks need to be worked out, but I believe my card supports accelaration. I'm not sure about GLXwithComposite tho.

I haven't any sure idea on this yet, but I'm starting to think my 2nd monitor won't support the same things as my 1st one. Namely resolutions and the such. One thing I noticed is my 1st monitor as DPMS whatever that is.

This was just a trial to one day later get 2 monitors working that are actually work well.
My 1st monitor is all around grey...ish and my 2nd is all around yellow...ish.
Which is laughable considering the second monitor was supposed to be good. In second hand, but good. But for 25&#8364; what do you want?

---

### Post by Vlammend on 2005-11-28
[QUOTE=sfink01]I've created a HOWTO on TwinView for Ubuntu Breezy and it can be found at
[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)
it should work for Hoary also but hasn't been tested as of yet.

Enjoy![/QUOTE]

I used the howto, thanks!!

But I still got two questions:
Can you please also explain the line:
```
Screen 0 "Default Screen" 0 0
```

Personally I am think about using two workplaces, one at each monitor. If I want to try this, how could I accomplish that?

---

### Post by sfink01 on 2005-12-10
[QUOTE=Vlammend]I used the howto, thanks!!

But I still got two questions:
Can you please also explain the line:
```
Screen 0 "Default Screen" 0 0
```

Personally I am think about using two workplaces, one at each monitor. If I want to try this, how could I accomplish that?[/QUOTE]


The line:
```
Screen 0 "Default Screen" 0 0
```

is part of the ServerLayout section.  Let's break it down like this:
```
Screen 0 "Default Screen"
```
refers back to the
```

Section "Screen"
Identifier "Default Screen"

```
then the ```
0 0
``` section refers to the orientation of the screen
coordinates,  this case being the upper left most corner to begin.

To read more on this visit the X.org Wiki at:

[http://wiki.x.org/X11R6.8.2/doc/DESIGN2.html](http://wiki.x.org/X11R6.8.2/doc/DESIGN2.html)

Best,

Steve

---

### Post by sfink01 on 2006-01-09
This HowTo has now been tested in Hoary.  It works there too.

Steve

---

### Post by slagermvd on 2006-01-10
[QUOTE=sfink01]The line:
```
Screen 0 "Default Screen" 0 0
```

is part of the ServerLayout section.  Let's break it down like this:
```
Screen 0 "Default Screen"
```
refers back to the
```

Section "Screen"
Identifier "Default Screen"

```
then the ```
0 0
``` section refers to the orientation of the screen
coordinates,  this case being the upper left most corner to begin.

To read more on this visit the X.org Wiki at:

[http://wiki.x.org/X11R6.8.2/doc/DESIGN2.html](http://wiki.x.org/X11R6.8.2/doc/DESIGN2.html)

Best,

Steve[/QUOTE]

First of all, thanx for the howto.. 

I still don't understand the configuration for the default display. Twinview is working fine right now, but my default screen is the external connected monitor on my laptop. I'd like to have my laptop screen as primary display.

Can you give an example how to configure this, and also make gdm use this default display?

Regards Michael

---

### Post by sfink01 on 2006-01-30
Sorry for the delayed response.

Please post your xorg.conf file and I'll take a look.

Best,

Steve

---

### Post by Pausanias on 2006-02-14
Hi Steve

Thanks for the HOWTO. I got it to work, mostly. Then only problem I am having is that I cannot get both monitors to display the same screen. This is on a laptop with Quadro card (Dell Precision M70).

Basically, if the second monitor is attached X will appear there, but nothing will appear on my laptop LCD. If the second monitor is detached, then after restarting X will appear on my laptop screen. Also, if the second monitor (a CRT) is attached, and I set "ConnectedMonitor" to "dfp,dfp", then X will appear only on my laptop screen, and not on the second monitor.

Any advice on how I could get the same screen to display on both monitors (for presentations?)

---

### Post by Pausanias on 2006-02-14
Oh yeah, here's my xorg.conf.

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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
 Option        "LeftEdge"      "1700"
  Option        "RightEdge"     "5300"
  Option        "TopEdge"       "1700"
  Option        "BottomEdge"    "4200"
  Option        "FingerLow"     "25"
  Option        "FingerHigh"    "30"
  Option        "MaxTapTime"    "180"
  Option        "MaxTapMove"    "220"
  Option        "VertScrollDelta" "100"
  Option        "MinSpeed"      "0.09"
  Option        "MaxSpeed"      "0.18"
  Option        "AccelFactor"   "0.0015"
  Option        "SHMConfig"     "on"

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
#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#        Option          "SendCoreEvents"        "true"
#        Option          "Device"                "/dev/psaux"
#        Option          "Protocol"              "auto-dev"
#        Option		"HorizScrollDelta"	"0"
#EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV41GL [Quadro FX Go 1400]"
	Driver		"nvidia"
        Option          "NoLogo"
        Option          "NvAGP"   "2"
        Option          "Coolbits" "1"
#        Option          "ConnectedMonitor" "dfp,dfp"
        Option          "NoPowerConnectorCheck"
        Option          "TwinView" "1"
        Option          "MetaModes" "1680x1050,1024x768; 1024x768,1024x768; 1680x1050,NULL; 1024x768,1680x1050"
#        Option          "Xinerama" "Off"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41GL [Quadro FX Go 1400]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
                ViewPort        0 0
		Modes		"1680x1050 1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
                ViewPort        0 0
		Modes		"1680x1050 1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
                ViewPort        0 0
		Modes		"1680x1050 1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
                ViewPort        0 0
		Modes		"1680x1050 1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
                ViewPort        0 0
		Modes		"1680x1050 1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
                ViewPort        0 0
		Modes		"1680x1050 1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad" "CorePointer"
        Option          "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by sfink01 on 2006-02-14
Pausanias,

For the line Option "ConnectedMonitor" "dfp, dfp"

Most Laptops will have to allow TwinView to probe what monitors are attached so leave that line out.

All mobile NVIDIA chips support TwinView. TwinView on a laptop can be configured in the same way as on a desktop machine, only that in a TwinView configuration using the laptop's internal flat panel and an external CRT, the CRT is the primary display device (specify its HorizSync and VertRefresh in the Monitor section of your X config file) and the flat panel is the secondary display device (specify its HorizSync and VertRefresh through the SecondMonitorHorizSync and SecondMonitorVertRefresh options).

TwinView doesn't support monitors with different resolutions so choose a resolution for your dual config that both monitors support in the line

Option "Metamodes" 

you will need to put something like this...

Option "Metamodes" "NULL,1680x1050; 1024x768,1024x768; 1024x768,NULL"

This way you can start without the external monitor disconnected ( NULL,1680x1050 ) or run with both (1024x768,1024x768 ) or external monitor only ( 1024x768,NULL).

Then the last but not least...  Add this line:

Option "TwinViewOrientation" "Clone"

This will allow both of the monitors to display exactly the same thing.

Hope this helps.

Best,

Steve

---

### Post by kenito443 on 2006-02-15
hi steve great howto, i was about to use it but some how it worked by just installing the new drivers...i didn't need to augment the xorg.conf file at all...my question is should i add any of the options you mentioned in the how to? here is my xorg.conf
(i have a bfg 6600gtOC pci-e and athlon 3200+ venice)

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Dec 14 16:39:22 PST 2005

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

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "L90D+ DVI"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "L90D+ DVI"
    DefaultDepth    24
    Option         "TwinView" "on"
    Option         "MetaModes" "1280x1024,1280x1024"
    Option         "DPMS"
    Option         "TwinViewOrientation" "RightOf"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

THANKS IN ADVANCE

---

### Post by sfink01 on 2006-02-15
Kenito,

Everything will work just how it is but, if you want to play some GL games or something, you might need to add some more meta modes to handle the requested resolutions for example:

Option "MetaModes" "1024x768,1024x768; 1024x768,NULL"

This will allow the game to turn off the second monitor while you're playing.

There are numerous other tweaks you can try.

Best,

Steve

---

### Post by kenito443 on 2006-02-15
thank you very much steve, i appreciate the quick response, i'll go ahead and add that option- one more quick question
Besides the option above and the ones in your how to guide..where i can find more of the aforementioned "tweaks" you are referring to.

---

### Post by Parkotron on 2006-02-16
[QUOTE=Mr_J_]Wonder if I can have the two monitors and diferent resolutions in each.[/QUOTE]
[QUOTE=poofyhairguy]Yes you can. But you can't have them act as one desktop (aka be able to drag applications from one monitor to the next).[/QUOTE]

That just plain isn't true. With TwinView you can use any available resolution on either monitor. As proof: [http://www.ubuntuforums.org/gallery/showimage.php?i=1973&original=1&c=13](http://www.ubuntuforums.org/gallery/showimage.php?i=1973&original=1&c=13)

I recently rescued a 15" monitor from the trash and hooked it up to see how well Linux supports multiple monitors. I quickly learned that with an nVidia card, setting up multiple monitors is a breeze. 

I was running my 17" primary monitor at 1280x960. After playing with some different configurations, I decided to set the 15" at 1024x768. (The meta mode being 1280x960,1024x768) This combination results in a roughly equivalent DPI for the two monitors, so fonts, icons etc. display at appoximately the same size on each, so nothing gets bigger or smaller when moved from one monitor to the other.

If two different resolutions are being used, the TwinView default is to have the top edge of the monitors line up, like so:
```

|-----------------|-------------|           |-----------------|
|                 |             |           |                 |
|                 |     15"     |           |                 |
|       17"       |  1024x768   |           |       17"       |-------------|
|    1280x960     |-------------|           |    1280x960     |             |
|                 |                         |                 |     15"     |
|                 |                         |                 |  1024x768   |
|-----------------|                         |-----------------|-------------|

          The default                               My preferred setup
```
I didn't much care for this, as I wanted my bottoms panels to line up with one another. So instead of letting TwinView position the screens automatically I specified the position of the second monitor manually by changing the metamode to 1280x960,1024x768+1280+192 .

The 15" monitor doesn't get a whole lot of use. Most of the time I just use it for amaroK and Konsoles, but if I'm doing homework or need to reference a webpage while writing something the increase in productivity is considerable. It's amazing how much faster you can work if you're not constantly clicking on the taskbar or alt+tabbing between applications.

---

### Post by Kasuko on 2006-02-19
This is my xorg.conf Im quite new to linux in itself and I was reading the nvidia README and this is what I got. It doesnt work. I have a really old Magitronic Monitor. I also couldnt load the how-to thats why it seems like I didnt go through it.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Dec 14 16:39:22 PST 2005

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

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "SAMSUNG"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
    Option "TwinView"
    Option "ConnectedMonitor"         "CRT-0, CRT-1"
    Option "MetaModes"                "1280x1024, 1024x768 @1024x1024; 1280x1014, NULL"
    Option "UseEdidFreqs" "boolean"
    #Option "SecondMonitorHorizSync"   "<hsync range(s)>"
    #Option "SecondMonitorVertRefresh" "<vrefresh range(s)>"
    Option "TwinViewOrientation"      "CRT-0 LeftOf CRT-1"


EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "SAMSUNG"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


```

---

### Post by Pausanias on 2006-02-19
Hi Steve,

Thanks very much---it worked! I did everything as you said and I was able to have a cloned display on my laptop and on the projector.

A couple of points that might help another user:

[list]
[*] I found that the default resolution was ultimately governed by GNOME, not by the order in which I listed my metamodes. When I plugged in the second monitor, GNOME recognized the valid states in the Preferences->Screen Resolutions dialog. I was able to move from 1680x1050 to 1024x768 and then the second monitor came up. When I rebooted, on bootup GNOME remembered the previously saved resolution and brought it up, even though no second monitor was connected.

[*] If you are making a presentation using Adobe Acrobat Reader, **and** you have a widescreen laptop monitor, then when you switch from your widescreen resolution to a non-widescreen one (1024x768 or whatever), Acrobat will by default attempt to correct for the "stretch" in the pixels. This has the result that your presentation will appear horizontally "squashed" on the projector! To correct this, go to the "Page Display" options in the Acrobat preferences, and manually set a DPI rather than having it read the system-default ones. This caused the presentation to display properly.
[/list]

Many thanks again,

P

[QUOTE=sfink01]Pausanias,

For the line Option "ConnectedMonitor" "dfp, dfp"

Most Laptops will have to allow TwinView to probe what monitors are attached so leave that line out.

All mobile NVIDIA chips support TwinView. TwinView on a laptop can be configured in the same way as on a desktop machine, only that in a TwinView configuration using the laptop's internal flat panel and an external CRT, the CRT is the primary display device (specify its HorizSync and VertRefresh in the Monitor section of your X config file) and the flat panel is the secondary display device (specify its HorizSync and VertRefresh through the SecondMonitorHorizSync and SecondMonitorVertRefresh options).

TwinView doesn't support monitors with different resolutions so choose a resolution for your dual config that both monitors support in the line

Option "Metamodes" 

you will need to put something like this...

Option "Metamodes" "NULL,1680x1050; 1024x768,1024x768; 1024x768,NULL"

This way you can start without the external monitor disconnected ( NULL,1680x1050 ) or run with both (1024x768,1024x768 ) or external monitor only ( 1024x768,NULL).

Then the last but not least...  Add this line:

Option "TwinViewOrientation" "Clone"

This will allow both of the monitors to display exactly the same thing.

Hope this helps.

Best,

Steve[/QUOTE]

---

### Post by muted on 2006-02-20
Allright so i have a question...

I have 2 monitors: 
1. IBM E74
2. Phillips 107T20

Now, when setting the vertical and horizontal scanning frequency (30 - 71, 50 - 160 on the Phillips and 30 - 69 Hz, 50 - 120 kHz for the IBM)... which should i write down?

I meanm shouldnt there be.... dunno... 2 setups, 1 for each screen?


xorg.conf:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
#	Load	"dri"
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

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"NoLogo"
#	Option		"NvAGP" "2"
	Option 		"RenderAccel" "0"
	Option 		"CursorShadow" "1"
	Option 		"Coolbits" "1"
	Option 		"ConnectedMonitor" "dfp, dfp"
	Option 		"NoPowerConnectorCheck"
	Option 		"TwinView" "1"
	Option 		"Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
	Option 		"SecondMonitorHorizSync" "31-82"
	Option 		"SecondMonitorVertRefresh" "56-76"
	# Option 	"NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"IBM E74"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"IBM E74"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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


---

### Post by Blind-Summit on 2006-02-24
I found this on some random Linspire page

 	Option "TwinView"
 	Option "MetaModes" "1280x1024,1600x1200"
 	Option "TwinViewOrientation" "LeftOf"

Just enter that in the device section for your card. This setting is for my dual view with a 21" on the left and a 17" on the right. Ubuntu normally opened on the 17". I had been looking for a fix for ages and this did the trick.

My conf file has this now:

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
 	Option "TwinView"
 	Option "MetaModes" "1280x1024,1600x1200"
 	Option "TwinViewOrientation" "LeftOf"
EndSection

---

### Post by Kratos on 2006-03-01
Good HOW-TO, but I have a question.

I have a nVidia GeForce 6200 card, and it has two heads on it: One CRT and the other DVI. I am using two CRT monitors with one connected via a CRT/DVI adapter dongle. So, in the .conf, do I put...

```
 Option "Connected Monitor" "crt, dfp"


```

...Or something different all together? I've tried running the .conf the way it's listed, with some obvious changes, but it tends to just not work. :confused: 

Help would be awesome.

Kratos

---

### Post by Parkotron on 2006-03-02
[QUOTE=Kratos]...it has two heads on it: One CRT and the other DVI. I am using two CRT monitors with one connected via a CRT/DVI adapter dongle.[/QUOTE]

I think your terminology is a little bit confused. You're video card has two outputs: one VGA and one DVI. This is a completely separate issue from the two common types of monitors: CRT and DFP. In general CRTs use VGA and DFPs use DVI, but you can buy CRTs with DVI and DFPs with VGA. 

xorg.conf is concerned with the type of monitor, not the connection used. So in your case you want:
```
Option "Connected Monitor" "crt, crt"
```
Hope that helps.

---

### Post by Kratos on 2006-03-02
[QUOTE=Parkotron]I think your terminology is a little bit confused. You're video card has two outputs: one VGA and one DVI. This is a completely separate issue from the two common types of monitors: CRT and DFP. In general CRTs use VGA and DFPs use DVI, but you can buy CRTs with DVI and DFPs with VGA. 

xorg.conf is concerned with the type of monitor, not the connection used. So in your case you want:
```
Option "Connected Monitor" "crt, crt"
```
Hope that helps.[/QUOTE]
Ohhhh.... I get it, now. :D

Thanks a lot!

---

### Post by isTHEr3mOr3 on 2006-03-03
It's driving me nuts! :cry: 

I would like to have twinview (TV-out) with my NVIDIA Geforce 2 MX400 graphics card. I think the xorg.conf below should work, but xserver crashes always with an error. When I change Option "ConnectedMonitor" "CTR, TV" to Option "ConnectedMonitor" "CTR, CRT" it doesn't crash but I have no TV. 
Works with Windows and sort of works with nvtv. 

(Error message: (WW) NVIDIA: More than on matching device section for instances (BUS ID: PCI:1:0:0) found : NVIDIA MX 400 (EE) Screen(s) found but none have a usable configuration.)

Please help... 



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
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option "TVStandard" "PAL-B"
        Option "TVOutFormat" "SVIDEO"
EndSection

Section "Monitor"
	Identifier	"Belinea10153"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Belinea10153"
	DefaultDepth	24
        Option "TwinView " "on"
        Option "TwinViewOrientation" "Clone"
        Option "MetaModes" "1024x768,NULL;800x600,NULL;640x480,640x480"
        Option "SecondMonitorHorizSync" "30-50"
        Option "SecondMonitorVertRefresh" "60-60"
	Option "ConnectedMonitor" "CTR, TV"
	Option "NoRenderAccel" "1"
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
	Option "Clone" "off"		
	Option "Xinerama" "off"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by bjk525 on 2006-03-05
I have my Twinview setup working but I can not figure out how to change my default display. I am running a 19" LCD and a 17" CRT. I want the primary display to be the LCD but gdm loads on the CRT. Is there any way to fix this?

---

### Post by isTHEr3mOr3 on 2006-03-05
The solution was installing the latest driver ( 1.0-8178 ) 

There is a how-to on the forum I followed to install it.

---

### Post by patsissons on 2006-03-05
Just went through the tutorial tonight, nice job man!  Everything works quite well, I only have one small issue which isn't that troubling.  My setup consists of a 17 and a 19 inch monitor.  Before using the twinview, I was just using a dual head setup, but I decided tonight that I wouldn't mind being able to move windows from one screen to the other.  So I ended up with a 1280x1024 (S), 1600x1200 (P) type setup.  Like I said, everything seems to work fine (YaKuake looks a little odd when its run on the monitor without the kde panel), the only issue is that some applications get confused with the different resolutions and think that there is available space below my 1280x1024 monitor.  fortunately, the issue is hardly ever made noticeable so I can live with it until a fix is made available.

---

### Post by t3h_mounty on 2006-03-09
Hi, I've been trying without any real success for quite a while now to get twinview to work, and it really isn't working :(.
I have the latest nvidia drivers and still nothing.

this is my xorg.conf file

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
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
	Driver		"nv"
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
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
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

my other monitor's settings are 
HF: 30-70
VF: 50-120

any help would be greatly appreciated.

---

### Post by Ninnghizidha on 2006-03-09
Hello!

I got a problem, and i think it is twinview-related:

I'm using KDE with nvidia-twinview. Works great, but all my movies seem to be 32:9 instead of 16:9 - they display way to wide! I didn't found a switch to disable this behavior. May someone help me out? :???: 

Ninn;

---

### Post by sfink01 on 2006-03-09
[QUOTE=t3h_mounty]Hi, I've been trying without any real success for quite a while now to get twinview to work, and it really isn't working :(.
I have the latest nvidia drivers and still nothing.

this is my xorg.conf file

[snipped]

my other monitor's settings are 
HF: 30-70
VF: 50-120

any help would be greatly appreciated.[/QUOTE]

t3h_mounty

There doesn't seem to be anything about TwinView in your xorg.conf at all.

Please follow the HowTo at [http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html) and you should be fine.

RePost if you have any problems.

Best,

Steve

---

### Post by sfink01 on 2006-03-09
[QUOTE=isTHEr3mOr3]It's driving me nuts! :cry: 

I would like to have twinview (TV-out) with my NVIDIA Geforce 2 MX400 graphics card. I think the xorg.conf below should work, but xserver crashes always with an error. When I change Option "ConnectedMonitor" "CTR, TV" to Option "ConnectedMonitor" "CTR, CRT" it doesn't crash but I have no TV. 
Works with Windows and sort of works with nvtv. 

(Error message: (WW) NVIDIA: More than on matching device section for instances (BUS ID: PCI:1:0:0) found : NVIDIA MX 400 (EE) Screen(s) found but none have a usable configuration.)

Please help... 



[snipped]

	Option "ConnectedMonitor" "CTR, TV"

[snipped]

EndSection[/QUOTE]


This line should read:

     Option "ConnectedMonitor" "CRT, TV"

Hope this helps.

Best,

Steve

---

### Post by t3h_mounty on 2006-03-09
Hi Steve

I went back to my default xorg.conf file before posting because I figured I had probably changed some stuff that didn't need changing and didn't want to make things worse for whoever tired to fix my xorg file.

and for some reason, that link doesn't work for me. I've heard many a good thing about the howto, but for some reason ublog always times out.

---

### Post by niC666 on 2006-03-10
Hi..

I'm running breezy on an amd64 arch, I have followed the instructions on the howto posted above and everything seems to be peachy up to and including my GDM login screen. I get the expected display and can move my mouse cursor through time and space from the edge of one display to the other.. how exciting. however once i log in and my desktop starts up (gnome) i lose the second display, its goes blank with flashing power led. also i can 'feel' the edge of my primary display when i move the cursor there.. there is a 'wall' my cursor can no longer pass.. its not like i've just lost the display of the 'second' desktop.. it doesnt appear to be there at all..

any ideas on how to get this working? unfortunately my desktop manager doesnt seem to know anything about the new configuration.. change screen resolution options dont acknowledege the new setup..

tia
niC

---

### Post by niC666 on 2006-03-10
[QUOTE=niC666]Hi..

I'm running breezy on an amd64 arch, I have followed the instructions on the howto posted above and everything seems to be peachy up to and including my GDM login screen. I get the expected display and can move my mouse cursor through time and space from the edge of one display to the other.. how exciting. however once i log in and my desktop starts up (gnome) i lose the second display...
niC[/QUOTE]

Apologies for replying to my own post, but just in case anyone else has the same problem..

I removed "1280x1024,NULL; 1024x768,NULL" from the line
Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"

in xorg.conf and it works fine now.

niC

---

### Post by sfink01 on 2006-03-10
[QUOTE=niC666]Apologies for replying to my own post, but just in case anyone else has the same problem..

I removed "1280x1024,NULL; 1024x768,NULL" from the line
Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"

in xorg.conf and it works fine now.

niC[/QUOTE]

Nic,

After booting with the Metamodes line still in tact you should have been able to go to System ---> Preferences ---> Screen Resolution and had several options to choose from and select 2560x1024 or 2048x768.

Glad it works somehow...

Best,

Steve

---

### Post by niC666 on 2006-03-10
aaaaah.. i see.

Those modes were available but it didnt put 2 and 2 together.. just thought they were some weird stuff as i've never heard of them before (d'oh). after removing the null lines those two resolutions were the only ones available and obviously the desktop manager just picked one and i saw my other screen.

all makes sense now.

Thanks for that.

niC

---

### Post by m0o0oeh on 2006-03-21
hey guys.

I am a complete n00b at Linux and I want to get my duals working.

Can you guys  give me a nice and easy way to get duals to work.

Joe

---

### Post by sfink01 on 2006-03-21
[QUOTE=m0o0oeh]hey guys.

I am a complete n00b at Linux and I want to get my duals working.

Can you guys  give me a nice and easy way to get duals to work.

Joe[/QUOTE]

Joe,

Did you follow the HowTo?

It's at [http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html)

It should get you through.

Best,

Steve

---

### Post by kayas80 on 2006-03-21
[quote=m0o0oeh]hey guys.

I am a complete n00b at Linux and I want to get my duals working.

Can you guys  give me a nice and easy way to get duals to work.

Joe[/quote]

If you have a Nvidia graphics card you could follow the guide in this Wiki.

[https://wiki.ubuntu.com/NvidiaTVOut](https://wiki.ubuntu.com/NvidiaTVOut)

---

### Post by petok on 2006-03-22
Hi,

I have a Geforce 6600 GT with one vga and one dvi output. The dvi output is connected through a vga-dvi connector to my vga monitor. The vga is connected to a vga monitor. I cannot use the 'nvidia' drivers but I can use the 'nv' drivers. Do I need the nvidia drivers for twinview? And why can't I use them? My second screen now only displays 'input not supported'.
Also I editted the "monitor" to "AL1711" because X gave an error it couldn't find "monitor".

---

### Post by sfink01 on 2006-03-22
[QUOTE=petok]Hi,

I have a Geforce 6600 GT with one vga and one dvi output. The dvi output is connected through a vga-dvi connector to my vga monitor. The vga is connected to a vga monitor. I cannot use the 'nvidia' drivers but I can use the 'nv' drivers. Do I need the nvidia drivers for twinview? And why can't I use them? My second screen now only displays 'input not supported'.
Also I editted the "monitor" to "AL1711" because X gave an error it couldn't find "monitor".[/QUOTE]

Petok,

Yes the Nvidia drivers are required.

Generally when you get a message like "Input Not Supported" it's because you've exceeded the monitors capability.

Double check the specifications for your monitor that gives you the message and ensure those specifications are correct in your xorg.conf

Best,

Steve

---

### Post by petok on 2006-03-23
How come when i change my drivers to 'nvidia' instead of 'nv' xorg wont run anymore? I think I installed latest drivers...

---

### Post by sfink01 on 2006-03-23
[QUOTE=petok]How come when i change my drivers to 'nvidia' instead of 'nv' xorg wont run anymore? I think I installed latest drivers...[/QUOTE]

You can check using info from this post [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) 

If you have the drivers installed properly post your /var/log/Xorg.0.log and I'll check it out.

Best,

Steve

---

### Post by CornMaster on 2006-03-25
I thought I would add my experiences to this thread.  When I tried to use the How To provided...both of my monitors died and wouldn't start up.  Maybe because I had the freq wrong for my second monitor...but I'm not sure.

I then went to the Nvidia site and looked at their directions.  I figured that my second monitor (Daewoo 777D) was too old to be detected automatically (it wasn't listed in my Nvidia settings).

So...I plopped these settings under device:
```
        Option "TwinView"
        Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL"
        Option "SecondMonitorHorizSync"   "30-70"
        Option "SecondMonitorVertRefresh" "50-150"
        Option "ConnectedMonitor" "CRT, CRT"

```
To force my second monitor and configue the settings...I also added a section for my second monitor:
```

Section "Monitor"
        Identifier      "777D"
#        Option          "DPMS"
        HorizSync    30 - 70
        VertRefresh  50 - 150
EndSection

``` (I'm not sure what DPMS stands for, so I figured I would disable it)

I also deleted all of the other video modes that I knew I would probably never use from my default screen.

But at this point it still didn't work...X would start, but my second monitor was off still....so I went into the Screen Resolution changer, and I was able to select 2560x1024 and THEN the monitor finally came on.

I do have some questions though...I'm not sure how much of what I did is necessary.  I'll post my file, and if anyone has any suggestions for tweaks, let me know.

Also, only 75Hz is available for my refresh rate.  Before I had from 60-100..can anyone tell me what influences that?

Thanks

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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "TwinView"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL"
	Option "SecondMonitorHorizSync"   "30-70"
	Option "SecondMonitorVertRefresh" "50-150"
	Option "ConnectedMonitor" "CRT, CRT"
EndSection

Section "Monitor"
	Identifier	"A91f+"
	Option		"DPMS"
EndSection

Section "Monitor"
        Identifier      "777D"
#        Option          "DPMS"
	HorizSync    30 - 70
	VertRefresh  50 - 150
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A91f+"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
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

### Post by sfink01 on 2006-03-26
[QUOTE=CornMaster]I thought I would add my experiences to this thread.  When I tried to use the How To provided...both of my monitors died and wouldn't start up.  Maybe because I had the freq wrong for my second monitor...but I'm not sure.

I then went to the Nvidia site and looked at their directions.  I figured that my second monitor (Daewoo 777D) was too old to be detected automatically (it wasn't listed in my Nvidia settings).

So...I plopped these settings under device:
Snipped[/QUOTE]

It is **vitally** important to have the correct settings for your monitors if you use settings too high for your monitor to display most turn off, as you've experienced. Some do not and it can physically damage the monitor.

As you found out your Daewoo 777d is:

Frequency (H): 30 - 70 KHz
Frequency (V): 50 - 150 Hz
Max. Resolution: 1280 x 1024
640 x 480 @ 150 Hz
800 x 600 @ 110 Hz
1024 x 768 @ 90 Hz
1280 x 1024 @ 65 Hz

Your Viewsonic A91F+ is:

Frequency (H): 30 - 86kHz
Frequency (V): 50 - 180Hz
Max. Resolution: 1792x1344

This means that X is going to have to utilize the lowest common denominator to build a screen.

Remove the section:

Section "Monitor"
        Identifier      "777D"
#        Option          "DPMS"
	HorizSync    30 - 70
	VertRefresh  50 - 150
EndSection

And change the section:

Section "Monitor"
	Identifier	"A91f+"
	Option		"DPMS"
EndSection

To:

Section "Monitor"
	Identifier	"A91f+"
	Option		"DPMS"
      HorizSync   30 - 86
      VertRefresh 50 - 180
EndSection

This will not change anything noticable to you but to X it's a big difference.  DPMS is a power managment function to put the screen to sleep.  Both of your monitors support DPMS.

Best,

Steve

---

### Post by Bazon on 2006-03-27
You **don't need to edit xorg.conf in order to get clone mode on TV**!

See [this thread.](http://ubuntuforums.org/showthread.php?t=114425)

Greetings,
Bazon

---

### Post by ... on 2006-04-23
Has anyone figured out how to to change the default display?
I have a 19" lcd connectod through a dvi->vga connector going to the lcd, and a 15" crt connected to the other vga port on the back of the card (geforce 440mx).  Everything seems to work, but the primary desktop (the one with the login screen and all of the menus) is on the crt instead of the crt...

I tried putting in the 
option "twinvieworientation" "leftof", but that just made it so that you could drag windows from the primary off to the left instead of the right...
I also tried changing the 
Screen 0 "Default Screen" 0 0
to
Screen 1 "Default Screen" 0 0
but that just made it so that I lost the lcd completly after I login :-/

here is my xorg.conf...
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, 
using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual 
page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades 
*only*
# if it has not been modified since the last upgrade of the 
xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically 
updated
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

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
 VendorName "Videocard vendor"
 BoardName "NVIDIA GeForce 4 MX"
	BusID		"PCI:1:0:0"
 Option "NvAGP" "2"
Option "NoLogo" "1"
#Option "RenderAccel" "0"
Option "CursorShadow" "1"
#Option "Coolbits" "1"
#Option "ConnectedMonitor" "dfp, dfp"
Option "NoPowerConnectorCheck"
Option "TwinView" "1"
Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 
1280x1024,NULL; 1024x768,NULL"
Option "SecondMonitorHorizSync" "29-82"
Option "SecondMonitorVertRefresh" "50-150"
# Option "NoTwinViewXineramaInfo"
Option "TwinViewOrientation" "LeftOf"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
 Viewport 0 0
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
 Viewport 0 0
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
 Viewport 0 0
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
 Viewport 0 0
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
 Viewport 0 0
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
 Viewport 0 0
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
 Screen 0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by sfink01 on 2006-04-23
[QUOTE=...]Has anyone figured out how to to change the default display?
I have a 19" lcd connectod through a dvi->vga connector going to the lcd, and a 15" crt connected to the other vga port on the back of the card (geforce 440mx).  Everything seems to work, but the primary desktop (the one with the login screen and all of the menus) is on the crt instead of the crt...
--snipped---
EndSection[/CODE][/QUOTE]

Sounds like you have both monitors attached via analog vga ports. Have you tried just switching the cables?

Best,

Steve

---

### Post by ... on 2006-04-23
I can't, the adapter that the lcd is connected is male on both ends (designed to connect directly to the monitor), while the crt has a hard wired cable...

---

### Post by Elmaco on 2006-04-30
First of all, excuse me for my poor language...

I can't get this twinview-thing to work. Feels like I have tried every "how-to" and xorg.conf example available on the net ;)

My graphic card: Nvidia Geforce FX 5200, 128mb

I have one TFT and one CRT. I wan't to use the TFT as primary.

TFT:
Samsung SyncMaster 940B '19
horizontal sync: 30-81KHz
vertical sync: 56-75Hz

CRT:
Samsung SyncMaster 957MB '19
horizontal sync: 30-96 kHz 
vertical sync: 50-160 Hz

I have installed the packages nvidia-glx and nvidia-settings. Do I need to get a new driver from Nvidia's homepage??? Some "how-to's" says this others don't. If this is the case, are there other packages that i need???

In fact I goot dual screen working once (at loginscreen, but that configuration is gone ;) ) when logged in only the crt appeard =(

This is how my xorg.conf looks like now (kind of basic setting because it doesn't give me two black screens :) ):

```

Section "Module"
	Load	"GLcore"
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
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

If someone could help me or even better someone who experienced the same problem would this be super!

Thanks in advance!!!

---

### Post by sfink01 on 2006-04-30
[QUOTE=Elmaco]First of all, excuse me for my poor language...

I can't get this twinview-thing to work. Feels like I have tried every "how-to" and xorg.conf example available on the net ;)

My graphic card: Nvidia Geforce FX 5200, 128mb

I have one TFT and one CRT. I wan't to use the TFT as primary.

TFT:
Samsung SyncMaster 940B '19
horizontal sync: 30-81KHz
vertical sync: 56-75Hz

CRT:
Samsung SyncMaster 957MB '19
horizontal sync: 30-96 kHz 
vertical sync: 50-160 Hz

I have installed the packages nvidia-glx and nvidia-settings. Do I need to get a new driver from Nvidia's homepage??? Some "how-to's" says this others don't. If this is the case, are there other packages that i need???

In fact I goot dual screen working once (at loginscreen, but that configuration is gone ;) ) when logged in only the crt appeard =(

--Snipped-- 

If someone could help me or even better someone who experienced the same problem would this be super!

Thanks in advance!!![/QUOTE]

Elmaco,

Your xorg.conf file seems to be missing the additional information to make TwinView work properly.

Example:

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
Driver "nvidia"
VendorName "Videocard vendor"
BoardName "NVIDIA GeForce 6600 GT"
BusID	"PCI:1:5:0"
Option	"NvAGP" "2"
Option	"NoLogo" "1"
Option	"RenderAccel" "0"
Option	"CursorShadow" "1"
Option	"Coolbits" "1"
Option "ConnectedMonitor" "dfp, dfp"
Option	"NoPowerConnectorCheck"
Option "TwinView" "1"
Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
Option "SecondMonitorHorizSync" "31-82"
Option "SecondMonitorVertRefresh" "56-76"
#	Option	"NoTwinViewXineramaInfo"
EndSection

Follow the HowTo at [http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html) this will take you through step-by-step how to edit your xorg.conf file to be successful.

If you still have problems post the output of /var/log/Xorg.0.log and we'll be able to help troubleshoot more.

Best,

Steve

---

### Post by Elmaco on 2006-04-30
> **sfink01]Elmaco,

Your xorg.conf file seems to be missing the additional information to make TwinView work properly.

Example:

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
Driver "nvidia"
VendorName "Videocard vendor"
BoardName "NVIDIA GeForce 6600 GT"
BusID	"PCI:1:5:0"
Option	"NvAGP" "2"
Option	"NoLogo" "1"
Option	"RenderAccel" "0"
Option	"CursorShadow" "1"
Option	"Coolbits" "1"
Option "ConnectedMonitor" "dfp, dfp"
Option	"NoPowerConnectorCheck"
Option "TwinView" "1"
Option "Metamodes" "1280x1024,1280x1024 said:**
> http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html[/url] this will take you through step-by-step how to edit your xorg.conf file to be successful.

If you still have problems post the output of /var/log/Xorg.0.log and we'll be able to help troubleshoot more.

Best,

Steve

Yeah, I wrote that the conf-file was "basic" ;)

Anyway, I tried that HowTo one more time and i finally got it to worked :D 

But I had to change a few things, this is my final xorg.conf:

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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	VendorName "Videocard vendor"
	BoardName "NVIDIA GeForce FX 5200"
	BusID		"PCI:1:0:0"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "ConnectedMonitor" "crt-0, dfp-1"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
 	[COLOR="Red"]Option "TwinViewOrientation" "LeftOf"[/COLOR] # My TFT stands to the left -> I'm using it as primary now :D
	[COLOR="Red"]Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; NULL,1280x1024; NULL,1024x768"[/COLOR] # Important to not set a screen in the first pair of resolution to null
	Option "SecondMonitorHorizSync" "30-65"
	Option "SecondMonitorVertRefresh" "50-75"
	# Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		[COLOR="Red"]Viewport 0 0[/COLOR] #Important to get it to work obviously
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
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

Section "ServerLayout"
I	dentifier "TwinView Configuration"
	Screen 0 "Default Screen" 0 0
	InputDevice "Configured Mouse"
I	nputDevice "Generic Keyboard"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

But the first time i run startx -> Only one screen (the CRT to the right)

I had read somewhere about someone who had to change the screenresolution. so I did -> to 2560x1024. And that's all.

SWEEEEET!!!

---

### Post by monomaniacpat on 2006-05-07
I followed the how-to to the letter. However, with the edited xorg file I cannot restart X successfully. Can you tell me what I'm doing wrong?

I am only trying to enable my computer to switch between monitors when ubuntu is loaded, as my laptop minces the image after switching using the FN. I can only switch during boot.

Here's my file:

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	VendorName	"Nvidia"
	BoardName "NVIDIA GeForce4 440 Go"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "ConnectedMonitor" "dfp, dfp"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
	Option "SecondMonitorHorizSync" "31-82"
	Option "SecondMonitorVertRefresh" "56-76"
	# Option "NoTwinViewXineramaInfo"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Hope you can help!

mono.

---

### Post by sfink01 on 2006-05-07
> **monomaniacpat]I followed the how-to to the letter. However, with the edited xorg file I cannot restart X successfully. Can you tell me what I'm doing wrong?

I am only trying to enable my computer to switch between monitors when ubuntu is loaded, as my laptop minces the image after switching using the FN. I can only switch during boot.

Here's my file:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
--snipped--

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	VendorName	"Nvidia"
	BoardName "NVIDIA GeForce4 440 Go"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "ConnectedMonitor" "dfp, dfp"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "1280x1024,1280x1024 said:**
> "
	Monitor		"Generic Monitor"
	DefaultDepth	24

--snipped--

	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Hope you can help!

mono.

monomaniacpat,

Laptops are a whole different animal...

All mobile NVIDIA chips support TwinView. TwinView on a laptop can be configured in the same way as on a desktop machine, only that in a TwinView configuration using the laptop's internal flat panel and an external CRT, the CRT is the primary display device (specify its HorizSync and VertRefresh in the Monitor section of your X config file) and the flat panel is the secondary display device (specify its HorizSync and VertRefresh through the SecondMonitorHorizSync and SecondMonitorVertRefresh options).

For the line Option "ConnectedMonitor" "dfp, dfp"

Most Laptops will have to allow TwinView to probe what monitors are attached so leave that line out.

Option "Metamodes"

you will need to put something like this...

Option "Metamodes" "NULL,1600x1200; 1024x768,1024x768; 1024x768,NULL"

This way you can start without the external monitor disconnected ( NULL,1600x1200 ) or run with both (1024x768,1024x768 ) or external monitor only ( 1024x768,NULL).  In order to change monitors you have to use CTRL+ALT+plus (on number pad) or CTRL+ALT+minus (on number pad) for most laptops you have to put the num lock on and use the fn key to get the correct + or - key.

I chose 1600x1200 as the resolution because that's what you have defined in the config file above in the display section. If that's not your preferred resolution make sure your meta modes and your display match.  You cannot have 1280x1024 in a meta mode and call 1600x1200 in the display section.

Then the last but not least... Add this line:

Option "TwinViewOrientation" "Clone"

This will allow both of the monitors to display exactly the same thing.

Hope this helps.

Best,

Steve

---

### Post by monomaniacpat on 2006-05-07
Thanks, I'll try that tomorrow. How do I know the horizsynch and vertrefresh? It doesn't work with those additions at the moment.

---

### Post by monomaniacpat on 2006-05-08
Here's my file as it stands now:

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	VendorName	"Nvidia"
	BoardName "NVIDIA GeForce4 440 Go"
	Option "TwinViewOrientation" "Clone"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "NULL,1600x1200; 1024x768,1024x768; 1024x768,NULL"
	Option "SecondMonitorHorizSync" "31-82"
	Option "SecondMonitorVertRefresh" "56-76"
	# Option "NoTwinViewXineramaInfo"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Pausanias on 2006-05-08
Just a heads-up on getting TwinView work on dapper. I had used this HOWTO to get it working on Breezy. I've just upgraded to dapper, and it seems that with the newer drivers, the order of recognition for laptop LCDs and external LCDs is switched. I.e., in Breezy, the laptop LCD came up as the "second monitor"; in dapper it's now the first monitor, as it should be :)

---

### Post by hjm on 2006-05-09
VERY helpful howto and thread - the best on the web as far as I can find.

Also running amd64 optx2, ASUS mb. XFX nvidia Geforce 6600GT 256MB PCI-e w/dual DVI ports into 2xSamsung 204b 1600x1200 LCD panels, nvidia drivers version 1.0-8756 on custom 2.6.16.5 SMP kernel on top of Dapper flight 6(?).  Everything working EXCEPT that twinview won't come up.

Using version 1.0-8756a of the Nvidia drivers, the driver compiled  and installed perfectly.   Both monitors show the bios screen and text during bootup, and using one port on the card, KDE comes up and works perfectly, but when I plug the other monitor into the other port, using 1 or 2 monitors, the screen goes blank when booting into graphics mode.  The other port works perfectly by itself, but when there are monitors connected to both ports, both monitors go blank when entering graphics mode and cannot be made to drop back to text mode.  Both monitors work perfectly when connected to the 'working' port. The 'working port' can be set to different resolutions and works the way it's supposed to and both monitors work identically when connected to it.

Both monitors display the same text thru bootup and in text mode.  It's only when starting X does the setup go irreveribly blank (killing X doesn't work, only a reboot brings it back).  

To save space, I'm running the xorg.conf file that was listed in the howto with the expection that I commented out these lines:
#       BusID       "PCI:1:5:0"
#       Option      "NvAGP" "2"

as my card is a PCI-e card and so the PCI address is different (and is found automatically and correctly)

Has anyone seen this behavior and is it a hardware problem or config? The XFX website is near-useless.  Even if it's not the card, I wouldn't rec it for the infinitestimal amount of technical info available and the uselessness of the website support.  <frustrated rant>They collect scads of personal info and then then after entering the support message, the submission page goes to neverland </frustrated rant>.

Much obiliged if you could ping via email as well as posting! [email]hjm@tacgi.com[/email]

---

### Post by sfink01 on 2006-05-09
[QUOTE=hjm]VERY helpful howto and thread - the best on the web as far as I can find.

Also running amd64 optx2, ASUS mb. XFX nvidia Geforce 6600GT 256MB PCI-e w/dual DVI ports into 2xSamsung 204b 1600x1200 LCD panels, nvidia drivers version 1.0-8756 on custom 2.6.16.5 SMP kernel on top of Dapper flight 6(?).  Everything working EXCEPT that twinview won't come up.

Using version 1.0-8756a of the Nvidia drivers, the driver compiled  and installed perfectly.   Both monitors show the bios screen and text during bootup, and using one port on the card, KDE comes up and works perfectly, but when I plug the other monitor into the other port, using 1 or 2 monitors, the screen goes blank when booting into graphics mode.  The other port works perfectly by itself, but when there are monitors connected to both ports, both monitors go blank when entering graphics mode and cannot be made to drop back to text mode.  Both monitors work perfectly when connected to the 'working' port. The 'working port' can be set to different resolutions and works the way it's supposed to and both monitors work identically when connected to it.

Both monitors display the same text thru bootup and in text mode.  It's only when starting X does the setup go irreveribly blank (killing X doesn't work, only a reboot brings it back).  

To save space, I'm running the xorg.conf file that was listed in the howto with the expection that I commented out these lines:
#       BusID       "PCI:1:5:0"
#       Option      "NvAGP" "2"

as my card is a PCI-e card and so the PCI address is different (and is found automatically and correctly)

Has anyone seen this behavior and is it a hardware problem or config? The XFX website is near-useless.  Even if it's not the card, I wouldn't rec it for the infinitestimal amount of technical info available and the uselessness of the website support.  <frustrated rant>They collect scads of personal info and then then after entering the support message, the submission page goes to neverland </frustrated rant>.

Much obiliged if you could ping via email as well as posting! [email]hjm@tacgi.com[/email][/QUOTE]

hjm,

Check the resolution setting in System --> Preferences --> Screen Resolution.
Choose one that is 3360x1050, 2560x1024 or 2048x768.

Post again if this doesn't help and include your Xorg.0.log we'll take a look.

Best,

Steve

---

### Post by sfink01 on 2006-05-09
> **monomaniacpat]Here's my file as it stands now:

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	VendorName	"Nvidia"
	BoardName "NVIDIA GeForce4 440 Go"
	Option "TwinViewOrientation" "Clone"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "NULL,1600x1200 said:**
> "
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

In this section:

SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1600x1200"
	EndSubSection

You need to add the display of 1024x768 or 1280x1024 so X can set the display, make sure that this section matches the Meta modes so to match the xorg.conf file above you would put.

SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1600x1200" "1024x768"
	EndSubSection

Make sure you use the Depth 24 section because that's the color depth you're calling above too.

I usually add the "1024x768" to all the color depths.

Later,

Steve

---

### Post by monomaniacpat on 2006-05-09
My xorg file now reads:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	VendorName	"Nvidia"
	BoardName "NVIDIA GeForce4 440 Go"
	Option "TwinViewOrientation" "Clone"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "NULL,1600x1200; 1024x768,1024x768; 1024x768,NULL"
	Option "SecondMonitorHorizSync" "28-80"
	Option "SecondMonitorVertRefresh" "43-60"
	# Option "NoTwinViewXineramaInfo"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

*snipped*

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1600x1200" "1024x768"
	EndSubSection
EndSection
```

It still doesn't work - what do I need to do?

Thanks!

---

### Post by ronzo on 2006-05-09
I still do not understand everything in xorg.conf. How can I configure Twinview for a 19"-TFT with a resolution of 1280x1024 and a 15"-CRT with a resolution of 800x600 (or maybe 1024x768)?

(in other words: How can I assign a fixed resolution to each monitor?)

OK. I found it out by myself. Here's the solution:

Simply edit the Option-Metamodes-Line in the Device-Section of xorg.conf to something like that:

Option      "Metamodes" "CRT-0: 800x600, DFP-0: 1280x1024"

That's it.

---

### Post by hjm on 2006-05-10
[QUOTE=sfink01]hjm,

Check the resolution setting in System --> Preferences --> Screen Resolution.
Choose one that is 3360x1050, 2560x1024 or 2048x768.

Best,

Steve[/QUOTE]

Thanks for your reply and my apologies for the delay in answering - I lost the list address and only found it again today.

What utility are you referring to above?  I'm running kubuntu / KDE and the closest thing I have to that is the "System Settings -> Display" control panel. Are you suggesting that I choose a resolution that equals a 2*1600x1200 display?

I used your latest xorg.conf file as a template and while it gives a spiffy 1 -screen image, it has the same problem as the I described earlier - either a beautiful single screen (when the 'bad' port is not connected or both screens irreversibly blanking when it's connect to the 2nd monitor.

I played around with changing the bios settings to see if that could possibly have an effect - ended up causing a 'failed VGA card error' that forced me to
switch the video card to the other PCI-e slot.  That fixed the VGA error, but also caused the xorg.conf file to be over-written on startup.  

This autoconfig'ed xorg.conf file used the **nv** driver not the **nvidia** driverand showed a 1280x1024 image on one screen and also a scrambled image on the other screen (but scrambled multicolored  text, the 1st time ANYTHING has shown up on  the second screen, so the card can obvously drive something out both ports simultaneously).  As noted above, I'm using the latest nvidia driver 1.0-8756.  Which driver version are you using?  Could it be a driver problem??

As noted above, the xorg file that gives me the best image so far is the one you posted and that I used verbatim, mod the PCI bus id and the AGP lines.

This really seems like a driver and or hardware problem.  I haven't tried the nv driver with straight xinerama, but I may have to.  Or back down to to an older nvidia driver.  Then again, I may just return the card for a different make.
Regardless, thanks very much for the input.

---

### Post by hjm on 2006-05-12
From the 'don't kjnow when to quit' dept, I borrowed a PCI-e 6800XT card to test whether the original 6600GT was working OK.  Both were XFX cards unfortunately, but the upshot is that both work very similarly.  I have found that the previously inexplicable blanking of both displays is due to the metamodes line.  When there is a NULL entry first  (ie Option "Metamodes" "1600x1200,NULL"), one monitor works fine by itself.  If I replace that with:
"Metamodes" "1600x1200,1600x1200; 1600x1200,NULL", both monitors blank and lock up.  It seems like there's something about driving both screen in graphics mode that locks them up (on both cards).  There was a warnign about older nvidia cards:
Q: Why can I not get a resolution of 1600x1200 on the second display
   device when using a GeForce2 MX?

A: Because the second display device on the GeForce2 MX was designed to
   be a digital flat panel, the Pixel Clock for the second display device
   is only 150 MHz.  This effectively limits the resolution on the second
   display device to somewhere around 1280x1024 (for a description of
   how Pixel Clock frequencies limit the programmable modes, see the
   XFree86 Video Timings HOWTO).  This constraint is not present on
   GeForce4 chips -- the maximum pixel clock is the same on both heads.

but this shouldn't be the case with my situation.

in the nvnews forum, I just discovered that there is an AMD64 issue with the XFX 6600gt's and possibly others in the series. 

[http://www.nvnews.net/vbulletin/showthread.php?t=68044&highlight=twinview+linux](http://www.nvnews.net/vbulletin/showthread.php?t=68044&highlight=twinview+linux)

The card goes back tomorrow.  Thanks for the help tho...

Harry

---

### Post by woot on 2006-05-12
Hey,

Im having problems with my dual head setup. Im on a dell inspiron laptop with a geforce4 mx card. The laptop screen is 1600x1200 and the 2nd screen is a nuovo f-417 flatscreen 1280x1024. When booting into win xp or ubuntu breezy 5.10 all is fine, whilst under ubuntu dapper drake my dual head setup works....almost

the laptop display is fine but the 2nd screen has 6 cm of just plain black unreachable area in the vertical axis. (i hope i make myself clear with this..) So i can drag and drop stuff from one screen to another but i loose quit some space on my screen....

i just used the same xorg.conf as i have under breezy and all should be fine...not i guess

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"TwinView"
	Option 		"MetaModes" "1280x1024,1600x1200; NULL,1600x1200"
       	Option          "SecondMonitorHorizSync" "28-80"
       	Option          "SecondMonitorVertRefresh" "43-60"
       	Option          "TwinViewOrientation" "LeftOf"   
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
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

```


hope someone can help me out...oh ofcourse, when picking screen resolution in the system menu i select 2880x1200 (which should be just fine)

---

### Post by sfink01 on 2006-05-12
[QUOTE=monomaniacpat]My xorg file now reads:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
--snipped--

1600x1200" "1024x768"
	EndSubSection
EndSection
```

It still doesn't work - what do I need to do?

Thanks![/QUOTE]

I believe your problem is your Horizontal and Vertical Sync.  Post your /var/log/Xorg.0.log.

Best,

Steve

---

### Post by monomaniacpat on 2006-05-12
Hopefully, you should find it attached.


Thanks for all the help.

---

### Post by sfink01 on 2006-05-13
[QUOTE=monomaniacpat]Hopefully, you should find it attached.


Thanks for all the help.[/QUOTE]

mono,

From the log file it looks like your connected monitor is: 

(II) NV(0): Serial No: 12DRY1BG008N
(II) NV(0): Monitor name: DELL P991
(II) NV(0): Ranges: V min: 48  V max: 120 Hz, H min: 30  H max: 107 kHz, PixClock max 230 MHz

This should go in the section "Monitor"

Section "Monitor"
	Identifier	"Dell P991"
	Option		"DPMS"
	HorizSync	30-107
	VertRefresh	48-120
EndSection

Your built in monitor is not fully DDC2B compliant and did not tell X it's capabilities so you'll have to do some homework to find out.
More than likely when you setup Ubuntu it used the Generic Monitor settings for your built in LCD.
So you could try putting:

Option "SecondMonitorHorizSync" "28-80"
Option "SecondMonitorVertRefresh" "56-76"

Here's what it says:

(II) NV(0): Manufacturer: DEL  Model: 5178  Serial#: 808466510
(II) NV(0): Year: 2001  Week: 46
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 37  vert.: 27
(II) NV(0): Gamma: 2.50
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): GTF timings supported
(II) NV(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) NV(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz

Then X cannot find the nVidia GLX driver:

(EE) Failed to initialize GLX extension (NVIDIA X driver not found)

Check in Synaptic to ensure nVidia GLX package is installed, if all the nVidia packages are installed, you might want to tag them for "Complete Removal" and re-install.


Best,

Steve

---

### Post by monomaniacpat on 2006-05-13
[QUOTE=sfink01]Check in Synaptic to ensure nVidia GLX package is installed, if all the nVidia packages are installed, you might want to tag them for "Complete Removal" and re-install.[/quote]

OK, I changed all the default monitor references in the xorg file (there were more than we thought) but now I believe it is reporting the same error: it cannot find the nvidia x driver. I tried uninstalling the drivers completely and reinstalling them, but this made no difference.

I have Nvidia-glx (1.0.7667-0ubuntu25.1), Nvidia-settings (1.0-3ubuntu6) and linux-restricted-modules-2.6.1;2.6.12.4-11, -2.6.1;2.6.12.4-11.1 (and legacy version). I previously had some dev versions installed, but I didn't reinstall those.

Any ideas?

---

### Post by sfink01 on 2006-05-15
[QUOTE=monomaniacpat]OK, I changed all the default monitor references in the xorg file (there were more than we thought) but now I believe it is reporting the same error: it cannot find the nvidia x driver. I tried uninstalling the drivers completely and reinstalling them, but this made no difference.

I have Nvidia-glx (1.0.7667-0ubuntu25.1), Nvidia-settings (1.0-3ubuntu6) and linux-restricted-modules-2.6.1;2.6.12.4-11, -2.6.1;2.6.12.4-11.1 (and legacy version). I previously had some dev versions installed, but I didn't reinstall those.

Any ideas?[/QUOTE]

mono,

You cannot have more than one version of linux-restricted-modules.  Pick the version that matches your kernel (uname -a) and do a complete removal of all linux-restricted-modules reboot and then reinstall the matching linux-restricted-modules only.  To accomplish this you will have to switch to the VESA driver nv in your xorg.conf while the linux-restricted-modules are removed or you won't be able to run X.

Best,

Steve

---

### Post by monomaniacpat on 2006-05-15
OK, my version is 2.6.12-10-386, so I installed linux-restricted-modules-2.6.12-10-386 using synaptic, but no change. Have I got the wrong package?

---

### Post by sfink01 on 2006-05-15
[QUOTE=monomaniacpat]OK, my version is 2.6.12-10-386, so I installed linux-restricted-modules-2.6.12-10-386 using synaptic, but no change. Have I got the wrong package?[/QUOTE]

mono,

No it sounds like you have the right package now, but having all of those other packages may have caused some kernel module confilicts.

After installing the packages did you reboot?  This happens to be one of the few times where you need to reboot Linux.

If you have rebooted and it still doesn't load the nVidia module ( lsmod |grep -i nvidia ).

Then follow this [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) to attempt to get the nVidia module loaded prior to trying your TwinView configuration.

Best,

Steve

---

### Post by hjm on 2006-05-17
[QUOTE=hjm]
in the nvnews forum, I just discovered that there is an AMD64 issue with the XFX 6600gt's and possibly others in the series. 

[http://www.nvnews.net/vbulletin/showthread.php?t=68044&highlight=twinview+linux](http://www.nvnews.net/vbulletin/showthread.php?t=68044&highlight=twinview+linux)

The card goes back tomorrow.  Thanks for the help tho...

Harry[/QUOTE]

Well, that was it.  I ordered an evga egforce6600GT PCIe card, stuck it into a slot and within 10 minutes it was working.  
Thanks to newegg to taking it back 1 day past the return date and getting the new one  to me in 2 days.  Here's the xorg.conf for the record:

Reminder: 2xopteron, AMD64, Kubuntu Dapper, evga egforce nvidia 6600GT PCIe, nvidia driver NVIDIA-Linux-x86_64-1.0-8756-pkg2, custom SMP kernel 2.6.16.5

```
# modified for nvidia card, Samsung displays
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Mar 29 15:31:59 PST 2006
#  2xopteron, AMD64, Kubuntu Dapper, evga egforce nvidia 6600GT PCIe, 
#  nvidia driver NVIDIA-Linux-x86_64-1.0-8756-pkg2, 
#  custom SMP kernel 2.6.16.5, hjm@tacgi.com

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
	Identifier "Default Layout"
	Screen "Screen0" 0 0
	Screen "Screen1" RightOf "Screen0"
	InputDevice "Mouse0" "CorePointer"
	InputDevice "Keyboard0" "CoreKeyboard"
	Option "Xinerama" "1"
EndSection

Section "Files"

# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
     Load "i2c"
     Load "bitmap"
     Load "ddc"
     Load "extmod"
     Load "freetype"
     Load "glx"
     Load "int10"
     Load "type1"
     Load "vbe"
 EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung0"
    ModelName      "SyncMaster 204B_0"
    HorizSync       28.0 - 80.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Samsung1"
    ModelName      "SyncMaster 204B_1"
    HorizSync       28.0 - 80.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "GeForce_6600_GT_0"
    Driver         "nvidia"
    Option         "Twinview"
    Option         "Metamodes" "1600x1200,1600x1200"
    Option         "SecondMonitorHorizSync"     "28.0 - 80.0"
    Option         "SecondMonitorVertRefresh"   "43.0 - 60.0"
#    Screen         0
#    BusID          "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "GeForce_6600_GT_0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" 
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "GeForce_6600_GT_0"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" 
    EndSubSection
EndSection

```

Thanks for all the help Steve!

---

### Post by Mr_J_ on 2006-05-17
I have 2 monitors.
1 CRT which uses VGA and 1 LCD which uses DVI.

I want to get twinview working, but with two independent resolutions and 2 independent frequencies.

I'd like 1 big desktop, but i believe poofyhairyguy said it couldn't happen and he's  all knowing...

[Here is my xorg.conf which makes both monitors work, but I can't change the resolution, or the frequencies.]("http://pastebin.com/723721")

---

### Post by E-Jey on 2006-05-25
Thanks for making this HOW TO. I have an Nvidia 6600 and two Hitachi CML174SX TFT display's. I've changed the xorg.conf file and installed the nvidia driver but it doesn't work. Both screens are active, but they don't display anything. They are just black. I've checked the xorg.0.log file and there are no errors in it. Could anybody help me? Thanks in advance! 

Here is my xorg.conf file: 

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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	VendorName 	"nvidia
 	BoardName 	"NVIDIA GeForce 6600"
	BusID		"PCI:1:0:0"
	Option 		"NoLogo" "1"
	Option 		"RenderAccel" "0"
	Option 		"CursorShadow" "1"
	Option 		"Coolbits" "1"
	Option 		"ConnectedMonitor" "dfp,dfp"
	Option 		"NoPowerConnectorCheck"
	Option 		"TwinView" "1"
	Option 		"Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
	Option 		"SecondMonitorHorizSync" "24-80"
	Option 		"SecondMonitorVertRefresh" "56-60"
EndSection

Section "Monitor"
	Identifier	"CML174SX"
	Option		"DPMS"
	
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"CML174SX"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier 	"TwinView Configuration"
	Screen 0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option 		"Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection



```

---

### Post by hjm on 2006-05-25
ejay
How do you mean the monitors are blank - do they show text mode?  Also, what make is your card?  I had the same experience on 2 nvidia-based cards from XFX.  Displayed well in text mode but blanked when invoking twinview /X. Was OK in single monitor mode. If this sounds familiar, you might try the latest nvidia driver (1.0-8762).  It specifically mentions a fix for this kind of thing.:

- Fixed a system crash starting X with TwinView on certain GPUs.

The README also has a good section on configuring the xorg.conf for twinview and linux.

post to say if the new driver fixed it.  I've already swapped teh cards that weren't working for an evga card with the same GPU, which works fine.

---

### Post by E-Jey on 2006-05-25
[QUOTE=hjm]ejay
How do you mean the monitors are blank - do they show text mode?  Also, what make is your card?  I had the same experience on 2 nvidia-based cards from XFX.  Displayed well in text mode but blanked when invoking twinview /X. Was OK in single monitor mode. If this sounds familiar, you might try the latest nvidia driver (1.0-8762).  It specifically mentions a fix for this kind of thing.:

- Fixed a system crash starting X with TwinView on certain GPUs.

The README also has a good section on configuring the xorg.conf for twinview and linux.

post to say if the new driver fixed it.  I've already swapped teh cards that weren't working for an evga card with the same GPU, which works fine.[/QUOTE]

I think I have te same problem. In text mode or with only 1 display it works good. But when I try to start with twinview the screen gets black after I logged in. I'm currently running the 1.0.8756 driver. It's the newest version Synaptic could found. Actually I have no idea how to update it :X I guess the new driver is the solution since I have also a nvidia based XFX card.

---

### Post by E-Jey on 2006-05-26
hjm, i've updated the nvidia-glx driver and it works perfectly! The new driver solves the problem. Thanks for your support.

---

### Post by mo_roodi on 2006-05-30
Hi

I'm fairly new to Linux so I'm a little lost on this one. I've been trying to get TwinView working. I've installed the NVidia drivers using apt-get install nvidia-glx and the nvidia settings and the kernel modules as required. I've included my xorg.conf file below, which includes the changes I've made. I'm just not sure why it doesn't work! Sorry I decided to include alot of the file as I'm not sure which bits are relevant and which aren't (I am such a newb!).

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

Section "Device"
	Identifier	"NVidia_6600GT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VendorName 	"AOpen"
	BoardName 	"NVIDIA GeForce 6600GT"
	Option		"NvAGP" "true"
	Option		"NoLogo" "true"
	Option		"RenderAccel" "true"
	Option		"AllowGLXWithComposite" "true"
	Option		"CursorShadow" "true"
	Option		"Coolbits" "true"
	Option		"ConnectedMonitor" "crt, crt"
	Option 		"NoPowerConnectorCheck"
	Option		"TwinView" "true"
	Option		"Metamodes" "1280x1024, 1280x1024; 1024x768, 1280x1024; 800x600, 1280x1024; 1280x1024,NULL;"
	Option		"SecondMonitorHorizSync" "30-60"
	Option		"SecondMonitorVertRefresh" "50-150"
	Option		"NoTwinViewXineramaInfo"
	
EndSection

Section "Monitor"
	Identifier	"COMPAQ S710"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"SAMSUNG 793DF"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NVidia_6600GT"
	Monitor		"COMPAQ S710"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"NVidia_6600GT"
	Monitor		"SAMSUNG 793DF"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier 	"Default Layout"
	Screen	 	"Screen0" 0 0 
	InputDevice 	"Generic Keyboard"
	InputDevice 	"Configured Mouse"
	#Option		"Xinerama" "On"
EndSection

I'm using an AOpen Aeolus NVidia 6600GT... Nice card, just need this dual monitor to work and I'll be very happy. I'm using 2 17" CRT monitors one running through a DVI->VGA converter (works fine under Windows XP - again such a newb!). I'm trying to span my desktop accross both monitors so I can drag applications accross the pair!

Hope you can help!

Cheers, 

Mo

---

### Post by Mr_J_ on 2006-05-30
Try to coment out that NvAGP deal because you have a PCI card...
try to coment out coolbits, cursorshadow just never seemed to work with me and I have the same card only from a diferent vendor.

---

### Post by mo_roodi on 2006-05-30
Thanks for the suggestion, still no luck I'm afraid... I'm just not sure what it is! I've made a few more changes to my xorg.conf now, although it looks pretty much the same. I am using an AGP card so I've changed the PCI to an AGP. Commented out those lines suggested and I've removed the 2nd montior as it's been defined in the device section. Also read somewhere that I may need to change the resolution of the screen to 2560x1024 by going through System->Preferences->Screen Resolution, but that only gives me the option to use the resultion as 1280x1024. Just not sure what else to try. 

Any help would be more than welcome. 

Cheers, 

Mo

---

### Post by mo_roodi on 2006-05-30
Just managed to fix it. I did what I should've done in the first place (such a newb) and checked the X server logs. Turns out the monitor's refresh rates weren't configured properly and so the 2nd monitor wasnt kicking in properly (if that makes any sense!). I googled the monitor (which is quite an old one so it took some finding) got the refresh rates and hey presto it works. It's beautiful... Ah the extra space is immense! Happy now! Thanks for all the help... Mo

---

### Post by chalkeye on 2006-06-07
Hi guys,

I have twinview working okay (thanks for the excellent tut). I am using a 19" (primary) crt and a 17" crt, and I am unsure as to how to fine tune the second monitor. This first is set up OK, as it hs retained its origional settings from when I was only using one display. 

When I go to System>Preferences>Screen resolution, I get a fixed box of 2560X1024 (which is correct over the two monitors, both are running at 1280x1024)   and a fixed box of 85 Hz (fixed as in I have no other options)

The problem I have is that my second, older monitor (Phillips 107E) is extremely blurry, dark and appears to have a very low refresh rate (my 19" IBM monitor is spot on by comparison).

When I used: 

Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL" it appeared to go straight through to the 2nd to last option; deleting all but "1280x1024, 1280x1024;" works fine however.

here is my xorg.conf, any help or pointers is appreciated!

btw, I am using a PCI-e 6600GT



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

Section "Device"
	Identifier "NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver "nvidia"
	VendorName "Videocard vendor"
	BoardName "NVIDIA GeForce 6600 GT"
	BusID "PCI:5:0:0"
	# Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "ConnectedMonitor" "crt, crt"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "1280x1024,1280x1024"
# Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
	Option "SecondMonitorHorizSync" "30-70"
	Option "SecondMonitorVertRefresh" "60-85"
	# Option "DisplaySize 320 240"
	# Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0		
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "TwinView Configuration"
	Screen 0 "Default Screen" 0 0
	InputDevice "Configured Mouse"
	InputDevice "Generic Keyboard"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by sfink01 on 2006-06-10
Your Metamode resolutions and your SubSection Display's resolutions don't match.  

Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"

Should have a corrosponding Screen SubSection Display like this:

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
Monitor "Generic Monitor"
DefaultDepth 24
Viewport 0 0
Depth 24
Modes "1280x1024" "1024x768"
EndSubSection
EndSection

Also double check the Sync Settings for your Second Monitor I found

Horizontal Scanning Frequency :  30 - 86 KHz

Vertical Scanning Frequency :  50 - 160 Hz

For a Phillips 107E on Google.

Hope this helps.

Best,

Steve

---

### Post by andefeldt on 2006-06-10
I'm looking for a way to have the same desktop on 2 screens (clone) but each screen is running a different resolution. My primary screen is running 1280x1024 and my secondary is running 1360x768. 

Is there someway to do this with TwinView? I've tried:

```

Section "Monitor"
    Identifier     "Philips 190S"
    ModelName      "1280x1024 @ 60 Hz"
    HorizSync       31.5 - 64.3
    VertRefresh     50.0 - 70.0
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "DPMS"
    Option         "Coolbits" "1"
    Option         "IgnoreDisplayDevices" "DFP, TV"
    Option         "IgnoreEDID" "1"
    Option         "NoLogo" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "TwinView"
    Option         "TwinViewOrientation" "Clone"
    Option          "MetaModes" "1280x1024, 1360x768; 1280x1024, NULL"
    Option          "SecondMonitorHorizSync" "38 - 60"
    Option          "SecondMonitorVertRefresh" "60 - 75"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "Philips 190S"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

```

I get an the same desktop on both screens, but the resolution on the secondary screen is still1280x1024 (I think), cause I'm missing a bit of the top and bottom desktop and it's a bit too wide on my secondary screen. 

Can't this be done? Should I try Xinerama instead? And if so, how should I set it up?

Anders

---

### Post by mtron on 2006-06-11
Hi!

My first screen is a CRT, the second X Screen runs on the TV. Is there a way to send a running app from the CRT to the xscreen of the TV "on the go"?

cheers mtron

---

### Post by sfink01 on 2006-06-12
mtron,

I've never used the TV type connection but, you should be able to just drag any application to the TV just like another monitor.

Best,

Steve

---

### Post by mtron on 2006-06-12
no, you can't drag a window from one XScreen and drop it on the other Xscreen. that doesn't work or i did not figure out how.

---

### Post by frogotronic on 2006-06-13
[QUOTE=sfink01]I've created a HOWTO on TwinView for Ubuntu Breezy and it can be found at
[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)
it should work for Hoary also but hasn't been tested as of yet.

Enjoy![/QUOTE]

Does this work for Dapper Drake?

---

### Post by frogotronic on 2006-06-13
[QUOTE=cement_head]Does this work for Dapper Drake?[/QUOTE]

yes, it does...i just learned to read.

L8R

---

### Post by mority on 2006-07-01
Hi Steve,

thanks a lot for the howto!

It worked perfectly for me, at least initially. I followed exactly the steps in your howto and restarted the X server with CTRL+ALT+DEL. Then I had to go to *System -> Preferences -> Screen Resolution* and choose the resolution of 3200x1200 and I had a whole second screen as additional workspace. Gnome did handle this situation wonderful and exactly as I wanted it to. I was totally like yeah, this rocks!

But today I started my machine and had just one screen and when I go to the Screen Resolution menu I can't choose the 3200x1200 resolution anymore. There's just the normal one screen resolution of 1600x1200 :(

I checked and double checked my xorg.conf and it is exactly like it was when it worked and I compared it to the xorg.conf from your howto, too. It really looks okay. I could post it here if someone wants to have a look at it.

Now that's really annoying, cause I know this thing **should** work cause I've seen it doing so and I don't know where to start debugging.

There are no errors in */var/log/Xorg.0.log*.

Just one line made me suspicious:
```

(II) NVIDIA(0):     "1600x1200,1600x1200"
(II) NVIDIA(0):     "1600x1200,NULL"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200

```
Why is the last line saying virtual screen size is 1600x1200? Shouldn't it be 3200x1200?

So I thougt it could be a fault of the nvidia module and did
```

aptitude reinstall nvidia-glx

```
but that did'nt help.

Any ideas anyone?

---

### Post by sfink01 on 2006-07-01
[QUOTE=mority]Hi Steve,

thanks a lot for the howto!

It worked perfectly for me, at least initially. I followed exactly the steps in --snipped--
Any ideas anyone?[/QUOTE]

Mority,

Sounds more like a video init problem, ie when the PC was turned on the second monitor was not powered up and the video card did not init properly.  Completely shut down and check your data cable on your second monitor then power after that boot the PC.

Best,

Steve

---

### Post by mority on 2006-07-01
[QUOTE=sfink01]Mority,

Sounds more like a video init problem, ie when the PC was turned on the second monitor was not powered up and the video card did not init properly.  Completely shut down and check your data cable on your second monitor then power after that boot the PC.

Best,

Steve[/QUOTE]


Thanks for your reply.

I see output in both screens if I swtich to text mode, so the graphics card seems to be aware of the second the screen. Would that be the case if it would be an vido init problem as you call it?

edit: two monitor setup works great in Windows, too. So I really don't think that the video card did not recognize the second screen. I could imagine that it's a Gnome problem. My xorg.conf must be good since I saw it working with exactly that xorg.conf. But Gnome just does not give me the meta resolution in it's menu. I have no idea why, but my guess is, that it's not a problem wit the X server.

---

### Post by commodore on 2006-07-02
I can't even install nvidia-glx and nvidia-settings! If I install nvidia-settings then synaptic/apt uninstalls nvidia-glx and if I install nvidia-glx then nvidia-settings will be uninstalled. I just set up to monitors on Windows and it was soooooooooooooooooooooooooooooo much easier.

---

### Post by tseliot on 2006-07-02
[QUOTE=commodore]I can't even install nvidia-glx and nvidia-settings! If I install nvidia-settings then synaptic/apt uninstalls nvidia-glx and if I install nvidia-glx then nvidia-settings will be uninstalled. I just set up to monitors on Windows and it was soooooooooooooooooooooooooooooo much easier.[/QUOTE]
nvidia-settings is already included in nvidia-glx. The package nvidia-settings is needed by the legacy driver.

Please read my guide (see Method 1):

Guide for Dapper
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)

Guide for Breezy
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by mority on 2006-07-02
I just thought I'll add my xorg.conf. For the related problem look at my posts above, please.

```

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
#	Load	"dri"
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

Section "Device"
        Identifier      "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP" "2"
        Option          "NoLogo" "1"
        Option          "RenderAccel" "0"
        Option          "CursorShadow" "1"
        Option          "Coolbits" "0"
        Option          "ConnectedMonitor" "crt, crt"
        Option          "NoPowerConnectorCheck"
        Option          "TwinView" "1"
        Option          "Metamodes" "1600x1200,1600x1200; 1600x1200,NULL"
        Option          "SecondMonitorHorizSync" "30-117"
        Option          "SecondMonitorVertRefresh" "50-180"
#	Option          "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"HP P1130"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-170
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"HP P1130"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by sfink01 on 2006-07-02
[QUOTE=mority]I just thought I'll add my xorg.conf. For the related problem look at my posts above, please.
[/QUOTE]

mority,

Please post your Xorg.0.log.

What is your second monitor?

Best,

Steve

---

### Post by mority on 2006-07-02
[QUOTE=sfink01]mority,

Please post your Xorg.0.log.

What is your second monitor?
[/QUOTE]

The second monitor is a Sony / Silicon Graphics GDM-5011P.

Here's the Xorg.0.log:
```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux mir 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul  2 16:30:28 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "HP P1130"
(**) |   |-->Device "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "Off"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0746 card 1849,0746 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0963 card 0000,0000 rev 25 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1849,5513 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1849,7012 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7002 card 1849,7001 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1849,8201 rev 90 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0250 card 10b0,1528 rev a3 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcdd00000 - 0xcfefffff (0x2200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbd900000 - 0xcdbfffff (0x10300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV25 [GeForce4 Ti 4600] rev 163, Mem @ 0xce000000/24, 0xc0000000/27, 0xcdb80000/19, BIOS @ 0xcfee0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[6] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[13] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[6] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[13] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[22] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "1"
(**) NVIDIA(0): Option "NvAGP" "2"
(**) NVIDIA(0): Option "ConnectedMonitor" "crt, crt"
(**) NVIDIA(0): Option "RenderAccel" "0"
(**) NVIDIA(0): Option "CursorShadow" "1"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30-117"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "50-180"
(**) NVIDIA(0): Option "MetaModes" "1600x1200,1600x1200; 1600x1200,NULL"
(**) NVIDIA(0): Option "NoPowerConnectorCheck"
(**) NVIDIA(0): Option "Coolbits" "0"
(**) NVIDIA(0): Disabling RENDER acceleration
(**) NVIDIA(0): Enabling cursor shadow
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "crt, crt"
(**) NVIDIA(0): Use of AGPGART requested
(II) NVIDIA(0): Skipping Power Connector Check.
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4600 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.25.00.28.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4600 at PCI:1:0:0:
(--) NVIDIA(0):     HP P1130 (CRT-0)
(--) NVIDIA(0):     Silicon Graphics GDM-5011P (CRT-1)
(--) NVIDIA(0): HP P1130 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Silicon Graphics GDM-5011P (CRT-1): 350.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200,1600x1200"
(II) NVIDIA(0):     "1600x1200,NULL"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] 0	0	0xce000000 - 0xceffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[8] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[9] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[10] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[13] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200,1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
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
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Sun Jul  2 16:30:31 2006: 7506 X: client 2 rejected from local host
AUDIT: Sun Jul  2 16:30:31 2006: 7506 X: client 2 rejected from local host

```

---

### Post by sfink01 on 2006-07-02
Mority,

I've been through all of the "usual suspects" everything looks great.  You might try adding some additional modes for X to drop down to (1280x1024,1280x1024) and see if one of those works then check the Screen Resolution and see if you can select 3200x1200 after it boots.

Does your card happen to have a need for an extra power connector?

Mine does but it was not connected and TwinView worked for about 30 days and then I couldn't get X to run at all then I found out about the power and plugged it in and that fixed everything.

Best,

Steve

---

### Post by mority on 2006-07-03
[QUOTE=sfink01]Mority,

I've been through all of the "usual suspects" everything looks great.  You might try adding some additional modes for X to drop down to (1280x1024,1280x1024) and see if one of those works then check the Screen Resolution and see if you can select 3200x1200 after it boots.

Does your card happen to have a need for an extra power connector?

Mine does but it was not connected and TwinView worked for about 30 days and then I couldn't get X to run at all then I found out about the power and plugged it in and that fixed everything.

Best,

Steve[/QUOTE]

I will try to add additional resolutions as soon as I'm at home again.

No, my graphics card does not have a separate power connector.

So, if you did not find any mistakes, probably the error is caused by gnome? Like everything works fine, the only problem is, that gnome does not let me pick the right resolution. Know what I mean?

edit:
Okay, I tried it now and it seems to work somehow. But not the way I want it to. If I add other resolutions and meta resolutions then 1600x1200,1600x1200 I am able to get something on the second screen again. But it doesn't behave the way I want it to. That is: a) No matter what resolutions I write to the xorg.conf, I am not able to get the 3200x1200 meta resolution again although exactly that resolution was possible when I first set this twinview thing up (see my first post). b) Gnome is expanding the desktop (including the gnome panels) to both screens as if they were one. But when I first set it up that wasn't the way Gnome behaved. Then I had the Gnome panels just on one screen and the second screen was just some additional space... I liked that far more..

Regarding the resolutions: It just seems to me as if Gnome wouldn't "believe" me anymore that the second screen is capable of a resolution of 1600x1200 but I can't see any reason why since it worked at the first place :(

edit2:

I am able to get a setup the way I want it to when I choose a resolution of 1400x1050 or 1280x960 for both screens and then use the corresponding meta resolution in gnome (2800x1050 or 2560x960) but with 1400x1050 the screens deliver an ugly display quality and 1280x960 is really a poor resolution for 21" screens and I absolutely know that both can do better.

It just can't get it that the 3200x1200 meta resolution worked in the first place and then suddenly It doesn't no matter what I do.

And again: In Windows it works fine with 1600x1200 on both screens.

---

### Post by sfink01 on 2006-07-04
[QUOTE=mority]I will try to add additional resolutions as soon as I'm at home again.

-- snipped --
edit:
Okay, I tried it now and it seems to work somehow. But not the way I want it to. If I add other resolutions and meta resolutions then 1600x1200,1600x1200 I am able to get something on the second screen again. But it doesn't behave the way I want it to. That is: a) No matter what resolutions I write to the xorg.conf, I am not able to get the 3200x1200 meta resolution again although exactly that resolution was possible when I first set this twinview thing up (see my first post). b) Gnome is expanding the desktop (including the gnome panels) to both screens as if they were one. But when I first set it up that wasn't the way Gnome behaved. Then I had the Gnome panels just on one screen and the second screen was just some additional space... I liked that far more..

Regarding the resolutions: It just seems to me as if Gnome wouldn't "believe" me anymore that the second screen is capable of a resolution of 1600x1200 but I can't see any reason why since it worked at the first place :(

edit2:

I am able to get a setup the way I want it to when I choose a resolution of 1400x1050 or 1280x960 for both screens and then use the corresponding meta resolution in gnome (2800x1050 or 2560x960) but with 1400x1050 the screens deliver an ugly display quality and 1280x960 is really a poor resolution for 21" screens and I absolutely know that both can do better.

It just can't get it that the 3200x1200 meta resolution worked in the first place and then suddenly It doesn't no matter what I do.

And again: In Windows it works fine with 1600x1200 on both screens.[/QUOTE]

mority,

Remove the comment in front of the Option "NoTwinViewXineramaInfo" to make X not span the application across both monitors.

Any chance that things "stopped working" around the time of an update?

Also the resolutions you mentioned are for wide screens (16:10) apect ratio, try standard resolutions see if that makes them not look so wierd.

Best,

Steve

---

### Post by mority on 2006-07-04
[QUOTE=sfink01]mority,

Remove the comment in front of the Option "NoTwinViewXineramaInfo" to make X not span the application across both monitors.

Any chance that things "stopped working" around the time of an update?

Also the resolutions you mentioned are for wide screens (16:10) apect ratio, try standard resolutions see if that makes them not look so wierd.

Best,

Steve[/QUOTE]

Thanks a lot, Steve, but this won't bring me my 1600x1200 resolution on both screens back. I think I will try and install Xubuntu and look how that behaves. I think the problem must have to do with Gnome or with the nvidia module.

I'll come back here after I tried Xubuntu.

---

### Post by sfink01 on 2006-07-04
[QUOTE=mority]Thanks a lot, Steve, but this won't bring me my 1600x1200 resolution on both screens back. I think I will try and install Xubuntu and look how that behaves. I think the problem must have to do with Gnome or with the nvidia module.

I'll come back here after I tried Xubuntu.[/QUOTE]


mority,

I'm sure a re-install of Ubuntu or Kubuntu will probably solve it, possibly for good possibly for just a short time.  I'm wondering if one of the Ubuntu updates had something to do with your resolution disappearing.

Best,

Steve

---

### Post by mority on 2006-07-04
[QUOTE=sfink01]mority,

I'm sure a re-install of Ubuntu or Kubuntu will probably solve it, possibly for good possibly for just a short time.  I'm wondering if one of the Ubuntu updates had something to do with your resolution disappearing.

Best,

Steve[/QUOTE]

Unfortunately I cannot tell if there was an update involved before the resolution disappeared as I was playing in the updates pretty carelessly since I thought they shouldn't do any harm in a stable distribution like dapper.

edit:

Tried Xubuntu. But stupid me did install the upgrades _before_ trying twin view. Got the same crappy results as with Gnome. Will install again and then try twin view again before upgrading the system. And then I will upgrade one package by one and see if any package is breaking the stuff. Aaargh, this stupid *#!@# is killing me.
At least I know now that it's not a Gnome-only problem.

---

### Post by javierfh on 2006-07-06
[QUOTE=sfink01]I've created a HOWTO on TwinView for Ubuntu Breezy and it can be found at
[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)
it should work for Hoary also but hasn't been tested as of yet.

Enjoy![/QUOTE]



Hello,

im planing to try twinview with my new 20" flat monitor and an old 19" CRT monitor i've got, but before that i want to check that i understood everything correctly and dont screw things in the way (might happend but for other reasons :-) )

My setup will be: 
.-Samsung SyncMaster 205BW which is a 1680x1050 wide screen monitor  
.-Sony multiscan G400 CRT monitor.
.-GeForce 7600GT with dual DVI output 

So what i want is to have the Samsung as primary and set the other as secondary so i can move some windows or applications there. Someone said it is not possible to do it with different resolutions, but some others claim that it is. Do you think it would be possible?
I guess ill try with 1680x1050 in the LCD using the DVI and 1600x1024 in the CRT using the VGA connector with the DVI->VGA adapter attached to the back of my graphics card.

Then, when following your tutorial, Steve, you mention install the Nvidia-glx and the linux-restricted-modules. What are these Linux-restricted-modules and from where and how do i get them? ( now you can just realize how newby into linux i am  :-) ) 

Next things i wonder are the options, for some of them, you set them on, some off. So what happens if i dont put some of them at all? are they considered as off? Im just thinking about for example that RenderAccel, what if i dont put that line at all? or the coolbits? im just scared of screwing something that works, so far.. so as they say , if it works dont touch it. Also one that i wonder is the NvAGP, i dont have AGP card but PCIe, is it then another option? or can i completely remove that one and replace it with something about pcie? in such case do you know the name for that option?

And last but not least where it says ConnectedMonitor, do i need to put (dfp,crt)? and i that case, does the order matter, which one i put first or second? Where do you select which monitor will be the "primary"?


Thanks in advance for all help you can provide me and i appreciate the effort you took with that tutorial, it is very good.

Javi


P.S. I add here my xorg.conf just in case you can see something odd that i should change or remove.

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
	Option		"XkbLayout"	"fi"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
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

### Post by mority on 2006-07-06
[QUOTE=mority]Unfortunately I cannot tell if there was an update involved before the resolution disappeared as I was playing in the updates pretty carelessly since I thought they shouldn't do any harm in a stable distribution like dapper.

edit:

Tried Xubuntu. But stupid me did install the upgrades _before_ trying twin view. Got the same crappy results as with Gnome. Will install again and then try twin view again before upgrading the system. And then I will upgrade one package by one and see if any package is breaking the stuff. Aaargh, this stupid *#!@# is killing me.
At least I know now that it's not a Gnome-only problem.[/QUOTE]

Okay, tried it on a fresh Ubuntu installtion without upgrading. It still does not work. I'm giving up now. Very disappointing :(
Nevertheless, thanks a lot for all the effort you put in to help me, Steve.

Chances are good that I get my hands on a Radeon 9600XT in the next weeks. Do you know anything about dual screen setup with Radeon cards in Linux?

@javierfh:

I can tell you that two different resolutions definitely works, but it's not very nice.
And just follow Steve's howto. The options he's using won't break anything as long as you keep a backup of the xorg.conf file.

---

### Post by javierfh on 2006-07-07
Hello, 

i have tried to configure it, and well doesnt work.
I get both monitors on, but the only thing i can see in both of them is, the upper half black and the lower half white. It feels like it is trying to test different modes (it blinks couple of times), but doesnt work at the end and the only way i know to exit it is doing a hard reset.

Could any of you please tell me if i am doing anything wrong?
I have the nvidia glx but what are the restricted modules? 
Check my previous post where i describe the setup im using.

Thanks in advance, hope someone sees the error.

Javi

P.S. i add here the xorg.conf im using and the xorg.0.log


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
	Load	"GLcore"
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
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

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
        # Option "NvAGP" "2"
        Option 		"NoLogo" "0"
        Option 		"RenderAccel" "0"
        Option 		"CursorShadow" "1"
        Option 		"Coolbits" "1"
        Option 		"ConnectedMonitor" "dfp, crt"
        Option 		"NoPowerConnectorCheck"
        Option 		"TwinView" "1"
        Option 		"Metamodes" "1680x1050,1600x1024; 1280x1024,1280x1024; 1024x768,1024x768; 800x600,800x600; 1680x1050,NULL; 1280x1024,NULL; 1024x768,NULL"
        Option 		"SecondMonitorHorizSync" "30-107"
        Option 		"SecondMonitorVertRefresh" "40-120"
        # Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	VendorName   	"Samsung"
	ModelName    	"SyncMaster 205BW"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by sfink01 on 2006-07-07
javierfh,

I downloaded the attachment and it was the xorg.conf again.  Please attach the xorg.0.log for review.

I would bet it's due to the different resolutions.  Try using 1600x1200 on both monitors.

Best,

Steve

---

### Post by blitzd on 2006-07-07
> So what i want is to have the Samsung as primary and set the other as secondary so i can move some windows or applications there. Someone said it is not possible to do it with different resolutions, but some others claim that it is. Do you think it would be possible?
I guess ill try with 1680x1050 in the LCD using the DVI and 1600x1024 in the CRT using the VGA connector with the DVI->VGA adapter attached to the back of my graphics card.

I had read that as well, but I found that eventually I got my two monitors (20.1" widescreen LCD @ 1680x1050 and 17" laptop LCD @ 1280 x 800) set up and working just fine. The virtual screen size is still rectangular so there is a bit of dead space below the bottom of the laptop display, but any window I have maximized on that screen set itself to the proper 1280 x 800 size.

> Then, when following your tutorial, Steve, you mention install the Nvidia-glx and the linux-restricted-modules. What are these Linux-restricted-modules and from where and how do i get them? ( now you can just realize how newby into linux i am  :-) )

The restricted modules are just binary modules that are not really released under an open source license. Your best installation method if you have an nvidia card and are new to linux is Automatix. There is a thread in the forums for it here:

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

I had my nvidia card set up and working with hardware acceleration in mere minutes with that.

> Next things i wonder are the options, for some of them, you set them on, some off. So what happens if i dont put some of them at all? are they considered as off? Im just thinking about for example that RenderAccel, what if i dont put that line at all? or the coolbits? im just scared of screwing something that works, so far.. so as they say , if it works dont touch it. Also one that i wonder is the NvAGP, i dont have AGP card but PCIe, is it then another option? or can i completely remove that one and replace it with something about pcie? in such case do you know the name for that option?

I initially had quite a few problems with my setup, I went for minimal options and have just tweaked from there to get it working. This is what my serverlayout/module/device/screen sections of my xorg.conf look like for options:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option	   "NoLogo" "1"
    Option	   "TwinView" "1"
    Option	   "Metamodes" "1680x1050,1280x800;1680x1050, NULL; NULL, 1280x800"
    Option	   "SecondMonitorHorizSync" "UseEdidFreqs"
    Option	   "SecondMonitorVertRefresh" "UseEdidFreqs"
    Option	   "HWCursor" "off"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
	Viewport    0 0
        Depth       1
        Modes      "1680x1050" "1280x800"
    EndSubSection
    SubSection     "Display"
 	Viewport    0 0
        Depth       4
        Modes      "1680x1050" "1280x800"
    EndSubSection
    SubSection     "Display"
	Viewport    0 0
        Depth       8
        Modes      "1680x1050" "1280x800"
    EndSubSection
    SubSection     "Display"
	Viewport    0 0
        Depth       15
        Modes      "1680x1050" "1280x800"
    EndSubSection
    SubSection     "Display"
	Viewport    0 0
        Depth       16
        Modes      "1680x1050" "1280x800"
    EndSubSection
    SubSection     "Display"
	Viewport    0 0
        Depth       24
        Modes      "1680x1050" "1280x800"
    EndSubSection
EndSection

```

> And last but not least where it says ConnectedMonitor, do i need to put (dfp,crt)? and i that case, does the order matter, which one i put first or second? Where do you select which monitor will be the "primary"?


I took that line out of my config, depending on your hardware setup the X server may be able to detect those options itself when it starts. The majority of my setup above lets X determine what the best values are by polling the hardware, that may or may not work with your hardware config.

If you do get stuck with an unworkable X server again, try CTRL-ALT-F1. It should switch you to a console. You can login and modify your x config through that using nano/vi or whatever console text editor you prefer. You can get back to the X server by hitting CTRL-ALT-F7, and restart it using CTRL-ALT-BACKSPACE. Alternatively through the console you can use:

```
sudo /etc/init.d/gdm restart
```

Anyways, hope that helps you out a bit. There are a whole whack of knowledgeable people floating around on these forums so I am sure you'll get your config set straight.. Just wanted to let you know that the dual monitors with disparate resolutions is indeed possible, and works quite nicely :)

Just as a side note the reason I decided to give linux a whirl again was due to recent experiences with the latest Vista beta - if you haven't tried it, trust me - you're doing the right thing :)

---

### Post by RawMustard on 2006-07-08
> **mority said:**
> Okay, tried it on a fresh Ubuntu installtion without upgrading. It still does not work. I'm giving up now. Very disappointing :(
Nevertheless, thanks a lot for all the effort you put in to help me, Steve.

Chances are good that I get my hands on a Radeon 9600XT in the next weeks. Do you know anything about dual screen setup with Radeon cards in Linux?



ATI cards suck in linux compared to nvidia.

mority, what problems did you have setting up twinview in dapper, I have it running here fine including XGL/Compiz!

---

### Post by javierfh on 2006-07-08
Hi Steve and Blitzd,

i have tried to get the log, but not sure if it is the right one anymore, since i put the old resolution back and dont know if it overwrites the previous one.

Anyway i have done some little modification according to what blitzd mentiones and guess what? i made it work :-)
But, not the way i want. Basically now the one that seems to be primary screen is the crt, which i dont like that much. So i wonder if thats because the line that i commented out about the type of monitor.

Then the second thing that i dont like that much is the frecuency that you see when selecting the resolution. 
My monitor, the LCD, has a resolution of 1680x1050 at 60hz, but now when selecting the biggest resolution, 3280x1050 i get a refresh rate of 50 hz and i can see some flickering things in the left side of the screen.
If i select 2560x1024 then the refresh rate goes to 51Hz and then i dont see that, but still i wonder if it is too low or will screw my monitor.

I would like to have the lcd as primary monitor and work with normal resolution and then if i want select the secondary in some occasions. Currently seems that the primary is the CRT, at least when i select one of these metamodes which has the null thing...it switches off the lcd


Any ideas?

I add here my xorg.conf as it looks now. I try also to add the log again :)


Thanks again, 

Javi


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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
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

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
        # Option "NvAGP" "2"
        Option 		"NoLogo" "1"
        Option 		"CursorShadow" "1"
        Option 		"Coolbits" "1"
 #       Option 		"ConnectedMonitor" "dfp, crt"
        Option 		"NoPowerConnectorCheck"
        Option 		"TwinView" "1"
        Option 		"Metamodes" "1680x1050,1600x1024; 1280x1024,1280x1024; 1024x768,1024x768; 800x600,800x600; 640x480,640x480; 1680x1050,NULL; 1280x1024,NULL; 1024x768,NULL"
        Option 		"SecondMonitorHorizSync" "30-107"
        Option 		"SecondMonitorVertRefresh" "40-120"
        # Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	VendorName   	"Samsung"
	ModelName    	"SyncMaster 205BW"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection



```

---

### Post by javierfh on 2006-07-09
New update:

I have noticed that when in using the twinview options trying to play a video crashes badly my system. All gets frozen and only way to recover from it,it is a hard reset, so not very promising.

Has anyone faced similar problems?
Or has something to do with some of the settings I have in the xorg.conf?

Thanks again,

Javi

---

### Post by mority on 2006-07-09
> **RawMustard said:**
> ATI cards suck in linux compared to nvidia.

mority, what problems did you have setting up twinview in dapper, I have it running here fine including XGL/Compiz!

I posted a lot about my problem with TwinView in this thread. Please look further above if you like.

I get TwinView running but just not with the resolution I want it to have, although it works with that resolution in Windows. As I said please read my postings above for details.

---

### Post by RawMustard on 2006-07-10
javierfh.  You only list one type of monitor in your xorg file, yet you had "dfp, crt" as an option.  What kind of monitors do you have, I know one is a "SyncMaster 205BW" but what's the other one?

Also what's the purpose of Viewport 0 0, I've never used that option, and my twinview setup has worked without issue for years!

I have no problems with video and never have because of twinview.  Either you've set it up wrong, which looks like it to me, or you have other issues!

---

### Post by RawMustard on 2006-07-10
mority.  Do you still want to get it working?  I'll help you, can you post your last config for me and I'll have a look at it!  We'll get it working, coz it works fine, I've never really had any issues with twinview or xinerama using many differnet cards.  I have found the nVidia's to be more reliable in linux tho, I have been using dual screens for over 8 years now!

Having read through some of your latest posts, it would seem to me you're putting far too much faith in Gnomes res-switcher.  Here's a tip, it's a buggy useless POS!  Set you xorg.conf file up, and don't touch that pos switcher, really - it will driver you to suicide ](*,)  It might be ok for single screen users, but not for dual displays!

---

### Post by javierfh on 2006-07-10
Hello RawMustard, 
thanks for your interest.

Well answering to your questions, the other monitor i have it is an old Sony Multiscan G400, but if i remember rigtht that line about the connected monitors it is removed now in my xorg.conf (i add it at the end of this post)

About the second comment, why  the viewport, i really dont understand about the different options, so i copied it from the how to.

But now the situation it is so that i had to park for a while the twinview until i understand these options. Currently seemed to work pretty nice..until i have discovered that trying to play a video, crashes so badly the whole system. I can have videos or dvd played with my old xorg.conf without twinview, but when i add the twinview thing it wont play anymore...it will just appear a thick white line in the middle of the player window. And that happens both with the two screens, in other words the 3000 something resolution..or just with one monitor or in other words the 1680x1050 resolution...it simply crashes and only way to recover from it it is hard reset. 

Anyone have heard that before?


Javi
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
	Load	"i2c"
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
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


Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
        Option 		"CursorShadow" "1"
        Option 		"Coolbits" "1"
#        Option 		"ConnectedMonitor" "crt,dfp"
        Option 		"NoPowerConnectorCheck"
        Option 		"TwinView" "1"
        Option 		"Metamodes" "1680x1050,1600x1024; 1280x1024,1280x1024; 1024x768,1024x768; 800x600,800x600; 640x480,640x480; NULL,1680x1050; NULL,1280x1024; NULL,1024x768"
        Option 		"SecondMonitorHorizSync" "30-107"
        Option 		"SecondMonitorVertRefresh" "40-120"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	VendorName   	"Samsung"
	ModelName    	"SyncMaster 205BW"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse" 
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by RawMustard on 2006-07-10
@javierfh

Can you try this for me and let me know how it goes!
```
# /etc/X11/xorg.conf (xorg X display server configuration file for nVidia TwinView)
#
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
        Load    "record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
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

Section "Device"
        Identifier     "Card0"
        Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "GeForce 7600GT"
        BusID          "PCI:5:0:0"
        Option         "ConnectedMonitor"          "DFP, CRT"
        Option         "TwinView"                  "1"
        Option         "TwinViewOrientation"       "RightOf"
        Option         "RenderAccel"               "1"
        Option         "HWcursor"                  "1"
        Option         "CursorShadow"              "1"
        Option         "NoLogo"                    "1"
        Option         "MetaModes"                 "1680x1050, 1600x1024; 1680x1050, NULL; NULL, 1600x1024"
        Option         "HorizSync"    "DFP-0: 30-107; CRT-0: 30-81"
        Option         "VertRefresh"  "DFP-0: 40-120; CRT-0: 56-75"
EndSection

Section "Monitor"
        Identifier     "Sony multiscan G400"
	Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Card0"
        Monitor        "SyncMaster 205BW"
	DefaultDepth    24
	SubSection "Display"
	       Depth    24
               Modes   "1680x1050"
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen    0     "Screen0" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

Unfortunately, I can't test it for you because I don't have your setup.

---

### Post by javierfh on 2006-07-10
Hello,

thanks for the help, i tried and it crashed.
I have copied the content of the Xorg.0.log.

Here you have and see if that says anything to you.

Thanks for been there helping with my "little" problem.


Javi

```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux javi-desktop 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 10 23:56:32 2006
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined Monitor "SyncMaster 205BW" referenced by Screen "Screen0".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor



```

---

### Post by nuclearw on 2006-07-10
Hello,

I feel obliged to append the fact that I'm new to this and might need a bit more explanation on some command line functions.

I've got a GeForce2 Go on an Inspiron8200. I've got the TV output working, but not that way I want it.

First, I'm not sure if I've got the nvidia legacy drivers installed properly. When I ran the .run package I got a message saying couldn't find "ld" in package "binutils". However, I see the Nvidia splash screen and TV-out is working, so, I'm not sure if it's properly installed. Is there anyway I can find out?

Second, when my TV-out works, my DFP screen is at the same resolution as the TV, but when I login, my monitor jumps to the proper resolution. The TV, on the otherhand only shows the top right hand corner of the screen.

Is there anyway I can enable "panning" so that I can view the entire contents of my DFP monitor by moving the mouse and the TV display follows my mouse?

Also, right now, the way it works is that if I open additional applications in the same screen space as my video, it overlaps itself, and I can't see the video. Is there anyway I can force the video output to play at full screen on the TV, while allowing me to use my entire desktop space on the DFP display?

I've attached the relevant parts (I think) of my xorg.conf and xorg.0.log files.

One thing that might be odd, are my metamodes settings. The order seems to be DFP-0, TV-0 in the xorg.0.log file, but it seems like I have to set my metamodes resolution opposite (TV-0 resolution, DFP-0 resolution). If I do the opposite "1400x1050,640x480" I don't get any output on the TV.

Any assistant, suggestions are truly appreciated. Really looking forward to getting this setup up and running smoothly. The log file is attached. The xorg.conf section is below.

Section "Device"
Identifier "NVIDIA Corporation NV11 [GeForce2 Go]"
Option "NoLogo" "True"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "TwinView"
#Option "ConnectedMonitor" "DFP-0,TV-0"
Option "MetaModes" "640x480,1400x1050"
Option "HorizSync" "DFP-0:28-70; TV-0:31.5-48.4"
Option "VertRefresh" "DFP-0:43-60; TV-0:60-60.3"
Option "TwinViewOrientation" "Clone"
Option "TVStandard" "NTSC-M"
Option "TVOutFormat" "Composite"

EndSectio

---

### Post by Theo21 on 2006-07-10
I read through your guide, and I just wanted to double check my xorg.conf file to see if I got it right.

I am running a Nvidia GeForce FX 5700 ultra with a 21" Nokia 445Xpro at 1280x1024, and a 15" Samsung SyncMaster 152T at 1024x768

Here's my xorg.conf:

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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
	Driver		"nvidia"
	VendorName	"Videocard vendor"
	BoardName	"NVIDIA GeForce FX 5700 Ultra"
	BusID		"PCI:1:0:0"
	Option		"NvAGP" "2"
	Option		"NoLogo" "1"
	Option		"RenderAccel" "0"
	Option		"CursorShadow" "1"
	Option		"Coolbits" "1"
	Option		"ConnectedMonitor" "crt" "dfp"
	Option		"NoPowerConnectorCheck"
	Option		"TwinView" "1"
	Option		"Metamodes" "1280x1024,1024x768; 1280x960,1024x768; 1152x864,1024x768; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "31-75"
	Option		"SecondMonitorVertRefresh" "56-75"
	# Option	"NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"Nokia 445Xpro 125k"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
	Monitor		"Nokia 445Xpro 125k"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

thanks

---

### Post by RawMustard on 2006-07-11
> **javierfh said:**
> Hello,
thanks for the help, i tried and it crashed.
I have copied the content of the Xorg.0.log.

Here you have and see if that says anything to you.

Thanks for been there helping with my "little" problem.


With your config that you said sort of worked, can you run this command for me?
```
nvidia-xconfig --query-gpu-info
```
and post its output.

---

### Post by javierfh on 2006-07-11
Hi Raw,

im still at office :-) , but i will be leaving soon , maybe in one hour (or couple of hours maximun) and ill try that as soon as i arrive.
Thanks for helping with that issue.
I will post the result in about two hours maximun.

Javi

---

### Post by javierfh on 2006-07-11
Hi Raw ,

here you have the output of the command you mentioned 

javi@javi-desktop:~$ nvidia-xconfig --query-gpu-info
Number of GPUs: 1

GPU #0:
  Name      : GeForce 7600 GT
  PCI BusID : PCI:5:0:0

  Number of Display Devices: 2

  Display Device 0 (CRT-0):
     EDID Name             : Sony CPD-G400
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 107.000 kHz
     Minimum VertRefresh   : 48 Hz
     Maximum VertRefresh   : 120 Hz
     Maximum PixelClock    : 350.000 MHz
     Maximum Width         : 1800 pixels
     Maximum Height        : 1440 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 1024 pixels
     Preferred VertRefresh : 85 Hz
     Physical Width        : 370 mm
     Physical Height       : 270 mm

  Display Device 1 (DFP-1):
     EDID Name             : Samsung SyncMaster
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 81.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 75 Hz
     Maximum PixelClock    : 160.000 MHz
     Maximum Width         : 1680 pixels
     Maximum Height        : 1050 pixels
     Preferred Width       : 1680 pixels
     Preferred Height      : 1050 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 430 mm
     Physical Height       : 270 mm



Sounds interesting that in preferred vertRefresh of the LCD says 60 but still goes to 50 or 51, when both could have 60Hz.

Can you see anything interesting there?


Javier

---

### Post by javierfh on 2006-07-11
One more update,

with the twinview configuration that works, i was wrong, if i have two monitors working, then it plays correctly the video, it crashes when i go to the resolution of NULL,1680x1050 in other words when i select to work only with the LCD.
Its interesting though that the resolution of 3280x1050 with 50hz its not good enough, the lcd has some flickering in the left hand side of the screen.
If i use 2560x1024 with 51hz then no flickering whatsoever.

The other interesting thing, it is that for some reason, uses the crt as main window so when it boots, the login screen appears there and the bar where the  menus are it is also there.

Any idea how to change that behaviour?

I guess that main issues i need to fix here would be:

.- to use the maximun resolution without flickering, i guess it would be good if i could increase the refresh rate to the 60hz as suggested by manufacturer. 
.- to fix the problem that the video hangs when using only one screen
.- to select the lcd as main screen


I attach here the Xorg.0.log from the time when it crashed.

Javi

---

### Post by RawMustard on 2006-07-11
> **javierfh said:**
> One more update,

with the twinview configuration that works, i was wrong, if i have two monitors working, then it plays correctly the video, it crashes when i go to the resolution of NULL,1680x1050 in other words when i select to work only with the LCD.


I have nothing but trouble also if I use the res switcher in Gnome with dual screens, it doesn't seem to work very well.  I would suggest not using it at all to switch to single display.

I have another xorg file setup just for single display and use a couple of scripts in my nautilus scripts folder to change xorg.conf files when I need to and then just(cnrl+alt+bkspc) log out and back in again.  X is not too good with on the fly res switching, it has to do with the way it works which makes me think the way Gnome does its thing is causing all the problems.

> 
Its interesting though that the resolution of 3280x1050 with 50hz its not good enough, the lcd has some flickering in the left hand side of the screen.
If i use 2560x1024 with 51hz then no flickering whatsoever.


This could be a limitation of the card, they're some pretty big res's you're trying to display!  How does it work in windows, do you still get flickering?  I'm assuming you still have windows running?

> 
The other interesting thing, it is that for some reason, uses the crt as main window so when it boots, the login screen appears there and the bar where the  menus are it is also there.

Any idea how to change that behaviour?


The only way is to swap the plugs on the back of your card!
Can you do this and still run your DFP via DVI, does your card have two DVI ports, or only one?

> 
I guess that main issues i need to fix here would be:

.- to use the maximun resolution without flickering, i guess it would be good if i could increase the refresh rate to the 60hz as suggested by manufacturer. 
.- to fix the problem that the video hangs when using only one screen
.- to select the lcd as main screen

I attach here the Xorg.0.log from the time when it crashed.

Javi

I don't know that I can help you with the flickering yet, we need to determine if the card can actually handle those res's.  I think it should.  As for which screen is screen 0 -main, see if you can do what I mentioned ealier, swaping cables.

I would be curious to know if you still get crashing on your DFP, running it with a single setup xorg.conf?

---

### Post by mority on 2006-07-13
> **RawMustard said:**
> mority.  Do you still want to get it working?  I'll help you, can you post your last config for me and I'll have a look at it!  We'll get it working, coz it works fine, I've never really had any issues with twinview or xinerama using many differnet cards.  I have found the nVidia's to be more reliable in linux tho, I have been using dual screens for over 8 years now!

Having read through some of your latest posts, it would seem to me you're putting far too much faith in Gnomes res-switcher.  Here's a tip, it's a buggy useless POS!  Set you xorg.conf file up, and don't touch that pos switcher, really - it will driver you to suicide ](*,)  It might be ok for single screen users, but not for dual displays!

Hi RawMustard! Sorry for not answering for so long. I was pretty busy the last days. It would be really cool if I would get the TwinView running with the right resolutions. I will come back here and give you my xorg.conf at the weekend, cause now I'm at work...

edit:

Alright, here's the xorg.conf I'm currently using. It does give me working twin view but with different resolutions on the two screens (as you can see in the "Metamodes" line). That is better than no twin view at all but pretty much sucks nevertheless. I want to have 1600x1200 on both screens and I know my hardware can handle this since it's working in Windows...

```

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
#	Load	"dri"
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

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAGP" "1"
	Option		"NoLogo" "1"
	Option		"RenderAccel" "0"
	Option		"CursorShadow" "1"
	Option		"Coolbits" "1"
	Option		"ConnectedMonitor" "crt, crt"
	Option		"NoPowerConnectorCheck"
	Option		"TwinView" "1"
	Option		"Metamodes" "1600x1200,1280x1024; 1600x1200,NULL"
	Option		"SecondMonitorHorizSync" "30-117"
	Option		"SecondMonitorVertRefresh" "50-180"
#	Option		"NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"HP P1130"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-170
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"HP P1130"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1600x1200" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by RawMustard on 2006-07-24
Hi mority.

In your config, you have two different refresh rates, yet you have two monitors the same.  Do you have identical monitors?  If so, can you tell me which is the correct vrefresh and hozsync?  Also, do you have your second screen to the left or right of your primary screen?

Anyway, try this.

```

# /etc/X11/xorg.conf (xorg X display server configuration file for nVidia TwinView)
#
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
        Load    "record"
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
	Identifier     "Configured Mouse"
	Driver         "mouse"
	Option         "CorePointer"
	Option         "Device"           "/dev/input/mice"
	Option         "Protocol"         "ExplorerPS/2"
	Option         "ZAxisMapping"     "4 5"
	Option         "Emulate3Buttons"  "true"
EndSection

Section "Device"
        Identifier     "Card0"
        Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "GeForce4 Ti 4600"
        BusID          "PCI:1:0:0"
	Option         "NvAGP" "1"
        Option         "ConnectedMonitor"          "CRT, CRT"
        Option         "TwinView"                  "1"
        Option         "TwinViewOrientation"       "RightOf"
        Option         "RenderAccel"               "1"
        Option         "HWcursor"                  "1"
        Option         "CursorShadow"              "1"
        Option         "CursorShadowAlpha"         "64"
        Option         "CursorShadowXOffset"       "4"
        Option         "CursorShadowYOffset"       "2"
        Option         "Coolbits"                  "1"
        Option         "NoLogo"                    "1"
        Option         "MetaModes"                 "1600x1200,1600x1200; 1280x1024,1280x1024; 1600x1200,NULL; 1280x1024,NULL"
        Option         "UseEdidFreqs"              "1"
        Option         "SecondMonitorHorizSync"    "30-117"
        Option         "SecondMonitorVertRefresh"  "50-180"
EndSection

Section "Monitor"
        Identifier     "HP P1130"
	Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Card0"
        Monitor        "HP P1130"
	DefaultDepth    24
	SubSection "Display"
	       Depth    24
               Modes   "1600x1200" "1280x1024"
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen    0     "Screen0" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

---

### Post by TheSeal on 2006-07-24
i cant get it to work!
The only thing that happens is that my laptopmonitor turns blank and my external monitor got the wrong resolution..
Xorg.conf:
```
Section "Device"
	Identifier	"geforce"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "ConnectedMonitor" "dfp, dfp"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "1280x800,1440x900; 1280x800,NULL"
	Option "TwinViewOrientation" "LeftOf"
	Option "SecondMonitorHorizSync" "28-72"
	Option "SecondMonitorVertRefresh" "43-60"
EndSection

Section "Monitor"
        Identifier      "Zepto"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
	Identifier "screen0"
	Device "geforce"
	Monitor "Zepto"
	DefaultDepth 24
SubSection "Display"
	Viewport 0 0
	Depth 24
	Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
EndSection

Section "ServerLayout"
	Identifier "TwinView Configuration"
	Screen		"screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option "Xinerama" "Off"
EndSection
```

---

### Post by RawMustard on 2006-07-25
@TheSeal

Well you've set your primary screen up to use your secondary screens settings. Screen0 is your laptop screen.  What do you get when you run nvidia-xconfig --query-gpu-info with both screens attached.

---

### Post by TheSeal on 2006-07-25
hmm okay, im not so good at this then ;)
nvidia-xconfig --query-gpu-info gives me this:
```

GPU #0:
  Name      : GeForce Go 6600
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 2

  Display Device 0 (CRT-0):
     EDID Name             : Samsung SyncMaster
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 81.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 75 Hz
     Maximum PixelClock    : 140.000 MHz
     Maximum Width         : 1440 pixels
     Maximum Height        : 900 pixels
     Preferred Width       : 1440 pixels
     Preferred Height      : 900 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 410 mm
     Physical Height       : 260 mm

  Display Device 1 (DFP-0):
     EDID Name             : CPT
     Minimum HorizSync     : 48.934 kHz
     Maximum HorizSync     : 48.934 kHz
     Minimum VertRefresh   : 60 Hz
     Maximum VertRefresh   : 60 Hz
     Maximum PixelClock    : 68.900 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 800 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 800 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 330 mm
     Physical Height       : 210 mm

```

---

### Post by mority on 2006-07-25
> **RawMustard said:**
> Hi mority.

In your config, you have two different refresh rates, yet you have two monitors the same.  Do you have identical monitors?  If so, can you tell me which is the correct vrefresh and hozsync?  Also, do you have your second screen to the left or right of your primary screen?


I don't have identical monitors. My primary screen is a HP P1130 with a max sync range of 170 Hz x 130 kHz and the secondary screen, which is right to the primary one, is a SGI GDM-5011P (it's in fact a Sony screen) with a max sync range of 180 Hz x 117 kHz.

Here is the data sheet to the HP screen: [http://www.hp.com/hpinfo/newsroom/press_kits/2002/ia32/hpP1130DataSheet.pdf](http://www.hp.com/hpinfo/newsroom/press_kits/2002/ia32/hpP1130DataSheet.pdf)

For the SGI / Sony I wasn't able to find a proper data sheet but the information about the sync rates I found here: [http://www.amxtrading.com/index.asp?PageAction=VIEWPROD&ProdID=184](http://www.amxtrading.com/index.asp?PageAction=VIEWPROD&ProdID=184)

Will try your xorg.conf this evening.

So long!

---

### Post by RawMustard on 2006-07-25
@mority

Then my config probably wont work, a simple nvidia-xconfig --query-gpu-info in a terminal with both monitors connected mority, will yield all the info we need to set it up correctly.
So in  a terminal
```

nvidia-xconfig --query-gpu-info > ~/Desktop/gpu-query-info.txt

```

Then copy the contents of the text file here :)

Here, try this one if you reckon your original worked but with wrong res.

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
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
#	Load	"dri"
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

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"AGP:1:0:0"
	Option		"NoLogo" "1"
	Option		"RenderAccel" "0"
	Option		"CursorShadow" "1"
	Option		"Coolbits" "1"
	Option		"ConnectedMonitor" "CRT, CRT"
	Option		"NoPowerConnectorCheck"
	Option		"TwinView" "1"
	Option		"Metamodes" "1600x1200,1600x1200; 1600x1200,NULL"
	Option		"SecondMonitorHorizSync" "30-117"
	Option		"SecondMonitorVertRefresh" "50-180"
#	Option		"NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"HP P1130"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-170
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"HP P1130"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by RawMustard on 2006-07-25
@TheSeal

Interesting results huh? I've never set up a laptop with two different screens before.  It would seem the card sees your external screen as screen0 hmm?  Ok I'll try to figure something out for you, give me a sec or maybe an hour :)

---

### Post by mority on 2006-07-25
> **RawMustard said:**
> @mority

Then my config probably wont work, a simple nvidia-xconfig --query-gpu-info in a terminal with both monitors connected mority, will yield all the info we need to set it up correctly.
So in  a terminal
```

nvidia-xconfig --query-gpu-info > ~/Desktop/gpu-query-info.txt

```

Then copy the contents of the text file here :)


Man, this is a really useful command. Will have to remember that. Will post the output this evening when I'm home again...

---

### Post by TheSeal on 2006-07-25
> **RawMustard said:**
> @TheSeal

Interesting results huh? I've never set up a laptop with two different screens before.  It would seem the card sees your external screen as screen0 hmm?  Ok I'll try to figure something out for you, give me a sec or maybe an hour :)
Okay thanks :)
Im new to linux/ubuntu and dont know so much about all this.

---

### Post by RawMustard on 2006-07-25
We're all new TheSeal, helping you guys is teaching me stuff as well :)  It's all about helping each other and learning as we go!

---

### Post by RawMustard on 2006-07-25
@TheSeal

Hmm I had a thought I should have asked you before.  How do you instend using your second screen on your laptop, I mean what do you want it to do?  Extend your desktop so you can drag stuff between the two or as a clone? A clone being a duplication of what's happening on you laptop screen.

Because being a laptop, you can't really set stuff up on your second screen unless you're going to carry it around with you :)
Your desktop will get messed up when you unplug it.  Have you thought about any of this?

Also I need the rest of your xorg.conf file, post your current one that your laptop is using at the moment!

---

### Post by TheSeal on 2006-07-25
I had in mind to extend my desktop, just like dualview in Windows.
My laptop doesn't travel so much and most stands home beside my external screen. 
But it would be nice if it would work as "normal" when i unplugg the external screen. Is thats possible?

Here is my xorg.conf:
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
	Option		"XkbLayout"	"se"
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
	Identifier	"geforce"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "ConnectedMonitor" "DFP, CRT"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "1280x800,1440x900; 1280x800,NULL"
	Option "TwinViewOrientation" "LeftOf"
	Option "SecondMonitorHorizSync" "28-72"
	Option "SecondMonitorVertRefresh" "43-60"
EndSection

Section "Monitor"
        Identifier      "Zepto"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
	Identifier "screen0"
	Device "geforce"
	Monitor "Zepto"
	DefaultDepth 24
SubSection "Display"
	Viewport 0 0
	Depth 24
	Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
EndSection

Section "ServerLayout"
	Identifier "TwinView Configuration"
	Screen		"screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection
```
likely many wrong settings in it, i tried much things. :P

---

### Post by RawMustard on 2006-07-25
@TheSeal

Is this config working for you?

---

### Post by TheSeal on 2006-07-25
Depend on how you see things :P
It works to use the computer but no twinview or something like that. If my externalscreen is connected the laptopscreen turns blank and the externalscreen gets 1280x800 resolution.
So no :P

---

### Post by RawMustard on 2006-07-25
@TheSeal

OK!  Lets try this one.
```

# /etc/X11/xorg.conf (xorg X display server configuration file for nVidia TwinView - For TheSeal)
#
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
        Load    "record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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

Section "Device"
        Identifier     "Card0"
        Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "GeForce Go 6600"
        BusID          "PCI:1:0:0"
        Option         "ConnectedMonitor"          "CRT-0, DFP-0"
        Option         "TwinView"                  "1"
        Option         "TwinViewOrientation"       "LeftOf"
#Blanked for now        Option         "RenderAccel"               "1"
#Blanked for now        Option         "HWcursor"                  "1"
#Blanked for now        Option         "CursorShadow"              "1"
#Blanked for now        Option         "CursorShadowAlpha"         "64"
#Blanked for now        Option         "CursorShadowXOffset"       "4"
#Blanked for now        Option         "CursorShadowYOffset"       "2"
#Blanked for now        Option         "Coolbits"                  "1"
        Option         "NoLogo"                    "1"
        Option         "MetaModes"                 "CRT-0: 1440x900, DFP-0: 1280x800"
        Option         "UseEdidFreqs"              "1"
        Option         "HorizSync"    "DFP-0: 49-49; CRT-0: 30-81"
        Option         "VertRefresh"  "DFP-0: 60-60; CRT-0: 56-75"
EndSection

Section "Monitor"
        Identifier     "Monitor0"
	Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Card0"
        Monitor        "Monitor0"
	DefaultDepth    24
	SubSection "Display"
	       Depth    24
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen    0     "Screen0" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

```

In a terminal windows do the following:

```
sudo cp /etc/X11/xorg.conf xorg.conf.bk
```
```
sudo gedit /etc/X11/xorg.conf
```

Now delete what's there and copy the code I posted above, save and close gedit.

Now cntrl alt bckspc to kill xorg.  If everything goes alright, you shuold be able to log in.  If not, then just log in to your terminal screen and type:
```
sudo cp /etc/X11/xorg.conf.bk xorg.conf
```
Then
```
sudo /etc/init.d/gdm restart
```
This will get you back to where we started.

Let me know what happens? :-k

---

### Post by TheSeal on 2006-07-25
It worked, almost perfect.
But the externalscreen became primary, i would like to have the laptopscreen as primary and the external as "slave". 
But i think you can do that ;)
thanks :)

---

### Post by RawMustard on 2006-07-25
Hmm.  I don't know if I can do that.  Normaly you need to swap the plugs on the screens, but you can't do that on a laptop.  I'll have to read the nVidia docs some more to see if I can achieve this for you.  If you're interested, have a look yourself also.

[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html)

I'll see what I can dig up :)

Oh also, I made a slight change you might like to try.  I added another option in the above config. -         Option         "UseEdidFreqs"              "1"

---

### Post by TheSeal on 2006-07-25
Okey, im not sure that to look for.

Now when i rebooted and tried without my external screen i couldn't do anything, because the loginscreen were on the other screen.
Can that be solved? If not, im think i have to use windows again :(

---

### Post by RawMustard on 2006-07-25
Ok can you try this for me?

Change
Option "ConnectedMonitor" "CRT-0, DFP-0"

to 

Option "ConnectedMonitor" "DFP-0, CRT-0"

Also add this option just underneath the above one.

Option "NoPowerConnectorCheck" "1"

and let me know what happens.

---

### Post by TheSeal on 2006-07-25
Unfortunately it makes no difference. :(
Is this a lost case?

---

### Post by RawMustard on 2006-07-25
Try blanking out this option like so.
#Option "ConnectedMonitor" "DFP-0, CRT-0"

---

### Post by RawMustard on 2006-07-25
We'll be able to solve the problem of not seeing your boot screen when you disconnect your second display, but from what I've been able to gather from nvidia, when you connect a second monitor on a laptop, it becomes your primary screen :(

What happens in windows with your second monitor connected?

---

### Post by TheSeal on 2006-07-25
> **RawMustard said:**
> Try blanking out this option like so.
#Option "ConnectedMonitor" "DFP-0, CRT-0"
that didnt have any effect at all :(

> **RawMustard said:**
> We'll be able to solve the problem of not seeing your boot screen when you disconnect your second display, but from what I've been able to gather from nvidia, when you connect a second monitor on a laptop, it becomes your primary screen :(

What happens in windows with your second monitor connected?

In windows my laptopscreen became primary by default.

---

### Post by RawMustard on 2006-07-25
But when you boot up, which screen show the boot sequence when both screens are connected?

---

### Post by TheSeal on 2006-07-25
hmm, both.

---

### Post by RawMustard on 2006-07-25
Ok. You can't set your laptop screen as primary in linux because there's a [**_bug_**]("http://www.nvnews.net/vbulletin/showthread.php?t=54638") in the nVidia drivers :(

So the only way I can see to fix the problem of no display when you disconnect your second display until this bug is fixed, is to have a second xorg.conf file setup for single display and you switch to that when you know you're not going to use your second screen.  I can set that up for you if you like, it's a no brainer :)

---

### Post by TheSeal on 2006-07-25
Okey. But then im going back to windows :( i will get wryneck to have my externalscreen as primary :(
But thanks for everything :)

Ubuntu will be my first choice on my next computer, with only one screen :P

---

### Post by RawMustard on 2006-07-25
It's really only a problem for laptops and people with different screens.  My rig here has identical DFP's and it is just superb, runs better than windows.  On windows I get constant flickering and crap every time I click on a video file, when logging in or doing something in display properties, it's a real pain in the kuhoonies :(  But I don't use windows much so its no big deal to me really :)

---

### Post by TheSeal on 2006-07-25
Okey.
Thanks again, and i might come back to you in the future ;)

---

### Post by mority on 2006-07-26
@RawMustard

Alright, here's the output of 'nvidia-xonfig --query-gpu-info'. The values for hsync and vrefresh differ slightly from those I got from the net. Do you think that's what causing the trouble?

But the values for Maximum Width and Maximum Height for the second screen cannot be true since I get a 1600x1200@75Hz resolution for that SGI screen in Windows...

```

Number of GPUs: 1

GPU #0:
  Name      : GeForce4 Ti 4600
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 2

  Display Device 0 (CRT-0):
     EDID Name             : HP P1130
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 130.000 kHz
     Minimum VertRefresh   : 48 Hz
     Maximum VertRefresh   : 170 Hz
     Maximum PixelClock    : 300.000 MHz
     Maximum Width         : 1800 pixels
     Maximum Height        : 1440 pixels
     Preferred Width       : 1600 pixels
     Preferred Height      : 1200 pixels
     Preferred VertRefresh : 85 Hz
     Physical Width        : 400 mm
     Physical Height       : 300 mm

  Display Device 1 (CRT-1):
     EDID Name             : Silicon Graphics GDM-5011P
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 107.000 kHz
     Minimum VertRefresh   : 48 Hz
     Maximum VertRefresh   : 160 Hz
     Maximum PixelClock    : 141.820 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 1024 pixels
     Physical Width        : 400 mm
     Physical Height       : 300 mm

```

---

### Post by RawMustard on 2006-07-27
@Mority.

[quote=Mority]
The values for hsync and vrefresh differ slightly from those I got from the net. Do you think that's what causing the trouble?[/quote]

Nope!

[quote=Mority]
But the values for Maximum Width and Maximum Height for the second screen cannot be true since I get a 1600x1200@75Hz resolution for that SGI screen in Windows...[/quote]

Well these values are what your monitors are reporting to the nvidia kernel modual, so they must be true :)

Any Os can force a monitor to do more than it's capable and you get away with sometimes.  But most times you'll just burn out the fly transformer quicker than it's suppose to last.

Anyway, try this config, it should work just fine.  You might want to change the RightOf option to LeftOf if it's not how you want.  You can also enable the blanked options particularly RenderAccel and see what your card can handle once you get it all working right.

```

# /etc/X11/xorg.conf (xorg X display server configuration file for nVidia TwinView - For Mority)
#
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
        Load    "record"
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

Section "Device"
        Identifier     "Card0"
        Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "GeForce4 Ti 4600"
        BusID          "PCI:1:0:0"
        Option         "ConnectedMonitor"          "CRT-0, CRT-1"
        Option         "TwinView"                  "1"
        Option         "TwinViewOrientation"       "RightOf"
#Blanked for now        Option         "RenderAccel"               "1"
#Blanked for now        Option         "HWcursor"                  "1"
#Blanked for now        Option         "CursorShadow"              "1"
#Blanked for now        Option         "CursorShadowAlpha"         "64"
#Blanked for now        Option         "CursorShadowXOffset"       "4"
#Blanked for now        Option         "CursorShadowYOffset"       "2"
        Option         "NoLogo"                    "1"
        Option         "MetaModes"                 "1600x1200,1600x1200; 1600x1200,NULL"
        Option         "UseEdidFreqs"              "1"
        Option         "HorizSync"    "CRT-0: 30-130; CRT-1: 30-107"
        Option         "VertRefresh"  "CRT-0: 48-170; CRT-1: 48-160"
EndSection

Section "Monitor"
        Identifier     "Monitor0"
	Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Card0"
        Monitor        "Monitor0"
	DefaultDepth    24
	SubSection "Display"
	       Depth    24
               Modes   "1600x1200"
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen    0     "Screen0" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

Let me know how you get on :)

---

### Post by mority on 2006-07-28
RawMustard,

I tried the xorg.conf you posted above. The second screen stays just black with it. Do you need the Xorg.0.log?

---

### Post by eightysix on 2006-07-28
Hey guys, I'm having trouble with TwinView streching my screen too far. For example. when I try to fullscreen Firefox, it goes the full 2560x1024. I'm using a triple-head setup, by the way. It was working fine before I added the other card (I was having problems with it before, but I got them fixed), but now, the whole screen streches. Here's my xorg.conf:

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
	Identifier 	"dev0"
	Driver 		"nvidia"
	VendorName 	"eVGA"
	BoardName 	"NVIDIA GeForce 6200"
	BusID 		"PCI:1:0:0"
	Option 		"NvAGP" "3"
	Option 		"NoLogo" "1"
	Option 		"RenderAccel" "0"
	Option 		"CursorShadow" "1"
	Option 		"Coolbits" "1"
	Option 		"ConnectedMonitor" "crt, crt"
	Option 		"NoPowerConnectorCheck"
	Option 		"TwinView" "1"
	Option 		"Metamodes" "1280x1024, 1280x1024;"
	Option 		"TwinViewOrientation" "RightOf"
	Option 		"SecondMonitorHorizSync" "27-92"
	Option 		"SecondMonitorVertRefresh" "50-160"
	# Option 	"NoTwinViewXineramaInfo"
EndSection

Section "Device"
	Identifier 	"dev2"
	VendorName 	"Matrox Graphics, Inc. G400/G450 (rev 85)"
	Driver 		"mga"
	BusID 		"PCI:3:0:0"
	# Option 	"OldDmainit" "boolean"
	Option 		"OldDmainit" "false"
	VideoRam    	32768
	Option	    	"MGASDRAM"
EndSection 

Section "Monitor"
	Identifier	"mon0"
	VendorName	"Samsung Syncmaster 753DF"
	Option		"DPMS"
	HorizSync	50-160
	VertRefresh	30-70
EndSection

Section "Monitor"
	Identifier	"mon2"
	VendorName	"Sun GDM-4510"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"dev0"
	Monitor		"mon0"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth 		24
		Modes 		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen2"
	Device		"dev2"
	Monitor		"mon2"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth 		24
		Modes 		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Multi-head Configuration"
	Screen "screen0" LeftOf "screen2"
	Screen "screen2" 0 0
	InputDevice "Configured Mouse"
	InputDevice "Generic Keyboard"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by RawMustard on 2006-07-29
@Mority

Really?  Hmm, that's strange.  Yes, can you post your log?
Also, what does gnome res switcher say, see if you can select 3200x1200?

Also try blanking out
#Option "UseEdidFreqs" "1"

---

### Post by mority on 2006-07-29
> **RawMustard said:**
> @Mority

Really?  Hmm, that's strange.  Yes, can you post your log?
Also, what does gnome res switcher say, see if you can select 3200x1200?

Also try blanking out
#Option "UseEdidFreqs" "1"

Gnome res switcher does not let me choose another resolution then 1600x1200. Blanking out the "UseEdidFreqs" Option does not seem to change anything.

Here's the Xorg.0.log (I had "UseEdidFreqs" turned off when this log was created):
```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux mir 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 29 13:07:35 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "off"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0746 card 1849,0746 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0963 card 0000,0000 rev 25 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1849,5513 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1849,7012 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7002 card 1849,7001 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1849,8201 rev 90 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0250 card 10b0,1528 rev a3 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcdd00000 - 0xcfefffff (0x2200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbd900000 - 0xcdbfffff (0x10300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV25 [GeForce4 Ti 4600] rev 163, Mem @ 0xce000000/24, 0xc0000000/27, 0xcdb80000/19, BIOS @ 0xcfee0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[6] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[13] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[6] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[13] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[22] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "1"
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT-0, CRT-1"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1600x1200,1600x1200; 1600x1200,NULL"
(**) NVIDIA(0): Option "HorizSync" "CRT-0: 30-130; CRT-1: 30-107"
(**) NVIDIA(0): Option "VertRefresh" "CRT-0: 48-170; CRT-1: 48-160"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "CRT-0, CRT-1"
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4600 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.25.00.28.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4600 at PCI:1:0:0:
(--) NVIDIA(0):     HP P1130 (CRT-0)
(--) NVIDIA(0):     Silicon Graphics GDM-5011P (CRT-1)
(--) NVIDIA(0): HP P1130 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Silicon Graphics GDM-5011P (CRT-1): 350.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200,1600x1200"
(II) NVIDIA(0):     "1600x1200,NULL"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] 0	0	0xce000000 - 0xceffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[8] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[9] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[10] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[13] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200,1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
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
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Sat Jul 29 13:07:37 2006: 5191 X: client 2 rejected from local host

```

---

### Post by RawMustard on 2006-07-29
@Mority
That's an AGP card right?  not pci-Express?

Can you try changing
BusID "PCI:1:0:0"
to
BusID "AGP:1:0:0"
Also, re-enable UseEdidFreqs

---

### Post by mority on 2006-07-29
> **RawMustard said:**
> @Mority
That's an AGP card right?  not pci-Express?

Can you try changing
BusID "PCI:1:0:0"
to
BusID "AGP:1:0:0"
Also, re-enable UseEdidFreqs

Did so. No success. Second screen stays black, Gnome res switcher just offers the 1600x1200 resolution.

Yes, it is an AGP card.

Further suggestions?

---

### Post by RawMustard on 2006-07-29
@eightysix

If you want to use 2 cards you need to use xinerama.  I don't think you can combine twinview and xinerama.
check out this page for some more help.

[http://gentoo-wiki.com/HOWTO_Dual_Monitors]("http://gentoo-wiki.com/HOWTO_Dual_Monitors")

---

### Post by RawMustard on 2006-07-29
@Mority

Did you try rebooting after setting the new config mority?  Also did you have both monitors turned on when booting up?  Just need to make sure of the simple things first :) Also, which screen is connected to your DVI port and are you using a DVI to VGA connector?  Something funny's going on here; that config should work :-k

---

### Post by RawMustard on 2006-07-29
@Mority.

Another change to try.
Set BusID "AGP:1:0:0" back to BusID "PCI:1:0:0"
then add Option "NvAGP" "1" just below it - like you had in your old config.

If that doesn't work, can you try something for me or maybe you already have.  Can you swap screens around so your preferred screen is the second screen, by physically swapping around the plugs on the back of your pc.  Also, do you know what chipset your motherboard uses?

---

### Post by mority on 2006-07-30
Hi RawMustard,

yes, I rebooted with both monitors turned on after changing the config. I have two DVI connectors on my graphics card. Both monitors are connected with DVI-to-VGA adapters.

I tried the "NvAGP" Option in your config, but it changes nothing.

I also tried to physically swap around the VGA cables on the graphics card and the result is somewhat marvellous: one screen (the HP P1130) stays primary, no matter in which order I connect the VGA cables. I really don't understand how this is possible :confused: 

In my box is a cheap crap ASRock K7S8X mainboard with a SiS 746FX chipset.

---

### Post by RawMustard on 2006-07-30
@Mority.

Hi Mority, I haven't given up on you yet :)

Anyway, It would seem xorg or the nvidia module is having a bit of a problem with your second screen the Silicon Graphics GDM-5011P.  I don't think it's reporting its correct capabilities.

Could you try this for me if you already haven't?
Use this config with your Silicon Graphics GDM-5011P on its own, disconnect your other screen and plug the SG into your primary socket and see if it will run at 1600x1200 res on its own under Ubuntu.
```

# /etc/X11/xorg.conf (xorg X display server configuration file for nVidia SingleView)
#
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
        Load    "record"
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

Section "Device"
	Identifier     "GF4Ti4600"
	Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "GeForce4 Ti 4600"
	BusID	       "PCI:1:0:0"
        Option         "ConnectedMonitor"          "CRT"
        Option         "NoLogo"                    "1"
        Option         "UseEdidFreqs"              "1"
EndSection

Section "Monitor"
        Identifier     "Silicon Graphics GDM-5011P"
	Option         "DPMS"
        HorizSync       30-107
        VertRefresh     48-160
EndSection

Section "Screen"
	Identifier      "Default Screen"
	Device          "GF4Ti4600"
	Monitor         "Silicon Graphics GDM-5011P"
	DefaultDepth    24
	SubSection "Display"
           Depth        24
           Modes        "1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier      "Default Layout"
	Screen          "Default Screen"
	InputDevice     "Generic Keyboard"
	InputDevice     "Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

I have a feeling that this monitor is causing us the grief and want to try it on its own before we try to force it to display that res in dual mode.

Sorry this is taking longer than I thought, I was sure my first config would have worked :(

The reason I think your second screen is the problem, is from your log. Everything goes fine till it comes time for the nvidia module to calculate the virtual screen.  It calculates it to be 1600x1200, it should be 3200x1200.  Also in my own log, I get
```

(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
```
which I don't see in your log.  I'm no expert on these things, but I feel that because your second screen doesn't report its full DDC values, it's being ignored.  I could be totally off on this, just trying to think out aloud :)

---

### Post by mority on 2006-07-30
> **RawMustard said:**
> 
Anyway, It would seem xorg or the nvidia module is having a bit of a problem with your second screen the Silicon Graphics GDM-5011P.  I don't think it's reporting its correct capabilities.

Could you try this for me if you already haven't?
Use this config with your Silicon Graphics GDM-5011P on its own, disconnect your other screen and plug the SG into your primary socket and see if it will run at 1600x1200 res on its own under Ubuntu.

I'm no expert on these things, but I feel that because your second screen doesn't report its full DDC values, it's being ignored.  I could be totally off on this, just trying to think out aloud :)

Seems you are somewhat right about this. I connected just the SG and rebooted with the xorg.conf you posted above. It boots normally as long as it is in text/framebuffer mode but the screens goes black in the moment the X server is loaded :(

Here's the Xorg.0.log:
```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux mir 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 30 16:51:57 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Silicon Graphics GDM-5011P"
(**) |   |-->Device "GF4Ti4600"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0746 card 1849,0746 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0963 card 0000,0000 rev 25 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1849,5513 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1849,7012 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7002 card 1849,7001 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1849,8201 rev 90 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0250 card 10b0,1528 rev a3 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcdd00000 - 0xcfefffff (0x2200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbd900000 - 0xcdbfffff (0x10300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV25 [GeForce4 Ti 4600] rev 163, Mem @ 0xce000000/24, 0xc0000000/27, 0xcdb80000/19, BIOS @ 0xcfee0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[6] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[13] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[6] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[13] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[5] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[6] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[7] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[22] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "1"
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT"
(**) NVIDIA(0): Option "UseEdidFreqs" "1"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): ConnectedMonitor string: "CRT"
(WW) NVIDIA(0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4600 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.25.00.28.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4600 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] 0	0	0xce000000 - 0xceffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[8] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[9] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[10] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[13] -1	0	0xcdb80000 - 0xcdbfffff (0x80000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
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
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

So the SG / Sony monitor seems to be cheap and nasty... Do you still see any chance to get this running?

And please don't apologize for this taking so long. I very much appreciate the time you are spending on this just to help me! Thanks..! :)

---

### Post by RawMustard on 2006-07-30
Yep I was right.
```

(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
```

Did you see that bit in the log?  Looks like we might have to get  the nvidia driver to ignore the EDID information and force our own settings, just reading up on this at the moment, stay tuned :)

---

### Post by RawMustard on 2006-07-30
Mority, can you do this for me?  Can you plug in your screens how you want them.  Load up this config. Then hit CNTRL+ALT+F1 to get to a terminal.  Login to this terminal with your normal username and password and then stop gdm ```
sudo /etc/init.d/gdm stop
``` once you've stopped gdm, type this command```
startx -- -logverbose 6
```
This will startx and give me a better log to see why your second monitor is being ignored.  Once X starts, make a copy of the log and post it here!

Actually, can you try this first.
```

# /etc/X11/xorg.conf (xorg X display server configuration file for nVidia TwinView - For Mority)
#
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
        Load    "record"
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

Section "Device"
        Identifier     "Card0"
        Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "GeForce4 Ti 4600"
        BusID          "PCI:1:0:0"
        Option         "ConnectedMonitor"          "CRT-0, CRT-1"
        Option         "TwinView"                  "1"
        Option         "TwinViewOrientation"       "RightOf"
        Option         "RenderAccel"               "1"
#Blanked for now        Option         "HWcursor"                  "1"
#Blanked for now        Option         "CursorShadow"              "1"
#Blanked for now        Option         "CursorShadowAlpha"         "64"
#Blanked for now        Option         "CursorShadowXOffset"       "4"
#Blanked for now        Option         "CursorShadowYOffset"       "2"
        Option         "NoLogo"                    "1"
        Option         "MetaModes"                 "1600x1200,1600x1200; 1600x1200,NULL"
        Option         "UseEDID"   "0"
        Option         "HorizSync"    "CRT-0: 30-130; CRT-1: 30-107"
        Option         "VertRefresh"  "CRT-0: 48-170; CRT-1: 48-160"
EndSection

Section "Monitor"
        Identifier     "Monitor0"
	Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Card0"
        Monitor        "Monitor0"
	DefaultDepth    24
	SubSection "Display"
	       Depth    24
               Modes   "1600x1200"
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen    0     "Screen0" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

---

### Post by eightysix on 2006-07-30
> **RawMustard said:**
> @eightysix

If you want to use 2 cards you need to use xinerama.  I don't think you can combine twinview and xinerama.
check out this page for some more help.

[http://gentoo-wiki.com/HOWTO_Dual_Monitors]("http://gentoo-wiki.com/HOWTO_Dual_Monitors")

Yeah, I ended up just using Xinerama anyways. You wouldn't know how to fix the Print Screen problem with Xinerama, would you? I couldn't find anything on it.

---

### Post by RawMustard on 2006-07-30
@eightysix

What problem would that be exactly?

---

### Post by mority on 2006-08-02
RawMustard,

this last xorg.conf you gave me is working perfectly with 1600x1200 resolution on both screens!! That's damn cool.

Thanks so much. I will call you God of TwinView from now on ;)

=D>

Am I right when I assume that the ```
Option "UseEDID" "0"
``` line is the crucial one?

---

### Post by RawMustard on 2006-08-03
@Mority

Great stuff :-D  Yeah, that's what we needed coz your second screen doesn't report enough info for the nvidia module to configure x correctly.  Anyway, great to hear you're happy :)

Now you can try and re-enable those blanked out options and see how you go, though they're only eye candy :)

---

### Post by RawMustard on 2006-08-03
I don't know why this double posted, I only clicked the button once :(

---

### Post by mdampier on 2006-08-03
Help!!! I am a Linux Newbie and I am about in tears ](*,)!
I have 2 20" Dell 2001LP monitors that I am trying to get twinview to work with.

Let me give you a little history here. 
When I first loaded Ubuntu on my machine the dual monitors worked like magic with dvi to analog hookups and I switched them to DVI hookups and it still worked but then I came in one morning and only 1 screen would come up, that was my secondary. After rebooting and fiddling with the wires some and switching back to analog I determind to just give a fresh install of Ubuntu since I didn't really know what I was doing as far as configs went. And it seems the driver still didn't work even after the fresh install.

I have a  NV34 [GeForce FX 5200] card so the next step was I downloaded the newest glx driver and changed my xconfig file to this.

```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
      # Load    "dri"
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
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "CursorShadow" "1"
         Option "Coolbits" "1"
        Option "NoPowerConnectorCheck"
      #  Option "ConnectedMonitor" "dfp, dfp"
        Option "Twinview" "1"
      #  Option "TwinviewOrientation" "LeftOf"
        Option "Metamodes" "1280x1024,1680x1050; 1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
        Option "SecondMonitorHorizSync" "31-82"
        Option "SecondMonitorVertRefresh" "56-76"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        #HorizSync      28-51
        #VertRefresh    43-60
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        #HorizSync      28-51
        #VertRefresh    43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
         Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"        EndSubSectionEndSection

Section "ServerLayout"
        Identifier      "Twinview Configuration"
        #Identifier     "Default Layout"
        Screen 1        "Default Screen"
        #Screen         "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
                           
                                             
```
This seemed to work for the DVI to analog connectors but when I tried to hook my same monitors with the DVI connectors it didn't work even when I changed the MonitorsConnected arguments to dfp,dfp.
So next I tried your How to and here is my new xconfig file:
```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
      # Load    "dri"
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
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "NoLogo" "1"
        Option "RenderAccel" "0"
        Option "CursorShadow" "1"
        Option "Coolbits" "1"
        Option "ConnectedMonitor" "dfp, dfp"
        Option "NoPowerConnectorCheck"
        Option "TwinView" "1"
        Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
        Option "SecondMonitorHorizSync" "31-81"
        Option "SecondMonitorVertRefresh" "56-76"
        # Option "NoTwinViewXineramaInfo"
        Option "TwinViewOrientation" "Clone"
EndSection


Section "Monitor"
 Identifier      "Generic Monitor"
        Option          "DPMS"
        #HorizSync      28-51
        #VertRefresh    43-60
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        #HorizSync      28-51
        #VertRefresh    43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
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
                Viewport 0 0
                Depth           24
                Modes           "1280x1024" "1280x960" "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "TwinView Configuration"
        #Identifier     "Default Layout"
        Screen 0        "Default Screen" 0 0
 #Screen         "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        Option "Xinerama" "Off"
EndSection

Section "DRI"
        Mode    0666
EndSection



```

So what is happening now is basically my secondary monitor is starting up but not my primary sometimes I am able to get my username password in even though I can't see it then I find my toolbar somehow and drag it over to my secondary screen mean while the whole time my primary screen is in powersave mode I then try to set the resolution to 2560x1024 at 50HZ nothing new happens. Now I have set it to Clone so I can see the login information at least.

Help Me I am at my wits end!!!!

---

### Post by RawMustard on 2006-08-04
@mdampier

You need to run this command for me before we do anything.
```
nvidia-xconfig --query-gpu-info > ~/Desktop/gpu-query-info.txt
```
Then post the contents of the text file that gets created on your desktop.  Also, tell me how your screens are connected, ie.  vga or dvi connectors.  make sure both of your screens are connected and turned on.

---

### Post by mdampier on 2006-08-04
> **RawMustard said:**
> @mdampier

You need to run this command for me before we do anything.
```
nvidia-xconfig --query-gpu-info > ~/Desktop/gpu-query-info.txt
```
Then post the contents of the text file that gets created on your desktop.  Also, tell me how your screens are connected, ie.  vga or dvi connectors.  make sure both of your screens are connected and turned on.

Thanks for your response here is the info from the command you asked about:
```
Number of GPUs: 1

GPU #0:
  Name      : GeForce FX 5200
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 2

  Display Device 0 (DFP-0):
     EDID Name             : Dell 2001FP
     Minimum HorizSync     : 31.000 kHz
     Maximum HorizSync     : 80.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 76 Hz
     Maximum PixelClock    : 162.000 MHz
     Maximum Width         : 1600 pixels
     Maximum Height        : 1200 pixels
     Preferred Width       : 1600 pixels
     Preferred Height      : 1200 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 410 mm
     Physical Height       : 310 mm

  Display Device 1 (DFP-1):
     EDID Name             : Dell 2001FP
     Minimum HorizSync     : 31.000 kHz
     Maximum HorizSync     : 80.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 76 Hz
     Maximum PixelClock    : 162.000 MHz
     Maximum Width         : 1600 pixels
     Maximum Height        : 1200 pixels
     Preferred Width       : 1600 pixels
     Preferred Height      : 1200 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 410 mm
     Physical Height       : 310 mm
```

Both of my monitors are connected by DVI connectors. Both screens are securely connected to the machine and both have power. 
I have tested the exact same set up (same video card model and monitors) on my widows machine and they have worked fine.

This might be helpful for you as well:
My left screen is set up for my primary and my right screen is set up for my secondary (which is the one that actually displays). When I physically switch the displays on the DVI connetors then the right screens goes into powersave mode and the left comes on to display the secondary portion of the ubuntu desktop ie no menus.

---

### Post by RawMustard on 2006-08-04
Here ya go, yours was easy, almost the same as mine :)

```

# /etc/X11/xorg.conf (xorg X display server configuration file for nVidia TwinView for mdampier)
#
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
        Load    "record"
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
        Option          "Device"           "/dev/input/mice"
        Option          "Protocol"         "ExplorerPS/2"
        Option          "Emulate3Buttons"  "true"
        Option          "ZAxisMapping"     "4 5"
EndSection

Section "Device"
        Identifier     "Card0"
        Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "GeForce FX 5200"
        BusID          "PCI:1:0:0"
        Option         "ConnectedMonitor"          "DFP, DFP"
        Option         "TwinView"                  "1"
        Option         "TwinViewOrientation"       "RightOf"
        Option         "RenderAccel"               "1"
        Option         "HWcursor"                  "1"
        Option         "CursorShadow"              "1"
        Option         "CursorShadowAlpha"         "64"
        Option         "CursorShadowXOffset"       "4"
        Option         "CursorShadowYOffset"       "2"
        Option         "NoLogo"                    "1"
        Option         "MetaModes"                 "1600x1200,1600x1200; 1280x1024,1280x1024; 1024x768,1024x768; 800x600,800x600; 1600x1200,NUL; 1280x1024,NULL; 1024x768,NULL; 800x600,NULL"
        Option         "UseEdidFreqs"              "1"
#        Option         "UseEdidDpi"   "0"
#        Option         "DPI"          "86 x 86"
        Option         "HorizSync"    "DFP-0: UseEdidFreqs; DFP-1: UseEdidFreqs"
        Option         "VertRefresh"  "DFP-0: UseEdidFreqs; DFP-1: UseEdidFreqs"
EndSection

Section "Monitor"
        Identifier     "Dell 2001FP"
	Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Card0"
        Monitor        "Dell 2001FP"
	DefaultDepth    24
	SubSection "Display"
	       Depth    24
               #Modes   "1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen    0     "Screen0" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

You'll notice two options commented out "UseEdidDpi" and "DPI"
If you run this command
```
xdpyinfo |grep resolution -A 1 -B 1
```

which will return something like this:

```

  dimensions:    3200x1200 pixels (820x312 millimeters)
  resolution:    85x86 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
```

You can then set the correct dpi settings and un-comment those two options.  Nvidia will probably say 85x86 which isn't correct.

Of course you'll need to load up my config first before doing this :)

Let me know how you get on!

---

### Post by mdampier on 2006-08-04
> 

You'll notice two options commented out "UseEdidDpi" and "DPI"
If you run this command
```
xdpyinfo |grep resolution -A 1 -B 1
```

which will return something like this:

```

  dimensions:    3200x1200 pixels (820x312 millimeters)
  resolution:    85x86 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
```

You can then set the correct dpi settings and un-comment those two options.  Nvidia will probably say 85x86 which isn't correct.

Of course you'll need to load up my config first before doing this :)

Let me know how you get on!

I used the config file you gave me exactly but I still only have one screen coming up. :confused: 
However I now have the 3200x1200 @ 50hz resolution option which i didn't before. I chose that and nothing happened. 

I ran the command you gave me and these are the specs I got:
```
 dimensions:    3200x1200 pixels (821x311 millimeters)
  resolution:    99x98 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
```

then i went to the config file and changed one of the commented out DPI settings:
```
#        Option         "UseEdidDpi"   "0"
  Option         "DPI"          "99 x 98"
```
I left the other one commented out because I wasn't exactly sure how the format of the argument went so.....

I rebooted after that just in case... but still one monitor.
Anymore suggestions?
I also want to thank you for all the time you have already spent pondering my problem.

---

### Post by RawMustard on 2006-08-04
Can you do this for me?  Can you plug in your screens how you want them.  Load up the config I gave you. Then hit CNTRL+ALT+F1 to get to a terminal.  Login to this terminal with your normal username and password and then stop gdm ```
sudo /etc/init.d/gdm stop
``` once you've stopped gdm, type this command```
startx -- -logverbose 6
```
This will startx and give me a better log to see why your second monitor is being ignored.  Once X starts, open a terminal and type ```
gedit /var/log/Xorg.0.log
``` and copy the contents of it here.

---

### Post by Jose Catre-Vandis on 2006-08-06
Pleased to report success in sorting out a variant of twinview action, in terms of a TFT monitor and 36" widescreen TV. This was using a Shuttle PC with two VGA outputs and an SVideo output. TFT in one VGA, TV in SVideo. The big problem was with the Metamode settings. After about 4 hours of trying different settings I finally realised that I couldn't run the TFT at a different resolution to the TV, and this sorted things. The only other setting really needed was Twinview = true, practically no other settings were required. Both Clone and Rightof/Leftof work fine. This was the only way I could get a full screen displayed on the TV. The TV won't display full screen on anything above 1024x768. xorg.conf below:
```
Section "ServerLayout"
Identifier "single head configuration"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
#RgbPath "/usr/X11R6/lib/X11/rgb"
#FontPath "unix/:7100"
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
Load "dbe"
Load "extmod"
Load "glx"
Load "record"
Load "freetype"
Load "type1"
Load "dri"
EndSection

Section "ServerFlags"
Option "allowmouseopenfail"
EndSection

Section "InputDevice" Identifier "Keyboard0"
Driver "keyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "PS/2"
Option "Device" "/dev/psaux"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "yes"
EndSection

Section "InputDevice" Identifier "DevInputMice"
Driver "mouse"
Option "Protocol" "IMPS/2"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "no"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "DGM"
HorizSync 30.0 - 85.0
VertRefresh 48.0 - 120.0
Option "dpms"
EndSection

Section "Device"

Option "SecondMonitorHorizSync" "30.0-60.0"
Option "SecondMonitorVertRefresh" "48.0-80.0"
#Option "UseEdidFreqs" "true" #Probes for HorizSync and VertRefresh
Option "TwinView" "true" #Enables TwinView
Option "NoLogo" "true" #Turns off nvidia logo at x startup
Option "ConnectedMonitor" "TV-0, CRT-0"
Option "TwinviewOrientation" "clone" #Second monitor is clone of first
# Option "TwinviewOrientation" "RightOf" #Second monitor is desktop right of first
#######################################################
Option  "Metamodes" "1024x768,1024x768; 800x600,800x600"
#######################################################
# Option "TVStandard" "PAL-I"
# Option "TVOutFormat" "SVIDEO"
# Option "NvAGP" "2"
# Option "CursorShadow" "1"
# Option "CursorShadowAlpha" "64"
# Option "CursorShadowYOffset" "2"
# Option "CursorShadowXOffset" "2"
Identifier "Videocard0"
Driver "nvidia"
VendorName "Videocard vendor"
BoardName "NVIDIA GeForce 4 MX (generic)"
BusID "PCI:2:0:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
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
Depth 		24
Modes 		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
#Modes 		"1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "DRI"
Group 0
Mode 0666
EndSection
```

If anyone can suggest improvements to this, please let me know :-)

---

### Post by mdampier on 2006-08-07
> **RawMustard said:**
> Can you do this for me?  Can you plug in your screens how you want them.  Load up the config I gave you. Then hit CNTRL+ALT+F1 to get to a terminal.  Login to this terminal with your normal username and password and then stop gdm ```
sudo /etc/init.d/gdm stop
``` once you've stopped gdm, type this command```
startx -- -logverbose 6
```
This will startx and give me a better log to see why your second monitor is being ignored.  Once X starts, open a terminal and type ```
gedit /var/log/Xorg.0.log
``` and copy the contents of it here.


Ok I have performed what you requested here is a link to the results since the file length prevents me from posting here. 
Thanks again!

---

### Post by d4nd4n on 2006-08-08
Hey, I've got a similar problem to somebody further back in this thread regarding a laptop with external monitor. My problem is a little different however, I can get twinview to work fine but only with the same resolution on both monitors. Ideally, I want to use the widescreen highres on my laptop screen. Without this, the res is low and stretched a bit.

I don't mind having my external monitor as primary (down to the nvidia bug) and will have a seperate xorg.conf for single screen setups.

Here is my gpu info:
[http://psycho.g0at.net/gpu-info]("http://psycho.g0at.net/gpu-info")

Here is a debug which works, with both screens on 1280x1024:
[http://psycho.g0at.net/Xorg.0.log_working]("http://psycho.g0at.net/Xorg.0.log_working")
Here is a debug which doesn't work, with the 1280x1024,1920x1440:
[http://psycho.g0at.net/Xorg.0.log_broken]("http://psycho.g0at.net/Xorg.0.log_broken")

Here are the relevant bits of my configs (in their currently untidy mid-testing state)...

WORKING config with identical resolutions:
[http://psycho.g0at.net/xorg.conf_working]("http://psycho.g0at.net/xorg.conf_working")
BROKEN config with different resolutions:
[http://psycho.g0at.net/xorg.conf_broken]("http://psycho.g0at.net/xorg.conf_broken")

The main issue is that when I set the different resolutions, they are accepted and the X server seems happy with them, until the virtual screen is setup at only the resolution of the external monitor.

```

(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:1280x1024,DFP-0:1920x1440"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024

```

Any ideas/pointers here would be very helpful....

---

### Post by RawMustard on 2006-08-10
@mdampier.

Sorry M, it would seem you're suffering from a pretty well known bug I think with the fx 5200 cards and dual dvi output.  Your log files show that your xorg file is working properly.  I suggest you visit this forum, and ask the nvidia people about your problem.  That's the best I myself can offer you :(

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by paperdiesel on 2006-08-10
RawMustard,

Apparently you're a genius.  Can you help me too?

I'm trying to get xinerama to work.  (I know this is a twinview section).  I think I'm having the same problems that most people here are having.  The second monitor doesn't even turn on, and my main monitor displays at 1600x1200, even though I set it to 1280x1024.  Here's my config:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

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
  
  # path to defoma fonts
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "evdev"
  option "CorePointer"
  option "Device" "/dev/input/event9"
EndSection

Section "Monitor"
  identifier "viewSonic_monitor"
  vendorname "ViewSonic"
  modelname "ViewSonic E90"
  HorizSync 30-87
  VertRefresh 50-180
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  gamma 1.0
EndSection

Section "Monitor"
  identifier "AOC_monitor"
  vendorname "AOC"
  modelname "AOC SPECTRUM 7Glr & 7GlrA"
  HorizSync 30.0-95.0
  VertRefresh 50.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  gamma 1.0
EndSection

Section "Device"
  identifier "nvidia_device"
  boardname "NVIDIA GeForce 6800 (generic)"
  busid "PCI:1:0:0"
  driver "nvidia"
  vendorname "NVIDIA"
  #Option         "UseEdidDpi"   "0"
  #Option         "DPI"          "90 x 96"
  screen 0
EndSection

Section "Device"
  identifier "sis_device"
  boardname "XGI - Xabre Graphics Inc Volari Z7"
  busid "PCI:0:8:0"
  driver "sis"
  screen 1
EndSection

Section "Screen"
  Identifier "nvidia_screen"
  Device "nvidia_device"
  Monitor "viewSonic_monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@75" "1280x960@60" "1280x854" "1280x960@85" "1152x768@54" "1280x1024@60" "1152x864@75" "1280x960@75" "1024x768@43" "1400x1050@60" "1024x768@60" "1400x1050@75" "1024x768@70" "1600x1200@65" "1024x768@75" "1600x1200@60" "1024x768@85" "1600x1200@70" "832x624@75" "1792x1344@60" "800x600@60" "1856x1392@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection

Section "Screen"
  Identifier "sis_screen"
  Device "sis_device"
  Monitor "AOC_monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1024x768@75" "1024x768@70" "1024x768@85" "1024x768@60" "832x624@75" "1024x768@43" "800x600@60" "1152x864@75" "800x600@85" "1152x768@54" "800x600@75" "1280x854" "800x600@72" "1280x1024@75" "800x600@56" "1280x960@60" "640x480@85" "1280x960@85" "640x480@75" "1280x1024@85" "640x480@72" "1280x1024@60" "640x480@60" "1280x960@75" "1400x1050@60" "1400x1050@75" "1600x1200@65" "1600x1200@60" "1600x1200@75" "1600x1200@70" "1792x1344@60" "1856x1392@60" "1920x1440@60" "2048x1536@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "nvidia_screen"
  screen 1 "sis_screen" leftof "nvidia_screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
EndSection

Section "ServerFlags"
  Option "Xinerama" "on" 
EndSection

```

And here is an except from my /var/log/xorg.0.log:

```
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffff600 - 0xdffff6ff (0x100) MX[B]
	[5] -1	0	0xdffff780 - 0xdffff7ff (0x80) MX[B]
	[6] -1	0	0xdfff8000 - 0xdfffbfff (0x4000) MX[B]
	[7] -1	0	0xdffff800 - 0xdfffffff (0x800) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xdffe0000 - 0xdffe7fff (0x8000) MX[B](B)
	[14] -1	0	0xdff80000 - 0xdffbffff (0x40000) MX[B](B)
	[15] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B](B)
(WW) SIS: No matching Device section for instance (BusID PCI:0:8:0) found
(--) Chipset Volari Z7 (XG20) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffff600 - 0xdffff6ff (0x100) MX[B]
	[5] -1	0	0xdffff780 - 0xdffff7ff (0x80) MX[B]
	[6] -1	0	0xdfff8000 - 0xdfffbfff (0x4000) MX[B]
	[7] -1	0	0xdffff800 - 0xdfffffff (0x800) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xdffe0000 - 0xdffe7fff (0x8000) MX[B](B)
	[14] -1	0	0xdff80000 - 0xdffbffff (0x40000) MX[B](B)
	[15] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B](B)
(EE) Screen 1 deleted because of no matching config section.
(II) UnloadModule: "sis"
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffff600 - 0xdffff6ff (0x100) MX[B]
	[5] -1	0	0xdffff780 - 0xdffff7ff (0x80) MX[B]
	[6] -1	0	0xdfff8000 - 0xdfffbfff (0x4000) MX[B]
	[7] -1	0	0xdffff800 - 0xdfffffff (0x800) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xdffe0000 - 0xdffe7fff (0x8000) MX[B](B)
	[14] -1	0	0xdff80000 - 0xdffbffff (0x40000) MX[B](B)
	[15] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[34] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.40.02.12.01
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic E90-4 (CRT-1)
(--) NVIDIA(0): ViewSonic E90-4 (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "1600x1200@70"; removing.
(WW) NVIDIA(0): No valid modes for "1792x1344@60"; removing.
(WW) NVIDIA(0): No valid modes for "1856x1392@60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024@75"
(II) NVIDIA(0):     "1280x960@60"
(II) NVIDIA(0):     "1280x854"
(II) NVIDIA(0):     "1280x960@85"
(II) NVIDIA(0):     "1152x768@54"
(II) NVIDIA(0):     "1280x1024@60"
(II) NVIDIA(0):     "1152x864@75"
(II) NVIDIA(0):     "1280x960@75"
(II) NVIDIA(0):     "1024x768@43"
(II) NVIDIA(0):     "1400x1050@60"
(II) NVIDIA(0):     "1024x768@60"
(II) NVIDIA(0):     "1400x1050@75"
(II) NVIDIA(0):     "1024x768@70"
(II) NVIDIA(0):     "1600x1200@65"
(II) NVIDIA(0):     "1024x768@75"
(II) NVIDIA(0):     "1600x1200@60"
(II) NVIDIA(0):     "1024x768@85"
(II) NVIDIA(0):     "832x624@75"
(II) NVIDIA(0):     "800x600@60"
(II) NVIDIA(0):     "800x600@85"
(II) NVIDIA(0):     "800x600@75"
(II) NVIDIA(0):     "800x600@72"
(II) NVIDIA(0):     "800x600@56"
(II) NVIDIA(0):     "640x480@85"
(II) NVIDIA(0):     "640x480@75"
(II) NVIDIA(0):     "640x480@72"
(II) NVIDIA(0):     "640x480@60"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (90, 96); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[1] 0	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdffff600 - 0xdffff6ff (0x100) MX[B]
	[8] -1	0	0xdffff780 - 0xdffff7ff (0x80) MX[B]
	[9] -1	0	0xdfff8000 - 0xdfffbfff (0x4000) MX[B]
	[10] -1	0	0xdffff800 - 0xdfffffff (0x800) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0xdffe0000 - 0xdffe7fff (0x8000) MX[B](B)
	[17] -1	0	0xdff80000 - 0xdffbffff (0x40000) MX[B](B)
	[18] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[37] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024@75"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
```

So when I try xinerama, my second screen stays off, and my main screen has a large virtual resolution.  Any ideas?

---

### Post by RawMustard on 2006-08-11
@paperdiesel and d4nd4n

Can you run this command for me before we do anything.
```
nvidia-xconfig --query-gpu-info > ~/Desktop/gpu-query-info.txt
```
Then post the contents of the text file that gets created on your desktop. Make sure both of your screens are connected and turned on.

I'' then see what I can do for you's both.

@paperdiesel I wouldn't say I'm a genius with this stuff, far from it :)

---

### Post by mtang on 2006-08-13
Hi everyone, I'm currently trying to work out the kinks of a new Dapper install (my second), and I've gotten TwinView to the point where I'm almost happy with it.  The only problem is that I'd like to switch the "default" monitor, so that my login screen shows up there.  The GNOME panels and everything else I'm not too worried about, because I can move those around.

My setup right now is an LCD through DVI on the left, and an LCD through VGA on the right.  Ideally, I'd like the left screen to be the primary display.

The output from nvidia-xconfig:
```

Number of GPUs: 1

GPU #0:
  Name      : GeForce 7600 GS
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 2

  Display Device 0 (CRT-1):
     EDID Name             : Dell E193FP
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 83.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 76 Hz
     Maximum PixelClock    : 140.000 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 1024 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 1024 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 380 mm
     Physical Height       : 300 mm

  Display Device 1 (DFP-0):
     EDID Name             : Dell 1905FP
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 81.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 76 Hz
     Maximum PixelClock    : 140.000 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 1024 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 1024 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 380 mm
     Physical Height       : 310 mm

```

And my current xorg.conf:
```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
    Option      "Buttons" "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier  "NVIDIA Corporation NVIDIA Default Card"
        Driver      "nvidia"
        BusID       "PCI:1:0:0"
        Option      "ConnectedMonitor" "DFP-0,CRT-1"
        Option      "NoLogo" "1"
        Option      "NoPowerConnectorCheck"
        Option      "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 1024x768,1024x768; 800x600,800x600; 1280x1024,NULL; 1024x768,NULL"
        Option      "TwinView" "True"
        Option      "TwinViewOrientation" "DFP-0 LeftOf CRT-1"
        Option      "UseEdidFreqs" "True"
EndSection

Section "Monitor"
        Identifier      "DELL 1905FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "DELL 1905FP"
        DefaultDepth    24
        SubSection "Display"
        Viewport    0 0
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          1 "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option      "Xinerama" "Off"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Thanks!

---

### Post by d4nd4n on 2006-08-14
@RawMustard

All the info you should need is in the links I put in my original post. Here is the GPU one again: [http://psycho.g0at.net/gpu-info]("http://psycho.g0at.net/gpu-info")

My problem specifically is getting the correct different resolutions across both monitors (laptop and flatscreen CTX). Cheers for any help you can give me. I can only get it working if I put both screens as 1280x1024 :(

---

### Post by mdampier on 2006-08-16
> **RawMustard said:**
> @mdampier.

Sorry M, it would seem you're suffering from a pretty well known bug I think with the fx 5200 cards and dual dvi output.  Your log files show that your xorg file is working properly.  I suggest you visit this forum, and ask the nvidia people about your problem.  That's the best I myself can offer you :(

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Thanks RawMustard for all your help!

---

### Post by jstritar on 2006-09-06
I'm also trying to make the left monitor my "default" so that the login screen appears there. Also, how can I make it so that when I maximize/fullscreen a window it just fits the screen its currently in, rather than both of my monitors?

> **mtang said:**
> Hi everyone, I'm currently trying to work out the kinks of a new Dapper install (my second), and I've gotten TwinView to the point where I'm almost happy with it.  The only problem is that I'd like to switch the "default" monitor, so that my login screen shows up there.  The GNOME panels and everything else I'm not too worried about, because I can move those around.

My setup right now is an LCD through DVI on the left, and an LCD through VGA on the right.  Ideally, I'd like the left screen to be the primary display.

The output from nvidia-xconfig:
```

Number of GPUs: 1

GPU #0:
  Name      : GeForce 7600 GS
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 2

  Display Device 0 (CRT-1):
     EDID Name             : Dell E193FP
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 83.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 76 Hz
     Maximum PixelClock    : 140.000 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 1024 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 1024 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 380 mm
     Physical Height       : 300 mm

  Display Device 1 (DFP-0):
     EDID Name             : Dell 1905FP
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 81.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 76 Hz
     Maximum PixelClock    : 140.000 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 1024 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 1024 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 380 mm
     Physical Height       : 310 mm

```

And my current xorg.conf:
```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
    Option      "Buttons" "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier  "NVIDIA Corporation NVIDIA Default Card"
        Driver      "nvidia"
        BusID       "PCI:1:0:0"
        Option      "ConnectedMonitor" "DFP-0,CRT-1"
        Option      "NoLogo" "1"
        Option      "NoPowerConnectorCheck"
        Option      "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 1024x768,1024x768; 800x600,800x600; 1280x1024,NULL; 1024x768,NULL"
        Option      "TwinView" "True"
        Option      "TwinViewOrientation" "DFP-0 LeftOf CRT-1"
        Option      "UseEdidFreqs" "True"
EndSection

Section "Monitor"
        Identifier      "DELL 1905FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "DELL 1905FP"
        DefaultDepth    24
        SubSection "Display"
        Viewport    0 0
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
        Viewport    0 0
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          1 "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option      "Xinerama" "Off"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Thanks!

---

### Post by LTBookman on 2006-09-13
Hi, I followed your instructions to configure TwinView and it **did** work, but I'm experiencing a problem I haven't managed to fix: the clone of my desktop doesn't fill all the screen of my TV, but is instead kind of embedded into a black frame. Is there any way (I could do that on Windows, so I bet there must be one) I can *expand* the image so its size fits that of the TV?

TIA

---

### Post by mtron on 2006-09-15
if i'm not wrong it's impossible to "clone" the CRT with another resolution to the TV, better to setup 2 X-Screens,

---

### Post by munk on 2006-10-11
Thanks for the HOWTO! Worked beautifully for me on Dapper with a Geforce 7900 GT into twin 19" Benq LCDs via DVI.

Cheers

---

### Post by Lego on 2006-10-31
I have an lcd monitor (1280x1024) and a tv (1280x720), connected via hdmi/dvi to a geforce 7800gt

I'd like to use the tv to watch videos
In windows I'd set the resolution to 1280x720p cloned on both screen, resulting with a 1280x720 stretched to 1280x1024 on the lcd screen

I've tried all the combinations I could think of, but I can't get a similar setup on linux
I can't set a stretched 1280x720 on the lcd
The best I could get was a 1280x1024 on the lcd, and a 1280x720 on the tv (but representing only a portion of the desktop)
I also tried using two separates x screen, but it's not a good solution for me, as I use the tv only to watch movies!

I'd really like to have a setup similar to my windows one!

thanks :)

edit:
If I try to set a NULL, 1280x720 metamode to have only the tv on, the desktop is not correctly centered, but it has what it should be the top on the center of the screen
sorry for the bad english :mad:

---

### Post by vipjun on 2007-01-14
I've been trying get twinview working for about three days now.  I think I spent about 20hrs yesterday.
Hopefully someone can help me out after I wake up because I haven't slept for about 25hrs trying to get this thing working lol.

Im using Dapper 6.06
Driver version 8776
Geforece FX 5200 on 2 of the same HC194D LCD monitors. one dvi the other vga.

I don't know why my second monitor is being detected as 350mhz or  doesn't seem to be recongized
I have tried explicitly stating the frequency using both methods, SecondMonitorHorizSync and just the regular HorizSync Attribute. Both yield the same results.

If you see something commented out, it means I've tried that setting before.

xorg.conf

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option "Xinerama" "Off"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option "TwinView" "1"
    Option "TwinViewOrientation" "RightOf"   
    Option "SecondMonitorHorizSync" "31-81"
    Option "SecondMonitorVertRefresh" "56-75"
    Option "UseEdidFreqs" "false"
    #Option "MetaModes" "1280x1024, 1280x1024; 800x600, 800x600"
    Option "UseDisplayDevice" "DFP"
    Option "ConnectedMonitor" "DFP, CRT"
EndSection
Section "Monitor"
	Identifier "HC194D"
	Option "DPMS"
EndSection
Section "Screen"
    Identifier	   "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "HC194D"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480" "640x400"
    EndSubSection
EndSection

---

### Post by vipjun on 2007-01-14
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux jun-ubuntu 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
Build Date: 16 March 2006

Module Loader present

(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 14 06:18:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "HC194D"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "Off"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 8086,2560 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 8086,4232 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 8086,4232 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 8086,4232 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 8086,4232 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 8086,4232 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 8086,4232 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 8086,0109 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:06:0: chip 1095,3112 card 1095,3112 rev 01 class 01,80,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 8086,301e rev 82 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc800000 - 0xfe8fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4500000 - 0xf45fffff (0x10100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0206 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfeafffff (0x200000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4600000 - 0xf46fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfe8e0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffdff (0x200) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d080 - 0x0000d0bf (0x40) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffdff (0x200) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d080 - 0x0000d0bf (0x40) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffdff (0x200) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d080 - 0x0000d0bf (0x40) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[27] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]

---

### Post by vipjun on 2007-01-14
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffdff (0x200) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d080 - 0x0000d0bf (0x40) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[27] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffdff (0x200) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d080 - 0x0000d0bf (0x40) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[30] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP, CRT"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "31-81"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "56-75"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(WW) NVIDIA(0): No TwinView "MetaModes" specified; will fall back to Display
(WW) NVIDIA(0):     SubSection modes.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP, CRT"
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.27.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     HSD HC194D (CRT-0)
(--) NVIDIA(0):     HSD HC194D (DFP-0)
(--) NVIDIA(0): HSD HC194D (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): HSD HC194D (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): HSD HC194D (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0".
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "832x624"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(WW) NVIDIA(0): No valid modes for "640x640"; removing.
(WW) NVIDIA(0): No valid modes for "640x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffdff (0x200) MX[B]
	[8] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[9] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[10] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[14] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d080 - 0x0000d0bf (0x40) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[23] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[27] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[32] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "640x480"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
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
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by vipjun on 2007-01-14
I put metamodes in back in and commented out

#Option "UseDisplayDevice" "DFP"
#Option "ConnectedMonitor" "DFP, CRT"

Ubuntu detected the second monitor after that.

The problem now is the destkop is showing on the right screen, instead of the left screen, making the VGA connected monitor the primary instead of the DVI.

I wouldn't mind it so much if not for the KVM switch that only connects via VGA so I prefer my primary monitor be on DVI.

So how do I set this without breaking twinview yet again?

---

### Post by vipjun on 2007-01-14
I put metamodes in back in and commented out

#Option "UseDisplayDevice" "DFP"
#Option "ConnectedMonitor" "DFP, CRT"

Ubuntu detected the second monitor after that.

The problem now is the destkop is showing on the right screen, instead of the left screen, making the VGA connected monitor the primary instead of the DVI.

I wouldn't mind it so much if not for the KVM switch that only connects via VGA so I prefer my primary monitor be on DVI.

So how do I set this without breaking twinview yet again?

Update--

The monitor is off the KVM switch now, and seems like it hasn't fixed anything.
Should I use a different method to do this instead of Twinview from what I know it's not the only option?

---

### Post by vipjun on 2007-01-14
> **jstritar said:**
> I'm also trying to make the left monitor my "default" so that the login screen appears there. Also, how can I make it so that when I maximize/fullscreen a window it just fits the screen its currently in, rather than both of my monitors?

You can try putting this in your Section "Device"

Option "UseDisplayDevice" "DFP-0"

substitute "DFP-0" for the monitor you want as primary,

Then
Option      "TwinViewOrientation" "DFP-0 LeftOf CRT-1"

I think this is what should happen, even tho It doesn't seem like its working for me.

---

### Post by -::Bas::- on 2007-01-21
I can't get this twinview to work.
I have a 6600gt, lcd connected through dvi and tv via s-video. Would the s-video be the problem? Does X think I have my tv attached to my vga-port?

It bothers me like hell, I keep having to go back to m$ windh0w$ when I want to watch a film..:frown: 

Here is my xorg.conf : 
```
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
	Option		"XkbVariant"	"intl"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
	Option 		"TwinView" 		"True"
	Option 		"TwinViewOrientation" 	"LeftOf"   
	Option 		"UseEdidFreqs" 		"True"
	Option 		"MetaModes" 		"1440x900,1024x768" 
	Option 		"UseDisplayDevice" 	"DFP,TV" 
	Option 		"ConnectedMonitor"	"DFP,TV"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
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
```

---

### Post by Skeorx13 on 2007-03-01
Alrighty. I'm more or less brand new to Linux this week. I'm on Ubuntu 6.10 and I have two LCD monitors on an XFX GeForce 7600 gt XXX PCI-E card. One is 19" DVI (which I'm using as my primary screen) and the other is a 15" VGA plugged into a VGA>DVI adapter plug. The 19" is a ViewEra V192WD with max resolution of 1280x1024, Horizontal at 30-81 KHz, and Vertical at 55-75 Hz. The 15" is a KDS rad5 with max res of 1024x768, Horizontal at 30-60 KHz, and Vertical at 55-75 Hz. I ganked some code from my brother's setup (who is far more experienced than I with Linux) and tweaked my way through this thread. I got my monitors to work in twinview, but with a slight problem. The largest graphics mode I can get to is 2304x1024. Problem is my 15" monitor can only support 1024x768. So 256 pixels at the bottom of my small screen (ie the bottom task bar thingy) is cut off. I was curious if someone could recommend an edit to my xorg.conf file to correct the resolution so I am not losing this space (without messing with the Viewera 19" monitor's resolution. I was also wondering if there was a way to split the screens into two separate and individual desktops (like using the tabs at the bottom right corner to switch between them or what have you. I'd really like to have to separate desktop backgrounds (but isn't all that vital as I'm pretty comfortable with my graphical editing skills to make a wide spanning background file that merely incorporates two "individual" jpgs). This seemed WAY easier to setup in windows, but I'm sure that the Linux way is far more tweakable to personal preference... I'm also not sure if the display subsections for depth 1-16 are necessary, but they were there to begin with so I didn't want to delete something that could have an ill effect. [COLOR="Silver"]Also after editing this my volume icon in the upper taskbar thingy swapped spots with the date and shutdown button (which is now in the direct middle of my 15" monitor's top taskbar - I'd get a screenshot but I have yet to figure out how to do that...). What the hell did that is beyond me.[/COLOR] So anyone that can help me [COLOR="Silver"]fix that[/COLOR] or merely edit my file to be more efficient or organized would be great too. Thanks a lot for putting up with my n00b questions. 

Edit: Figured out how to manipulate the task bars and moved the stuff that was locked in the cut off space to the top bar, so now it's just a matter of other applications getting cut off when loaded (errors in azureus are completely unseen).

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

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
    Screen      0  "Default Screen [0]" 0 0
    Screen      1  "Default Screen [1]" RightOf "Default Screen [0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Radius [0]"
    Option         "DPMS"
    HorizSync	   30-60
    VertRefresh	   55-75
EndSection

Section "Monitor"
    Identifier     "ViewEra [1]"
    Option         "DPMS"
    HorizSync	   30-81
    VertRefresh	   55-75
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen	   0
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card1"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen	   1
EndSection

Section "Screen"
    Identifier     "Default Screen [0]"
    Device         "NVIDIA Corporation NVIDIA Default Card0"
    Monitor        "Radius [0]"
    DefaultDepth    24
    Option         "Twinview" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "55-75"
    Option         "NvAGP" "1"
    Option         "HWCursor" "0"
    Option         "SWCursor" "1"
    Option         "NoLogo" "False"
    Option         "RenderAccel" "True"
    Option         "MetaModes" "1280x1024,1024x768; 1024x768,1280x1024; 1280x1024,1280x1024; 1152x864,1152x864; 1024x768,1024x768; 832x624,832x624; 800x600,800x600; 720x400,720x400; 640x480,640x480; 1280x1024,null; 1152x684,null; 1024x768,null; 832x624,null; 800x600,null; 720x400,null; 640x480,null"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Default Screen [1]"
    Device         "NVIDIA Corporation NVIDIA Default Card1"
    Monitor        "ViewEra [1]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection



---

### Post by JohnSCS on 2007-03-15
Hi All,

I'm new to this forum and new to Ubuntu (not so new to linux). Started playing around about a week ago due to the usual reasons (M$). I Love this OS.

My first problem was that I couldn't dock my laptop and use the external monitor only. The Fn+F8 key rarely worked and when it did the resolutions were wrong. Many posts explain how to get two monitors working, which is not a major project, but I found very little about docking and swapping between the laptop screen and an external.

My laptop setup is as follows

Dell D620 Core Duo 1.83Ghz
1gb RAM, 100Gb SATA HDD
Intel® PRO/Wireless 3945ABG
DVD+-RW Drive
Nvidia NVS110M Video 256Mb
1440x900 WXGA+ screen
Dell Advanced D/Port replicator with FP1905 external TFT monitor via DVI

OS - Ubuntu Edgy 6.10 (upgraded from 6.06) kernel - 2.6.17.11-386

Had issues installing 6.10 (the second time) - problem with the ipw3945 wireless drivers and hardware conflicting during boot up - reason for upgrade from 6.06 as the  system could install 6.06.

Wireless updated to WPA and running as per forum posts on this issue.
Nvidia driver updated and running as per forum posts.

Running dual monitors was not a big issue, but did take time - this thread was great for achieving this. But to run the external monitor only when docked and the laptop screen when undocked was an issue. Due to issues with the Nvidia driver, Fn+F8 seems to be erratic or not working at all.

So heres my solution - not true plug and play, but atleast you don't have to reboot the laptop every time you dock/undock

Below is my settings from my xorg.conf file that has gotten me to this stage.

How it works -
With the laptop running and at the desktop - dock it, Ctrl+Alt+Backspace. The screens should swap to the external screen to log back in.
To undock - remove from dock, Ctrl+Alt+Backspace. The screens should swap back to the laptop to login again.

Of course you can't keep programs open to do this, but it does save on reboot time.

My xorg.conf has 1440x900 resolution for ny laptop screen, and 1280x1024 for my external screen (this may need to be changed for different monitors)

But as I said, I am happy at this stage, would love Fn+F8 to work - but maybe latter. The benefit of this OS over M$ makes up for it.

Good luck.



Section "Device"
        Identifier     "Card0"
        Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "Nvidia Quadra NVS110M"
        BusID          "PCI:1:0:0"
	Option		"NvAGP"	"1"
        Option         "UseDisplayDevice"          "DFP-1, CRT-0"
        Option         "TwinView"                  "1"
        Option         "TwinViewOrientation"       "LeftOf"
       Option         "NoLogo"                    "1"
        Option         "MetaModes"                 "CRT-0: 1440x900, DFP-1: 1280x1024"
        Option         "UseEdidFreqs"              "1"
        Option         "HorizSync"    "CRT-0: 55-56; DFP-1: 30-81"
        Option         "VertRefresh"  "CRT-0: 60-60; DFP-1: 56-76"
EndSection

Section "Monitor"
        Identifier     "Monitor0"
	Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Card0"
        Monitor        "Monitor0"
	DefaultDepth    24
	SubSection "Display"
	       Depth    24
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen    0     "Screen0" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by RyanGT on 2007-09-29
Is it possible to have two different aspect ratios when doing a projector output?  I would like 1680x1050 on my widescreen laptop and 1280x1024 on the projector.  I can't seem to make this work.  

If this can't be done, what my laptop does in windows in this situation is switch the laptop monitor to run in non-widescreen mode.  I set the resolution to 1280x1024 and push a button, the black space is left on the right and left of my screen.  This keeps the laptop display from looking squashed.  Is this possible?

Thanks,

Ryan

---

### Post by DouglasAWh on 2007-11-02
Can someone post a HOWTO for Gutsy?  Mine keeps asking for a driver...for a monitor.  Sounds weird to me.

---

### Post by ElSeeDee on 2008-04-04
Ooh... no one has posted here in a while. I wonder if it's still being watched.

Anywho, I followed the How-to with 7.10, a GeForce2 MX400 dual-head video card, a 17' CRT (primary) and a 17" LCD (secondary) (both VGA). Both monitors get recognized. I can drag windows from on to the other. "Ok. What's the problem," you say? My second monitor screen is blue. :confused:  No other colors - shades of blue & shades of black. And no matter which monitor I plug into the 2nd head, it's blue.

Here is my xorg:

```
Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"NvAGP"		"2"
	Option		"RenderAccel"	"False"
	Option		"CursorShadow"	"True"
	Option		"CoolBits"	"True"
	Option		"ConnectedMonitor"	"crt, dfp"
	Option		"NoPowerConnectorCheck"
	Option		"TwinView"	"True"
	Option		"Metamodes"	"1024x768,1024x768; 800x600,800x600; 1024x768,NULL"
	Option		"SecondMonitorHorizontalSync"	"31-82"
	Option		"SecondMonitorVertRefresh"	"56-76"
	# Option	"NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Viewport 0 0
		Modes		"1024x768"	"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Option	"Xinerama"	"Off"
```

Anybody see/know anything that might solve my "blue screen of life"?

BTW, I'm only using 2 resolutions because I'm setting it for my mom. She doesn't see too well and I'm going to use the second monitor for screen magnification of the first monitor.

---

### Post by ElSeeDee on 2008-04-04
OK. nevermind. I did a little more digging in the forums. I found a post that recommended the nvidia-glx-legacy package for GeForce2 cards. I switched packages and poof! no more "blue screen of life"!

---

### Post by mteppo on 2008-04-17
> **Lego said:**
> I have an lcd monitor (1280x1024) and a tv (1280x720), connected via hdmi/dvi to a geforce 7800gt

I'd like to use the tv to watch videos
In windows I'd set the resolution to 1280x720p cloned on both screen, resulting with a 1280x720 stretched to 1280x1024 on the lcd screen
<snip>

edit:
If I try to set a NULL, 1280x720 metamode to have only the tv on, the desktop is not correctly centered, but it has what it should be the top on the center of the screen
sorry for the bad english :mad:

I have similar issue. 
I'm using LG vga-LCD as primary (1280x1024) and Sanyo PLZ5 (1280x720) as secondary (hdmi) - secondary mainly used for tv & movies.
My mobo (Asus M2N-VM hdmi) has Nvidia 7050 integrated and I have fresh Gutsy install on that.

I can get the "clone" to work as follows:

```

+-------------------+
|                   |
|  LG + Sanyo       |
|                   |
+-------------------+
|                   |
|  LG only          |
+-------------------+

```

But on my radeon 9200 I also could get which is perfect for 16:9 movies and tolerable for 4:3
```

+-------------------+
|  LG only          |
+-------------------+
|                   |
|  LG + Sanyo       |
|                   |
+-------------------+
|  LG only          |
+-------------------+

```

The thing I'm not sure on my previous radeon 9200 & Edgy/Feisty setup is that whether the Sanyo was actually fed 4:3 picture which it just smartly cropped. On radeon the sanyo was connected to analog (thru dvi - analog converter but I think this should have no effect on the issue itself).

Anyway the question is - is this possible?
I tried tweaking with nvidia-settings but could not figure out a way.


EDIT:
Ok - so if I configured the screens as separate I could position them more freely. So Xinerama on and Twinview off.
This is until I think of better way of doing this.
And this was doable with nvidia-settings

---

### Post by bharkins on 2008-04-29
OK, I have been reading this long thread of 22 pages and found a wealth of information for dual monitors. Here is my xorg.conf (Hardy 8.04 LTS): Sorry, I don't know how to get the nice box around the code that everybody uses. I am using my HP notebook as primary display and a Samsung HDTV as the 2nd monitor to demonstrate my limited Ubuntu knowledge to a small Windows group. Notice that this file is much shorter than the ones shown in prior posts which were for earlier Ubuntu Versions. Should I start to edit this file based on some of the early files shown, or is there a better way? Nvidia Settings did not set it up correctly, but "sort of" worked. Any advise greatly appreciated.

CODE

[SIZE="1"][FONT="Arial"]# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection[/FONT][/SIZE]

---

### Post by madiga01 on 2008-10-08
Hello
I have been got TwinView working.However is there anyway to make a fullscreen application open only in one monitor?
Thanks

---

### Post by padeossa on 2008-12-04
i`ll try the howto..  because always i have trouble with this configuration, and never works the things that i try..

Mi Vcard es a fx5900xt

---

### Post by BarryM on 2009-04-17
Hello there,this is my first post. I am sure I am being incredibly thick over this, but is there an idiot guide for setting up twinview?

I have a new DFP (Samsung 1680 x 1050) that I want to set up as the primary screen and an old analogue LCD (Proview 1280 x 1024) that I want as secondary screen, and am worried that if I tinker with xorg.conf and get it wrong I may end up with a system I cannot boot.

Barry

---

### Post by alek66 on 2009-05-19
hi everyone, i got working my tv out. But I want to clone what I see on my monitor to what i see on the TV out. 
How can I do that?

---

