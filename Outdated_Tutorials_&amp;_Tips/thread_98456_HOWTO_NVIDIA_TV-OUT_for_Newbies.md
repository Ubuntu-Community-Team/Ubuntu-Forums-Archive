---
title: "HOWTO: NVIDIA TV-OUT for Newbies"
date: 2005-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-12-03
**[COLOR="Red"]This guide works on Ubuntu Breezy and Ubuntu Dapper. Now it works also with driver 8762[/COLOR]**

**NOTE: this guide has been translated into German by cfBuba:**
[http://www.ubuntu-forum.de/thread.php?threadid=13096](http://www.ubuntu-forum.de/thread.php?threadid=13096)

This guide is inspired to Promethe's, who I really want to thank because I have managed to get my TV-OUT to work thanks to his guide: [HOWTO: TV-out in Hoary (nVidia?)]("http://ubuntuforums.org/showthread.php?t=23628&highlight=Tv-out")

My guide is aimed at newbies who want to enable the TV-OUT port of their Nvidia graphic card. It works ONLY if you have a Nvidia card and it requires the Nvidia proprietary drivers.
If you need a guide to the installation of the Nvidia drivers your can try mine: 

[Guide for Breezy]("http://ubuntuforums.org/showthread.php?t=75074")

[Guide for Dapper]("http://www.ubuntuforums.org/showthread.php?t=139264")

If you have problems with the resolution of your main Monitor: [HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")


Make a backup of your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
.
Edit your xorg.conf
If you use GNOME
```
sudo gedit /etc/X11/xorg.conf
```
OR if you use KDE
```
sudo kedit /etc/X11/xorg.conf
```
OR (this will work on every graphical interface)
```
sudo nano /etc/X11/xorg.conf
```

Get to the  &#8220;Monitor&#8221; section and change the name (i.e. the identifier) of your current monitor to &#8220;Monitor[0]&#8221; and make it look like the following example:

Before:
```
Section "Monitor"
	Identifier	"AL1715"
	Option		"DPMS"
EndSection
```
After:
```
Section "Monitor"
	Identifier "Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync 31.5-80 
        	VertRefresh 56.3-75 
EndSection
```

In my case the monitor had been detected by Ubuntu as "AL1715" therefore no refresh parameters were set (because that name corresponded to a particular profile)
If your monitor already has the its HorizSync and  VertRefresh leave them as they are. 
If it doesn't have them then you will have to put them manually as in the previous example (you can find the frequencies of vertical and horizontal refresh for your monitor in its manual or on the internet, in the website of its manufacturer)

Now you have to add your TV as the second monitor. You have to add the following lines under the section of the 1st monitor.

```
 Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection
``` 

If you wish, you can change the HorizSync and VertRefresh, but those values should work fine on most new TVs.

Get to the "Device" section.
Now you have to change the name (i.e. the identifier) of your primary device (i.e. your graphic card) to "Device[0]" and add the parameter &#8220;screen 0&#8221; as in the (2nd) example:
Before:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection
```

After:
```
Section "Device"
	Identifier	[COLOR="Red"]"Device[0]"[/COLOR]
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	[COLOR="Red"]screen 0[/COLOR]
EndSection
```

Now you have to add the TV-OUT as a device below your Device[0] and add all the options listed below. Make it look EXACTLY like this example:

```
Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-G" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection
```

You might want to change 2 things in the example above:
1)You can change "Composite" to  &#8220;SVIDEO&#8221; (according to the type of video cable you use)
2)You can change your TVstandard from  &#8220;PAL-G&#8221; to &#8220;NTSC-M&#8221; or "NTSC-J" according to your tv.

If you did everything correctly you should have two Section &#8220;Device&#8221; like in the example below:

```
Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-G" #or NTSC-M etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection
```


Get to the &#8220;Screen&#8221; section and change Identifier, Monitor and Screen like in the (2nd) example below:

Before:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"AL1715"
etc.
```

After:
```
Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
```

[Of course the Screen section is longer than the one in the example (it contains your screen resolution, etc.)]

Now you have to put another section under the previous. Make the new section look EXACTLY like the following example: 

```
Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection
```


**NOTE if your TV does not support a refresh rate of 60Hz you might want to set this line "Modes "1024x768_60"" as "Modes "1024x768_50"" in order to set the refresh rate to 50Hz**

If you did everything correctly you should have two Section &#8220;Screen&#8221; like in the example below (OF COURSE the resolutions you have in your xorg.conf are likely to be different from mine, therefore leave them as they are):

```
Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]" 
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

Section "Screen" 
   Device "Device[1]" 
   Identifier "Screen[1]" 
   Monitor "Monitor[1]" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       EndSubSection    
EndSection
```


Now you have to change your "ServerLayout" section and make it look like the following example:

```
Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "[COLOR="Red"]Mouse1[/COLOR]" "CorePointer" 
   InputDevice "[COLOR="Blue"]Keyboard1[/COLOR]" "CoreKeyboard" 
EndSection
```

Then change the two words in red and blue in the previous example with the ones you can find in your &#8220;InputDevice" section (which I will put in red and blue respectively):

In my case the "InputDevice" Section is the following:
```
Section "InputDevice"
	Identifier	"[COLOR="Blue"]Generic Keyboard[/COLOR]"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"[COLOR="Red"]Configured Mouse[/COLOR]"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

Therefore in my case the result would be the following:

```
Section "ServerLayout" 
   	Identifier  "Simple Layout" 
       	Screen 0 "Screen[0]" 
       	Screen 1 "Screen[1]" RightOf "Screen[0]" 
   	InputDevice "[COLOR="Red"]Configured Mouse[/COLOR]" "CorePointer" 
   	InputDevice "[COLOR="Blue"]Generic Keyboard[/COLOR]" "CoreKeyboard" 
EndSection
```

Ok, now save your xorg.conf and exit.

Now, let's try it.
Plug in the video cable (make sure that both your TV and your graphic card are linked by this cable)
Log out
Restart your computer.
Then log in and you will be able to see your desktop on your TV screen (ONLY after you login). Keep in mind that it is not a clone of your current desktop. It has its own resolution and you can use it INDEPENDENTLY from the desktop you can see on your main monitor.

For example you can watch a film (in full screen) on your TV screen while writing a text or surfing the web on your main monitor. 

Here's how it works:

Move your mouse to the extreme right part of the screen until it disappears from your main monitor.  You will now be able to see the cursor on your TV. From there you can use the cursor to open the files you need etc.

If you need to use the mouse cursor in your 1st desktop you have to move it to the extreme left of the screen until it disappears from your TV and reappears on your main Monitor.

Enjoy!

Alberto

---

### Post by corruption on 2005-12-05
I've run through all the listed steps in both this guide and the previously referenced one, and I never get anything displayed on my television. X loads fine, everything seems to be working, but to get display, I have to run the nvtv frontend and configure everything by hand, which ends with me having cloned screens and locked resolution. Any ideas as to what I may be doing wrong?

---

### Post by tseliot on 2005-12-05
[QUOTE=corruption]I've run through all the listed steps in both this guide and the previously referenced one, and I never get anything displayed on my television. X loads fine, everything seems to be working, but to get display, I have to run the nvtv frontend and configure everything by hand, which ends with me having cloned screens and locked resolution. Any ideas as to what I may be doing wrong?[/QUOTE]
Did you restart your computer?
nvtv is automatically launched every time you boot Ubuntu.

---

### Post by tabinin on 2005-12-05
Thank you for this Howto.  This has been the biggest struggle that I have had with Linux, right after Japanese input. 

I have a display on my tv, with its own task bar.  I am still having a couple of small problems...

One is that my autostart applications are starting and running on both screens.  Any way I can get them to start only on "screen 0"?

The other problem is that I would like to be able to drag a mplayer window into screen 1 (TV), like I could in Windows.  Any way to do that (or, are there any easy tricks or commands to get mplayer to open/play a movie directly on the tv?

I am using Kubuntu and a FX5200 card.

---

### Post by slide on 2005-12-05
I followed the guide step by step (even went back through it a few times to make sure) but it just wont work. Whenever gdm starts all i see is a black screen. In order to get the actual login prompt to show up i have to manually change the resolution. The mouse can always go off to the right of the screen but it just comes right back on the left side. I can tell though that its trying to use a resolution of 1024x768 as the mouse is restricted to the upper left corner. I noticed in my Xorg.0.log that i get 
```
(WW) NVIDIA(1): Invalid ConnectedMonitor string token: "Monitor[1]";
(WW) NVIDIA(1):      discarding token.
```

and futher down it says

```
(II) NVIDIA(1): Connected display device(s): CRT-0
```

My xorg.conf [http://rafb.net/paste/results/68jSsd63.html](http://rafb.net/paste/results/68jSsd63.html)
My Xorg.0.log [http://rafb.net/paste/results/asBLj525.html](http://rafb.net/paste/results/asBLj525.html)

Thanks

---

### Post by tabinin on 2005-12-05
Slide,

One thing I noticed is that

```

Option "TVOutFormat" "SVIDEO"

```

should be with a dash in "S**-**VIDEO"

```
Option "TVOutFormat"  "S-VIDEO"
```

I don't know if that si going to solve your problem, but is worth the addition.


I found something else.  Take a look at this section from my (working) config:

Section "Device"
   	Identifier      "Device[0]" 
   	Driver      	"nvidia" 
   	BusID      	"PCI:1:0:0" 
   	Screen       	0 
   	Option          "ConnectedMonitor" "Monitor[0]"
	Option 		"NoLogo" "true
EndSection

Section "Device" 
   Driver          "nvidia" 
   Identifier      "Device[1]" 
   Screen 	1
	Option       "TwinView" "true" 
   Option          "TVOutFormat" "COMPOSITE"
   Option          "TVStandard" "NTSC**-M**"
   Option          "ConnectedMonitor" "**TV**" 
   BusID           "PCI:1:0:0" 
EndSection

The bolded parts are different than yours.

---

### Post by slide on 2005-12-05
Yes, got it to work! :)
Ok, so tabinin you were right about the TVStandard being NTSC-M, but the TVOutFormat can only be SVIDEO and COMPOSITE, this is what i got in the log when i set it to S-VIDEO.

```

(**) NVIDIA(1): Option "TVOutFormat" "S-VIDEO"
(**) NVIDIA(1): Unknown TVOutFormat value.  Known values are "SVIDEO" and
(**) NVIDIA(1):      "COMPOSITE"
```

I don't know exactly what was wrong, it seems that xorg didnt like the name Monitor[1] and when i changed it to TV it works now, shrug. Thanks! :)

---

### Post by tseliot on 2005-12-06
[QUOTE=slide]Yes, got it to work! :)
Ok, so tabinin you were right about the TVStandard being NTSC-M, but the TVOutFormat can only be SVIDEO and COMPOSITE, this is what i got in the log when i set it to S-VIDEO.

```

(**) NVIDIA(1): Option "TVOutFormat" "S-VIDEO"
(**) NVIDIA(1): Unknown TVOutFormat value.  Known values are "SVIDEO" and
(**) NVIDIA(1):      "COMPOSITE"
```

I don't know exactly what was wrong, it seems that xorg didnt like the name Monitor[1] and when i changed it to TV it works now, shrug. Thanks! :)[/QUOTE]

Weird... Anyhow I'll fix the s-video thing

---

### Post by Knorhaen on 2005-12-06
I too had to change "Monitor[1]" to "TV".

However, my TV screen is still blank. I have the following messages in X.org's logfile:
```

(II) NVIDIA(0): Connected display device(s): CRT-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display

```
What's going on?

---

### Post by tseliot on 2005-12-06
[QUOTE=Knorhaen]I too had to change "Monitor[1]" to "TV".

However, my TV screen is still blank. I have the following messages in X.org's logfile:
```

(II) NVIDIA(0): Connected display device(s): CRT-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display

```
What's going on?[/QUOTE]

Post your /etc/X11/xorg.conf , please.

---

### Post by Knorhaen on 2005-12-06
I've attached my xorg.conf to this message.

---

### Post by misse- on 2005-12-06
My Xorg.0.log gave me the following error (except those about "(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)") 

```
(EE) NVIDIA(1): This GPU cannot be shared by 2 X screens
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ddc"
```

I'm not quite sure what to make of it, my Geforce 3 Ti 200 works in windows with tv-tools with PAL and color.. when I use the frontend for nvtv, I can clone the image, but no color on my TV. :-?

Here's my Xorg.conf

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
	BusID		"PCI:1:0:0"
	VideoRam	64000
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   	Option          "TVStandard" "NTSC-M" #or NTSC etc 
	#Option          "ConnectedMonitor" "TV" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection


Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"TV" #TV
	HorizSync 60
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
   	Monitor "TV" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "800x600" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
	Screen	0	"Screen[0]"
	Screen 	1	"Screen[1]" rightof "Screen[0]"
	InputDevice "Configured Mouse"	"CorePointer"
	InputDevice "Generic Keyboard"	"CoreKeyboard"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by tseliot on 2005-12-06
[QUOTE=Knorhaen]I've attached my xorg.conf to this message.[/QUOTE]
I hope I can help you tomorrow because today (I have deadlines) I have to finish writing (correcting actually) the abstract of my thesis (I'm going to get my degree on December 14).
Please, don't feel abandoned;) .

---

### Post by Knorhaen on 2005-12-06
[QUOTE=tseliot]I hope I can help you tomorrow because today (I have deadlines) I have to finish writing (correcting actually) the abstract of my thesis (I'm going to get my degree on December 14).
Please, don't feel abandoned;) .[/QUOTE]
I wont, don't worry! ;) 

I'll try to fiddle around with the settings a bit, maybe I can work this out on my own.

---

### Post by Knorhaen on 2005-12-06
I managed to remove all errors by renaming "Monitor[0]" to "CRT" and "Monitor[1]" to TV.

I still don't have an image on my TV, though. I suspect the composite-cable is broken: all software appears to be working fine, but the image on my TV is not recognizable and completely distorted.

---

### Post by misse- on 2005-12-06
[QUOTE=Knorhaen]I managed to remove all errors by renaming "Monitor[0]" to "CRT" and "Monitor[1]" to TV.

I still don't have an image on my TV, though. I suspect the composite-cable is broken: all software appears to be working fine, but the image on my TV is not recognizable and completely distorted.[/QUOTE]

I'll try that, thanks. :)
Do you think you can find the time to go through my xorg.conf, that I've posted earlier? I've looked through it several times, but my head's full of schoolwork so I can't really focus.

Oh,and tseliot, I've installed the latest nvidia drivers through automatix, and they're working properly with the splash-image 'n all. Do I still have to re-install them according to your guide?

---

### Post by el3ktro on 2005-12-06
Thanks for this how-to, I'll try it this evening. One question though, what is nvtv actually used for? What does it do? Some people said they used nvtv to configure this thing, so where is the difference then configuring it in xorg.conf? Well it seems that with your how-to you get two full-blown desktops, is there a way to get a blank, black screen on the TV, and just display a video from e.g. mplayer/xine on the TV?


Tom

---

### Post by tseliot on 2005-12-07
[QUOTE=misse-]My Xorg.0.log gave me the following error (except those about "(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)") 

```
(EE) NVIDIA(1): This GPU cannot be shared by 2 X screens
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ddc"
```

I'm not quite sure what to make of it, my Geforce 3 Ti 200 works in windows with tv-tools with PAL and color.. when I use the frontend for nvtv, I can clone the image, but no color on my TV. :-?

Here's my Xorg.conf

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
	BusID		"PCI:1:0:0"
	VideoRam	64000
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   	Option          "TVStandard" "NTSC-M" #or NTSC etc 
	#Option          "ConnectedMonitor" "TV" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection


Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"TV" #TV
	HorizSync 60
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
   	Monitor "TV" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "800x600" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
	Screen	0	"Screen[0]"
	Screen 	1	"Screen[1]" rightof "Screen[0]"
	InputDevice "Configured Mouse"	"CorePointer"
	InputDevice "Generic Keyboard"	"CoreKeyboard"
EndSection

Section "DRI"
	Mode	0666
EndSection

```[/QUOTE]

Add this option in the "Section Device" of your xorg.conf: 
```
Option "IgnoreEDID" "True"
```
Then log out and press CTRL+ALT+BACKSPACE

If this doesn't solve the problem try this:
press CTRL+ALT+F1
type "sudo /etc/init.d/gdm stop" OR (if you use KDE) "sudo /etc/init.d/kdm stop"
then "startx -- -verbose 5 -logverbose 5"

and post the output

---

### Post by tseliot on 2005-12-07
[QUOTE=el3ktro]Thanks for this how-to, I'll try it this evening. One question though, what is nvtv actually used for? What does it do?[/QUOTE]
According to the description in Synaptic "This is a program to control the TV encoder chips on NVidia cards under
Linux, in order to get tv-out with a wide range of resolutions and
sizes, including "overscan" modes."

[QUOTE=el3ktro]Some people said they used nvtv to configure this thing, so where is the difference then configuring it in xorg.conf?[/QUOTE]
I know that another way to get tv-out to work that is Twinview (you can find a good guide in this forum about it). However I can tell you that (according to my experience) if you play movies on your tv with Twinview they would not be perfect, perhaps there's something wrong with refresh rate but the movies don't seem to run smoothly. I don't know how to explain it better.

[QUOTE=el3ktro]Well it seems that with your how-to you get two full-blown desktops, is there a way to get a blank, black screen on the TV, and just display a video from e.g. mplayer/xine on the TV?[/QUOTE]
Yes, it's possible but it doesn't work for me. The following method is a quotation from the guide which inspired mine:

... we will add small bash feature, which will let us to run players on second screen easly.
Do following in terminal:

```
sudo gedit /etc/bash.bashrc
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
tv totem movie.avi
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

---

### Post by tseliot on 2005-12-07
[QUOTE=Knorhaen]I managed to remove all errors by renaming "Monitor[0]" to "CRT" and "Monitor[1]" to TV.

I still don't have an image on my TV, though. I suspect the composite-cable is broken: all software appears to be working fine, but the image on my TV is not recognizable and completely distorted.[/QUOTE]
Please try with another cable and let me know

---

### Post by Knorhaen on 2005-12-08
I've replaced the composite-cable. The distortion is gone, but now the TV-screen stays black. Looking at X's logfile, it ought to be working... I really don't understand what's going on.

(I tried to attach X's logfile, but the forum says it's to big. I don't have any webspace myself...)

---

### Post by tseliot on 2005-12-08
[QUOTE=Knorhaen]I've replaced the composite-cable. The distortion is gone, but now the TV-screen stays black. Looking at X's logfile, it ought to be working... I really don't understand what's going on.

(I tried to attach X's logfile, but the forum says it's to big. I don't have any webspace myself...)[/QUOTE]
Do this:
CTRL+ALT+F1
sudo /etc/init.d/gdm stop
startx -- -verbose 5 -logverbose 5

and post the output

(if it doesn't fit the page you can split the output in two posts)

---

### Post by Knorhaen on 2005-12-09
OK, here's part 1 of of Xorg.log:
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux vhe-400113 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-686 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:25:32 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  9 10:48:48 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "CRT"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Generic Keyboard"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7190 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:02:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:0e:0: chip 13f6,0111 card 153b,1144 rev 10 class 04,01,00 hdr 00
(II) PCI: 00:10:0: chip 10b7,9004 card 10b7,9004 rev 04 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 104c,8400 card 1186,3b01 rev 00 class 02,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0110 card 1554,1081 rev a1 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0088 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 161, Mem @ 0xdc000000/24, 0xd0000000/27
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
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[1] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[2] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[3] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[7] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[9] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[1] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[2] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[3] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[7] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[9] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
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
	[5] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[6] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[7] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[8] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
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
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7667
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
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
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7667
	Module class: XFree86 Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7667  Fri Jun 17 07:03:12 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Found 2 PCI NVIDIA devices
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[6] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[7] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[8] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) NVIDIA(1): Sharing PCI entity with Screen 0
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[6] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[7] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[8] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[22] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.2, 1.2, 1.2)
(**) NVIDIA(0): Option "HWcursor" "true"
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT"
(**) NVIDIA(0): Using HW cursor
(==) NVIDIA(0): Video key set to default value of 0x101fe
(**) NVIDIA(0): ConnectedMonitor string: "CRT"
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xDC000000
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(0): Boot display device(s): CRT-0
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce2 MX/MX 400
(II) NVIDIA(0): Chip Architecture: 0x10
(II) NVIDIA(0): Chip Implementation: 0x11
(II) NVIDIA(0): Chip Revision: 0xa1
(--) NVIDIA(0): VideoBIOS: 03.11.00.07.00
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(II) NVIDIA(0): Bus detected as AGP
(II) NVIDIA(0): Detected AGP rate: 2X
(--) NVIDIA(0): VideoRAM: 32768 kBytes
(II) NVIDIA(0): Using ConnectedMonitor string "CRT-0"
(II) NVIDIA(0): Enabled display device(s): CRT-0
(II) NVIDIA(0): Mapping display device 0 (CRT-0) to CRTC 0
(--) NVIDIA(0): CRT-0: maximum pixel clock: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): --- EDID Information for display device CRT-0 ---
(II) NVIDIA(0): Manufacturer: AOC  Model: a785  Serial#: 17140
(II) NVIDIA(0): Year: 2000  Week: 27
(II) NVIDIA(0): EDID Version: 1.2
(II) NVIDIA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NVIDIA(0): Sync:  Separate
(II) NVIDIA(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) NVIDIA(0): Gamma: 2.20
(II) NVIDIA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NVIDIA(0): First detailed timing is preferred mode
(II) NVIDIA(0): redX: 0.626 redY: 0.340   greenX: 0.288 greenY: 0.608
(II) NVIDIA(0): blueX: 0.148 blueY: 0.064   whiteX: 0.283 whiteY: 0.298
(II) NVIDIA(0): Supported VESA Video Modes:
(II) NVIDIA(0): 720x400@70Hz
(II) NVIDIA(0): 640x480@60Hz
(II) NVIDIA(0): 640x480@75Hz
(II) NVIDIA(0): 800x600@75Hz
(II) NVIDIA(0): 1024x768@75Hz
(II) NVIDIA(0): Manufacturer's mask: 0
(II) NVIDIA(0): Supported Future Video Modes:
(II) NVIDIA(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NVIDIA(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NVIDIA(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NVIDIA(0): #3: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NVIDIA(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) NVIDIA(0): Supported additional Video Mode:
(II) NVIDIA(0): clock: 135.0 MHz   Image Size:  300 x 230 mm
(II) NVIDIA(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NVIDIA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NVIDIA(0): Serial No: YESA017140
(II) NVIDIA(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 85 kHz, PixClock max 160 MHz
(II) NVIDIA(0): Monitor name: C787
(II) NVIDIA(0): --- End of EDID Information for display device CRT-0 ---
(II) NVIDIA(0): EDID reported maximum dimensions for display device CRT-0:
(II) NVIDIA(0):      width  : 1600
(II) NVIDIA(0):      height : 1200
(II) NVIDIA(0): Processing requested modes for display device CRT-0:
(II) NVIDIA(0):      "1024x768"
(II) NVIDIA(0):      "800x600"
(II) NVIDIA(0):      "640x480"
(II) NVIDIA(0): CRT: Using hsync range of 30.00-85.00 kHz
(II) NVIDIA(0): CRT: Using vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,CRT) mode clock 162MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,CRT) mode clock 175.5MHz exceeds DDC maximum 160MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,CRT) mode clock 204.8MHz exceeds DDC maximum 160MHz
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1920x1200,CRT) mode clock 193.16MHz exceeds DDC maximum 160MHz
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "896x672" (height 1344 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): Display dimensions: (320, 240) mm
(--) NVIDIA(0): DPI set to (81, 81)
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

```

---

### Post by Knorhaen on 2005-12-09
And part 2:
```

(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(==) NVIDIA(1): Using HW cursor
(**) NVIDIA(1): Forcing COMPOSITE video output
(==) NVIDIA(1): Video key set to default value of 0x101fe
(**) NVIDIA(1): ConnectedMonitor string: "TV"
(**) NVIDIA(1): TV Standard string: "PAL-B"
(--) NVIDIA(1): Linear framebuffer at 0xD0000000
(--) NVIDIA(1): MMIO registers at 0xDC000000
(--) NVIDIA(1): Found 2 CRTCs on board
(II) NVIDIA(1): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(1): Boot display device(s): CRT-0
(II) NVIDIA(1): NVIDIA GPU detected as: GeForce2 MX/MX 400
(II) NVIDIA(1): Chip Architecture: 0x10
(II) NVIDIA(1): Chip Implementation: 0x11
(II) NVIDIA(1): Chip Revision: 0xa1
(--) NVIDIA(1): VideoBIOS: 03.11.00.07.00
(--) NVIDIA(1): Interlaced video modes are not supported on this GPU
(II) NVIDIA(1): Bus detected as AGP
(II) NVIDIA(1): Detected AGP rate: 2X
(--) NVIDIA(1): VideoRAM: 32768 kBytes
(II) NVIDIA(1): Using ConnectedMonitor string "TV-0"
(II) NVIDIA(1): Enabled display device(s): TV-0
(--) NVIDIA(1): Detected TV Encoder: Chrontel 7005
(II) NVIDIA(1): Supported TV modes:
(II) NVIDIA(1):   TV Standard: NTSC-M: 320x200
(II) NVIDIA(1):   TV Standard: NTSC-M: 320x240
(II) NVIDIA(1):   TV Standard: NTSC-M: 400x300
(II) NVIDIA(1):   TV Standard: NTSC-M: 640x400
(II) NVIDIA(1):   TV Standard: NTSC-M: 640x480
(II) NVIDIA(1):   TV Standard: NTSC-M: 720x480
(II) NVIDIA(1):   TV Standard: NTSC-M: 800x600
(II) NVIDIA(1):   TV Standard: NTSC-M: 1024x768
(II) NVIDIA(1):   TV Standard: NTSC-J: 320x200
(II) NVIDIA(1):   TV Standard: NTSC-J: 320x240
(II) NVIDIA(1):   TV Standard: NTSC-J: 400x300
(II) NVIDIA(1):   TV Standard: NTSC-J: 640x400
(II) NVIDIA(1):   TV Standard: NTSC-J: 640x480
(II) NVIDIA(1):   TV Standard: NTSC-J: 720x480
(II) NVIDIA(1):   TV Standard: NTSC-J: 800x600
(II) NVIDIA(1):   TV Standard: NTSC-J: 1024x768
(II) NVIDIA(1):   TV Standard: PAL-M: 320x200
(II) NVIDIA(1):   TV Standard: PAL-M: 320x240
(II) NVIDIA(1):   TV Standard: PAL-M: 400x300
(II) NVIDIA(1):   TV Standard: PAL-M: 640x400
(II) NVIDIA(1):   TV Standard: PAL-M: 640x480
(II) NVIDIA(1):   TV Standard: PAL-M: 720x480
(II) NVIDIA(1):   TV Standard: PAL-M: 800x600
(II) NVIDIA(1):   TV Standard: PAL-M: 1024x768
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 320x200
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 320x240
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 400x300
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 640x400
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 640x480
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 720x576
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 800x600
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 1024x768
(II) NVIDIA(1):   TV Standard: PAL-N: 320x200
(II) NVIDIA(1):   TV Standard: PAL-N: 320x240
(II) NVIDIA(1):   TV Standard: PAL-N: 400x300
(II) NVIDIA(1):   TV Standard: PAL-N: 640x400
(II) NVIDIA(1):   TV Standard: PAL-N: 640x480
(II) NVIDIA(1):   TV Standard: PAL-N: 720x576
(II) NVIDIA(1):   TV Standard: PAL-N: 800x600
(II) NVIDIA(1):   TV Standard: PAL-N: 1024x768
(II) NVIDIA(1):   TV Standard: PAL-NC: 320x200
(II) NVIDIA(1):   TV Standard: PAL-NC: 320x240
(II) NVIDIA(1):   TV Standard: PAL-NC: 400x300
(II) NVIDIA(1):   TV Standard: PAL-NC: 640x400
(II) NVIDIA(1):   TV Standard: PAL-NC: 640x480
(II) NVIDIA(1):   TV Standard: PAL-NC: 720x576
(II) NVIDIA(1):   TV Standard: PAL-NC: 800x600
(II) NVIDIA(1):   TV Standard: PAL-NC: 1024x768
(II) NVIDIA(1): Mapping display device 0 (TV-0) to CRTC 1
(--) NVIDIA(1): TV-0: maximum pixel clock: 650 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(1): TVs do not provide EDIDs; skipping EDID probe on TV-0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(1): Saved console TV mode: 3
(II) NVIDIA(1): Processing requested modes for display device TV-0:
(II) NVIDIA(1):      "1024x768"
(II) NVIDIA(1): TV: Using hsync range of 30.00-50.00 kHz
(II) NVIDIA(1): TV: Using vrefresh value of 60.00 Hz
(II) NVIDIA(1): Clock range:  12.00 to 650.00 MHz
(II) NVIDIA(1): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1152x768" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "576x384" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(1): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(1): Not using default mode "1280x768" (width too large for virtual size)
(WW) NVIDIA(1): Not using mode "640x384" (not a valid TV mode)
(WW) NVIDIA(1): Not using mode "512x384" (not a valid TV mode)
(**) NVIDIA(1): Validated modes for display device TV-0:
(**) NVIDIA(1):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(1):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(1):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(1):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(1):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(1):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(==) NVIDIA(1): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/X11R6/lib/modules/libfb.a
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/X11R6/lib/modules/libramdac.a
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/X11R6/lib/modules/librac.a
(II) Module rac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[2] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[3] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[4] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[5] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[6] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[7] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[8] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[9] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[10] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[11] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[12] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): No MetaMode found for mode "1024x768"
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) NVIDIA(1): Memory mapped
(II) NVIDIA(1): Not allocating video overlay for second X screen sharing this
(II) NVIDIA(1):      GPU
(II) NVIDIA(1): Not allocating external video decoder object
(II) NVIDIA(1): kernel module enabled successfully
(II) NVIDIA(1): Interrupts enabled
(II) NVIDIA(1): No MetaMode found for mode "1024x768"
(II) NVIDIA(1): Setting mode "1024x768"
(II) NVIDIA(1): First mode initialized
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Visuals set up
(II) NVIDIA(1): Pixmap depths set up
(II) NVIDIA(1): GLX visuals set up
(II) NVIDIA(1): Framebuffer set up
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(II) NVIDIA(1): Default colormap initialized.
(II) NVIDIA(1): Palette loaded
(II) NVIDIA(1): Screen initialization complete
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(II) Initializing extension GLX
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/mice"
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
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

```

---

### Post by tseliot on 2005-12-09
[QUOTE=Knorhaen]And part 2:[/QUOTE]

Ok, Add this option in the "Section Device" of your xorg.conf: 
```
Option "IgnoreEDID" "True"
```
Then log out and press CTRL+ALT+BACKSPACE

If this doesn't solve the problem try this:
press CTRL+ALT+F1
type "sudo /etc/init.d/gdm stop" OR (if you use KDE) "sudo /etc/init.d/kdm stop"
then "startx -- -verbose 5 -logverbose 5"

and post the output

Tell me how it goes

---

### Post by Knorhaen on 2005-12-09
That had no noticable effect (I added the line to both "Dervice" sections, BTW).

X's logfile, part 1:
```


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux vhe-400113 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-686 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:25:32 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  9 13:13:04 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "CRT"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Generic Keyboard"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7190 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:02:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:0e:0: chip 13f6,0111 card 153b,1144 rev 10 class 04,01,00 hdr 00
(II) PCI: 00:10:0: chip 10b7,9004 card 10b7,9004 rev 04 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 104c,8400 card 1186,3b01 rev 00 class 02,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0110 card 1554,1081 rev a1 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0088 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 161, Mem @ 0xdc000000/24, 0xd0000000/27
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
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[1] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[2] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[3] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[7] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[9] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[1] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[2] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[3] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[7] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[9] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
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
	[5] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[6] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[7] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[8] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
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
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7667
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
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
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7667
	Module class: XFree86 Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7667  Fri Jun 17 07:03:12 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Found 2 PCI NVIDIA devices
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[6] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[7] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[8] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) NVIDIA(1): Sharing PCI entity with Screen 0
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[6] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[7] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[8] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[22] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.2, 1.2, 1.2)
(**) NVIDIA(0): Option "HWcursor" "true"
(**) NVIDIA(0): Option "IgnoreEDID" "True"
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT"
(**) NVIDIA(0): Using HW cursor
(==) NVIDIA(0): Video key set to default value of 0x101fe
(**) NVIDIA(0): Ignoring EDIDs
(**) NVIDIA(0): ConnectedMonitor string: "CRT"
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xDC000000
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(0): Boot display device(s): CRT-0
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce2 MX/MX 400
(II) NVIDIA(0): Chip Architecture: 0x10
(II) NVIDIA(0): Chip Implementation: 0x11
(II) NVIDIA(0): Chip Revision: 0xa1
(--) NVIDIA(0): VideoBIOS: 03.11.00.07.00
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(II) NVIDIA(0): Bus detected as AGP
(II) NVIDIA(0): Detected AGP rate: 2X
(--) NVIDIA(0): VideoRAM: 32768 kBytes
(II) NVIDIA(0): Using ConnectedMonitor string "CRT-0"
(II) NVIDIA(0): Enabled display device(s): CRT-0
(II) NVIDIA(0): Mapping display device 0 (CRT-0) to CRTC 0
(--) NVIDIA(0): CRT-0: maximum pixel clock: 350 MHz
(II) NVIDIA(0): Not probing EDIDs.
(II) NVIDIA(0): Processing requested modes for display device CRT-0:
(II) NVIDIA(0):      "1024x768"
(II) NVIDIA(0):      "800x600"
(II) NVIDIA(0):      "640x480"
(II) NVIDIA(0): CRT: Using hsync range of 30.00-85.00 kHz
(II) NVIDIA(0): CRT: Using vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(==) NVIDIA(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found

```

---

### Post by Knorhaen on 2005-12-09
Part 2:
```

(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "IgnoreEDID" "True"
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(==) NVIDIA(1): Using HW cursor
(**) NVIDIA(1): Forcing COMPOSITE video output
(==) NVIDIA(1): Video key set to default value of 0x101fe
(**) NVIDIA(1): Ignoring EDIDs
(**) NVIDIA(1): ConnectedMonitor string: "TV"
(**) NVIDIA(1): TV Standard string: "PAL-B"
(--) NVIDIA(1): Linear framebuffer at 0xD0000000
(--) NVIDIA(1): MMIO registers at 0xDC000000
(--) NVIDIA(1): Found 2 CRTCs on board
(II) NVIDIA(1): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(1): Boot display device(s): CRT-0
(II) NVIDIA(1): NVIDIA GPU detected as: GeForce2 MX/MX 400
(II) NVIDIA(1): Chip Architecture: 0x10
(II) NVIDIA(1): Chip Implementation: 0x11
(II) NVIDIA(1): Chip Revision: 0xa1
(--) NVIDIA(1): VideoBIOS: 03.11.00.07.00
(--) NVIDIA(1): Interlaced video modes are not supported on this GPU
(II) NVIDIA(1): Bus detected as AGP
(II) NVIDIA(1): Detected AGP rate: 2X
(--) NVIDIA(1): VideoRAM: 32768 kBytes
(II) NVIDIA(1): Using ConnectedMonitor string "TV-0"
(II) NVIDIA(1): Enabled display device(s): TV-0
(--) NVIDIA(1): Detected TV Encoder: Chrontel 7005
(II) NVIDIA(1): Supported TV modes:
(II) NVIDIA(1):   TV Standard: NTSC-M: 320x200
(II) NVIDIA(1):   TV Standard: NTSC-M: 320x240
(II) NVIDIA(1):   TV Standard: NTSC-M: 400x300
(II) NVIDIA(1):   TV Standard: NTSC-M: 640x400
(II) NVIDIA(1):   TV Standard: NTSC-M: 640x480
(II) NVIDIA(1):   TV Standard: NTSC-M: 720x480
(II) NVIDIA(1):   TV Standard: NTSC-M: 800x600
(II) NVIDIA(1):   TV Standard: NTSC-M: 1024x768
(II) NVIDIA(1):   TV Standard: NTSC-J: 320x200
(II) NVIDIA(1):   TV Standard: NTSC-J: 320x240
(II) NVIDIA(1):   TV Standard: NTSC-J: 400x300
(II) NVIDIA(1):   TV Standard: NTSC-J: 640x400
(II) NVIDIA(1):   TV Standard: NTSC-J: 640x480
(II) NVIDIA(1):   TV Standard: NTSC-J: 720x480
(II) NVIDIA(1):   TV Standard: NTSC-J: 800x600
(II) NVIDIA(1):   TV Standard: NTSC-J: 1024x768
(II) NVIDIA(1):   TV Standard: PAL-M: 320x200
(II) NVIDIA(1):   TV Standard: PAL-M: 320x240
(II) NVIDIA(1):   TV Standard: PAL-M: 400x300
(II) NVIDIA(1):   TV Standard: PAL-M: 640x400
(II) NVIDIA(1):   TV Standard: PAL-M: 640x480
(II) NVIDIA(1):   TV Standard: PAL-M: 720x480
(II) NVIDIA(1):   TV Standard: PAL-M: 800x600
(II) NVIDIA(1):   TV Standard: PAL-M: 1024x768
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 320x200
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 320x240
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 400x300
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 640x400
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 640x480
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 720x576
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 800x600
(II) NVIDIA(1):   TV Standard: PAL-BDGHI: 1024x768
(II) NVIDIA(1):   TV Standard: PAL-N: 320x200
(II) NVIDIA(1):   TV Standard: PAL-N: 320x240
(II) NVIDIA(1):   TV Standard: PAL-N: 400x300
(II) NVIDIA(1):   TV Standard: PAL-N: 640x400
(II) NVIDIA(1):   TV Standard: PAL-N: 640x480
(II) NVIDIA(1):   TV Standard: PAL-N: 720x576
(II) NVIDIA(1):   TV Standard: PAL-N: 800x600
(II) NVIDIA(1):   TV Standard: PAL-N: 1024x768
(II) NVIDIA(1):   TV Standard: PAL-NC: 320x200
(II) NVIDIA(1):   TV Standard: PAL-NC: 320x240
(II) NVIDIA(1):   TV Standard: PAL-NC: 400x300
(II) NVIDIA(1):   TV Standard: PAL-NC: 640x400
(II) NVIDIA(1):   TV Standard: PAL-NC: 640x480
(II) NVIDIA(1):   TV Standard: PAL-NC: 720x576
(II) NVIDIA(1):   TV Standard: PAL-NC: 800x600
(II) NVIDIA(1):   TV Standard: PAL-NC: 1024x768
(II) NVIDIA(1): Mapping display device 0 (TV-0) to CRTC 1
(--) NVIDIA(1): TV-0: maximum pixel clock: 650 MHz
(II) NVIDIA(1): Not probing EDIDs.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(1): Saved console TV mode: 3
(II) NVIDIA(1): Processing requested modes for display device TV-0:
(II) NVIDIA(1):      "1024x768"
(II) NVIDIA(1): TV: Using hsync range of 30.00-50.00 kHz
(II) NVIDIA(1): TV: Using vrefresh value of 60.00 Hz
(II) NVIDIA(1): Clock range:  12.00 to 650.00 MHz
(II) NVIDIA(1): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1152x768" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "576x384" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(1): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(1): Not using default mode "1280x768" (width too large for virtual size)
(WW) NVIDIA(1): Not using mode "640x384" (not a valid TV mode)
(WW) NVIDIA(1): Not using mode "512x384" (not a valid TV mode)
(**) NVIDIA(1): Validated modes for display device TV-0:
(**) NVIDIA(1):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(1):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(1):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(1):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(1):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(1):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(==) NVIDIA(1): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/X11R6/lib/modules/libfb.a
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/X11R6/lib/modules/libramdac.a
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/X11R6/lib/modules/librac.a
(II) Module rac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[2] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[3] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[4] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[5] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[6] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[7] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[8] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[9] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[10] -1	0	0xdf010000 - 0xdf010fff (0x1000) MX[B]
	[11] -1	0	0xdf011000 - 0xdf01107f (0x80) MX[B]
	[12] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): No MetaMode found for mode "1024x768"
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) NVIDIA(1): Memory mapped
(II) NVIDIA(1): Not allocating video overlay for second X screen sharing this
(II) NVIDIA(1):      GPU
(II) NVIDIA(1): Not allocating external video decoder object
(II) NVIDIA(1): kernel module enabled successfully
(II) NVIDIA(1): Interrupts enabled
(II) NVIDIA(1): No MetaMode found for mode "1024x768"
(II) NVIDIA(1): Setting mode "1024x768"
(II) NVIDIA(1): First mode initialized
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Visuals set up
(II) NVIDIA(1): Pixmap depths set up
(II) NVIDIA(1): GLX visuals set up
(II) NVIDIA(1): Framebuffer set up
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(II) NVIDIA(1): Default colormap initialized.
(II) NVIDIA(1): Palette loaded
(II) NVIDIA(1): Screen initialization complete
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(II) Initializing extension GLX
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/mice"
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
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

```

---

### Post by tseliot on 2005-12-09
[QUOTE=Knorhaen]Part 2:[/QUOTE]

Please put a space (a blank line) between a section and the next one. For example:
```
Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	50-160
	Gamma 1.2 1.2 1.2
EndSection
Section "Monitor" 
	Identifier "TV" #TV 
	HorizSync 60 
	VertRefresh 30-150 
EndSection
```

should be
```
Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	50-160
	Gamma 1.2 1.2 1.2
EndSection

Section "Monitor" 
	Identifier "TV" #TV 
	HorizSync 60 
	VertRefresh 30-150 
EndSection
```

Do it for all your xorg.conf.

I'll give you further instructions later

---

### Post by Knorhaen on 2005-12-09
[QUOTE=tseliot]
Do it for all your xorg.conf.
[/QUOTE]
Done.

---

### Post by tseliot on 2005-12-09
[QUOTE=Knorhaen]Done.[/QUOTE]
Everything seems ok in your xorg.conf.
I have some advices for you:
1) Try to switch (with your remote) between the A/V
2) You can see something on your TV only after you log in (in other words you will not be able to see the GDM or KDM login manager)

If those advices don't provide you the solution I apologise. I really can't think because I'm stressed as I'm going to get my degree next wednesday and I'm studying. I hope I can help you better after my degree.

---

### Post by corruption on 2005-12-10
I managed to get it working for myself, by doing as others mentioned and renaming the device names in xorg.conf. The only catch I've run into is I must have the tv on the input channel when I start X otherwise I'm stuck at a black screen on the CRT with no display on the tv. Small consolation for a 2nd desktop on the tv. Thanks!

---

### Post by tseliot on 2005-12-10
[QUOTE=corruption]I managed to get it working for myself, by doing as others mentioned and renaming the device names in xorg.conf. The only catch I've run into is I must have the tv on the input channel when I start X otherwise I'm stuck at a black screen on the CRT with no display on the tv. Small consolation for a 2nd desktop on the tv. Thanks![/QUOTE]
Ok, I'll fix the guide as soon as possible.

---

### Post by corruption on 2005-12-10
One more question... less of an issue, more personal curiosity.. does anyone know a way to set independent desktop backgrounds for each display? The image I use on my desktop, for lack of a better term, 'washes out' on the tv.. that is, the image is kind of blurry, a little distorted, and the colors seem to fluctuate in some spots.. when I've tried less color-intensive images, it looks fine, but I'm locked to the same image on both screens. Any help?

Also, and this one is really purely for the geek factor.. is there any way to start an xscreensaver session on the tv monitor, and leave the desktop monitor usable? This one is more of a pipe dream for myself, but it sure would be cool ;)

---

### Post by polt on 2005-12-22
How does this all work out on an HDTV? I'm using an nVidia 6600GT card with HDTV output. The TV standard in xorg.conf is set to HD1080i. Output is through an S-video connector to an nVidia adapter that breaks that out into component video. This plugs into the back of the HDTV. It looks REALLY NICE! except that it is a 1024x768 window sitting on a 1920x1080 background. I wish I could figure out how to make the window 1920x1080 (to match the TV) or at least 1600x900 (which nVidia recommends because of 15% overscan on most TVs). Any ideas on how to convince the nVidia drivers to do their thing? (BTW, I have Breezy Badger 5.10 AMD64, fresh install, on an Intel945 board.)

---

### Post by mo_x on 2005-12-22
refering to original post of tseliot.
The syntax used for the ConnectedMonitor option is incorrect. It is better to not use the ConnectedMonitor option unless you are experiencing problems.
The procedure of setting up multiple X screens is also descriped in the nvidia README that comes with the driver. It also explains al the options you can use in your xorg.conf.
I attached my xorg.conf as an example.

---

### Post by tseliot on 2005-12-22
[QUOTE=polt]How does this all work out on an HDTV? I'm using an nVidia 6600GT card with HDTV output. The TV standard in xorg.conf is set to HD1080i. Output is through an S-video connector to an nVidia adapter that breaks that out into component video. This plugs into the back of the HDTV. It looks REALLY NICE! except that it is a 1024x768 window sitting on a 1920x1080 background. I wish I could figure out how to make the window 1920x1080 (to match the TV) or at least 1600x900 (which nVidia recommends because of 15% overscan on most TVs). Any ideas on how to convince the nVidia drivers to do their thing? (BTW, I have Breezy Badger 5.10 AMD64, fresh install, on an Intel945 board.)[/QUOTE]
Try to modify the following section of your xorg.conf:
```
Section "Screen" 
   Device "Device[1]" 
   Identifier "Screen[1]" 
   Monitor "Monitor[1]" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 24 
               Modes "[COLOR="Red"]1024x768[/COLOR]" 
       EndSubSection    
EndSection
```

And make it look like this:
```
Section "Screen" 
   Device "Device[1]" 
   Identifier "Screen[1]" 
   Monitor "Monitor[1]" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 24 
               Modes "[COLOR="Red"]1920x1080[/COLOR]" 
       EndSubSection    
EndSection
```

Log out and CTRL+ALT+BACKSPACE

OR if it doesn't work have a look at the following guide to set the correct resolution: [Howto: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---

### Post by tseliot on 2005-12-22
[QUOTE=mo_x]refering to original post of tseliot.
The syntax used for the ConnectedMonitor option is incorrect. It is better to not use the ConnectedMonitor option unless you are experiencing problems.
The procedure of setting up multiple X screens is also descriped in the nvidia README that comes with the driver. It also explains al the options you can use in your xorg.conf.
I attached my xorg.conf as an example.[/QUOTE]
```
Option "ConnectedMonitor" "string"

    Allows you to override what the NVIDIA kernel module detects is
    connected to your video card. This may be useful, for example, if you
    use a KVM (keyboard, video, mouse) switch and you are switched away
    when X is started. In such a situation, the NVIDIA kernel module
    cannot detect what display devices are connected, and the NVIDIA X
    driver assumes you have a single CRT.

    Valid values for this option are "CRT" (cathode ray tube), "DFP"
    (digital flat panel), or "TV" (television); if using TwinView, this
    option may be a comma-separated list of display devices; e.g.: "CRT,
    CRT" or "CRT, DFP".

    NOTE: anything attached to a 15 pin VGA connector is regarded by the
    driver as a CRT. "DFP" should only be used to refer to flatpanels
    connected via a DVI port.
Default: string is NULL.
```
Ok I know it's not enabled  by default but it might solve some users' problems (this guide is for newbies). It won't damage or spoil anything so I don't see any problem. Anyhow if you do see a problem you can explain it to me (I'm kind of openminded)

---

### Post by mo_x on 2005-12-22
This is from your howto:
Option          "ConnectedMonitor" "Monitor[1]" 
but the valid options are "CRT", "DFP" or "TV". If you have a crt monitor and a tv connected is should be something like:
Option          "ConnectedMonitor" "CRT,TV"
Most of the time the driver will detect what devices are connected and the option is not necessary. When te option is not used correctly it can also cause problems.

---

### Post by tseliot on 2005-12-22
[QUOTE=mo_x]This is from your howto:
Option          "ConnectedMonitor" "Monitor[1]" 
but the valid options are "CRT", "DFP" or "TV". If you have a crt monitor and a tv connected is should be something like:
Option          "ConnectedMonitor" "CRT,TV"
Most of the time the driver will detect what devices are connected and the option is not necessary. When te option is not used correctly it can also cause problems.[/QUOTE]
I see your point, I don't have any problem but I'll fix that (I have to fix the entire guide according to the suggestions of the other users who had other problems)

---

### Post by mo_x on 2005-12-22
Because of the wrong syntax the ConnectedMonitor option is probably ignored. You can check /var/log/Xorg.0.log for warnings and errors.

---

### Post by tseliot on 2005-12-22
[QUOTE=mo_x]Because of the wrong syntax the ConnectedMonitor option is probably ignored. You can check /var/log/Xorg.0.log for warnings and errors.[/QUOTE]
Ok, thanks but I'll remove the option for now.

---

### Post by polt on 2005-12-22
This relates to HDTV support. My xorg.conf is now modified to bring it into line with this HowTo

> Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	60
	VertRefresh	30-150
        Option          "TVStandard" "HD1080i"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

When I reboot it comes up in 1024x768 mode. The output looks very good -- HDTV quality, but still a smaller window on a larger (1920x1080) screen.  /var/log/xorg.0.log reports that 1600x900 is a non-existent mode (even though nVidia 6600GT docs clearly show it exists). 

Most modes are not supported at this hsync rate, so I would suggest increasing your recommendation when HDTV is involved. When I raised it to 150 kHz the HDTV displayed only a part of the window. I'll report later on if anything in between works out.

Also, if you read carefully below you will see there are no 16x9 modes at all. I feel like there must be a setting that will guide the driver to start looking for these modes (like 1920x1080) because the card supports them.

> 
(II) NVIDIA(0): Generic Monitor: Using hsync value of 60.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 30.00-150.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 650.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x175" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x400" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "720x400" (hsync out of range)
(II) NVIDIA(0): Not using default mode "360x200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x240" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x240" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x240" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x240" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "832x624" (hsync out of range)
(II) NVIDIA(0): Not using default mode "416x312" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x800" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x400" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(0): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using mode "1600x900" (no mode of this name)
(II) NVIDIA(0): Not using mode "800x600" (no mode of this name)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "512x384" (not a valid TV mode)
(**) NVIDIA(0): Validated modes for display device TV-0:
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768


---

### Post by mo_x on 2005-12-22
I think in the howto the values for HorizSync and VertRefresh have been mixed up
from the howto:
```
HorizSync 60 
VertRefresh 30-150
```
from the nvidia readme:
```
HorizSync 30-50
VertRefresh 60
```

---

### Post by tseliot on 2005-12-22
[QUOTE=mo_x]I think in the howto the values for HorizSync and VertRefresh have been mixed up
from the howto:
```
HorizSync 60 
VertRefresh 30-150
```
from the nvidia readme:
```
HorizSync 30-50
VertRefresh 60
```[/QUOTE]
Thanks for making me notice. I suppose the stress due to my graduation made me do many mistakes. I should have some rest;) .

---

### Post by tseliot on 2005-12-22
[QUOTE=polt]This relates to HDTV support. My xorg.conf is now modified to bring it into line with this HowTo.
Also, if you read carefully below you will see there are no 16x9 modes at all. I feel like there must be a setting that will guide the driver to start looking for these modes (like 1920x1080) because the card supports them.[/QUOTE]
If Mo_x suggestion (i.e. correction) doesn't work for you you should have a look at the following guide [http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---

### Post by polt on 2005-12-22
HorizSync vs. VertRefresh

Well, we're all trying to figure this out. If we knew it, we wouldn't be here.  ;)   I found something on the nVidia website called NVIDIA Accelerated Linux Driver Set README and Installation Guide. Its available by FTP (HTTP doen't work!?) at [http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8178/README/index.html]("ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-8178/README/index.html")
It might be a little out of date

Anyhow, they recommend using

> #
    HorizSync 30-50
    VertRefresh 60


I think that's a little low for a decent HDTV.

When I increase HorizSync to 30-100 the video doesn't work right and GUI is unusable. (Use Ctrl-Alt-F1 to get back to terminal and recover your xorg.conf backup.) Notice that we now need a range of Vertical Refresh rates to satisfy the card.

I don't want to pollute this sytem with XP, but I'm tempted to try it just to see what the Windows driver can do. The xorg.0.log file gives me no hope that HDTV is supported in 16x9 aspect ratio with the Linux driver, but the video card user manual is very clear that those modes *are* supported.

> 
(II) NVIDIA(0): Generic Monitor: Using hsync range of 30.00-100.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 650.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "576x432" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x512" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x512" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "576x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "576x432" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "700x525" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "700x525" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "700x525" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "960x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "960x720" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "928x696" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "896x672" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "960x600" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "840x525" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "700x525" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "640x512" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "720x450" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "640x384" (not a valid TV mode)
(WW) NVIDIA(0): Not using mode "512x384" (not a valid TV mode)
(**) NVIDIA(0): Validated modes for display device TV-0:
(**) NVIDIA(0):      Default mode "1024x768": 133.5 MHz, 95.3 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768


---

### Post by mo_x on 2005-12-22
How are you connecting the HDTV, throught tv-out or dvi?
The 1.0-8178 is very recent (today).

---

### Post by polt on 2005-12-22
Connection Method

The card is a Gigabyte 6600GT.  My HDTV has only component video inputs (3 wires colored Red, Green and Blue) and no DVI connector (actually it has one but it is incompatible with the usual flat screen cable and they say not to plug a computer in there). There is an adapter that plugs into the S-VIDEO output on the video card and breaks that out into component video. That is what I'm using to connect with the HDTV.

---

### Post by tseliot on 2005-12-22
[QUOTE=polt]Connection Method

The card is a Gigabyte 6600GT.  My HDTV has only component video inputs (3 wires colored Red, Green and Blue) and no DVI connector (actually it has one but it is incompatible with the usual flat screen cable and they say not to plug a computer in there). There is an adapter that plugs into the S-VIDEO output on the video card and breaks that out into component video. That is what I'm using to connect with the HDTV.[/QUOTE]
What's the model of your HDTV?

---

### Post by polt on 2005-12-22
It's a big Sony  projection model a couple of years old. It's a 1080i system. I don't think 1080p is supported, but I'm not really sure yet. Can't find the manual to give exact model number.

It's pretty clear that the nVidia card is not talking with the monitor. The component video connection is recommended in the manual for HDTV connection. It is an analog, one-way communication. IMHO, it's something about the driver or the configuration that is preventing the 16x9 video modes from appearing.

---

### Post by tseliot on 2005-12-22
[QUOTE=polt]It's a big Sony  projection model a couple of years old. It's a 1080i system. I don't think 1080p is supported, but I'm not really sure yet.[/QUOTE]
If you know the name of the model you can find the supported refresh rates and resolutions.

---

### Post by tseliot on 2005-12-22
UPDATE: I've put Option  "ConnectedMonitor" back in the guide because in my case the Xserver doesn't work if I disable that option.

EDIT: I have installed driver 8178 and its GREAT. It adds an application "Nvidia X server settings" which lets you tweak both your TV and Monitor performance.

---

### Post by tseliot on 2005-12-22
[QUOTE=polt]It's a big Sony  projection model a couple of years old. It's a 1080i system. I don't think 1080p is supported, but I'm not really sure yet. Can't find the manual to give exact model number.

It's pretty clear that the nVidia card is not talking with the monitor. The component video connection is recommended in the manual for HDTV connection. It is an analog, one-way communication. IMHO, it's something about the driver or the configuration that is preventing the 16x9 video modes from appearing.[/QUOTE]
After you find the exact model of your HDTV have a look at this:
```
The "TVStandard" option should be added to your screen section; valid values are:
TVStandard	Description	
"PAL-B"	used in Belgium, Denmark, Finland, Germany, Guinea, Hong Kong, India, Indonesia, Italy, Malaysia, The Netherlands, Norway, Portugal, Singapore, Spain, Sweden, and Switzerland	
"PAL-D"	used in China and North Korea	
"PAL-G"	used in Denmark, Finland, Germany, Italy, Malaysia, The Netherlands, Norway, Portugal, Spain, Sweden, and Switzerland	
"PAL-H"	used in Belgium	
"PAL-I"	used in Hong Kong and The United Kingdom	
"PAL-K1"	used in Guinea	
"PAL-M"	used in Brazil	
"PAL-N"	used in France, Paraguay, and Uruguay	
"PAL-NC"	used in Argentina	
"NTSC-J"	used in Japan	
"NTSC-M"	used in Canada, Chile, Colombia, Costa Rica, Ecuador, Haiti, Honduras, Mexico, Panama, Puerto Rico, South Korea, Taiwan, United States of America, and Venezuela	
[COLOR="Red"]"HD480i"	480 line interlaced	
"HD480p"	480 line progressive	
"HD720p"	720 line progressive	
"HD1080i"	1080 line interlaced	
"HD1080p"	1080 line progressive	
"HD576i"	576 line interlace	
"HD576p"	576 line progressive[/COLOR]
```

---

### Post by polt on 2005-12-22
I'm not sure what you mean?

I have been using HD1080i all along and getting a very nice 1024x768 window. I can also coax it up to 1280x1024, but that runs into "overscan" problems.

The ideal resoltuion is "1600x900," but the Linux software does not recognize the existence of that TV mode. (Take a look at the xorg.0.log files I posted earlier.)

I have tried a very wide range of refresh rates and horizontal syncs. None of the settings gives me anything but 4x3 windows on a 16x9 screen.

The point is: the present thread is great for TV, but I have yet to see it work for HDTV. I'm hoping we can figure out how to improve it. Has anyone gotten the recommendations of this HowTo to work on HDTV (not flat-screen monitor)?

---

### Post by mo_x on 2005-12-23
@polt
I suggest you try the new 1.0-8178 driver. It has some improvements for HDTV modes.
Also take a look on the nvidia linux forums, there are various threads on making HDTV work.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by cdhotfire on 2005-12-24
Is is possible to only have one desktop? Meaning, is there a way to show whats on my monitor in the tv?

---

### Post by Luzbel on 2005-12-26
I would like to know whether it's possible to set X.org to open a different X session for the TV-Out, instead of with two cards and Xfree as explained [here]("http://disjunkt.com/dualhead/")

---

### Post by tseliot on 2005-12-27
[QUOTE=Luzbel]I would like to know whether it's possible to set X.org to open a different X session for the TV-Out, instead of with two cards and Xfree as explained [here]("http://disjunkt.com/dualhead/")[/QUOTE]
Only 1 card is required and you can use the 2 screens independently (e.g.you can watch a film on 1 screen and play games on the other one)

---

### Post by tseliot on 2005-12-27
[QUOTE=cdhotfire]Is is possible to only have one desktop? Meaning, is there a way to show whats on my monitor in the tv?[/QUOTE]
I'll let you know if I find a way to do that (the clone screen function didn't work for me).

In the meantime you can try with the guide about Nvidia Twinview (cloning screens works there)

---

### Post by Luzbel on 2005-12-27
[QUOTE=tseliot]Only 1 card is required and you can use the 2 screens independently (e.g.you can watch a film on 1 screen and play games on the other one)[/QUOTE]

Yes, I undestood so far, but as stated in the howto, you have to log into X and then you get both screens working. I was wondering if there is any chance two run two independent sessions of X(org), one for each screen, so I can log two different users at the same time with an individual screen for each. All that using the TV-Out thing, without needing to get one more graphic card. Thank you!

PS: I'll inform you if I manage to get this working.

---

### Post by a8ne on 2005-12-28
I changed my monitor names according to the Nvidia README but I'm still getting this warning in my Xorg.0.log:

```
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
```

Also, I added:

```
Option	 	"IgnoreEDID" "True"
```

but I'm still getting this warning:

```
(WW) NVIDIA(1): Unable to get display device TV-0's EDID; cannot compute DPI
(WW) NVIDIA(1):      from EDID.
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
```

My TV flickers when I boot then goes black.:( 

I'm attaching my xorg.conf in case maybe I have some stupid mistake:

---

### Post by tseliot on 2005-12-28
[QUOTE=a8ne]I changed my monitor names according to the Nvidia README but I'm still getting this warning in my Xorg.0.log:

```
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
```

Also, I added:

```
Option	 	"IgnoreEDID" "True"
```

but I'm still getting this warning:

```
(WW) NVIDIA(1): Unable to get display device TV-0's EDID; cannot compute DPI
(WW) NVIDIA(1):      from EDID.
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
```

My TV flickers when I boot then goes black.:( 

I'm attaching my xorg.conf in case maybe I have some stupid mistake:[/QUOTE]
Make modify this section like in the example:
```
Section "Monitor" 
	Identifier "TV" #TV 
	HorizSync [COLOR="Red"]30-50[/COLOR]  
	VertRefresh [COLOR="Red"]60[/COLOR] 
 EndSection
```

Anyhow you will be able to see anything on your TV ONLY AFTER you log in.
(the fact you can see the screen before booting Ubuntu doesn't mean anything)

---

### Post by a8ne on 2005-12-28
[QUOTE=tseliot]Make modify this section like in the example:
```
Section "Monitor" 
	Identifier "TV" #TV 
	HorizSync [COLOR="Red"]30-50[/COLOR]  
	VertRefresh [COLOR="Red"]60[/COLOR] 
 EndSection
```
[/QUOTE]

Um, I already had it that way.

---

### Post by tseliot on 2005-12-29
[QUOTE=a8ne]Um, I already had it that way.[/QUOTE]
Ok, then do this thing for me:
Press CTRL+ALT+F1 (you will only see the command line)
sudo /etc/init.d/gdm stop (if you use GDM)
OR
sudo /etc/init.d/kdm stop (if you use kDM)
startx -- -verbose 5 -logverbose 5

and post the output (which you can find under /var/log/Xorg.0.log )

---

### Post by Luzbel on 2005-12-29
I think I've already read about that, not sure thou. If getting a black and white image, is it the TV to blame? Are there any other possible reasons? Thank you!

Answering myself, it's most probably because of the cable. Will check with other TV when I have time.

---

### Post by dninja on 2005-12-30
Brilliant tutorial, worked first time, apart from I only get black and white on my tv. I'm in the UK and connecting with an SVIDEO -> scart cable. I put the following in my xorg.conf
```

Section "Device"
        Driver          "nvidia"
        Identifier      "Device[1]"
        Screen          1
        Option          "TVOutFormat" "SVIDEO" #or COMPOSITE etc
        Option          "TVStandard" "PAL-I" #or NTSC etc
        Option          "ConnectedMonitor" "Monitor[1]"
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci
EndSection

```
Any ideas how to get colour?

---

### Post by dninja on 2005-12-30
Another question, how do I get tv only output? The pc is going to be used with just the telly so I need to remove the crt output.

I tried the obvious stuff of removing the crt stuff and just leaving the tv sections but if I do that I get crt in tv resolution.

---

### Post by tseliot on 2005-12-30
----

---

### Post by dninja on 2005-12-30
No, I tried that, this is what I end up with and all I get is monitor output in 640x480.

```

Section "Device" 
        Driver          "nvidia"
        Identifier      "Device"   
        Option          "TVOutFormat" "SVIDEO" #or COMPOSITE etc
        Option          "TVStandard" "PAL-I" #or NTSC etc 
        Option          "ConnectedMonitor" "Monitor"   
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci
EndSection      
                
Section "Monitor" 
        Identifier      "Monitor" #TV   
        HorizSync       30-50
        VertRefresh     60
EndSection
        
Section "Screen" 
        Device "Device"
        Identifier "Screen"
        Monitor "Monitor"
        DefaultDepth 24
        SubSection "Display"
               Depth 24                                                                                                                                   
               Modes "640x480"
        EndSubSection
EndSection
        
Section "ServerLayout"  
        Identifier      "Default Layout"
        Screen          "Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

Have I missed anything?

---

### Post by a8ne on 2005-12-30
[QUOTE=tseliot]Ok, then do this thing for me:
Press CTRL+ALT+F1 (you will only see the command line)
sudo /etc/init.d/gdm stop (if you use GDM)
OR
sudo /etc/init.d/kdm stop (if you use kDM)
startx -- -verbose 5 -logverbose 5

and post the output (which you can find under /var/log/Xorg.0.log )[/QUOTE]
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation CVS repository.
See http://wiki.x.org/wiki/CvsPage for CVS access instructions.

X Window System Version 6.99.99.904 (7.0.0 RC 4)
Release Date: 14 December 2005
X Protocol Version 11, Revision 0, Release 6.99.99.904
Build Operating System:Linux 2.6.8.1 x86_64
Current Operating System: Linux box 2.6.15-9-amd64-generic #1 PREEMPT Wed Dec 21 14:22:40 UTC 2005 x86_64
Build Date: 15 December 2005
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 30 22:54:10 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "screen0" (0)
(**) |   |-->Monitor "DFP"
(**) |   |-->Device "nvidia0"
(**) |-->Screen "screen1" (1)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "nvidia1"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
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
	compiled for 6.99.99.904, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev a2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev a3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev a3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0140 card 107d,2009 rev a2 class 03,00,00 hdr 00
(II) PCI: 05:06:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 05:08:0: chip 1102,0007 card 1102,1006 rev 00 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600 GT] rev 162, Mem @ 0xc8000000/26, 0xc0000000/27, 0xcc000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd1000000 - 0xd10000ff (0x100) MX[B]
	[1] -1	0	0xd2000000 - 0xd2000fff (0x1000) MX[B]
	[2] -1	0	0xd2001000 - 0xd2001fff (0x1000) MX[B]
	[3] -1	0	0xd2003000 - 0xd20030ff (0x100) MX[B]
	[4] -1	0	0xd2002000 - 0xd2002fff (0x1000) MX[B]
	[5] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[8] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[9] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[11] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[12] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[13] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[14] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[22] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd1000000 - 0xd10000ff (0x100) MX[B]
	[1] -1	0	0xd2000000 - 0xd2000fff (0x1000) MX[B]
	[2] -1	0	0xd2001000 - 0xd2001fff (0x1000) MX[B]
	[3] -1	0	0xd2003000 - 0xd20030ff (0x100) MX[B]
	[4] -1	0	0xd2002000 - 0xd2002fff (0x1000) MX[B]
	[5] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[8] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[9] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[11] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[12] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[13] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[14] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[22] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
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
	[5] -1	0	0xd1000000 - 0xd10000ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2000fff (0x1000) MX[B]
	[7] -1	0	0xd2001000 - 0xd2001fff (0x1000) MX[B]
	[8] -1	0	0xd2003000 - 0xd20030ff (0x100) MX[B]
	[9] -1	0	0xd2002000 - 0xd2002fff (0x1000) MX[B]
	[10] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[18] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[19] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[20] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[21] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[23] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[24] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[25] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[26] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[29] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
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
	compiled for 6.99.99.904, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8174
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8174
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.99.99.902, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.902, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8174  Tue Nov 22 18:24:20 PST 2005
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd1000000 - 0xd10000ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2000fff (0x1000) MX[B]
	[7] -1	0	0xd2001000 - 0xd2001fff (0x1000) MX[B]
	[8] -1	0	0xd2003000 - 0xd20030ff (0x100) MX[B]
	[9] -1	0	0xd2002000 - 0xd2002fff (0x1000) MX[B]
	[10] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[18] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[19] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[20] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[21] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[23] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[24] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[25] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[26] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[29] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd1000000 - 0xd10000ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2000fff (0x1000) MX[B]
	[7] -1	0	0xd2001000 - 0xd2001fff (0x1000) MX[B]
	[8] -1	0	0xd2003000 - 0xd20030ff (0x100) MX[B]
	[9] -1	0	0xd2002000 - 0xd2002fff (0x1000) MX[B]
	[10] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[32] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[34] 0	0	0xcd0003b0 - 0xcd0003bb (0xc) IS[B]
	[35] 0	0	0xcd0003c0 - 0xcd0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling experimental RENDER acceleration
(--) NVIDIA(0): Linear framebuffer at 0xC0000000
(--) NVIDIA(0): MMIO registers at 0xC8000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce 6600 GT
(--) NVIDIA(0): VideoBIOS: 05.43.02.39.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
(--) NVIDIA(0): CRT-0: maximum pixel clock: 400 MHz
(II) NVIDIA(0): Frequency information for CRT-0:
(II) NVIDIA(0):   HorizSync   : 30.000-81.000 kHz
(II) NVIDIA(0):   VertRefresh : 56.000-75.000 Hz
(II) NVIDIA(0):      (HorizSync from EDID)
(II) NVIDIA(0):      (VertRefresh from EDID)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(WW) NVIDIA(0): Bad V_BIOS checksum
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(0): DFP: Using hsync range of 30.00-81.00 kHz
(II) NVIDIA(0): DFP: Using vrefresh range of 56.00-75.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 400.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "576x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "576x432" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config option
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)

```

---

### Post by a8ne on 2005-12-30
```
(**) NVIDIA(1): Option "IgnoreEDID" "True"
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "NTSC-M"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(**) NVIDIA(1): Option "RenderAccel" "true"
(**) NVIDIA(1): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(1): Enabling experimental RENDER acceleration
(**) NVIDIA(1): Forcing COMPOSITE video output
(**) NVIDIA(1): Ignoring EDIDs
(**) NVIDIA(1): ConnectedMonitor string: "TV"
(**) NVIDIA(1): TV Standard string: "NTSC-M"
(--) NVIDIA(1): Linear framebuffer at 0xC0000000
(--) NVIDIA(1): MMIO registers at 0xC8000000
(II) NVIDIA(1): NVIDIA GPU detected as: GeForce 6600 GT
(--) NVIDIA(1): VideoBIOS: 05.43.02.39.00
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): VideoRAM: 131072 kBytes
(II) NVIDIA(1): Using ConnectedMonitor string "TV-0"
(--) NVIDIA(1): Detected TV Encoder: NVIDIA
(--) NVIDIA(1): TV-0: maximum pixel clock: 400 MHz
(II) NVIDIA(1): Not probing EDIDs.
(II) NVIDIA(1): Frequency information for TV-0:
(II) NVIDIA(1):   HorizSync   : 30.000-50.000 kHz
(II) NVIDIA(1):   VertRefresh : 60.000 Hz
(II) NVIDIA(1):      (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(1):      (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(1):      section)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(WW) NVIDIA(0): Bad V_BIOS checksum
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(1): TV: Using hsync range of 30.00-50.00 kHz
(II) NVIDIA(1): TV: Using vrefresh value of 60.00 Hz
(II) NVIDIA(1): Clock range:  12.00 to 400.00 MHz
(II) NVIDIA(1): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1152x768" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "576x384" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(1): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(1): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(1): Not using default mode "1024x768" (width too large for virtual size)
(WW) NVIDIA(1): Not using mode "640x384" (not a valid TV mode)
(WW) NVIDIA(1): Not using mode "512x384" (not a valid TV mode)
(**) NVIDIA(1): Validated modes for display device TV-0:
(**) NVIDIA(1):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(1):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(1):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(1):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(1):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(1): Virtual screen size determined to be 800 x 600
(WW) NVIDIA(1): Unable to get display device TV-0's EDID; cannot compute DPI
(WW) NVIDIA(1):      from EDID.
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/lib/xorg/modules/libramdac.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after preInit:
	[0] 0	0	0xcc000000 - 0xccffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] 0	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B]
	[3] 0	0	0xcc000000 - 0xccffffff (0x1000000) MX[B]
	[4] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[5] 0	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B]
	[6] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[7] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[8] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[9] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[10] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[11] -1	0	0xd1000000 - 0xd10000ff (0x100) MX[B]
	[12] -1	0	0xd2000000 - 0xd2000fff (0x1000) MX[B]
	[13] -1	0	0xd2001000 - 0xd2001fff (0x1000) MX[B]
	[14] -1	0	0xd2003000 - 0xd20030ff (0x100) MX[B]
	[15] -1	0	0xd2002000 - 0xd2002fff (0x1000) MX[B]
	[16] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[27] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[28] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[29] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[30] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[32] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[33] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[34] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[35] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[37] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[38] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[39] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[40] 0	0	0xcd0003b0 - 0xcd0003bb (0xc) IS[B]
	[41] 0	0	0xcd0003c0 - 0xcd0003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "800x600"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
Screen 0 is using RAC for io
Screen 1 is using RAC for io
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
error opening security policy file /etc/xserver/SecurityPolicy
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
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

### Post by tseliot on 2005-12-30
> **a8ne]```
(**) NVIDIA(1): Option "IgnoreEDID" "True"
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "NTSC-M"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(**) NVIDIA(1): Option "RenderAccel" "true"
(**) NVIDIA(1): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(1): Enabling experimental RENDER acceleration
(**) NVIDIA(1): Forcing COMPOSITE video output
(**) NVIDIA(1): Ignoring EDIDs
(**) NVIDIA(1): ConnectedMonitor string: "TV"
(**) NVIDIA(1): TV Standard string: "NTSC-M"
(--) NVIDIA(1): Linear framebuffer at 0xC0000000
(--) NVIDIA(1): MMIO registers at 0xC8000000
(II) NVIDIA(1): NVIDIA GPU detected as: GeForce 6600 GT
(--) NVIDIA(1): VideoBIOS: 05.43.02.39.00
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): VideoRAM: 131072 kBytes
(II) NVIDIA(1): Using ConnectedMonitor string "TV-0"
(--) NVIDIA(1): Detected TV Encoder: NVIDIA
(--) NVIDIA(1): TV-0: maximum pixel clock: 400 MHz
(II) NVIDIA(1): Not probing EDIDs.
(II) NVIDIA(1): Frequency information for TV-0:
(II) NVIDIA(1):   HorizSync   : 30.000-50.000 kHz
(II) NVIDIA(1):   VertRefresh : 60.000 Hz
(II) NVIDIA(1):      (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(1):      (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(1):      section)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(WW) NVIDIA(0): Bad V_BIOS checksum
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(1): TV: Using hsync range of 30.00-50.00 kHz
(II) NVIDIA(1): TV: Using vrefresh value of 60.00 Hz
(II) NVIDIA(1): Clock range:  12.00 to 400.00 MHz
(II) NVIDIA(1): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1152x768" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "576x384" (vrefresh out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(1): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(1): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(1): Not using default mode "1024x768" (width too large for virtual size)
(WW) NVIDIA(1): Not using mode "640x384" (not a valid TV mode)
(WW) NVIDIA(1): Not using mode "512x384" (not a valid TV mode)
(**) NVIDIA(1): Validated modes for display device TV-0:
(**) NVIDIA(1):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(1):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(1):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(1):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(1):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(1): Virtual screen size determined to be 800 x 600
(WW) NVIDIA(1): Unable to get display device TV-0's EDID said:**
>  0	0	0xcc000000 - 0xccffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] 0	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B]
	[3] 0	0	0xcc000000 - 0xccffffff (0x1000000) MX[B]
	[4] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[5] 0	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B]
	[6] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[7] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[8] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[9] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[10] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[11] -1	0	0xd1000000 - 0xd10000ff (0x100) MX[B]
	[12] -1	0	0xd2000000 - 0xd2000fff (0x1000) MX[B]
	[13] -1	0	0xd2001000 - 0xd2001fff (0x1000) MX[B]
	[14] -1	0	0xd2003000 - 0xd20030ff (0x100) MX[B]
	[15] -1	0	0xd2002000 - 0xd2002fff (0x1000) MX[B]
	[16] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[27] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[28] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[29] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[30] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[32] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[33] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[34] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[35] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[37] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[38] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[39] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[40] 0	0	0xcd0003b0 - 0xcd0003bb (0xc) IS[B]
	[41] 0	0	0xcd0003c0 - 0xcd0003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "800x600"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
Screen 0 is using RAC for io
Screen 1 is using RAC for io
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
error opening security policy file /etc/xserver/SecurityPolicy
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
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```
Maybe this is your problem: [COLOR="Red"]NVIDIA(0): Bad V_BIOSchecksum[/COLOR]

You should ask for help in the Unofficial Nvidia Forum

---

### Post by tseliot on 2005-12-30
[QUOTE=dninja]No, I tried that, this is what I end up with and all I get is monitor output in 640x480.

```

Section "Device" 
        Driver          "nvidia"
        Identifier      "Device"   
        Option          "TVOutFormat" "SVIDEO" #or COMPOSITE etc
        Option          "TVStandard" "PAL-I" #or NTSC etc 
        Option          "ConnectedMonitor" "Monitor"   
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci
EndSection      
                
Section "Monitor" 
        Identifier      "Monitor" #TV   
        HorizSync       30-50
        VertRefresh     60
EndSection
        
Section "Screen" 
        Device "Device"
        Identifier "Screen"
        Monitor "Monitor"
        DefaultDepth 24
        SubSection "Display"
               Depth 24                                                                                                                                   
               Modes "640x480"
        EndSubSection
EndSection
        
Section "ServerLayout"  
        Identifier      "Default Layout"
        Screen          "Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

Have I missed anything?[/QUOTE]
Sorry but I was in a hurry before and I gave you a wrong answer (I had to have lunch).

Ok, set your xorg.conf following the guide except for this part:

```
Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" "Clone"  "Screen[0]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection
```

and restart X (CTRL+ALT+BACKSPACE)

Or

```
Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 1 "Screen[1]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection
```

and restart X (CTRL+ALT+BACKSPACE)
Tell me which one works (if there's one which works) and what happens.

---

### Post by tseliot on 2005-12-30
[QUOTE=Luzbel]I think I've already read about that, not sure thou. If getting a black and white image, is it the TV to blame? Are there any other possible reasons? Thank you!

Answering myself, it's most probably because of the cable. Will check with other TV when I have time.[/QUOTE]
I have a doubt. Could you try this thing?
Change the following parameters of your tv in the section "monitor"

HorizSync 30-50  
VertRefresh 50

EDIT: I think you should install the latest nvidia drivers 8178 (use method 2 of my guide about the drivers). There are some users who complain about the same problem and it often depends on the driver version (and on your card)

---

### Post by dninja on 2005-12-30
This works:
```

Section "Device"
        Driver          "nvidia"
        Identifier      "Device[1]"
        Screen          0
        Option          "TVOutFormat" "SVIDEO" 
        Option          "TVStandard" "PAL-I" 
        Option          "ConnectedMonitor" "Monitor[1]"
        BusID           "PCI:1:0:0" 
EndSection

Section "Monitor"
        Identifier      "Monitor[1]" #TV
        HorizSync       30-50
        VertRefresh     60
EndSection

Section "Screen"
        Device "Device[1]"
        Identifier "Screen[1]"
        Monitor "Monitor[1]"
        DefaultDepth 24
        SubSection "Display"
               Depth 24
               Modes "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
   Identifier  "Simple Layout"
       Screen 0 "Screen[1]"
   InputDevice "Configured Mouse" "CorePointer"
   InputDevice "Generic Keyboard" "CoreKeyboard"
EndSection

```

I removed all references to the crt and changed the screen number to 0 and that seems to have fixed it.

I also found that if I don't have a monitor plugged in then all terminal output goes to the tv.

How can I tell how high resolution my TV will go? Could I break the tv if I push the resolution too high?

Now all I need to do is get it in colour. I'll try upgrading to the latest drivers and see what happens.

Thanks

---

### Post by dninja on 2005-12-30
I've tried the latest version of the nvidia drivers (1.0-8178) and all is still black and white.

Something I did notice though is that the bios output is also in black and white so I'm wondering if it is something do do with the tv or the card. I've tried 2 different cables so it isn't the cable.

I'll try it with a different tv later and see.

---

### Post by Luzbel on 2005-12-30
My problem is similar to dninja's. TV is B/W since BIOS starts, so I supposed it was the cable. I've not tested other TV yet. Thank you!

---

### Post by odinriko on 2005-12-31
[QUOTE=tabinin]Thank you for this Howto.  This has been the biggest struggle that I have had with Linux, right after Japanese input. 

I have a display on my tv, with its own task bar.  I am still having a couple of small problems...

One is that my autostart applications are starting and running on both screens.  Any way I can get them to start only on "screen 0"?

The other problem is that I would like to be able to drag a mplayer window into screen 1 (TV), like I could in Windows.  Any way to do that (or, are there any easy tricks or commands to get mplayer to open/play a movie directly on the tv?

I am using Kubuntu and a FX5200 card.[/QUOTE]

I use an alias for mplayer that has these options
"mplayer -fs -display :0.1"
that should make it fullscreen on your tv

---

### Post by odinriko on 2005-12-31
[QUOTE=Luzbel]My problem is similar to dninja's. TV is B/W since BIOS starts, so I supposed it was the cable. I've not tested other TV yet. Thank you![/QUOTE]
likely you have the cable setting wrong.

        Option          "TVOutFormat" "SVIDEO" 
Change it to the type of cable you use.  RGB, composite, and SVIDEO are the only options I know of.

---

### Post by odinriko on 2005-12-31
Does anyone have recommendations on software that is readable/usable on a standard tv?  Or is there some settings that I'm missing that makes text easier to read?  I know there are interlacing problems with using a tv, but I am trying to find settings that will make it feasable to use only a tv on my system.  (My monitor is about to die, and I don't have the cash to buy another one, so this is fairly mission critical to me)

---

### Post by tseliot on 2005-12-31
[QUOTE=odinriko]Does anyone have recommendations on software that is readable/usable on a standard tv?  Or is there some settings that I'm missing that makes text easier to read?  I know there are interlacing problems with using a tv, but I am trying to find settings that will make it feasable to use only a tv on my system.  (My monitor is about to die, and I don't have the cash to buy another one, so this is fairly mission critical to me)[/QUOTE]
Perhaps the resolution is too high for your tv. Try with 640x480 and 800x600.
I hope it helps.

---

### Post by dninja on 2005-12-31
[QUOTE=Luzbel]My problem is similar to dninja's. TV is B/W since BIOS starts, so I supposed it was the cable. I've not tested other TV yet. Thank you![/QUOTE]
Just tried it on my better tv and I've got colour. The bios stuff is still in black and white but X is in colour. The picture quality is dreadful but I guess that is down to refresh rates. I'm desparatly trying to find my tv manual to find out what it can handle.

Something I do remember from the manual is that the tv has a svideo socket but there is a warning about not plugging computer equipment into it, possibly also mentioning a certain voltate (3v perhaps). With this vague description can anyone shed any light on svideo, voltages and what would happen if I stoped using my svideo to scart converter and plugged the svideo cable directly in?

Also, if anyone can suggest why one tv is black and white and the other colour with the same pc, cable and config then I'd be interested. Now I've started playing I'd like to get my main pc working with the tv that currently only does black and white so I can have movies playing while "working".

---

### Post by tseliot on 2005-12-31
[QUOTE=dninja]Just tried it on my better tv and I've got colour. The bios stuff is still in black and white but X is in colour. The picture quality is dreadful but I guess that is down to refresh rates. I'm desparatly trying to find my tv manual to find out what it can handle.

Something I do remember from the manual is that the tv has a svideo socket but there is a warning about not plugging computer equipment into it, possibly also mentioning a certain voltate (3v perhaps). With this vague description can anyone shed any light on svideo, voltages and what would happen if I stoped using my svideo to scart converter and plugged the svideo cable directly in?

Also, if anyone can suggest why one tv is black and white and the other colour with the same pc, cable and config then I'd be interested. Now I've started playing I'd like to get my main pc working with the tv that currently only does black and white so I can have movies playing while "working".[/QUOTE]

What's the model and brand of your TV (the one with black & white)?

---

### Post by dninja on 2005-12-31
A ferguson 626/TX91 G  GB.

---

### Post by tseliot on 2005-12-31
[QUOTE=dninja]A ferguson 626/TX91 G  GB.[/QUOTE]
I can't find anything useful about it on the internet. Perhaps it's just the refresh rate. 
Anyhow you should ask in the Unofficial Nvidia Forum [http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")

---

### Post by dninja on 2006-01-01
A friend suggested that last night so I'll try it later, I know when I've tried running the PS2 at 60 rather than 50 the picture has been messed up.

---

### Post by dninja on 2006-01-01
Sorted the pc and main telly. As I said before it was there and colour but with  really bad picture quality. It was originally in scart socket AV1, if I changed it to AV2 the picture quality was perfect but black and white again, but by accident I found that when chosing AV2 I could also chose AV2S which gave picture quality and colour. I've no idea what the S stands for and what the differences between AV1, AV2 and AV2S are but I now have a nice clear picture in colour.

Just got to fix the Ferguson portable with the desktop PC and all is well.

---

### Post by lucidite on 2006-01-01
Hi,

OK, so I've been playing with this for at least 5 hours & still can't seem to get it to work.

So here's what I've done so far:
Did all the modifications to xorg.conf that you mentionned. Rebooted my computer. Error message come up before I can get to the user-log-on GUI saying
"Failed to start the x server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"
Clicked on "Yes". Got another message that was similar to the first one, clicked on another "yes" button, got a terminal screen.
Thankfully I had followed your advice & backed up my previous xorg.conf file. I replaced the new file w/old one & rebooted. (and I was really, really happy to know the "sudo cp" command by heart!)

So I have this currently as my xorg.conf file:

[PHP]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"MG-17X"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"MG-17X"
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
EndSection[/PHP]



The odd thing is that when I rebooted by computer, my TV was showing everything fine until the loggon GUI, to which point all the screen does is show odd colours (pretty but useless...)
So my tv-out seems to kinda work... However as of now, I don't quite know what to do....

---

### Post by artnay on 2006-01-02
This is a basic trick when using two separate X instances. If you already have a file manager open (let's say Nautilus) in screen 0 (the primary monitor), you most probably don't want to navigate into same place in screen 1 just to click the movie file. This script should do it.

1. Open a text editor
2. Add the following lines:

# !/bin/sh
DISPLAY=:0.1 /usr/bin/gmplayer -fs "$*"

3. Save the document
4. Open Nautilus
5. Find something to watch, click it with the right mouse button
6. Choose "Open with", then choose "Open with another application"
7. Select "Use a custom command" and then type "sh /path/where/you/saved/document/that/you/created/in/phase3/document".  Then press "Open".

Now the movie should start in fullscreen mode in screen 1. This script should be visible in "Other Application" menu after you've used it once. This script assumes you have a symlink called gmplayer in your /usr/bin, but you can change it to whatever player you want. Hope it saves your time and nerves.

---

### Post by lucidite on 2006-01-02
Thanks for that, and I will be using that tip, however I still have my initial problem: my TV screen doesn't show anything coherant. 
I know it works, since the TV shows the first screens and the booting up of Ubuntu, however when the loggon GUI comes up, the screen becomes, well, an odd mixture of pigments and colours. Nothing like my screen. And it doesn't seem to have created a second "screen" -- when it shows stuff, it shows what's on my monitor.

---

### Post by tseliot on 2006-01-02
[QUOTE=lucidite]Hi,

OK, so I've been playing with this for at least 5 hours & still can't seem to get it to work.

So here's what I've done so far:
Did all the modifications to xorg.conf that you mentionned. Rebooted my computer. Error message come up before I can get to the user-log-on GUI saying
"Failed to start the x server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"
Clicked on "Yes". Got another message that was similar to the first one, clicked on another "yes" button, got a terminal screen.
Thankfully I had followed your advice & backed up my previous xorg.conf file. I replaced the new file w/old one & rebooted. (and I was really, really happy to know the "sudo cp" command by heart!)

So I have this currently as my xorg.conf file:

[PHP]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"MG-17X"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"MG-17X"
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
EndSection[/PHP]



The odd thing is that when I rebooted by computer, my TV was showing everything fine until the loggon GUI, to which point all the screen does is show odd colours (pretty but useless...)
So my tv-out seems to kinda work... However as of now, I don't quite know what to do....[/QUOTE]
You do not seem to have the nvidia drivers installed.
Please install them.

---

### Post by lucidite on 2006-01-02
Did that, and received another error message, similar to the first one. When my computer booted up, got the "Failed to start the x server (your graphical interface). It is likely that it is not set up correctly ."
Redid the same thing that I had done previously to fix problem (copy the old xorg.conf_backup to replace the new one) and it fixed the problem...

---

### Post by tseliot on 2006-01-02
[QUOTE=lucidite]Did that, and received another error message, similar to the first one. When my computer booted up, got the "Failed to start the x server (your graphical interface). It is likely that it is not set up correctly ."
Redid the same thing that I had done previously to fix problem (copy the old xorg.conf_backup to replace the new one) and it fixed the problem...[/QUOTE]
You need the drivers. You might:
1) Follow EVERY step of my guide [HOWTO: Latest NVIDIA drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")
2) Post the output of the error in that thread so that I can help you.
In other words you have to:
set the driver to "nvdia" in your /etc/X11/xorg.conf instead of "nv".
then do this thing for me:
Press CTRL+ALT+F1 (you will only see the command line)
sudo /etc/init.d/gdm stop (if you use GDM)
OR
sudo /etc/init.d/kdm stop (if you use kDM)
startx -- -verbose 5 -logverbose 5

and post the output (which you can find under /var/log/Xorg.0.log ).

NOTE:
If you can't us the Graphical interface any more try this:
then type sudo nano /etc/X11/xorg.conf
and set the driver back to "nv" (instead of "nvidia")
Then
CTRL+O to save
CTRL+X to exit
type "startx" and everything will work again

---

### Post by lucidite on 2006-01-02
So I re-installed the drivers and this time it worked, however my "screen" is larger then my monitor. In other words, it almost seems as if my desktop is almost twice the size of my monitor. Is that normal?

Did what you asked and tried to post my /var/log/Xorg.0.log however it's too long for a  single post and instead of dividing it up into many, many posts, is there something in particular I need to look for & post?

And thank you for your help!

---

### Post by tseliot on 2006-01-02
[QUOTE=lucidite]So I re-installed the drivers and this time it worked, however my "screen" is larger then my monitor. In other words, it almost seems as if my desktop is almost twice the size of my monitor. Is that normal?[/QUOTE]
No, it's not normal. It's likely that the monitor was not set up correctly. So that the xserver tries to apply a resolution which is larger than your monitor (according to settings) supports.
1) Post your xorg.conf
2) Post the refresh rate (vertical and horizontal) of your monitor (have a look at its manual or at the the specs provided on the website of the manufacturer of your monitor).

[QUOTE=lucidite]Did what you asked and tried to post my /var/log/Xorg.0.log however it's too long for a  single post and instead of dividing it up into many, many posts, is there something in particular I need to look for & post?

And thank you for your help![/QUOTE]
Well then post only the lines which begin with "(WW)"

---

### Post by lucidite on 2006-01-02
1) Here's my xorg.conf file

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
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"MG-17X"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"MG-17X"
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
```

2) I checked the manufacturer's web page and they didn't have anything about refresh rates but they did have something about frequency. Don't know if it's pertinent but I have an LCD monitor (X2 Gen MG-17X to be exact...):
 VERTICAL FREQUENCY  	 56 ~ 75 Hz
HORIZONTAL FREQUENCY 	31 ~ 80 Khz

3) And here are the sections from my /var/log/Xorg.0.log file that start with ww:

```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on
"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
... some more stuff ...
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
... some more stuff ...
(WW) Ignoring request to load module GLcore
... some more stuff ...
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
... some more stuff ...
(WW) (1600x1200,MG-17X) mode clock 162MHz exceeds DDC maximum 140MHz
... some more stuff ...
(WW) (1400x1050,MG-17X) mode clock 151MHz exceeds DDC maximum 140MHz
... some more stuff ...
(WW) (1680x1050,MG-17X) mode clock 147.14MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,MG-17X) mode clock 193.16MHz exceeds DDC maximum 140MHz
... some more stuff ...
(WW) NVIDIA(0): Not using mode "960x600" (height 1200 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "800x600" (height 1200 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
```

---

### Post by tseliot on 2006-01-03
[QUOTE=lucidite] 1) Here's my xorg.conf file
```
...
Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	[COLOR="Red"]#[/COLOR]Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver"nvidia"
	BusID"PCI:1:0:0"
	[COLOR="Red"]Option "UseEdidFreqs" "False"[/COLOR]
EndSection
...
```[/QUOTE]

Apply the corrections in red. Then log out and press CTRL+ALT+BACKSPACE. Tell me if it fixes the resolution problem.

[QUOTE=lucidite]2) I checked the manufacturer's web page and they didn't have anything about refresh rates but they did have something about frequency. Don't know if it's pertinent but I have an LCD monitor (X2 Gen MG-17X to be exact...):
 VERTICAL FREQUENCY  	 56 ~ 75 Hz
HORIZONTAL FREQUENCY 	31 ~ 80 Khz[/QUOTE]

Refresh rate or frequency is the same. Ok now we are sure the correct frequencies are set.

[QUOTE=lucidite]3) And here are the sections from my /var/log/Xorg.0.log file that start with ww:
...
[/QUOTE]
Which resolution do you need to use?

---

### Post by lucidite on 2006-01-03
> Apply the corrections in red. Then log out and press CTRL+ALT+BACKSPACE. Tell me if it fixes the resolution problem.


Made the modifications, rebooted and it didn't work. Well, at least it doesn't seem like it. My windows can still be dragged out of my monitor.

> Which resolution do you need to use?

As for the resolution, this is what the manufacturer's webpage had to say:
 RESOLUTION  	 1280 x 1024

---

### Post by tseliot on 2006-01-03
[QUOTE=lucidite]Made the modifications, rebooted and it didn't work. Well, at least it doesn't seem like it. My windows can still be dragged out of my monitor.



As for the resolution, this is what the manufacturer's webpage had to say:
 RESOLUTION  	 1280 x 1024[/QUOTE]
If you want to fix your problems with your screen resolution you can follow this awesome guide: [HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---

### Post by lucidite on 2006-01-05
[QUOTE=tseliot]If you want to fix your problems with your screen resolution you can follow this awesome guide: [HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")[/QUOTE]

Figured out that it was just me not knowing how to configure my desktop. (I'm kinda new at this whole configuring thing...)

With the new drivers, now everything seems to work. (yay!)

Thank you very much for your help & patience.

---

### Post by mflash on 2006-01-10
[QUOTE=dninja]Sorted the pc and main telly. As I said before it was there and colour but with  really bad picture quality. It was originally in scart socket AV1, if I changed it to AV2 the picture quality was perfect but black and white again, but by accident I found that when chosing AV2 I could also chose AV2S which gave picture quality and colour. I've no idea what the S stands for and what the differences between AV1, AV2 and AV2S are but I now have a nice clear picture in colour.

Just got to fix the Ferguson portable with the desktop PC and all is well.[/QUOTE]

I'd just like to add that I have a similar setup, but my telly has only a single
SCART socket. Then I have to select AV-S (instead of AV) to get colour.
Guess AV-S means S-VIDEO ? (BTW, it's a Ferguson as well)

---

### Post by dninja on 2006-01-10
I've fixed it!

I had got the media PC working and given up on getting the portable working with my desktop but mflashs mail spured me on again.

I've found the hidden menu option to get it to use AV-S rather than plain old AV. I've now got perfect quality output running on my tv. I've just got to find a way to get the tv save the setting.

---

### Post by Dagur on 2006-02-01
Hi, quick question.

I'm not going to be using my tv-out much and my tv will be unplugged most of the time (too few inputs). This is a problem because if I boot with my tv unplugged I just get a blank screen on my monitor. 
So is it possible to switch to tv-out only when needed or make my monitor work even if the tv-out isn't plugged in?

cheers

---

### Post by dninja on 2006-02-02
I'm in a similar position so I declared my LCD monitor as the main one and positioned the tv above it so that when the tv was on I could slip the mouse off the top of the screen to reach it. Having it left or right I kept disappearing off when I didn't want to.

With this setup everything works fine, no blank screens. Try this:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0 "LCDScreen" 
        Screen 1 "TVScreen" Above "LCDScreen" 
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

---

### Post by aToS on 2006-02-08
Hi, I have some problem with this...
[My Xorg.conf]("http://atos.uw.hu/logs/xorg.conf")
[And the log]("http://atos.uw.hu/logs/xorg.log")

Thx for help

*** There are two warnings, but I couldn't do anything with them...

---

### Post by mo_x on 2006-02-08
You are using the nv driver instead of the nvidia driver.
Also the ConnectedMonitor option is used wrong.

---

### Post by tseliot on 2006-02-08
[QUOTE=aToS]Hi, I have some problem with this...
[My Xorg.conf]("http://atos.uw.hu/logs/xorg.conf")
[And the log]("http://atos.uw.hu/logs/xorg.log")

Thx for help

*** There are two warnings, but I couldn't do anything with them...[/QUOTE]
I agree with mo_x.
You should install the nvidia drivers (see the link to my guide in my signature)
Moreover your option should be 
```
Option          "ConnectedMonitor" "TV"
```

---

### Post by gizm0 on 2006-02-09
I have installed newest nvidia drivers and i have amd64 kernel.

I have tried severaly to install TV-out for my Nvidia geforce 6600, but haven't got any luck with it. I checked the cables and cables are ok, because tv can get it's signal when i'm using windows xp.

I only got it working once, but then my LCD-screen didn't work. At the point when i got LCD-screen to work then my TV-screen didn't work.

Also i have noticed that my cursor can be scrolled all away to the next screen, but the TV-screen is still blank.

---

### Post by tseliot on 2006-02-09
[QUOTE=gizm0]I have installed newest nvidia drivers and i have amd64 kernel.

I have tried severaly to install TV-out for my Nvidia geforce 6600, but haven't got any luck with it. I checked the cables and cables are ok, because tv can get it's signal when i'm using windows xp.

I only got it working once, but then my LCD-screen didn't work. At the point when i got LCD-screen to work then my TV-screen didn't work.

Also i have noticed that my cursor can be scrolled all away to the next screen, but the TV-screen is still blank.[/QUOTE]
You have to find this part:
Option 		"ConnectedMonitor" "TV" 

and make it look  like this:
Option          "ConnectedMonitor" "[COLOR="Red"]Monitor[1][/COLOR]"

---

### Post by gizm0 on 2006-02-10
Ok....now i have fixed that line and rebooted computer, but it still does not work :(. 

Any ideas? Cables are ok...i checked cables with my other computer and windows xp.

---

### Post by tseliot on 2006-02-10
[QUOTE=gizm0]Ok....now i have fixed that line and rebooted computer, but it still does not work :(. 

Any ideas? Cables are ok...i checked cables with my other computer and windows xp.[/QUOTE]
Turn on your computer with the TV-OUT cable UNPLUGGED.

Then when you get to the login screen plug the cable in and press CTRL+ALT+Backspace.

Then login and an something should appear on your TV

---

### Post by gizm0 on 2006-02-10
I noticed few mix ups, when i turned the computer on (without the TV cable plugged in):
-TV-screen didn't work at the start
-LCD-screen had TV resolution on (so it was thinking that my LCD-screen is TV-screen)
-when i pressed alt-ctrl-backspace the LCD-screen turned to normal and TV-screen didn't do anything (just blinked one or two times)

---

### Post by tseliot on 2006-02-10
[QUOTE=gizm0]I noticed few mix ups, when i turned the computer on (without the TV cable plugged in):
-TV-screen didn't work at the start
-LCD-screen had TV resolution on (so it was thinking that my LCD-screen is TV-screen)
-when i pressed alt-ctrl-backspace the LCD-screen turned to normal and TV-screen didn't do anything (just blinked one or two times)[/QUOTE]
Try to remove this option:
Option "ConnectedMonitor" "DFP"

then log out and press CTRL+ALT+Backspace

---

### Post by gizm0 on 2006-02-10
Ok now it works, but i got new problem :D.

My LCD-screen is showing TV-resolution and TV-screen is showing LCD-resolution.

How to fix this problem?

And thanks for the help. I couldn't have done this without a help :).

---

### Post by tseliot on 2006-02-10
[QUOTE=gizm0]Ok now it works, but i got new problem :D.

My LCD-screen is showing TV-resolution and TV-screen is showing LCD-resolution.

How to fix this problem?

And thanks for the help. I couldn't have done this without a help :).[/QUOTE]
Perhaps the resolution for your TV is too low. Make it look like this:
```
Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 16 
       	SubSection "Display" 
               Depth 16 
               Modes "[COLOR="Red"]1024x768[/COLOR]" 
       EndSubSection
```

then log out and press CTRL+ALT+Backspace

[COLOR="Magenta"]IF (and ONLY IF)[/COLOR] that doesn't solve the problem you can try this:

```
Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		[COLOR="Red"]"Monitor[1]"[/COLOR]
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor [COLOR="Red"]"Monitor[0]"[/COLOR] 
   	DefaultDepth 16 
       	SubSection "Display" 
               Depth 16 
               Modes "1024x768" 
       	EndSubSection    
EndSection
```

---

### Post by gizm0 on 2006-02-10
Thanks!

I will try that later on today :).

---

### Post by gizm0 on 2006-02-10
I tried the solution for that but it didn't change anything. The problem is that my login screen etc. is on the TV-screen. Even though i change the resolution it wont put the login screen on my LCD-screen

So the problem is that Ubuntu think my LCD-screen is the second screen (not the primary).

---

### Post by tseliot on 2006-02-10
[QUOTE=gizm0]I tried the solution for that but it didn't change anything. The problem is that my login screen etc. is on the TV-screen. Even though i change the resolution it wont put the login screen on my LCD-screen

So the problem is that Ubuntu think my LCD-screen is the second screen (not the primary).[/QUOTE]
Ok, remove my 2nd suggestion (those which came after "IF (and ONLY IF) that doesn't solve the problem you can try this")

And remove this option:
Option "ConnectedMonitor" "Monitor[1]"

then log out and press CTRL+ALT+Backspace

---

### Post by gizm0 on 2006-02-10
Nope it didn't work. Any more suggestions? 

Btw. nothing didn't change and here is the new config file in the attachment

---

### Post by tseliot on 2006-02-10
[QUOTE=gizm0]Ok....now i have fixed that line and rebooted computer, but it still does not work :(. 

Any ideas? Cables are ok...i checked cables with my other computer and windows xp.[/QUOTE]
Remember not to boot (EVER) with the TV-OUT calbe plugged in.

The xorg.conf looks ok.

There are some users who can't use the Nvidia Tv-OUT (not only in Ubuntu).

If the TV-OUT doesn't work for you you can try Nvidia Twinview (there is a guide on this forum)

---

### Post by gizm0 on 2006-02-10
k i will try again tomorrow, to figure out the problem.

thank anyways :).

---

### Post by isTHEr3mOr3 on 2006-02-24
Hi all,

I've spend hours getting tv-out to work. It works on windows but I can't get it working on Linux. My card: NVIDIA GeForce2 MX/MX 400
I want to clone the desktop to the tv.

This is the xorg.conf I think should work, but there's no TV-image at all. 
Hope someone can help me here.

Thanks. 

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

Section "Monitor"
	Identifier	"Belinea10153"
	Option		"DPMS"
	HorizSync 	30-81
	VertRefresh 	56-76
EndSection



Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option 		"TVStandard" "PAL-B"
        Option	        "TVOutFormat" "COMPOSITE"
        Option              "TwinView" "true"
        Option              "TwinViewOrientation" "Clone"
        Option	         "SecondMonitorHorizSync" "30-50"
	Option 		"SecondMonitorVertRefresh" "60"
	Option 		"MetaModes"     "1024x768,1024x768;800x600,800x600;640x480,640x480"
        Option 		"ConnectedMonitor" "CRT, TV"
 EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Belinea10153"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"  "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"  "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"  "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"  "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"  "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"  "800x600" "640x480"
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

### Post by tseliot on 2006-02-24
[QUOTE=isTHEr3mOr3]I want to clone the desktop to the tv.[/QUOTE]
If you want to do that try this guide:
[http://www.ubuntuforums.org/showthread.php?t=85769&highlight=twinview]("http://www.ubuntuforums.org/showthread.php?t=85769&highlight=twinview")

---

### Post by isTHEr3mOr3 on 2006-02-24
Thank you for your reply, but I can't get anything on my TV so if you can help me with another solution it's ok too. 
The twinview link doesn't help me, it describes connecting 2 monitors and that's not my problem. 

I've tried a lot of xorg samples and I think I know how it works, but obviously I'm missing something.

---

### Post by tseliot on 2006-02-24
[QUOTE=isTHEr3mOr3]Thank you for your reply, but I can't get anything on my TV so if you can help me with another solution it's ok too. 
The twinview link doesn't help me, it describes connecting 2 monitors and that's not my problem. 

I've tried a lot of xorg samples and I think I know how it works, but obviously I'm missing something.[/QUOTE]
Pretend your TV is a 2nd monitor and follow that guide (I've tried it and it worked)

---

### Post by mcpish on 2006-02-25
I've used this guide and it works perfectly on my GeForce 6200 with S-Video out.  Thank you.

I now have it setup exactly the way I want.  

I setup a custom background wallpaper to display on the TV-Only desktop (the classic bars test-pattern to ensure the colors are accurate on the TV).  Then I removed the KDE application panel from the TV-desktop so that only my wallpaper shows on the TV without anything else (the TV color bar test pattern) when I'm not playing a video file.  I also copied the script recommended earlier and now I can just right-click on any video file and choose a new "**television**" option I created in the drop-down menu and the video will start playing automatically in full-screen on the TV (using mplayer) while I remain on my desktop on the PC monitor.  After configuring the TV-desktop I removed the  "*leftof*" section of the xorg.conf file and rebooted so that the mouse doesn't traverse desktops but always sticks on the PC desktop now.  I only use the TV for playing video files and for that I just simply use the method above to instantly send any video file to the TV.  After a file is done playing, the TV simply goes back to the Test Pattern.

---

### Post by tseliot on 2006-02-25
[QUOTE=mcpish]I've used this guide and it works perfectly on my GeForce 6200 with S-Video out.  Thank you.

I now have it setup exactly the way I want.  

I setup a custom background wallpaper to display on the TV-Only desktop (the classic bars test-pattern to ensure the colors are accurate on the TV).  Then I removed the KDE application panel from the TV-desktop so that only my wallpaper shows on the TV without anything else (the TV color bar test pattern) when I'm not playing a video file.  I also copied the script recommended earlier and now I can just right-click on any video file and choose a new "**television**" option I created in the drop-down menu and the video will start playing automatically in full-screen on the TV (using mplayer) while I remain on my desktop on the PC monitor.  After configuring the TV-desktop I removed the  "*leftof*" section of the xorg.conf file and rebooted so that the mouse doesn't traverse desktops but always sticks on the PC desktop now.  I only use the TV for playing video files and for that I just simply use the method above to instantly send any video file to the TV.  After a file is done playing, the TV simply goes back to the Test Pattern.[/QUOTE]
Thanks for reporting

---

### Post by eskomorko on 2006-03-16
[QUOTE=mcpish]I've used this guide and it works perfectly on my GeForce 6200 with S-Video out.  Thank you.

I now have it setup exactly the way I want.  

I setup a custom background wallpaper to display on the TV-Only desktop (the classic bars test-pattern to ensure the colors are accurate on the TV).  Then I removed the KDE application panel from the TV-desktop so that only my wallpaper shows on the TV without anything else (the TV color bar test pattern) when I'm not playing a video file.  I also copied the script recommended earlier and now I can just right-click on any video file and choose a new "**television**" option I created in the drop-down menu and the video will start playing automatically in full-screen on the TV (using mplayer) while I remain on my desktop on the PC monitor.  After configuring the TV-desktop I removed the  "*leftof*" section of the xorg.conf file and rebooted so that the mouse doesn't traverse desktops but always sticks on the PC desktop now.  I only use the TV for playing video files and for that I just simply use the method above to instantly send any video file to the TV.  After a file is done playing, the TV simply goes back to the Test Pattern.[/QUOTE]

I use the same method. Only downside is that I cant pause or stop the video, because I also removed leftof thingie from xorg.conf (dont like when mouse dissappears to tv screen when tv is not on).

Is it possible to use both screens without having to move the cursor from screen to screen. For example a shortcut key, which selects between screens. Its hard to explain when you dont speak english natively, but I hope you understand what I mean. ;)

---

### Post by tseliot on 2006-03-16
[QUOTE=eskomorko]I use the same method. Only downside is that I cant pause or stop the video, because I also removed leftof thingie from xorg.conf (dont like when mouse dissappears to tv screen when tv is not on).

Is it possible to use both screens without having to move the cursor from screen to screen. For example a shortcut key, which selects between screens. Its hard to explain when you dont speak english natively, but I hope you understand what I mean. ;)[/QUOTE]
I understand what you mean (I'm Italian) but the only thing I can suggest you is to have a look at this guide for Gentoo:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors]("http://gentoo-wiki.com/HOWTO_Dual_Monitors")

Then look for the "Moving focus between screens" section. There is a little app there which I haven't tried myself which should enable you to switch between screens.

Then you should look for a guide on the Ubuntu forums about key bindings in GNOME.

I wish I had the time to write a guide about that :(

---

### Post by redcell on 2006-04-03
[QUOTE=mcpish]I've used this guide and it works perfectly on my GeForce 6200 with S-Video out.  Thank you.

I now have it setup exactly the way I want.  

I setup a custom background wallpaper to display on the TV-Only desktop (the classic bars test-pattern to ensure the colors are accurate on the TV).  Then I removed the KDE application panel from the TV-desktop so that only my wallpaper shows on the TV without anything else (the TV color bar test pattern) when I'm not playing a video file.  I also copied the script recommended earlier and now I can just right-click on any video file and choose a new "**television**" option I created in the drop-down menu and the video will start playing automatically in full-screen on the TV (using mplayer) while I remain on my desktop on the PC monitor.  After configuring the TV-desktop I removed the  "*leftof*" section of the xorg.conf file and rebooted so that the mouse doesn't traverse desktops but always sticks on the PC desktop now.  I only use the TV for playing video files and for that I just simply use the method above to instantly send any video file to the TV.  After a file is done playing, the TV simply goes back to the Test Pattern.[/QUOTE]

I also used this guide with my Geforce 5200 and S-Video out, and it works perfectly, thnx

I was wondering how to remove the KDE application panel (kicker) from the TV-desktop, as you discribed in the above post.

---

### Post by redcell on 2006-04-03
[QUOTE=mcpish]I've used this guide and it works perfectly on my GeForce 6200 with S-Video out.  Thank you.

I now have it setup exactly the way I want.  

I setup a custom background wallpaper to display on the TV-Only desktop (the classic bars test-pattern to ensure the colors are accurate on the TV).  Then I removed the KDE application panel from the TV-desktop so that only my wallpaper shows on the TV without anything else (the TV color bar test pattern) when I'm not playing a video file.  I also copied the script recommended earlier and now I can just right-click on any video file and choose a new "**television**" option I created in the drop-down menu and the video will start playing automatically in full-screen on the TV (using mplayer) while I remain on my desktop on the PC monitor.  After configuring the TV-desktop I removed the  "*leftof*" section of the xorg.conf file and rebooted so that the mouse doesn't traverse desktops but always sticks on the PC desktop now.  I only use the TV for playing video files and for that I just simply use the method above to instantly send any video file to the TV.  After a file is done playing, the TV simply goes back to the Test Pattern.[/QUOTE]

I also used this guide with my Geforce 5200 and S-Video out, and it works perfectly, thnx

I was wondering how to remove the KDE application panel (kicker) from the TV-desktop, as you discribed in the above post, because Kicker uses about 30MB of ram.

---

### Post by km0ti0n on 2006-04-03
Thanks tseliot for a great thread, I was able to get my nvida drivers running perfectally so that I could adjust the contract and gamma settings that I always need to mod.

I have a GeForce FX 5200 card  and I am havign trouble getting Dual head/Multi view to work.

Does anyone have a working xorg.cong as I have seen many and none are particularly  similar.

This is my current config file.  Any help is greatly appricated.
  
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "HP D2837"
        Option          "DPMS"
EndSection

Section "Monitor"
	Identifier	"DELL"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"HP D2837"
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
		Modes		"1600×1200" "1280x1024" "1024x768" "800x600" "640x480"
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


Thanks

---

### Post by tseliot on 2006-04-04
[QUOTE=km0ti0n]Thanks tseliot for a great thread, I was able to get my nvida drivers running perfectally so that I could adjust the contract and gamma settings that I always need to mod.

I have a GeForce FX 5200 card  and I am havign trouble getting Dual head/Multi view to work.

Does anyone have a working xorg.cong as I have seen many and none are particularly  similar.

This is my current config file.  Any help is greatly appricated.[/QUOTE]
If you need to use multiple monitors you should use this guide:
[http://www.ubuntuforums.org/showthread.php?t=85769&highlight=nvidia+twinview]("http://www.ubuntuforums.org/showthread.php?t=85769&highlight=nvidia+twinview")
 
Or this one (which is related to Gentoo Linux)
[http://gentoo-wiki.com/HOWTO_Dual_Monitors]("http://gentoo-wiki.com/HOWTO_Dual_Monitors")

---

### Post by km0ti0n on 2006-04-04
Thanks for the reply,

Sorry to have wasted your time, I had just found that howto and managed to get my dual head working nicely.

Thanks again.

---

### Post by Ensnared on 2006-04-07
Follwing this howto made my TV-out work nicely, thanks :) Things like this helps when you've been using ATI for a decade and just now switched to something better ;)

I do have one question though - is there any way to get a widescreen resolution on my TV? I have a 32" Panasonic widescreen CRT TV, but the only resolution I get on it is 1024x768 but I'm fairly certain that the TV itself supports 1366x768 like most 32" widescreen TV's do. I tried entering that as the resolution under the Screen section for the TV (Device[1]/Monitor[1]) but that didn't help.

My board is an nVidia Geforce 6200 256MB, and I'm using the latest drivers on Dapper.

The (as far as I know) relevant lines my Xorg logfile is:
```
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "Monitor[1]"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(**) NVIDIA(1): Forcing COMPOSITE video output
(**) NVIDIA(1): ConnectedMonitor string: "Monitor[1]"
(WW) NVIDIA(1): Invalid ConnectedMonitor string token: "Monitor[1]";
(WW) NVIDIA(1):      discarding token.
(**) NVIDIA(1): TV Standard string: "PAL-B"
(--) NVIDIA(1): Linear framebuffer at 0xD0000000
(--) NVIDIA(1): MMIO registers at 0xE2000000
(II) NVIDIA(1): NVIDIA GPU detected as: GeForce 6200
(--) NVIDIA(1): VideoBIOS: 05.44.a2.07.00
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(II) NVIDIA(1): Detected AGP rate: 8X
(--) NVIDIA(1): VideoRAM: 262144 kBytes
(II) NVIDIA(1): Connected display device(s): CRT-0, TV-0
(--) NVIDIA(1): Detected TV Encoder: NVIDIA
(--) NVIDIA(1): TV-0: maximum pixel clock: 400 MHz
(II) NVIDIA(1): Frequency information for TV-0:
(II) NVIDIA(1):   HorizSync   : 30.000-50.000 kHz
(II) NVIDIA(1):   VertRefresh : 60.000 Hz
(II) NVIDIA(1):      (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(1):      (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(1):      section)
(II) NVIDIA(1): Monitor[1]: Using hsync range of 30.00-50.00 kHz
(II) NVIDIA(1): Monitor[1]: Using vrefresh value of 60.00 Hz
(II) NVIDIA(1): Clock range:  12.00 to 400.00 MHz
<removed several "not using default mode" lines due to vrefresh and hsync being out of range>
(II) NVIDIA(1): Not using mode "1366x768" (no mode of this name)
(WW) NVIDIA(1): Not using mode "1280x800" (not a valid TV mode)
(WW) NVIDIA(1): Not using mode "1280x768" (not a valid TV mode)
(WW) NVIDIA(1): Not using mode "640x384" (not a valid TV mode)
(WW) NVIDIA(1): Not using mode "512x384" (not a valid TV mode)
(**) NVIDIA(1): Validated modes for display device TV-0:
(**) NVIDIA(1):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(1):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(1):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(1):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(1):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(1):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(1): Unable to get display device TV-0's EDID; cannot compute DPI
(WW) NVIDIA(1):      from EDID.
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
```

This is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Dec 14 16:39:22 PST 2005


Section "ServerLayout"
    Identifier     "Layout0"
    Screen 0       "Screen[0]"
    Screen 1	   "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath        "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
#    Load	   "GLcore"
    Load	   "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    Option	   "Buttons" "6"
EndSection

#Section "InputDevice"
#    Identifier    "Mouse0"
#    Driver        "mouse"
#    Option        "Protocol" "evdev"
#    Option        "Dev Name" "Logitech USB-PS/2 Mouse M-BA47"
#    Option        "Dev Phys" "usb-0000:00:02.1-2/input0"
#    Option        "Device" "/dev/input/event1"
#    Option        "Buttons" "6"
#    Option        "ZAxisMapping" "4 5"
#EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
EndSection

Section "Monitor"
    Identifier     "Monitor[0]" # CRT Monitor
    VendorName     "Iiyama"
    ModelName      "HM903DTA"
    Option         "DPMS"
    HorizSync       30.0 - 132.0
    VertRefresh     45.0 - 200.0
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" # TV 
    HorizSync	   30-50
    VertRefresh	   60
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID	   "PCI:3:0:0"
    Option 	   "RenderAccel" "true"
    Option	   "AllowGLXWithComposite" "true" 
    Screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-B" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
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

Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```

So is there any way to make it work, or is this perhaps a limitation of the driver itself?

---

### Post by SSamiK on 2006-04-16
Thanks for a great HOWTO! Worked like a charm with my GeForce4 Ti4200. :D 
 

Just a few things....

[QUOTE=el3ktro] Well it seems that with your how-to you get two full-blown desktops, is there a way to get a blank, black screen on the TV, and just display a video from e.g. mplayer/xine on the TV?[/QUOTE]

Is it a way to do this? I have a [nautilus-script]("http://ubuntuforums.org/showpost.php?p=378322&postcount=54") witch allows me to rigth-click a file and display it on the TV in fullscreen, but i would like to remove the menus and maby even the wallpaper, as they are of no use.

Secondly,  i used to have running programs displayed on the gnome panel when minimized, but now they just vanish and i need to use the TAB button to find them again... Not a big deal, but annoying. Anyone who knows what causes this, and how to fix it? 

Last but not least: Is there a way to be able to drag a open program (and/or files), from the monitor over to the tv? As of now, programs and files stop at the right end of my monitor and only the mousepointer move over to the TV.

---

### Post by ralin on 2006-04-16
I followed the guide and my TV shows ubuntu starting up, shows the nvidia logo, and then it shows that grey screen that pops up right before the logon screen.  But it stays stuck there.  I have tried several different settigns to get it to work but i cant seem to be able to get anything other than a grey screen on the tv. i can move my mouse off the right side of my lcd desktop, so the server section seems to be working right. i think its probably something wrong with how i setup the tv as a monitor in my xorg.conf.  im running dapper flight 6 with xgl and compiz (it dosent work even i change to a normal session) but that could be causing alot of the problems. It also prevents me form useing twinview.  

here is my xorg.conf:

---

### Post by tseliot on 2006-04-16
> **Ensnared]Follwing this howto made my TV-out work nicely, thanks :) Things like this helps when you've been using ATI for a decade and just now switched to something better  said:**
> /Monitor[1]) but that didn't help.

My board is an nVidia Geforce 6200 256MB, and I'm using the latest drivers on Dapper.
Try this guide:
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---

### Post by tseliot on 2006-04-16
[QUOTE=SSamiK]Is it a way to do this? I have a [nautilus-script]("http://ubuntuforums.org/showpost.php?p=378322&postcount=54") witch allows me to rigth-click a file and display it on the TV in fullscreen, but i would like to remove the menus and maby even the wallpaper, as they are of no use.[/QUOTE]
Can't you do that? You should have 2 distinct desktops

[QUOTE=SSamiK]Secondly,  i used to have running programs displayed on the gnome panel when minimized, but now they just vanish and i need to use the TAB button to find them again... Not a big deal, but annoying. Anyone who knows what causes this, and how to fix it?[/QUOTE]
Right click on the gnome panel and add the taskbar.

[QUOTE=SSamiK]Last but not least: Is there a way to be able to drag a open program (and/or files), from the monitor over to the tv? As of now, programs and files stop at the right end of my monitor and only the mousepointer move over to the TV.[/QUOTE]
I don't know if it's possible. I usually open an application on the same display I need to use it.

---

### Post by tseliot on 2006-04-16
[QUOTE=ralin]I followed the guide and my TV shows ubuntu starting up, shows the nvidia logo, and then it shows that grey screen that pops up right before the logon screen.  But it stays stuck there.  I have tried several different settigns to get it to work but i cant seem to be able to get anything other than a grey screen on the tv. i can move my mouse off the right side of my lcd desktop, so the server section seems to be working right. i think its probably something wrong with how i setup the tv as a monitor in my xorg.conf.  im running dapper flight 6 with xgl and compiz (it dosent work even i change to a normal session) but that could be causing alot of the problems. It also prevents me form useing twinview.  

here is my xorg.conf:[/QUOTE]
Your xorg.conf seems ok (I'm saying "seems" bacause I've slept only 4 hours)

I haven't tried this guide with Dapper yet. I really wouldn't know how to help you.

Perhaps on the Unofficial Nvidia Forums they'll be able to help you

---

### Post by ralin on 2006-04-16
[QUOTE=tseliot]Your xorg.conf seems ok (I'm saying "seems" bacause I've slept only 4 hours)

I haven't tried this guide with Dapper yet. I really wouldn't know how to help you.

Perhaps on the Unofficial Nvidia Forums they'll be able to help you[/QUOTE]

thanks for taking a look. at least i know im not makeing some silly mistake

---

### Post by Titus A Duxass on 2006-04-17
Hello all,
I have just read this thread from start to end, unfortunately I am now totally confused as to which part of the how-to applies to me.

I want to set-up my pc to my tv only, I do not need or want another monitor (though I can connect one if necessary to assist with the set-up).

I am based in Germany so my tv is PAL-B (I think).

I am connecting via a SVIDEO (or is that S-VIDEO) and at present I have the ubuntu desktop on the tv but with terrrible colour renditioning (bright, garish colours and barely readable text) and it is to big.

My xorg.conf is a normally generated one, i.e. I have not carried out any changes as per the how-to.

I lot of the thread talks about twin set-up and focussing, which bit do I need to use to get tv only.

Thanks
Titus.

---

### Post by tseliot on 2006-04-17
[QUOTE=Titus A Duxass]Hello all,
I have just read this thread from start to end, unfortunately I am now totally confused as to which part of the how-to applies to me.

I want to set-up my pc to my tv only, I do not need or want another monitor (though I can connect one if necessary to assist with the set-up).

I am based in Germany so my tv is PAL-B (I think).

I am connecting via a SVIDEO (or is that S-VIDEO) and at present I have the ubuntu desktop on the tv but with terrrible colour renditioning (bright, garish colours and barely readable text) and it is to big.

My xorg.conf is a normally generated one, i.e. I have not carried out any changes as per the how-to.

I lot of the thread talks about twin set-up and focussing, which bit do I need to use to get tv only.

Thanks
Titus.[/QUOTE]
I have never tried such a thing. However if your problem is the resolution and refresh rate you can try this guide:
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---

### Post by Titus A Duxass on 2006-04-17
Okay, I managed to get it working.
I copy the xorg.conf posted by dninja on about page 8 of this thread.
Then I did some changes:
PAL-I to PAL-B
changed the mouse and keyboard entries in the server section to:
Generic Keyboard 
Configured Mouse

Fired it all up again, found the mouse was locked.
Cured that by removing power, removing the BIOS battery and resetting the BOIS.

Now it all works apart from MythTV being slightly bigger than the TV screen, I think I'll have to go to Myth Talk for that one.  I did try nvtv but it gives "segmentation fault".

---

### Post by cazz on 2006-04-29
Hmm I follow that guide and restart and now I cant see GNOME because that is something wrong with the Server-X.

I have attach that config that work (xorg.conf.orginal) and that config that dont work (xorg.conf.change)

Maybe someone can tell me what I did wrong :???:

---

### Post by elsupermang on 2006-04-29
For those of you with laptops here's how to set it up so X will activate any extra screens as a clone automatically. 


```
Section "Device"
	Identifier	"NVIDIA Corporation NV41.8 [GeForce Go 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"AllowGLXWithComposite"	"true"
	Option		"RenderAccel"	"true"
	Option		"CursorShadow"	"1"
	Option		"NoLogo"
	Option		"TwinView"	"true"
	Option		"TwinViewOrientation"	"Clone"
	Option		"TVOutFormat"		"SVIDEO"
	Option		"TVStandard"		"NTSC-M"
	Option		"Metamodes"	"dfp-0:1440x900,dfp-1:1024x768@1440x900;dfp-0:1440x900,tv:800x600@1440x900;dfp-0:1440x900,dfp-1:NULL"
EndSection
```

dfp-0 refers to your laptop screen, dfp-1 refers to any CRT or LCD connected via the 15 pin connector and tv refers to the S-VIDEO connection.

This way you can connect whatever you want and it will automatically setup everything without having to edit your xorg.conf. The last metamode is for running with only your laptop monitor activated when there is no connection present.

Also the 1024x768 @ 1440 x 900 makes it so you will output a resolution of 1024x768 with a panning area of 1440x900. Its for when the other monitor cant support that big a resolution but you want the whole screen to be panned. If your laptop monitor has a standard resolution of 1024x768 you dont need this.

---

### Post by cazz on 2006-04-29
Thanks I change orginal so it look like

```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
    Driver         "nvidia"
    Option 		"RenderAccel" 		"true"
    Option 		"AllowGLXWithComposite" "true" 
    Option		"IgnoreEDID"		"true"
    Option		"IgnoreEdidFreqs"	"true"
    Option		"GenerateRTList"	"0"
    Option		"OverridePolarity"	"1"
    Option		"TwinView"	"true"
    Option		"TwinViewOrientation"	"Clone"
    Option		"TVOutFormat"		"SVIDEO"
    Option		"TVStandard"		"PAL-B"
    Option		"Metamodes"	"dfp-0:1440x900,dfp-1:1024x768@1440x900;dfp-0:1440x900,tv:800x600@1440x900;dfp-0:1440x900,dfp-1:NULL"
EndSection
```

I can see a picture on my TV but that is black and white to big (only part of login script show) that I think that is because the picture is to little.
But I have no picture on my laptop, is just black screen.

---

### Post by elsupermang on 2006-04-29
You have to change the resolution, my laptop uses 1440X900 as its native resolution so you have to change it to match your laptop's native, unless it is 1440x900 as well.

For example if your laptops native is 1280x720 you would use 

Option		"Metamodes"	"dfp-0:1280x720,dfp-1:1280x720;dfp-0:1280x720,tv:800x600@1280x720;dfp-0:1280x720,dfp-1:NULL"

the @ is used when the maximum resolution supported by the other monitor is smaller than the resolution your first monitor is outputting. if anyone knows how to scale this so you can have different resolutions fit perfectly, please do tell.

---

### Post by cazz on 2006-04-30
Now I have picture on TV and my laptop but that is something strange.

1) I have a black and white picture on TV?

2) I change size of tv:XXXXXX but that is same size on the tv when I restart the X-server??

/EDIT

1) I change in the config file from SVIDEO to Composit (But I have a S-video contact) so now I have color (strong colour)

2) I have read about that a TV only can take 800x600 but that dont show whole desktop?

I have this now

```
"dfp-0:1280x800,dfp-1:1024x768@1280x800;dfp-0:1280x800,tv:800x600;dfp-0:1280x800,dfp-1:NULL"
```

---

### Post by kebabtomten on 2006-04-30
I have follow the guide and i get an picutre on my TV but it is black(it is wihte when the Nvidia logo is showed) This is my xorg.conf> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
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
#"ExplorerPS/2"

Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier "Monitor[0]" #CRT
        Option          "DPMS"
        HorizSync 31.5-70
                VertRefresh 50-120 
EndSection

 Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Device"
        Identifier      "Device[0]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        screen 0
EndSection

Section "Device" 
        Driver          "nvidia" 
        Identifier      "Device[1]" 
        Screen 1 
        Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
        Option          "TVStandard" "PAL-B" #or NTSC etc 
        Option          "ConnectedMonitor" "Monitor[1]" 
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
        Identifier  "Screen[0]" 
        Device      "Device[0]" 
        Monitor     "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1152x864" "1024x768" "800x600" "720x400" "640x480"
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


What is wrong? I know i use an SVIDEO and i have try with PAL-B and PAL-G. I am from Sweden so sorry for my bad English.

---

### Post by elsupermang on 2006-04-30
Cazz change tv:800x600 to tv:800x600@1280x800

It's not the best solution but its better than having to set your laptop screen to 800x600.

kebab try some other formats

> PAL-B
	

Belgium, Denmark, Finland, Germany, Guinea, Hong Kong, India, Indonesia, Italy, Malaysia, The Netherlands, Norway, Portugal, Singapore, Spain, Sweden, and Switzerland

PAL-D
	

China and North Korea

PAL-G
	

Denmark, Finland, Germany, Italy, Malaysia, The Netherlands, Norway, Portugal, Spain, Sweden, and Switzerland

PAL-H
	

Belgium

PAL-I
	

Hong Kong, Ireland, and United Kingdom

PAL-K1
	

Guinea

PAL-M
	

Brazil

PAL-N
	

France, Paraguay, and Uruguay

PAL-NC
	

Argentina

NTSC-J
	

Japan

NTSC-M
	

Canada, Chile, Colombia, Costa Rica, Ecuador, Haiti, Honduras, Mexico, Panama, Puerto Rico, South Korea, Taiwan, United States of America, and Venezuela

HD480i
	

480 line interlaced

HD480p
	

480 line progressive

HD720p
	

720 line progressive

HD1080i
	

1080 line interlaced

HD1080p
	

1080 line progressive

HD576i
	

576 line interlace

HD576p
	

576 line progressive

Also make sure your TV actually supports 1024x768, i know some that can only do 800x600 or 640x480

---

### Post by cazz on 2006-04-30
Thanks

I did try that but that is same result.
The picture on TV dont show whole desktop


```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
    Driver         "nvidia"
    Option 		"RenderAccel" 		"true"
    Option 		"AllowGLXWithComposite" "true" 
    Option		"IgnoreEDID"		"true"
    Option		"IgnoreEdidFreqs"	"true"
    Option		"GenerateRTList"	"0"
    Option		"OverridePolarity"	"1"
    Option		"TwinView"	"true"
    Option		"TwinViewOrientation"	"Clone"
    Option		"TVOutFormat"		"Composite" #SVIDEO
    Option		"TVStandard"		"PAL-B"
    Option		"Metamodes"	"dfp-0:1280x800,dfp-1:1024x768@1280x800;dfp-0:1280x800,tv:800x600@1280x800;dfp-0:1280x800,dfp-1:NULL"
EndSection
```


I going to try other then "clone"

No that was no good.

But someome told me to read Appendix P (Configuring Multiple X Screens on One Card)
Maybe that help.


/EDIT
The Appendix P is that exempel that start this thread and that I can't get to work, no picture in the TV.

---

### Post by cazz on 2006-04-30
I have try a little but nothing show on TV

I have never give up before and I dont going to give up yet. [-( 

I have attach my xorg.conf file
I see no error in the Xorg.0.log

---

### Post by kebabtomten on 2006-05-02
i change the resolutuion and now it works =) But there is one thing i dont like,  i cant switch of the tv on an easy way. Is that possibel?

---

### Post by elsupermang on 2006-05-02
Well all you have to do is disconnect the cable heh. But if your on a laptop some have a hardware switch (like FN + F8) that will kill the signals.

---

### Post by kebabtomten on 2006-05-03
[QUOTE=elsupermang]Well all you have to do is disconnect the cable heh. But if your on a laptop some have a hardware switch (like FN + F8) that will kill the signals.[/QUOTE]
I dont meen like that, i whant it to be like my xorg.conf_backup. Can i switch that on/off on any easy way?

---

### Post by gizm0 on 2006-05-04
I finally got my xorx.conf work with my DiBoss 32" (HDTV) LCD-TV. Now i have two kinds of problems: when i remove "ModeLine "720p" 73.825 1280 1320 1368 1640 720 722 724 751 +hsync +vsync" line from Monitor section, then LCD TV works great, BUT it has very big black borders around of the picture. The second problem is that, if i include "ModeLine "720p" 73.825 1280 1320 1368 1640 720 722 724 751 +hsync +vsync" line to monitor section, then the picture will overscan and i can't see the taskbars.

 I have tried to set the resolution to 1080i, but it did the same thing :(. I also have tried to remove and add virtual screen size, but it didn't help either. This is the only problem that i have with tv-out: overscan or black borders around the picture (empty space).

Has anybody got advices for this? Here is my xorg.conf in the attachment.

Here is my computers etc. specs: AMD 64 2800+,epox paj,nvidia 6600,breezy badger,nvidia drivers and DiBoss 32" LCD-TV (HDTV LT-32Q5LFH). LCD-Tv is connected to PC with component cable.

---

### Post by eerstkoffie on 2006-05-04
wow ! interesting and complete stuff here, but i could'nt find anything for my nvtv-problem.
maybe one of you can help me out.

after i installed nvtv, i could start my machine, and after login, pessing the F1 button starts my television.

but, the screen, the desktop that appears on my tv is huge. like zooming in and only seeing the centerpart of the desktop. it's way to big to resize it with the mouse.
changing resolution didn't help, and besides that, nvtv doesn't seem to remember any changes i made, after a restart.

i'm using a Asus 7100 card, believe it uses nvidia chipset.
nvidia drivers installed on my box.

hope someone has a tip...

---

### Post by Haegin on 2006-05-08
Hi,
I followed the guide in post 1 and my TV still isn't working. Its worked before so I know it isnt the hardware. Here is my xorg.conf and a snippet from my Xorg.0.log.
Can you see anything wrong?

---

### Post by Patok on 2006-05-08
Hey
Used your guide
Thing is, now my keyboard doesnt work and my mouse can move but not click
And the tvout doesnt wor k either, and my Gnome desktop was totally changed
Please what can i do
Thanx

edit:
I managed to restore the old xorg.conf file from the backup, but I would still really like to be able to have the tv-out, so what can I do?

---

### Post by Jonas_Henricsson on 2006-05-13
I followed the instructions, but after I tried restarting the computer, X doesn't load. I get some kind of error message. Good thing I got the backup.

There is one difference between my xorg,conf and the one described in the instructions: 
Section "Device"
	Identifier	"Device[0]"
	Driver		**"nv"**
	BusID		"PCI:1:0:0"
	Screen 0
EndSection

So it says nv instead of nvidia under driver. Can this be the cause of my problem?

/Jonas

---

### Post by tseliot on 2006-05-14
[QUOTE=Jonas_Henricsson]I followed the instructions, but after I tried restarting the computer, X doesn't load. I get some kind of error message. Good thing I got the backup.

There is one difference between my xorg,conf and the one described in the instructions: 
Section "Device"
	Identifier	"Device[0]"
	Driver		**"nv"**
	BusID		"PCI:1:0:0"
	Screen 0
EndSection

So it says nv instead of nvidia under driver. Can this be the cause of my problem?

/Jonas[/QUOTE]
Yes, of course that's the problem. It means that you haven't installed the nvidia proprietary driver. Please follow my guide about the installing the driver.

---

### Post by Jonas_Henricsson on 2006-05-14
[QUOTE=tseliot]Yes, of course that's the problem. It means that you haven't installed the nvidia proprietary driver. Please follow my guide about the installing the driver.[/QUOTE]

Oh. Well, I just tried installing the drivers using Automatix and it caused an error I've been having problems with for quite some time. After I installed the drivers, I couldn't even get into X before the computer got hung up. But that's probably some kind of hardware error with my graphics card and I probably shouldn't fiddle too much with it... It's actually the reason why I left windows for Ubuntu :)

Thanks for the help!

/Jonas

---

### Post by tseliot on 2006-05-14
[QUOTE=Jonas_Henricsson]Oh. Well, I just tried installing the drivers using Automatix and it caused an error I've been having problems with for quite some time. After I installed the drivers, I couldn't even get into X before the computer got hung up. But that's probably some kind of hardware error with my graphics card and I probably shouldn't fiddle too much with it... It's actually the reason why I left windows for Ubuntu :)

Thanks for the help!

/Jonas[/QUOTE]
Please read my guide:
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

If you want the latest version of the driver you will also find a link to my scripts there (for an automatic installation).

---

### Post by danzat on 2006-05-21
Well, I followed your guide, and the TV is blank.

I get this error in the console:
(EE) NVIDIA(1): No modes remaining for display device TV-0

---

### Post by tseliot on 2006-05-21
[QUOTE=danzat]Well, I followed your guide, and the TV is blank.

I get this error in the console:
(EE) NVIDIA(1): No modes remaining for display device TV-0[/QUOTE]
Perhaps your Tv doesn't support  the resolution you set. Try a lower resolution in your xorg.conf (only for your tv)

---

### Post by Lotherian on 2006-05-22
Hi there!

Thanks for an excellt guide! It worked flawless! :-D 

The only trouble I have is that the TV is in the other end of my room and my eyes are not eaglesharp! So can you point me to a (hopefully excellent) guide that instead of 2 diffrent work areas makes a clone of my desktop on the tv?

Keep up the good work!

/T

---

### Post by tseliot on 2006-05-22
[QUOTE=Lotherian]Hi there!

Thanks for an excellt guide! It worked flawless! :-D 

The only trouble I have is that the TV is in the other end of my room and my eyes are not eaglesharp! So can you point me to a (hopefully excellent) guide that instead of 2 diffrent work areas makes a clone of my desktop on the tv?

Keep up the good work!

/T[/QUOTE]
Use the search function and look for Nvidia Twinview (which is a method alternative to mine)

---

### Post by Jose Catre-Vandis on 2006-05-22
Oh, I have tried everything, having read all 17 pages, am nearly there but not quite.

I get flickering horizontal lines on my TV, you know, like a slightly out of tune TV station 

TV is a Panasonic TX 36 PL30, and behaves the same if the refresh scan mode is set to progressive or 100mhz

Cable OK, as can see text on boot and when not in X

PC is a Shuttle SN41G2, which has 2 x VGA heads and an SVIDEO out (this might be causing a problem?)

log shows problems with EDID, but tried the option and this did funny screen things to my desktop. Apart from this the CRT has been rock solid in terms of display.

Attached are xorg.conf and xorg.0.log in 2 halves

[ATTACH]9876[/ATTACH]

[ATTACH]9877[/ATTACH]

[ATTACH]9878[/ATTACH]

If it helps I also tried Twinview, this gave me a steady vertical picture, but skewed and in triplicate across the screen

---

### Post by tseliot on 2006-05-23
[QUOTE=Jose Catre-Vandis]Oh, I have tried everything, having read all 17 pages, am nearly there but not quite.

I get flickering horizontal lines on my TV, you know, like a slightly out of tune TV station 

TV is a Panasonic TX 36 PL30, and behaves the same if the refresh scan mode is set to progressive or 100mhz

Cable OK, as can see text on boot and when not in X

PC is a Shuttle SN41G2, which has 2 x VGA heads and an SVIDEO out (this might be causing a problem?)

log shows problems with EDID, but tried the option and this did funny screen things to my desktop. Apart from this the CRT has been rock solid in terms of display.

Attached are xorg.conf and xorg.0.log in 2 halves

[ATTACH]9876[/ATTACH]

[ATTACH]9877[/ATTACH]

[ATTACH]9878[/ATTACH]

If it helps I also tried Twinview, this gave me a steady vertical picture, but skewed and in triplicate across the screen[/QUOTE]
Since you say that also Twinview doesn't work I'm lead to think that is a hardware incompatibility (which perhaps can be solved).

Therefore I suggest you to start a new thread on the Unofficial Nvidia Forums (the Nvidia staff will help you there):
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")

---

### Post by caish5 on 2006-05-25
I got my TV working first go with the guide, but i cannot get my mouse to go over there!! Very Frustrating..
Here is my xorg.conf
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
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-G" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection
        
        
Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
        HorizSync 31.5-80 
        	VertRefresh 56.3-75 
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
EndSection

Section "Screen"
	Identifier	"Screen [0]"
	Device		"Device [0]"
	Monitor		"Monitor [0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "720x576" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	    Screen 0 "Screen[0]" 
            Screen 1 "Screen[1]" RightOf "Screen[0]" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
The only thing I think it could be is that i copied the vertrefresh and horizsync settings out of the guide because i could not find any for my monitor. But somehow i don't think that is the problem.
Ideas anyone????

---

### Post by tseliot on 2006-05-25
[QUOTE=caish5]I got my TV working first go with the guide, but i cannot get my mouse to go over there!! Very Frustrating..
Here is my xorg.conf
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
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-G" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection
        
        
Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
        HorizSync 31.5-80 
        	VertRefresh 56.3-75 
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
EndSection

Section "Screen"
	Identifier	"Screen [0]"
	Device		"Device [0]"
	Monitor		"Monitor [0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "720x576" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	    Screen 0 "Screen[0]" 
            Screen 1 "Screen[1]" RightOf "Screen[0]" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
The only thing I think it could be is that i copied the vertrefresh and horizsync settings out of the guide because i could not find any for my monitor. But somehow i don't think that is the problem.
Ideas anyone????[/QUOTE]
Can you remove the space between "Screen" and  "[0]" (do the same for the lines quoted below)
> Section "Screen"
	Identifier	"Screen [0]"
	Device		"Device [0]"
	Monitor		"Monitor [0]"

Then restart the xserver (or even better, unplug the cable and reboot)

---

### Post by caish5 on 2006-05-25
Thanks a lot. I removed the spaces and all is good. 
Allthough is there a way you can drag applications from one screen to another?

---

### Post by tseliot on 2006-05-25
[QUOTE=caish5]Thanks a lot. I removed the spaces and all is good. 
Allthough is there a way you can drag applications from one screen to another?[/QUOTE]
I really wouldn't know. Perhaps with Twinview you can do that

---

### Post by technophreak on 2006-05-25
I followed this guide exactly, but now when I boot Ubuntu, I get an error saying that X System couldnt start. How can I restore my default xorg.conf file so I can at least login?

Thanks

---

### Post by tseliot on 2006-05-25
[QUOTE=technophreak]I followed this guide exactly, but now when I boot Ubuntu, I get an error saying that X System couldnt start. How can I restore my default xorg.conf file so I can at least login?

Thanks[/QUOTE]
Type:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

and then reboot by typing:
```
sudo reboot
```

---

### Post by amr2205 on 2006-05-27
Great post! :D 
This is very useful for me, thanks a lot and keep the good work! =D>

---

### Post by psavva on 2006-05-28
Hi,
I'm new to Ubuntu.  I've been playing around with it for about a month now. Trying to get it working the way i want.

I've come accross a problem with my displays though.

I have an NVIDIA FX 5600 Graphics card (256 MB) with two Two Monitors capability.

I have followed the HOWTO: NVIDIA TV-OUT Guide and with no luck.

I've correctly installed the latest nvidia drivers (NVIDIA-Linux-x86-1.0-8762)

I can't seem to get my TV display working.  

Here's a copy of my xorg.conf file.



# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

-------------------------------------------------------------------------------------------

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
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
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
	Identifier 	"Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync 	31.5-80 
        VertRefresh 	56.3-75 
EndSection

 Section "Monitor" 
    Identifier "TV" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 		1 
	Option     	"TwinView"
   	Option          "TVOutFormat" "SVIDEO" #or Composite etc 
   	Option          "TVStandard" "PAL-I"
    	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
    	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "TV" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "800x600" 
       	EndSubSection    
EndSection


-----------------------------------------------------------------------------------------------

Any help will be greatly appreciated.

:smile: :smile:

---

### Post by Jose Catre-Vandis on 2006-05-28
> **tseliot]Since you say that also Twinview doesn't work I'm lead to think that is a hardware incompatibility (which perhaps can be solved).

Therefore I suggest you to start a new thread on the Unofficial Nvidia Forums (the Nvidia staff will help you there):
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")[/QUOTE]


Thought I would report back, on success, although it was with Twinview rather than your way! Found a config file used by someone on another distro, specifically for an SN41G2. Oddly, the way to do it was to remove all the configuration you might think would be needed. No need to indicate horiz and vert refresh rates, TV Standards or Output Format. Using an SVideo lead the picutre is crystal clear. Will try a similar config with your setup to see if that works too. I know this isn said:**
> Section "ServerLayout"
Identifier "single head configuration"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
RgbPath "/usr/X11R6/lib/X11/rgb"
FontPath "unix/:7100"
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
Option "XkbRules" "xfree86"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
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
ModelName "Dell P780"
HorizSync 30.0 - 85.0
VertRefresh 48.0 - 120.0
Option "dpms"
EndSection

Section "Device"

# Option "SecondMonitorHorizSync" "30.0-60.0"
# Option "SecondMonitorVertRefresh" "48.0-80.0"
Option "UseEdidFreqs" "true" #Probes for HorizSync and VertRefresh
Option "TwinView" "true" #Enables TwinView
Option "NoLogo" "true" #Turns off nvidia logo at x startup
Option "ConnectedMonitor" "CRT, CRT"
# Option "TwinviewOrientation" "clone" #Second monitor is clone of first
Option "TwinviewOrientation" "RightOf" #Second monitor is desktop right of first
Option "Metamodes" "1280x1024, 1024x768"
# Option "TVStandard" "NTSC-M"
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
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
"640x480"
EndSubSection
EndSection

Section "DRI"
Group 0
Mode 0666
EndSection

btw, this works perfectly whether I have both the vga and svideo outputs connected or either/or, and you can see everything from boot through to login etc

---

### Post by xlyz on 2006-05-28
[quote=tseliot]Remember not to boot (EVER) with the TV-OUT calbe plugged in.
[/quote]

why?

perchè?

---

### Post by tseliot on 2006-05-29
[QUOTE=xlyz]why?

perchè?[/QUOTE]
Otherwise it might not work. (I didn't write the drivers so I can't give you a technical answer)

---

### Post by tseliot on 2006-05-29
[QUOTE=Jose Catre-Vandis]Thought I would report back, on success, although it was with Twinview rather than your way! Found a config file used by someone on another distro, specifically for an SN41G2. Oddly, the way to do it was to remove all the configuration you might think would be needed. No need to indicate horiz and vert refresh rates, TV Standards or Output Format. Using an SVideo lead the picutre is crystal clear. Will try a similar config with your setup to see if that works too. I know this isn;t a Twinview place, but here is the xorg.conf I found that sorted my problem, hope it helps others:



btw, this works perfectly whether I have both the vga and svideo outputs connected or either/or, and you can see everything from boot through to login etc[/QUOTE]
Thanks for reporting

---

### Post by xlyz on 2006-06-03
[quote=tseliot]Otherwise it might not work. (I didn't write the drivers so I can't give you a technical answer)[/quote]
mine works ;)

I feared it could damage the tv

---

### Post by deus777 on 2006-06-04
I am having problems getting TV-Out working.  I am on a Dell Inspiron 8200 laptop, which has an Nvidia 4 Go 440 in it.  I installed the NVidia drivers using EasyUbuntu and nvtv using Synaptic. I am running Breezy and am up-to-date.  Here is my original xorg.conf: [ATTACH]10592[/ATTACH]

I tried to follow TSEliot's instructions and ended up with the following xorg.conf:[ATTACH]10593[/ATTACH]

When I boot with this xorg.conf, I get a black screen on my laptop with a pointer.  I can move the pointer to the right and onto another "screen" which appears on my laptop screen and the pointer changes to an X cursor.  The TV acts as if it is getting no signal.  The composite cable is plugged in and the TV is on the right input setting at the time Ubuntu boots.

I tried to follow elsupermang's instructions on a fresh copy of my xorg.conf and ended up with the following xorg.conf:[ATTACH]10594[/ATTACH]

When I boot with this xorg.conf, I can log into Ubuntu, but I still don't get anything on the TV.

Can anyone help me get this working?  Thanks in adavance for any help. :)

P.S. Please don't ask me to upgrade to Dapper because I tried with RC a few days before release and I couldn't even boot into X.

---

### Post by axm on 2006-06-04
I am trying (for two days now) to figure out, how to get the tv-out running. I failed and I am desperate for some help. This post has gotten a bit long, sorry.



Needing: use of TV-out, does not matter how in the first place, Situation:

-ubuntu 5.10

-nvidia GeForce 3 Ti 200

-Mini DIN S-Video / Scart Connection to TV

-TV: Grundig MW 82-100 (16:9 but also 4:3 capable and "recognizes" a 4:3 "no-"signal; 

	has a VGA in (I cannot use that one due to no second vga out), that specifies

        640x480@60Hz, 31.5hf, 60vf and understands as well some PALs as NTSCs.)

-running perfectly in this configuration under Win XP (switch view, not dual)



1) Firstly, I tried this howto. But after some doubts, if my graphics card can handle two screens at the same time (no TwinView support as for nvtv needed, I am still not sure if X11 can do that anyway, would be great), I tried this one:



2) [http://www.iofcea.de/cgi-bin/seite.pl?file=linuxtvout](http://www.iofcea.de/cgi-bin/seite.pl?file=linuxtvout)



..which goes for switching between two Xservers. Did not help either.



3) Then I tried to get the TV running as a single monitor like someone implicitely suggested in the "tv-out for newbies"-thread. But that did not work again, so I am assuming it is the configuration for the TV that is wrong.



Outcome: A blink on the TV every startup, then nothing. I cannot move the mouse cursor to the next screen, but I do not know if that should happen without TwinView. So far the big picture, now the errors.

_____



1) I constantly get this one while trying to load two screens:



(II) NVIDIA(0): Connected display device(s): CRT-0, TV-0

(WW) NVIDIA(0): Multiple displays connected, but only one display allowed

(WW) NVIDIA(0): 	using first display



Hence my thoughts about my graphics card not beeing able to do this, but I do really not know that. After all, I have seen this warning sometimes in error logs on the web, but it was not mentioned as a source of problems at all.


The real bugger should be:

(II) NVIDIA(1): Using ConnectedMonitor string "TV-0"
(EE) NVIDIA(1): The requested configuration of display devices is not
(EE) NVIDIA(1):      supported in the hardware.



[http://forum.michaxm.de/tv-out/xorg.conf.backup-dualscreen](http://forum.michaxm.de/tv-out/xorg.conf.backup-dualscreen)
[http://forum.michaxm.de/tv-out/Xorg.0.log-dual](http://forum.michaxm.de/tv-out/Xorg.0.log-dual)

2) For the switching method: Starts up perfectly (no Errors, no Warnings apart from APM or some missing fonts(?)), but does not switch to TV (becoming black and returning):



>sudo X -screen screen1 :1 -ac & sleep 2; DISPLAY=:1 totem && kill `ps aux | awk '/X\ -screen/ {print $2}' `



(EE) NVIDIA(0): No modes remaining for display device CRT-0

(EE) NVIDIA(0):   *** Aborting ***

(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:

no screens found
[...Exit 1]
Gtk-WARNING **: cannot open display

Again, I think that could hint to the tv configuration.



[http://forum.michaxm.de/tv-out/xorg.conf.backup-switching](http://forum.michaxm.de/tv-out/xorg.conf.backup-switching)
[http://forum.michaxm.de/tv-out/Xorg.0.log-switching](http://forum.michaxm.de/tv-out/Xorg.0.log-switching)

[http://forum.michaxm.de/tv-out/Xorg.1.log-switching](http://forum.michaxm.de/tv-out/Xorg.1.log-switching)

3) This is where it went really frustating. I removed the crt in the server layout of 1), only the tv remaining:

	Screen 0	"screen1"
	#Screen 1	"screen1" RightOf "screen0"

I paranoidly also tried commenting the crt monitor/device/screen sections and
renamed the tv sections from 1 to 0, with the same result:


(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
...
(EE) Screen 0 deleted because of no matching config section.
...

...resulting in a startup without X. So either there must be something wrong with the TV-config or it is not possible for linux to use a TV but no CRT, which I doubt. The TV is capable of at least 640x480 and should also be capable of standard freqencies.

[http://forum.michaxm.de/tv-out/xorg.conf.backup-tvonly](http://forum.michaxm.de/tv-out/xorg.conf.backup-tvonly)
[http://forum.michaxm.de/tv-out/Xorg.0.log-tvonly](http://forum.michaxm.de/tv-out/Xorg.0.log-tvonly)

I also rebooted with the tv-out cable unplugged, but no change except that the TV was not automatically recognized anymore. I hope someone has an idea, would be staggering to boot Windows just for that. Thanks in advance.

PS: Would be at least good to know:
a) apart from my problem: if it is possible to dual screen without a TwinView capable card
b) if the analysis (tv-configuration is the problem) should be correct

---

### Post by tseliot on 2006-06-05
[QUOTE=axm]I am trying (for two days now) to figure out, how to get the tv-out running. I failed and I am desperate for some help. This post has gotten a bit long, sorry.[/QUOTE]
1) Did you install the Nvidia driver?
2) If so, which version of the driver are you using?

I warn you that driver 8762 might cause you problems with TV-OUT (I use 8756)

---

### Post by axm on 2006-06-05
[QUOTE=tseliot]1) Did you install the Nvidia driver?
2) If so, which version of the driver are you using?

I warn you that driver 8762 might cause you problems with TV-OUT (I use 8756)[/QUOTE]

Yes, of course I installed nvidia drivers, but I have to be slapped for not thinking about bad versions. apt get gave me 1.0.7667-0ubuntu25.1, after your post I tried 1.0.7174-0ubuntu25.1 (legacy drivers) which changed nothing and now I have the 8756 from nvidia installed. That makes no visible difference, but one in the logs:


(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(I assume that means nothing important since device 0 is fine)
...
(WW) NVIDIA(1): There are only 1 CRTCs available, trimming display device list
(WW) NVIDIA(1):     from "TV-0" to "".
(II) NVIDIA(1): Assigned Display Device:
(WW) NVIDIA(1):
(WW) NVIDIA(1): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(1):     will be used as the requested mode.
(WW) NVIDIA(1):
(WW) NVIDIA(1): No valid modes for "nvidia-auto-select"; removing.
(WW) NVIDIA(1):
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1):
(WW) NVIDIA(1): No valid modes for "nvidia-auto-select"; removing.
(EE) NVIDIA(1): Unable to use default mode "nvidia-auto-select".

Again, I suspect the TV configuration, I did a little bit trial-and-error (achieving nothing) and at the moment I ended up with:

    HorizSync       30 - 50
    VertRefresh     40 - 60

and
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection

---

### Post by deus777 on 2006-06-05
[QUOTE=tseliot]1) Did you install the Nvidia driver?
2) If so, which version of the driver are you using?

I warn you that driver 8762 might cause you problems with TV-OUT (I use 8756)[/QUOTE]

I have the NVidia driver installed but I don't know which version it is.  Is there a command I can run to find out what version I have installed?

---

### Post by tseliot on 2006-06-06
[QUOTE=deus777]I have the NVidia driver installed but I don't know which version it is.  Is there a command I can run to find out what version I have installed?[/QUOTE]
```
dmesg | grep NVIDIA
```

---

### Post by tseliot on 2006-06-06
Guys, I suggest you to ask for help on the Unofficial Nvidia Forums (Nvidia's staff will help you there):
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&page=2&order=desc]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&page=2&order=desc")

---

### Post by tseliot on 2006-06-07
**[COLOR="Red"]UPDATE: I have solved the problem with TV-OUT and driver 8762 (with my card, I'm not sure if it works for you).[/COLOR]**

Get to the Screen Section regarding your TV in your xorg.conf and set the refresh rate of your TV just like in the example below:

```
Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_[COLOR="Red"]60[/COLOR]" 
       	EndSubSection    
EndSection
```

The word in red is the refresh rate.

**NOTE if your TV does not support a refresh rate of 60Hz you might want to set this line "Modes "1024x768_60"" as "Modes "1024x768_50"" in order to set the refresh rate to 50Hz**

---

### Post by walding on 2006-06-07
Hi,

I've been trawling through to find an answer to my question...sorry if this is a repeat question...

I want to set up multiple clones from my laptop:

RGB-out for my projector
SVIDEO out for my TV

Or as a second option, to have the RGB as clone, and SVIDEO as a second screen (can that be done with ~ "LCD Screen Clone RGB leftof SVIDEO"?) 

Can anyone help me do this, please?  I can't find a thorough guide on how to add devices and specify where they are.

Thanks

AW

---

### Post by tseliot on 2006-06-07
[QUOTE=walding]Hi,

I've been trawling through to find an answer to my question...sorry if this is a repeat question...

I want to set up multiple clones from my laptop:

RGB-out for my projector
SVIDEO out for my TV

Or as a second option, to have the RGB as clone, and SVIDEO as a second screen (can that be done with ~ "LCD Screen Clone RGB leftof SVIDEO"?) 

Can anyone help me do this, please?  I can't find a thorough guide on how to add devices and specify where they are.

Thanks

AW[/QUOTE]
You should look for the guide about Twinview

---

### Post by walding on 2006-06-07
Yeah - that's how I ended up here!  Never mind.

---

### Post by Riz on 2006-06-07
hi guys ive been trying to get tv out workingfor several days and finally got it working except that i can only see the top left quarter of the screen. Can anyone tell me how to change the picture size on the tv out? ive got a GeForce 5700and connect to my tv via a SVIDEO and scart adapter. the strange thing is that the picture is perfect all the way through booting its only once the nvidia logo screen comes up that it doesnt fit on the tv anymore.
This is my Xorg.conf file
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "ch"
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
    Identifier     "BenQ FP731 "
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "TV"
    Option         "TVStandard" "PAL-I"
    Option         "SVIDEO"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV36 [GeForce FX 5700]"
    Driver         "nvidia"

# twinview
    Option "TwinView"
    Option "TwinViewOrientation" "Clone"
    Option "SecondMonitorHorizSync" "30-50"
    Option "SecondMonitorVertRefresh" "50"
    Option "MetaModes" "1280x1024, 800x600"
    Option "TVStandard" "PAL-I"
    Option "ConnectedMonitor" "CRT, TV"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV36 [GeForce FX 5700]"
    Monitor        "BenQ FP731 "
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection
```

Thanks in advance for any help. :)

---

### Post by auburn on 2006-06-08
Thanks tseliot! I got my geforce4 mx 4000 to work under dapper. I'm pleased. My first attempt failed (I didn't copy and paste) but then I tried rewriting the xorg.conf one step at a time. First I changed all the names and stayed with the one crt, and when that worked I added the tv.

---

### Post by NaughtyusMaximus on 2006-06-08
I've been able to this to work as described on page 1 with my computer (dapper), but I want to do something else and can't figure it out on my own.

I've plugged two keyboards and two mice into my computer.  So what I want is for screen[0] (CRT) to use mouse[0] and keyboard[0], and screen[1] (TV) to use mouse[1] and keyboard[1]

I know this must be possible, but I'm at a loss for how to do it.

---

### Post by tseliot on 2006-06-08
[QUOTE=Riz]hi guys ive been trying to get tv out workingfor several days and finally got it working except that i can only see the top left quarter of the screen. Can anyone tell me how to change the picture size on the tv out? ive got a GeForce 5700and connect to my tv via a SVIDEO and scart adapter. the strange thing is that the picture is perfect all the way through booting its only once the nvidia logo screen comes up that it doesnt fit on the tv anymore.
This is my Xorg.conf file[/QUOTE]

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV36 [GeForce FX 5700]"
    Monitor        "BenQ FP731 "
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024[COLOR="Red"]_60[/COLOR]" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection
```

Set the refresh rate of your monitor in the part in red. For example if you want to use a 60Hz Refresh rate you have to write "_60" ("_75" for 75Hz and so on).

Then restart the xserver.

---

### Post by vic5 on 2006-06-10
I have Geforce mx 440. my   xorg.conf:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, 
# using values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual 
# page. (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option "NoLogo" "True"
       Option "TwinView" "1"
       Option "HorizSync" "CRT: 28-75, TV: 30-66"
       Option "VertRefresh" "CRT: 43-160, TV: 60"
       Option "SecondMonitorHorizSync" "30-66"
       Option "SecondMonitorVertRefresh" "60"
       Option "TwinViewOrientation" "Clone"
        Option  "MetaModes" "1024x768_75,1024x768"
        Option "ConnectedMonitor" "CRT, TV"
        Option "TVStandard" "PAL-B"
        Option        "RenderAccel"        "true" 
        Option        "AllowGLXWithComposite" "true"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-75
	VertRefresh	43-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
        Option "ExactModeTimingsDVI" "TRUE"
        Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768_75" "832x624" "800x600" "720x450" "720x400" "640x480" "640x400"
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



I have only  1024x768 50 Hz in my monitor. When i hash "Twin View" and restart x ten everything is ok, but there is no tv-out. What is wrong?

---

### Post by tseliot on 2006-06-10
[QUOTE=vic5]I have Geforce mx 440. my   xorg.conf:
I have only  1024x768 50 Hz in my monitor. When i hash "Twin View" and restart x ten everything is ok, but there is no tv-out. What is wrong?[/QUOTE]
Sorry but I don't use Twinview. You should ask for help on the thread about Twinview

---

### Post by Riz on 2006-06-10
> 
Set the refresh rate of your monitor in the part in red. For example if you want to use a 60Hz Refresh rate you have to write "_60" ("_75" for 75Hz and so on).

Then restart the xserver.


Tried several different refresh rates now, but it doesnt seem to make any difference whatsoever :-s . Anyone got any other ideas? Cheers

---

### Post by tseliot on 2006-06-11
[QUOTE=Riz]Tried several different refresh rates now, but it doesnt seem to make any difference whatsoever :-s . Anyone got any other ideas? Cheers[/QUOTE]
Sorry but I don't use Twinview. I didn't notice you were using Twinview.

---

### Post by vic5 on 2006-06-11
[QUOTE=tseliot]Sorry but I don't use Twinview. You should ask for help on the thread about Twinview[/QUOTE]

Ok. So now i have my x.org like this : 


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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"pl"
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
Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        screen 0
Option		"RenderAccel"		"true"
Option		"AllowGLXWithComposite" "true"
EndSection
Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "S-VIDEO" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-B" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
#Option		"RenderAccel"		"true"
#Option		"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	28-75
	VertRefresh	43-160

EndSection
Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
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
		Modes		"1280x1024""1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

EndSection
Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection
	


Section "ServerLayout"
	Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection

Section "DRI"
	Mode	0666
EndSection


Everything was fine. But i install XGL, and now on the TV i have only grey screen... What is wrong? (sorry for my English).Help!

---

### Post by tseliot on 2006-06-12
[QUOTE=vic5]Ok. So now i have my x.org like this : 





Everything was fine. But i install XGL, and now on the TV i have only grey screen... What is wrong? (sorry for my English).Help![/QUOTE]
Remove XGL

---

### Post by Mguel on 2006-06-14
Thanks for the How-to!

It worked fine on Kubuntu dapper 6.06 using geforce2 mx 400

I'm using a servicemenu to run videos on tv with kaffeine, I post it in case someone find it useful:

```
[Desktop Action PlayOnTV]
Exec=kaffeine -f -display :0.1 %F
Icon=kaffeine-play
Name=Play on TV

[Desktop Entry]
Actions=PlayOnTV
Encoding=UTF-8
Icon=kaffeine-play
ServiceTypes=video/*
``` 
I also commented the positioning of the second screen (RightOf or Below) so the mouse doesn't go of my crt screen since I only use tv out for movies which I start with the servicemenu I posted, and because before doing this sometimes apps opened on my TV (while working on the CRT what was a bit disturbing) [edit: sometimes when pressing alt+F2 the run command prompt still appears on the TV]

I haven't been able to do 2 things:

1.- preventing the kicker from the tv display from starting (I can kill it manually once started)

2.- change focus from the TV to the CRT. Once I launch movies they have focus, but if I do something on the screen (click a window for instance) I can't get focus back to the TV so I can for example pause the movie. A workaround would be a way to make mouse "jump" from one screen to the other

Thanks,
Mguel

---

### Post by Upuntu on 2006-06-17
Hi! I tested this HOW-TO, and I got a picture in TV, but it is black and white. I attached my Xorg.conf and Xorg.0.log here. I'm Living in Finland so I use PAL-B. My TV is LG Flatron and its 2-3 years old. My Graphic Card is NVIDIA PALIT GF 5200. TV-OUT connector is SVIDEO, but I have tested this with Composite cable too. If I try change Option          "TVOutFormat" to RGB, its still Black and white like with SVIDEO. If I use COMPOSITE, there is no picture in TV at all.

---

### Post by tseliot on 2006-06-17
[QUOTE=Upuntu]Hi! I tested this HOW-TO, and I got a picture in TV, but it is black and white. I attached my Xorg.conf and Xorg.0.log here. I'm Living in Finland so I use PAL-B. My TV is LG Flatron and its 2-3 years old. My Graphic Card is NVIDIA PALIT GF 5200. TV-OUT connector is SVIDEO, but I have tested this with Composite cable too. If I try change Option          "TVOutFormat" to RGB, its still Black and white like with SVIDEO. If I use COMPOSITE, there is no picture in TV at all.[/QUOTE]
Try with a different cable

---

### Post by Upuntu on 2006-06-17
[QUOTE=tseliot]Try with a different cable[/QUOTE]
I've got only one this long cable, but I have tested both cables with DVD Player, and they worked perfektly. So that's not the problem.

---

### Post by tseliot on 2006-06-17
[QUOTE=Upuntu]I've got only one this long cable, but I have tested both cables with DVD Player, and they worked perfektly. So that's not the problem.[/QUOTE]
I quote these posts which might be of help (they refer to your TV):

> Sorted the pc and main telly. As I said before it was there and colour but with really bad picture quality. It was originally in scart socket AV1, if I changed it to AV2 the picture quality was perfect but black and white again, but by accident I found that when chosing AV2 I could also chose AV2S which gave picture quality and colour. I've no idea what the S stands for and what the differences between AV1, AV2 and AV2S are but I now have a nice clear picture in colour.

> I've found the hidden menu option to get it to use AV-S rather than plain old AV. I've now got perfect quality output running on my tv. I've just got to find a way to get the tv save the setting.

---

### Post by Upuntu on 2006-06-17
[QUOTE=tseliot]I quote these posts which might be of help (they refer to your TV):[/QUOTE]
Thanks for you, but I just got one A/V channel and one Scart socket. So that didn't help me...

---

### Post by 3togo on 2006-06-21
Same to me....

if I set 
Option "TVOutFormat" "COMPOSITE" 
=> no TV out

if I disable this Option by putting a "#" like this
#Option "TVOutFormat" "COMPOSITE" 

I got a twinviews with greyed TV-out (no color).

---

### Post by brandt on 2006-06-22
Hi,
I'm just trying to get the X11 to do TV-out (no regular monitor) and I can't seem to get it to even do that.  From everything I've read, my configuration *should* work, but doesn't.  The only thing I can think of is that the card is a GeForce2 (roughly 5 years old) so maybe the nvidia drives don't play nicely with it.  TV-out works fine under windows, but I'd much rather run Linux.  Can someone take a look at my xorg.conf/log and see if I've overlooked something?  Thanks.

xorg.conf
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

Section "Device"
	Identifier	"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nvidia"
	Option		"RenderAccel" "true"
	Option		"ConnectedMonitor" "TV"
	Option          "TVOutFormat" "SVIDEO" #"COMPOSITE" or "SVIDEO"
   	Option          "TVStandard" "NTSC-M"
	#Option		"TVOverScan" "0.6"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Monitor		"TV"
	DefaultDepth 24 
	SubSection "Display" 
		Depth 24
		Modes "1024x768" "800x600" "640x480"
		#ViewPort 0 0
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


Xorg.0.log
```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux bill 2.6.16-ck12 #1 Wed Jun 21 03:00:10 MDT 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 22 01:24:30 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0691 card 0000,0000 rev c4 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8598 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0000 rev 40 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 0000,0000 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 16 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 16 class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 1106,3057 rev 40 class 06,00,00 hdr 00
(II) PCI: 00:07:5: chip 1106,3058 card 1106,3058 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:09:0: chip 109e,036e card 0000,0000 rev 11 class 04,00,00 hdr 80
(II) PCI: 00:09:1: chip 109e,0878 card 0000,0000 rev 11 class 04,80,00 hdr 80
(II) PCI: 00:0b:0: chip 100b,0020 card 1385,f311 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0150 card 1462,8831 rev a4 class 03,00,00 hdr 00
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
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:9:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xdf002000/12
(--) PCI:*(1:0:0) nVidia Corporation NV15 [GeForce2 GTS/Pro] rev 164, Mem @ 0xdc000000/24, 0xd0000000/27
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
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdf001000 - 0xdf001fff (0x1000) MX[B]
	[1] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[2] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[3] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[5] -1	0	0xdf002000 - 0xdf002fff (0x1000) MX[B](B)
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[9] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[12] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdf001000 - 0xdf001fff (0x1000) MX[B]
	[1] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[2] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[3] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[5] -1	0	0xdf002000 - 0xdf002fff (0x1000) MX[B](B)
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[9] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[12] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
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
	[4] -1	0	0xdf001000 - 0xdf001fff (0x1000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xdf002000 - 0xdf002fff (0x1000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
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
	[4] -1	0	0xdf001000 - 0xdf001fff (0x1000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xdf002000 - 0xdf002fff (0x1000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdf001000 - 0xdf001fff (0x1000) MX[B]
	[5] -1	0	0xdf000000 - 0xdf000fff (0x1000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xdf002000 - 0xdf002fff (0x1000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[22] 0	0	0xdd0003b0 - 0xdd0003bb (0xc) IS[B]
	[23] 0	0	0xdd0003c0 - 0xdd0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "TV"
(**) NVIDIA(0): Option "TVStandard" "NTSC-M"
(**) NVIDIA(0): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Forcing SVIDEO output
(**) NVIDIA(0): TV Standard string: "NTSC-M"
(**) NVIDIA(0): ConnectedMonitor string: "TV"
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by tseliot on 2006-06-22
[QUOTE=brandt]Hi,
I'm just trying to get the X11 to do TV-out (no regular monitor) and I can't seem to get it to even do that.  From everything I've read, my configuration *should* work, but doesn't.  The only thing I can think of is that the card is a GeForce2 (roughly 5 years old) so maybe the nvidia drives don't play nicely with it.  TV-out works fine under windows, but I'd much rather run Linux.  Can someone take a look at my xorg.conf/log and see if I've overlooked something?  Thanks.[/QUOTE]
Why don't you read my guide?

---

### Post by dhega on 2006-06-24
Hello, i have tried your guide all day now but i do not get any picture on my tv :(

I will post my xorg config and maybe someone can see what i have done wrong

I have a PCI-E 6800GS card btw.!

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen 0 "Screen0" 
    Screen 1 "Screen1" RightOf "Screen0" 
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option		"CoreKeyboard"
    Option		"XkbRules"	"xfree86"
    Option		"XkbModel"	"pc105"
    Option		"XkbLayout"	"se"
EndSection

Section "Monitor"
    Identifier     "Monitor0" #CRT
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor" 
    Identifier "Monitor1" #TV 
    HorizSync 50 
    VertRefresh 30-150 
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Screen 0
EndSection

Section "Device" 
   Driver          "nvidia" 
   Identifier      "Device1" 
   Screen 1 
   Option          "TVOutFormat" "SVIDEO" #or S-VIDEO etc 
   Option          "TVStandard" "PAL-B" #or NTSC etc 
   Option          "ConnectedMonitor" "Monitor1" 
  # BusID           "PCI:5:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen" 
   Device "Device1" 
   Identifier "Screen1" 
   Monitor "Monitor1" 
   DefaultDepth 24 
       SubSection "Display" 
               Depth 24 
               Modes "1024x768_50" 
       EndSubSection    
EndSection

```




My log file:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux dhega-desktop 2.6.15-23-amd64-generic #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 24 18:15:17 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/share/X11/fonts/TTF/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/OTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID/" does not exist.
	Entry deleted from font path.
(==) FontPath set to "/usr/share/X11/fonts/misc/,/usr/share/X11/fonts/Type1/,/usr/share/X11/fonts/100dpi/,/usr/share/X11/fonts/75dpi/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
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
(II) PCI: 00:00:0: chip 10de,005e card 1695,1010 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1695,1010 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1695,1010 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1695,1010 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1695,1010 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1695,1010 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1695,1010 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1695,1010 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:06:0: chip 173b,03ea card 1385,302a rev 15 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 10de,00c0 card 1682,2178 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfd800000 - 0xfd8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(5:0:0) nVidia Corporation NV41.0 rev 162, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[1] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[2] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[3] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[4] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[5] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[9] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[10] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[11] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[12] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[13] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[1] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[2] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[3] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[4] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[5] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[9] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[10] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[11] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[12] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[13] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
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
	[4] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[18] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[19] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
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
(II) NVIDIA X Driver  1.0-8762  Mon May 15 14:01:11 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Assigning device section with no busID to primary device
(--) Assigning device section with no busID to primary device
(WW) NVIDIA: More than one matching Device section found: Device1
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
	[4] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[18] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[19] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[21] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[22] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[24] 0	0	0xfc0003b0 - 0xfc0003bb (0xc) IS[B]
	[25] 0	0	0xfc0003c0 - 0xfc0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 GS at PCI:5:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.41.02.49.05
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 GS at PCI:5:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[24] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[25] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[27] 0	0	0xfc0003b0 - 0xfc0003bb (0xc) IS[B]
	[28] 0	0	0xfc0003c0 - 0xfc0003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xfree86"
(**) Keyboard0: XkbRules: "xfree86"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Keyboard0: XkbLayout: "se"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded



```

---

### Post by tseliot on 2006-06-24
[QUOTE=dhega]Hello, i have tried your guide all day now but i do not get any picture on my tv :(

I will post my xorg config and maybe someone can see what i have done wrong

I have a PCI-E 6800GS card btw.![/QUOTE]
Everything seems ok. Perhaps it's a problem of the driver (with you card).

Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

---

### Post by dhega on 2006-06-25
you didn't see anything wrong?

maybe i should try to manually download the latest nvidia drivers.

The ones i have right now was installed using Automatix. And i dont know if they are new or old :D

---

### Post by tseliot on 2006-06-25
[QUOTE=dhega]The ones i have right now was installed using Automatix. And i dont know if they are new or old :D[/QUOTE]
They are the latest

---

### Post by Vlatko on 2006-06-25
i just followed this guide and i, obviously, did something wrong. now i can't boot into kubuntu anymore. i made the backup of the file, how can i restore it so i can boot into kubuntu?

---

### Post by Vlatko on 2006-06-25
please someone, it's kind of a emergency. :(

---

### Post by Haegin on 2006-06-25
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by Vlatko on 2006-06-25
[QUOTE=Human Prototype]sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf[/QUOTE]
thanks. i am back in kde ;)

i saved a copy of the edited file so if someone feels like it, he can tell me what i did wrong. my card is 6600gt, monitor lg 1750s and i use a s-video cable with "s-video to composite" adapters on both ends. thanks. :)

---

### Post by ChicoMakani on 2006-06-28
Thanks!  This guide worked great for me. I'm running Dapper w/ a 6150 w/ an LCD on monitor 1 at 1280x1024 and an old CRT on 2 at 800x600.  

The only problem is that if I start mythtv from monitor 1 with -display :0.1 it comes up but will not display video on monitor 2.  If I start on monitor 2 it works.

Another thing is that the gnome menus get changed on monitor 1 , the sound, data get moved toward to center, and the trash is also moved toward the center on the bottom.

Any idea why full screen video can't be displayed this way?

Much nicer than twinview.  I didn't even know my hardware supported this functionality.

---

### Post by Jango on 2006-06-30
Guide is great, by mine still doesn't work.  The fine thing is that I actually can see that happens BEFORE the LOGIN screen and AFTER I LOGOUT =)))))))

Can anybody help me?

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
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"us"
	Option		"XkbOptions"	"us"
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
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:4:0:0"
	Option 		"RenderAccel" 		"true"
	Screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   	Option          "TVStandard" "NTSC-M" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:4:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
	HorizSync	24-83
	VertRefresh	55-77
EndSection

Section "Monitor" 
   Identifier "Monitor[1]" #TV 
   HorizSync 30-50
   VertRefresh 60 
EndSection


Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
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

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_50" 
       	EndSubSection    
EndSection

Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection

#Section "Extensions"
#          Option  "Composite" "Enable"
#EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by tseliot on 2006-06-30
[QUOTE=Jango]Guide is great, by mine still doesn't work.  The fine thing is that I actually can see that happens BEFORE the LOGIN screen and AFTER I LOGOUT =)))))))

Can anybody help me?

Here is my xorg.conf:[/QUOTE]
Reboot and see if it works. If it doesn't you can ask for help here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Jango on 2006-06-30
[QUOTE=tseliot]Reboot and see if it works. If it doesn't you can ask for help here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)[/QUOTE]

I tried. Still doesn't work. Hopefully guys there will help me. Thanks a lot.

---

### Post by M4LFUNCT10N on 2006-07-04
Hrm.... not working for me.  Followed the guide, but during a restart it fails to load Xserver.

I'm on a Toshiba Satellite 1415-S174, with a Nvidia 420.

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Screen[0]"
    Screen 1       "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Gene[ric Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
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
    Load           "dri"
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

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"evdev"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mx500" #this should be that underlined name from 19-local.rules
#EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
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
    Identifier     "Generic Monitor[0]"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

 Section "Monitor" 
    Identifier "Monitor[1]" TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    Option 	   "RenderAccel" 		"true"
    screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "NTSC-M" #or NTSC-J PAL-G etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection


Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option "ExactModeTimingsDVI" "TRUE" 
    Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

#Section "Extensions"
#          Option  "Composite" "Enable"
#EndSection

```

---

### Post by tseliot on 2006-07-05
[QUOTE=M4LFUNCT10N]Hrm.... not working for me.  Followed the guide, but during a restart it fails to load Xserver.

I'm on a Toshiba Satellite 1415-S174, with a Nvidia 420.

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Screen[0]"
    Screen 1       "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Gene[ric Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
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
    Load           "dri"
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

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"evdev"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mx500" #this should be that underlined name from 19-local.rules
#EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
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
    Identifier     "Generic Monitor[0]"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

 Section "Monitor" 
    Identifier "Monitor[1]" TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    Option 	   "RenderAccel" 		"true"
    screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "NTSC-M" #or NTSC-J PAL-G etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection


Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option "ExactModeTimingsDVI" "TRUE" 
    Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

#Section "Extensions"
#          Option  "Composite" "Enable"
#EndSection

```[/QUOTE]
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Scorpuk on 2006-07-08
Have been trying to follow this thread for half a day now and still can;t get a desktop on my TV.

When my computer boots up I see all the splash screens on my TV up until I get the graphical login and it goes blank.

Hitting ctrl+Alt+F1 I get the CLI login on my LCD and my TV.

Not sure if my xorg.conf file is correct, but here it is for you to check:

[xorg.conf]("http://scorpuk.plus.com/xorg.conf")

Also did the startx with verbose and the log file is:

[Xorg.0.log]("http://scorpuk.plus.com/Xorg.0.log")



Much appreciated if you can help me out.


John.

---

### Post by Mguel on 2006-07-08
Hi, my TV-Out is working great, but it seems that it caused me some other little problems (at least khotkeys not working correctly), some of which I described in: [Kubuntu 6.06 issues (screensaver, hotkeys, kcron, Ark part)]("http://ubuntuforums.org/showthread.php?t=207385")

I restored my old xorg.conf file (before following this guide) and the khotkeys work fine again (forgot to test kscreensaver and kcron problem).

When using the modified xorg.conf (with tv-out) I have two khotkeys running (the same as 2 kickers, 2 kdesktop, 2 kwin, etc). If I run khotkeys from konsole I get the following error:
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
``` 
Any help on how to solve this would be greatly appreciated since I won't like to quit on TV-Out nor mouse gestures+keyboard shortcuts.

Thanks,
Mguel

---

### Post by nuclearw on 2006-07-09
Hello,

I feel obliged to append the fact that I'm new to this and might need a bit more explanation on some command line functions.

I've got a GeForce2 Go on an Inspiron8200.  I've got the TV output working, but not that way I want it.

First, I'm not sure if I've got the nvidia legacy drivers installed properly.  When I ran the .run package I got a message saying couldn't find "ld" in package "binutils".  However, I see the Nvidia splash screen and TV-out is working, so, I'm not sure if it's properly installed.  Is there anyway I can find out?

Second, when my TV-out works, my login screen is at the same resolution as the TV, but when I login, my monitor jumps to the proper resolution.  The TV, on the otherhand only shows the top right hand corner of the screen.

Is there anyway I can enable "panning" so that I can view the entire contents of my DFP monitor by moving the mouse and the TV display follows my mouse?

Also, right now, the way it works is that if I open additional applications in the same screen space as my video, it overlays itself, and I can't see the video.  Is there anyway I can force the video output to play at full screen on the TV, while allowing me to use my entire desktop space on the DFP display?

I've attached the relevant parts (I think) of my xorg.conf and xorg.0.log files.

One thing that might be odd, are my metamodes settings.  The order seems to be DFP-0, TV-0 in the xorg.0.log file, but it seems like I have to set my metamodes resolution opposite (TV-0 resolution, DFP-0 resolution).  If I do the opposite "1400x1050,640x480" I don't get any output on the TV.

Any assistant, suggestions are truly appreciated.  Really looking forward to getting this setup up and running smoothly.  The log file is attached. The xorg.conf section is below.

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Option		"NoLogo"	"True"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"TwinView"
	#Option		"ConnectedMonitor" "DFP-0,TV-0"
	Option		"MetaModes" "640x480,1400x1050"
	Option 		"HorizSync"	"DFP-0:28-70;	TV-0:31.5-48.4"
	Option		"VertRefresh"	"DFP-0:43-60;	TV-0:60-60.3"
	Option		"TwinViewOrientation"	"Clone"
	Option 	"TVStandard"	"NTSC-M"
	Option	"TVOutFormat"	"Composite"
	
EndSection

---

### Post by tseliot on 2006-07-10
> **nuclearw said:**
> Hello,

I feel obliged to append the fact that I'm new to this and might need a bit more explanation on some command line functions.

I've got a GeForce2 Go on an Inspiron8200.  I've got the TV output working, but not that way I want it.

First, I'm not sure if I've got the nvidia legacy drivers installed properly.  When I ran the .run package I got a message saying couldn't find "ld" in package "binutils".  However, I see the Nvidia splash screen and TV-out is working, so, I'm not sure if it's properly installed.  Is there anyway I can find out?

Second, when my TV-out works, my login screen is at the same resolution as the TV, but when I login, my monitor jumps to the proper resolution.  The TV, on the otherhand only shows the top right hand corner of the screen.

Is there anyway I can enable "panning" so that I can view the entire contents of my DFP monitor by moving the mouse and the TV display follows my mouse?

Also, right now, the way it works is that if I open additional applications in the same screen space as my video, it overlays itself, and I can't see the video.  Is there anyway I can force the video output to play at full screen on the TV, while allowing me to use my entire desktop space on the DFP display?

I've attached the relevant parts (I think) of my xorg.conf and xorg.0.log files.

One thing that might be odd, are my metamodes settings.  The order seems to be DFP-0, TV-0 in the xorg.0.log file, but it seems like I have to set my metamodes resolution opposite (TV-0 resolution, DFP-0 resolution).  If I do the opposite "1400x1050,640x480" I don't get any output on the TV.

Any assistant, suggestions are truly appreciated.  Really looking forward to getting this setup up and running smoothly.  The log file is attached. The xorg.conf section is below.

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Option		"NoLogo"	"True"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"TwinView"
	#Option		"ConnectedMonitor" "DFP-0,TV-0"
	Option		"MetaModes" "640x480,1400x1050"
	Option 		"HorizSync"	"DFP-0:28-70;	TV-0:31.5-48.4"
	Option		"VertRefresh"	"DFP-0:43-60;	TV-0:60-60.3"
	Option		"TwinViewOrientation"	"Clone"
	Option 	"TVStandard"	"NTSC-M"
	Option	"TVOutFormat"	"Composite"
	
EndSection

You should ask in the thread about Twinview (because that's what you're using)

---

### Post by tseliot on 2006-07-10
**Scorpuk** and **Mguel**

Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by nuclearw on 2006-07-10
Thanks folks, sorry for posting in the wrong forum.

Cheers,
Ben

---

### Post by [pl]ice on 2006-07-14
hey, got Dapper with inspiron 5150 gForce 5200, work well on a huge plasma ;)
  questions:
1) i have no more F1-F6 cli :D i guess the output of those is to the wrong place... any ideas? :)
2)if i'll watch a movie, and on a CRT the pic is 'cut' on top and bottom, just black solid stripes, if i output that onto plasma, would that burn the plasma out? couse the picture in that places is stationary...of course it's black, but i'm not sure it i want to risk it!
[HTML]#
xorg file:
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
	Option		"XkbLayout"	"pl"
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
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "NoLogo"
	Screen  0
EndSection

  Section "Device"
	Identifier  "Device[1]"
	Screen 1
        Driver  "nvidia"
	Option "TVOutFormat" "SVIDEO"
	Option "TVStandard"  "NTSC-M"
	Option "ConnectedMonitor" "TV"
	BusID "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Monitor"
  Identifier "TV"
  HorizSync 30-50
  VertRefresh  60
EndSection


Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"CRT"
	DefaultDepth	16
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
	Identifier	"Simple Layout"
	Screen 0	"Screen[0]"
	Screen 1 	"Screen[1]" RightOf "Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


Section "Screen"
	Device "Device[1]"
	Identifier "Screen[1]"
	Monitor "TV"
	SubSection "Display"
		Depth 24
                Modes "1024x1024_60"
#		Modes "1024x768_60"
        EndSubsection
EndSection

Section "DRI"
	Mode	0666
EndSection

[/HTML]
  


  	
tseliot, congrats on graduation and good posts :cool:

---

### Post by tseliot on 2006-07-14
> **'[pl]ice said:**
> hey, got Dapper with inspiron 5150 gForce 5200, work well on a huge plasma ;)
  questions:
1) i have no more F1-F6 cli :D i guess the output of those is to the wrong place... any ideas? :)
Try point 13 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

> **'[pl]ice said:**
> 2)if i'll watch a movie, and on a CRT the pic is 'cut' on top and bottom, just black solid stripes, if i output that onto plasma, would that burn the plasma out? couse the picture in that places is stationary...of course it's black, but i'm not sure it i want to risk it!

The displayed area doesn't cover 100% of the screen. It's normal that 2 black stripes (very small on my 21" TV) appear on the upper and lower border of the screen.

I don't own a plasma TV but I can tell you that my Sony Wega 21" has not been damaged by those stripes.

---

### Post by Mguel on 2006-07-16
> **Mguel said:**
> Hi, my TV-Out is working great, but it seems that it caused me some other little problems (at least khotkeys not working correctly), some of which I described in: [Kubuntu 6.06 issues (screensaver, hotkeys, kcron, Ark part)]("http://ubuntuforums.org/showthread.php?t=207385")

I restored my old xorg.conf file (before following this guide) and the khotkeys work fine again (forgot to test kscreensaver and kcron problem).

When using the modified xorg.conf (with tv-out) I have two khotkeys running (the same as 2 kickers, 2 kdesktop, 2 kwin, etc). If I run khotkeys from konsole I get the following error:
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
``` 
Any help on how to solve this would be greatly appreciated since I won't like to quit on TV-Out nor mouse gestures+keyboard shortcuts.
I finally found a way to have khotkeys working with the xorg.conf with tv-out. I run:
killall khotkeys | khotkeys --display :0.0
and although I get an error message, it start to work (I created a link on the autostart folder, although a smarter thing would be to add the command line option wherever khotkeys is first launched on the kde startup process...)

---

### Post by Mguel on 2006-07-16
I have another problem:

After updating to linux-image-2.6.15-26-386 I can't startx, on the booting process I get a Fatal error telling that: ```
Module nvidia_legacy not found
Module nvidia not found
``` 
I can still run with kernel 2.6.15-25-386, so I'm using that, but I can't guess what is the problem with the newer one.

Thanks,
Mguel

---

### Post by tseliot on 2006-07-17
> **Mguel said:**
> I have another problem:

After updating to linux-image-2.6.15-26-386 I can't startx, on the booting process I get a Fatal error telling that: ```
Module nvidia_legacy not found
Module nvidia not found
``` 
I can still run with kernel 2.6.15-25-386, so I'm using that, but I can't guess what is the problem with the newer one.

Thanks,
Mguel

IF AND ONLY IF you installed the nvidia driver from Ubuntu's repos, try this command:
```
sudo apt-get install linux-386
```

and boot in the new kenrel.

OTHERWISE, if you installed the driver by means of the Nvidia installer or my script: 
boot in the new kernel and reinstall the driver

---

### Post by fanoodlehey on 2006-07-17
This howto works fine for me. Thanks.

---

### Post by [pl]ice on 2006-07-18
um, got another problem, wouldn't mind if a bit of help :-D 

   Got the video output working with plasma screen, but i can't get the audio to came out via SVIDEO from the tele... cable got two outputs, svideo and standard jack for (i assume) audio.
  anyone had problems? would it be with config? (i've posted it above)
thanks!!!

---

### Post by Mguel on 2006-07-18
> **tseliot said:**
> IF AND ONLY IF you installed the nvidia driver from Ubuntu's repos, try this command:
```
sudo apt-get install linux-386
```and boot in the new kenrel.
Yep, that was my case so intalled linux-386 and the new kernel runs fine :mrgreen:

Thanks!!!

---

### Post by unwoken on 2006-07-19
I'm hoping i can get some help.

I'm pretty sure that there is something minor i have missed out on.

very quickly, i can see picture on my TV:
1)as ubuntu shuts down (unloading modules)
2)through the whole boot process (including grub) - ends when x starts
3)in windows with minimal effort (sadly)

..i am using a cable which is s-video on the end plugged into my computer, and RCA on the end in the TV (i assume this is a composite cable?).

..i can log in to ubuntu fine.  when the plug is connected, i can move the cursor off my computer screen, but i can not see any picture at all on the TV.

..i am in australia and i am pretty sure we use PAL, so i left that section of the howto unchanged.

xorg.conf is as follows:
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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Screen[0]"
    Screen 1       "Screen[1]" RightOf "Screen[0]"  		
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
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
    Identifier     "Monitor[0]" #CRT"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-G" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "640x480_50" 
       	EndSubSection    
EndSection

```

i also tried 800x600 along with the original resolution suggested in the howto.  my tv is about 8 yrs old and on the back it says 50 HZ so i changed the TV mode to _50 (after 60 failed).  No joy at this stage.


i will complete the post in a new thread as my xorg.0.log is apparently too long.

u.

---

### Post by unwoken on 2006-07-19
part 2 (too many characters for 1 email)

xorg.0.log
```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux valhalla 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 20 09:43:23 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
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
(II) PCI: 00:00:0: chip 8086,27a0 card 103c,30a5 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 103c,30a5 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 103c,30a5 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 103c,30a5 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 103c,30a5 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 103c,30a5 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 103c,30a5 rev 01 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 103c,30a5 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d8 card 103c,30a5 rev a1 class 03,00,00 hdr 00
(II) PCI: 06:00:0: chip 8086,4222 card 103c,135b rev 02 class 02,80,00 hdr 00
(II) PCI: 08:06:0: chip 104c,8039 card 2400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 08:06:1: chip 104c,803a card 103c,30a5 rev 00 class 0c,00,10 hdr 80
(II) PCI: 08:06:2: chip 104c,803b card 103c,30a5 rev 00 class 01,80,00 hdr 80
(II) PCI: 08:06:3: chip 104c,803c card 103c,30a5 rev 00 class 08,05,00 hdr 80
(II) PCI: 08:08:0: chip 8086,1092 card 103c,30a5 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,9), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:28:2), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x52000000 - 0x520fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:30:0), (0,8,12), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd20fffff (0x100000) MX[B]
(II) Bus 8 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (8:6:0), (8,9,12), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 9 I/O range:
	[0] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[1] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
(II) Bus 9 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x01d8) rev 161, Mem @ 0xd1000000/24, 0xc0000000/28, 0xd0000000/24
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
(II) Active PCI resource ranges:
	[0] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[1] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[2] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[3] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[4] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[5] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[6] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[7] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[15] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[16] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[20] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[21] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[22] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[1] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[2] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[3] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[4] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[5] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[6] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[7] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[15] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[16] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[20] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[21] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[22] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
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
	[4] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[5] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[7] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[8] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[9] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[10] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[11] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[19] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[23] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
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
	[4] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[5] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[7] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[8] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[9] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[10] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[11] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[19] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[23] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[5] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[7] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[8] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[9] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[10] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[11] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[25] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[26] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[27] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7400 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.31.04
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7400 at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     QDS (DFP-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "Monitor[1]"
(**) NVIDIA(1): Option "TVStandard" "PAL-G"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing COMPOSITE video output
(**) NVIDIA(1): TV Standard string: "PAL-G"
(II) NVIDIA(1): NVIDIA GPU GeForce Go 7400 at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 05.72.22.31.04
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce Go 7400 at PCI:1:0:0:
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1):     QDS (DFP-0)
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: TV-0
(WW) NVIDIA(1): No valid modes for "640x480_50"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[8] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[9] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[10] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[11] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[12] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[13] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[14] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[15] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[25] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[26] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[27] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[28] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[29] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[30] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[31] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x800"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?

```

That's about all i can think of at the moment.  If i need to post anything else, please let me know and i will do my best.

u.

---

### Post by tseliot on 2006-07-20
> **unwoken said:**
> part 2 (too many characters for 1 email)

xorg.0.log
```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux valhalla 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 20 09:43:23 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
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
(II) PCI: 00:00:0: chip 8086,27a0 card 103c,30a5 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 103c,30a5 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 103c,30a5 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 103c,30a5 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 103c,30a5 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 103c,30a5 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 103c,30a5 rev 01 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 103c,30a5 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d8 card 103c,30a5 rev a1 class 03,00,00 hdr 00
(II) PCI: 06:00:0: chip 8086,4222 card 103c,135b rev 02 class 02,80,00 hdr 00
(II) PCI: 08:06:0: chip 104c,8039 card 2400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 08:06:1: chip 104c,803a card 103c,30a5 rev 00 class 0c,00,10 hdr 80
(II) PCI: 08:06:2: chip 104c,803b card 103c,30a5 rev 00 class 01,80,00 hdr 80
(II) PCI: 08:06:3: chip 104c,803c card 103c,30a5 rev 00 class 08,05,00 hdr 80
(II) PCI: 08:08:0: chip 8086,1092 card 103c,30a5 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,9), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:28:2), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x52000000 - 0x520fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:30:0), (0,8,12), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd20fffff (0x100000) MX[B]
(II) Bus 8 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (8:6:0), (8,9,12), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 9 I/O range:
	[0] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[1] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
(II) Bus 9 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x01d8) rev 161, Mem @ 0xd1000000/24, 0xc0000000/28, 0xd0000000/24
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
(II) Active PCI resource ranges:
	[0] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[1] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[2] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[3] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[4] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[5] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[6] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[7] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[15] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[16] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[20] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[21] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[22] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[1] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[2] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[3] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[4] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[5] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[6] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[7] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[15] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[16] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[20] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[21] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[22] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
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
	[4] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[5] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[7] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[8] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[9] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[10] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[11] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[19] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[23] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
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
	[4] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[5] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[7] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[8] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[9] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[10] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[11] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[19] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[23] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[5] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[6] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[7] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[8] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[9] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[10] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[11] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[25] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[26] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[27] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7400 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.31.04
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7400 at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     QDS (DFP-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "Monitor[1]"
(**) NVIDIA(1): Option "TVStandard" "PAL-G"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing COMPOSITE video output
(**) NVIDIA(1): TV Standard string: "PAL-G"
(II) NVIDIA(1): NVIDIA GPU GeForce Go 7400 at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 05.72.22.31.04
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce Go 7400 at PCI:1:0:0:
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1):     QDS (DFP-0)
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: TV-0
(WW) NVIDIA(1): No valid modes for "640x480_50"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd2006000 - 0xd2006fff (0x1000) MX[B]
	[8] -1	0	0xd2007800 - 0xd20078ff (0x100) MX[B]
	[9] -1	0	0xd2000000 - 0xd2003fff (0x4000) MX[B]
	[10] -1	0	0xd2007000 - 0xd20077ff (0x800) MX[B]
	[11] -1	0	0x52000000 - 0x52000fff (0x1000) MX[B]
	[12] -1	0	0xd2404400 - 0xd24047ff (0x400) MX[B]
	[13] -1	0	0xd2404000 - 0xd24043ff (0x400) MX[B]
	[14] -1	0	0xd2400000 - 0xd2403fff (0x4000) MX[B]
	[15] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xd2005000 - 0xd2005fff (0x1000) MX[B]
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[25] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[26] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[27] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[28] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[29] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[30] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[31] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x800"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?

```

That's about all i can think of at the moment.  If i need to post anything else, please let me know and i will do my best.

u.

Unfortunately I don't know too much about Tv-out. I think you should ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by unwoken on 2006-07-20
ok thanks.  i'll give it a go.

---

### Post by Beach on 2006-07-23
> **tseliot said:**
> Remove XGL
Has anyone figured out how to use this cool guide with Xgl/Compiz??  I only wanted to set this up so I could record from my S-Video.  I wanted to show my Windows-only friend how cool the Xgl/Compiz interface is.  

-Beach

---

### Post by Beach on 2006-07-23
Ok, got it to work with Xgl/Compiz by using Xinerama options with the setup information described here.  I will post my 'xorg.conf' file is anyone is interested.

-Beach

---

### Post by BerlinOliver on 2006-07-24
HI,

thanks for this guide. But it doesn't work at my place. I changed the xorg.conf as shown in your how-to.

Please find attached my original xorg.conf and the changed one for tv-out. I also attached the lspci -v output and the Xorg.logfile. It would be very kind of you, if you could help me.

---

### Post by MilesTEG1 on 2006-07-25
Hello,
Thanks for this tutorial.
It help me to configure TV-OUT on my Asus EN6600GT.
In following exactly what you said, I have some trouble.
I'm a french user of Kubuntu Dapper 64bits.
The TV image is trembling whith th **PAL-G** setting. To have a stable image I use **PAL**.
And I have to use the SVIDEO output methode.

All are ok now, hmmm almost...
I use Kde 3.5.3, and on the desk of my primary screen, i cannot take a windows to the tv screen... When I drop a window to the right after the border limit, the window go to the left border limit...
The same append to the up, left, down... so no windows can be droped to the TV like in Windows XP...
The Tv is not suitable to launch windows directly in the tv screen, because it is not easily readable...

Here you have my xorg.conf
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
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
	Identifier	"Device[0]"	# NVIDIA Corporation NV43 [GeForce 6600 GT]
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO , Composite etc 
   	Option          "TVStandard" "PAL" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

Section "Monitor"
	Identifier "Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
#    DisplaySize    270    203    # 1024x768 96dpi
#    DisplaySize    338    254    # 1280x960 96dpi
    DisplaySize    338    270    # 1280x1024 96dpi
#    DisplaySize    370    277    # 1400x1050 96dpi
#    DisplaySize    423    370    # 1600x1400 96dpi
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 	# NVIDIA Corporation NV43 [GeForce 6600 GT]
   	Monitor     "Monitor[0]"
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
	SubSection "Display"
		Depth		32
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
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
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

Can you help me to have this functionnal ?

Ps : I don't have "active borders of desktop" active... it is disabled.

Thanks
++
Miles

---

### Post by MTZeon on 2006-07-26
Well, after unsucessfully trying to get my laptop (FX5600Go & S-VIDEO) to work with my tv following this HOW TO, I came up with this config, which actualy did what I wanted! I use the TV to see some movies (no DVD player, so I use the laptop), and this is how I got it to work:

First make sure you have nvidia drivers installed...

edit your xorg.conf
$ sudo gedit /etc/X11/xorg.conf

find where it says:

> 
Section "Device"
    Identifier     "NVIDIA Corporation NV31M [GeForce FX Go5600]"
    Driver         "nvidia"
EndSection


and make it like:
> 
Section "Device"
    Identifier     "NVIDIA Corporation NV31M [GeForce FX Go5600]"
    Driver         "nvidia"
    [B]Option "TwinView" "1"
    Option "TwinViewOrientation" "Clone"
    Option "SecondMonitorHorizSync" "31-82"
    Option "SecondMonitorVertRefresh" "56-76"[/B]
EndSection


Save and that's it. Reboot your computer, tv on and you should have a cloned view of your laptop :)

This should work with composite or SVIDEO, since it should be managed by the drivers :)

Hope it helps!

---

### Post by mod187 on 2006-07-26
I tried many help tutorials on configuring TV out, and none worked. Some just caused more problems.

So...

I ran Automatix, and it fixed my TV out right away. No additional settings needed, it mirrors my monitor. No screen switching, etc...

Automatix does other cool stuff too...

---

### Post by MilesTEG1 on 2006-07-26
> **MTZeon said:**
> Well, after unsucessfully trying to get my laptop (FX5600Go & S-VIDEO) to work with my tv following this HOW TO, I came up with this config, which actualy did what I wanted! I use the TV to see some movies (no DVD player, so I use the laptop), and this is how I got it to work:

First make sure you have nvidia drivers installed...

edit your xorg.conf
$ sudo gedit /etc/X11/xorg.conf

find where it says:



and make it like:


Save and that's it. Reboot your computer, tv on and you should have a cloned view of your laptop :)

This should work with composite or SVIDEO, since it should be managed by the drivers :)

Hope it helps!

Ok, thanks.
But, it will clone my desk, right ?
I don't want that... I prefer Dual View like in XP.
If I do the modifications you said, will I be able to switch between the four desktop (1, 2, 3 and 4) and put in the 4 a movie player and watch it on TV and have another in my LCD ?

---

### Post by MilesTEG1 on 2006-07-27
Hello,
In doing a little modification of my xorg.conf to make this command functionnal :
```
mplayer -xineramascreen 1 -fs ton_film.avi
```
The little modification I do is to add :
```
Section "ServerFlags"
   Option "Xinerama" "true"
EndSection
```
And I have what I wanted in my first post !! Dual View like in XP !

So now I can drag&drop a window on my primary screen to the TV !

Yes ^^

The only restriction is that the display on the TV is dependent on the desktop displayed in the primary screen !
So if my windows come from the desk 1 and displayed on TV, if I switch to desk 2, on the TV it switch too so I don't see anymore my windows on the TV, to see it again, I must switch to the desk 1.
 
So here you have my xorg.conf :
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
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
	Identifier	"Device[0]"	# NVIDIA Corporation NV43 [GeForce 6600 GT]
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
	Option		"NoLogo"
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO , Composite etc 
   	Option          "TVStandard" "PAL" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

Section "Monitor"
	Identifier "Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
#    DisplaySize    270    203    # 1024x768 96dpi
#    DisplaySize    338    254    # 1280x960 96dpi
    DisplaySize    338    270    # 1280x1024 96dpi
#    DisplaySize    370    277    # 1400x1050 96dpi
#    DisplaySize    423    370    # 1600x1400 96dpi
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 	# NVIDIA Corporation NV43 [GeForce 6600 GT]
   	Monitor     "Monitor[0]"
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
               Modes "640x480" "640x480"
       	EndSubSection    
EndSection

Section "ServerFlags"
   Option "Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen 0 "Screen[0]" 
        Screen 1 "Screen[1]" RightOf "Screen[0]" 
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

Thanks for the help.

---

### Post by MTZeon on 2006-07-27
Hum... I guess you'll have always a cloned view of what you are seeing in the LCD to the TV... just as I said, I just wanted to have a cloned view of what I was seeing on the TFT to the TV :) Hum... you can try messing around this setting:

Option "TwinViewOrientation" "xxxx"

where you replace the xxxx for RightOf

Taken from: [http://download.nvidia.com/XFree86_40/1.0-2880/README.txt](http://download.nvidia.com/XFree86_40/1.0-2880/README.txt)
> 
Option "TwinViewOrientation" "string"
                Controls the relationship between the two display devices
                when using TwinView.  Takes one of the following values:
                "RightOf" "LeftOf" "Above" "Below" "Clone".  Please see
                APPENDIX I for details. Default: string is NULL.


Hope it helps anyone with troubles with TV-OUT... I like simple things :P

---

### Post by MilesTEG1 on 2006-07-27
> **MTZeon said:**
> Hum... I guess you'll have always a cloned view of what you are seeing in the LCD to the TV...
Nope, this is not a clone view. Actually I wrote this message, I see it on my LCD, but not on my TV. So It isn't a cloned view.

I try to put the twinview option, but It doesn't work : X dosn't start...

---

### Post by yakyu on 2006-07-31
hi,

i tried my best to set up the xorg.conf file but no success... any pointer is appreciated!

thanks in advance!!!

Video Card: Geforce 4 MX 440
Monitor: Samsung SyncMaster 753DF

xorg.conf
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

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor[1]"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	Option		"RenderAccel"	"true"
	BusID		"PCI:1:0:0"
	Screen 0
	Option		"ConnectedMonitor"	"CRT"
EndSection

Section "Device"
	Identifier	"Device[1]"
	Driver		"nvidia"
	BusID		"PCD:1:0:0"
	Screen 1
	Option		"TVOutFormat"	"COMPOSITE"
	Option		"TVStandard"	"NTSC-M"
	Option		"ConnectedMonitor"	"TV"
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
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

Section "Screen"
	Identifier	"Screen[1]"
	Device		"Device[1]"
	Monitor		"Monitor[1]"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen[0]"
	Screen 1	"Screen[1]" rightOf "Screen[0]"
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

Xorg.0.log
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux gattaca 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 31 21:04:09 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
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
(II) PCI: 00:00:0: chip 1106,0305 card 147b,a401 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8305 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0000 rev 40 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 0000,0000 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 16 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 16 class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 0000,0000 rev 40 class 06,00,00 hdr 00
(II) PCI: 00:09:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 13f6,0111 card 13f6,0111 rev 10 class 04,01,00 hdr 00
(II) PCI: 00:0d:0: chip 11d4,1805 card 11d4,1805 rev 00 class 07,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0171 card 0000,0000 rev a3 class 03,00,00 hdr 00
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
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 MX 440] rev 163, Mem @ 0xe4000000/24, 0xd0000000/27, 0xd8000000/19
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[1] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[1] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
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
	[4] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
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
	[4] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[20] 0	0	0xd80803b0 - 0xd80803bb (0xc) IS[B]
	[21] 0	0	0xd80803c0 - 0xd80803df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): ConnectedMonitor string: "CRT"
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 440 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.00.63.42
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 440 at PCI:1:0:0:
(--) NVIDIA(0):     Samsung S/M 753DF (CRT-0)
(--) NVIDIA(0): Samsung S/M 753DF (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (81, 81); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xd807ffff (0x80000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] 0	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[8] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[23] 0	0	0xd80803b0 - 0xd80803bb (0xc) IS[B]
	[24] 0	0	0xd80803c0 - 0xd80803df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
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

```

seems that screen 1, NVIDIA(1), never got setup... :(

cheers,

Al

---

### Post by tpnerdcore on 2006-07-31
hello and thanks for the howto. Seems to all be there, but im a little afraid to try it...i have XGL and Compiz installed. Does this work with XGL? If not, i have my XGL set to manually turn on and off, so does having XGL installed effect this? Thanks :)

-anthony

---

### Post by lefty.crupps on 2006-08-09
IT WORKS

After reading through the forums trying to get my Nvidia GeForce 5200 to clone my monitor with the TV-Out (TwinView?) i decided to cheat a little.  The new SimplyMEPIS 6 is based on Ubuntu and I have had a lot of luck with its Nvidia setups the past.  MEPIS has a great Control Center; unfortunately I do not think that it is GPL.  So, I installed MEPIS and used its XOrg.conf for Kubuntu.

I first used Automatix to install a recent Nvidia driver, and I had MEPIS do the same (via the MEPIS Control Center, which is now integrated into the overall KDE system settings).

This is my original XOrg.conf for Kubuntu (I removed only the intro comments so as to make it as easy to compare as possible):

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
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
    Identifier     "E151FP"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "E151FP"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
    EndSubSection
EndSection

```

And this is my new, Cloned TV-Out using an S-Video cable and NTCS in North America.  DO NOT USE this file exactly as this is, but it may give you great help:

```
Section "ServerLayout"
  Identifier "XFree86 Configured"
  Screen 0 "Screen0" 0 0
 #Screen 0 "ATIScreen" 0 0
  InputDevice "Keyboard0" "CoreKeyboard"
  InputDevice "PS/2 Mouse" "CorePointer"
 #InputDevice "USB Mouse" "CorePointer"
 #InputDevice "Touchpad" "CorePointer"
 #InputDevice "Stylus" "CorePointer"
 #InputDevice "Eraser" "CorePointer"
 #InputDevice "Cursor" "CorePointer"
 #InputDevice "Serial Mouse" "CorePointer"
EndSection

Section "ServerFlags"
  Option "AllowMouseOpenFail" "true"
EndSection

Section "Files"
# Xorg 7.0 font paths
    FontPath 	"/usr/share/X11/fonts/misc:unscaled"
    FontPath 	"/usr/share/X11/fonts/cyrillic"
    FontPath 	"/usr/share/X11/fonts/Type1"
    FontPath 	"/usr/share/X11/fonts/util"

# Legacy font paths
    FontPath 	"/usr/X11R6/lib/X11/fonts/misc:unscaled"
    FontPath 	"/usr/X11R6/lib/X11/fonts/cyrillic"
    FontPath 	"/usr/X11R6/lib/X11/fonts/Type1"
    FontPath 	"/usr/X11R6/lib/X11/fonts/util"

# Other font paths
    FontPath 	"/usr/share/fonts/truetype/ttf-lucida"
    FontPath 	"/usr/share/fonts/truetype/arphic"
    FontPath 	"/usr/share/fonts/truetype/freefont"
    FontPath 	"/usr/share/fonts/truetype/kochi"
    FontPath 	"/usr/share/fonts/truetype/latex-xft-fonts"
    FontPath 	"/usr/share/fonts/truetype/openoffice"
    FontPath 	"/usr/share/fonts/truetype/ttf-bitstream-vera"
    FontPath 	"/usr/share/fonts/type1/gsfonts"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

EndSection

Section "Module"
  Load "GLcore"
  Load "bitmap"
  Load "dbe"
  Load "ddc"
  Load "dri"
  Load "extmod"
  Load "freetype"
  Load "glx"
  Load "int10"
  Load "record"
  Load "type1"
  Load "v4l"
  Load "vbe"
  Load "synaptics"
EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "keyboard"
  Option "CoreKeyboard"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "us"
  Option "XKbOptions" ""
EndSection

Section "InputDevice"
  Identifier "Serial Mouse"
  Driver "mouse"
  Option  "Protocol" "Microsoft"
  Option  "Device" "/dev/ttyS0"
  Option  "Emulate3Buttons" "false"
  Option  "Emulate3Timeout" "70"
EndSection

Section "InputDevice"
 Identifier "Touchpad"
 Driver "synaptics"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "LeftEdge" "1700"
 Option "RightEdge" "5300"
 Option "TopEdge" "1700"
 Option "BottomEdge" "4200"
 Option "FingerLow" "25"
 Option "FingerHigh" "30"
 Option "MaxTapTime" "180"
 Option "MaxTapMove" "220"
 Option "VertScrollDelta" "100"
 Option "MinSpeed" "0.06"
 Option "MaxSpeed" "0.12"
 Option "AccelFactor" "0.0010"
 Option "SHMConfig" "on"
 Option "Repeater" "/dev/input/mice"
EndSection

Section "InputDevice"
  Identifier "PS/2 Mouse"
  Driver "mouse"
  Option "Protocol" "auto"
  Option "Device" "/dev/psaux"
  Option "Emulate3Buttons" "false"
  Option "Emulate3Timeout" "70"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection

Section "InputDevice"
  Identifier "USB Mouse"
  Driver "mouse"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "ExplorerPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection

Section "InputDevice"
  Identifier "Stylus"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "stylus"
  Option "Device" "/dev/input/wacom"
Endsection

# Settings for wacom eraser
Section "InputDevice"
  Identifier "Eraser"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "eraser"
  Option "Device" "/dev/input/wacom"
Endsection
# Settings for wacom cursor (mouse)
Section "InputDevice"
  Identifier "Cursor"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "cursor"
  Option "Device" "/dev/input/wacom"
Endsection

Section "Monitor"
  Identifier "Monitor0"
  VendorName "unknown"
  ModelName "unknown"
 #Option "DPMS" "true"
  HorizSync    30.0 - 75.0 # Warning: This may fry old Monitors
  VertRefresh  50.0 - 70.0 # Very conservative. May flicker.
  Modeline "640x480"     25.175 640  664  760  800   480  491  493  525 #60Hz
  Modeline "800x600"     40.12  800  848  968 1056   600  601  605  628 #60Hz
  Modeline "1024x768"    75    1024 1048 1184 1328   768  771  777  806 -hsync -vsync
  Modeline "1024x768"    85    1024 1056 1152 1360   768  784  787  823
  ModeLine "1152x864"    65    1152 1168 1384 1480   864  865  875  985 Interlace
  Modeline "1152x864"    92    1152 1208 1368 1474   864  865  875  895
  Modeline "1152x864"   110    1152 1240 1324 1552   864  864  876  908
  Modeline "1152x864"   135    1152 1464 1592 1776   864  864  876  908
  Modeline "1152x864"   137.65 1152 1184 1312 1536   864  866  885  902 -HSync -VSync
  Modeline "1280x768"    80.14 1280 1344 1480 1680   768  769  772  795
  ModeLine "1280x800"    80.58 1280 1344 1480 1680   800  801  804  827 -HSync -VSync
  Modeline "1280x1024"   80    1280 1296 1512 1568  1024 1025 1037 1165 Interlace
  Modeline "1280x1024"  110    1280 1328 1512 1712  1024 1025 1028 1054
  Modeline "1280x1024"  126.5  1280 1312 1472 1696  1024 1032 1040 1068 -HSync -VSync
  Modeline "1280x1024"  135    1280 1312 1456 1712  1024 1027 1030 1064
  Modeline "1280x1024"  135    1280 1312 1416 1664  1024 1027 1030 1064
  Modeline "1280x1024"  157.5  1280 1344 1504 1728  1024 1025 1028 1072 +HSync +VSync
  Modeline "1280x1024"  181.75 1280 1312 1440 1696  1024 1031 1046 1072 -HSync -VSync
  Modeline "1440x900"   106.47 1440 1520 1672 1904   900  901  904  932 +HSync +VSync
  Modeline "1400x1050"  129    1400 1464 1656 1960  1050 1051 1054 1100 +HSync +VSync
  Modeline "1600x1200"  162    1600 1664 1856 2160  1200 1201 1204 1250 +HSync +VSync
  Modeline "1600x1200"  189    1600 1664 1856 2160  1200 1201 1204 1250 -HSync -VSync
  Modeline "1600x1200"  202.5  1600 1664 1856 2160  1200 1201 1204 1250 +HSync +VSync
  Modeline "1600x1200"  220    1600 1616 1808 2080  1200 1204 1207 1244 +HSync +VSync
  Modeline "1680x1050"  147.14 1680 1784 1968 2256  1050 1051 1054 1087
  ModeLine "1800x1440"  230    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
  ModeLine "1800x1440"  250    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
  Modeline "1920x1200"  230    1920 1936 2096 2528  1200 1201 1204 1250 +HSync +VSync
EndSection

Section "Monitor"
  Identifier  "ATIMonitor"
  VendorName "unknown"
  ModelName "unknown"
 #Option "DPMS" "true"
  HorizSync    30.0 - 75.0 # Warning: This may fry old Monitors
  VertRefresh  50.0 - 70.0 # Very conservative. May flicker.
EndSection

Section "Device"
  Identifier  "Card0"
  Driver "nvidia"
  BoardName "unknown"

 #BusID  "PCI:1:0:0"
 #Option "sw_cursor" # needed for some ati cards
 #Option "hw_cursor"
 #Option "NoAccel"
 #Option "ShowCache"
 #Option "ShadowFB"
 #Option "UseFBDev"
 #Option "Rotate"
  Option "UseInternalAGPGART" "no"

# savage special options, use with care
 #Option "NoUseBios"
 #Option "BusType" "PCI"
  Option "DmaMode" "None"

# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "false"
  Option "IgnoreEdid" "true" # needs to be true for some nvidia cards
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 16
  
  SubSection "Display"
  Depth 8
  Modes "1024x768"
  EndSubSection
  SubSection "Display"
  Depth 15
  Modes "1024x768"
  EndSubSection
  SubSection "Display"
  Depth 16
  Modes "1024x768"
  EndSubSection
  SubSection "Display"
  Depth 24
  Modes "1024x768"
  EndSubSection
  SubSection "Display"
  Depth 32
  Modes "1024x768"
  EndSubSection
  
  # Only the official NVIDIA driver supports twinview
  # these setting are an example
  Option "TwinView" "true"
  Option "SecondMonitorVendorName" "unknown"
  Option "SecondMonitorModelName" "unknown"
  Option "SecondMonitorHorizSync" "30-75"
  Option "SecondMonitorVertRefresh" "50-70"
  Option "MetaModes" "1024x768, 1024x768"
  Option "TwinViewOrientation" "Clone"
  Option "ConnectedMonitor" "dfp,dfp"
EndSection

Section "Screen"
  Identifier "ATIScreen"
  Device "Card0"
  Monitor "ATIMonitor"
  DefaultColorDepth 24
  
  SubSection "Display"
  Depth 24
  Modes "1024x768"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

```

Is it right?  I don't know.  Does it work perfectly so far?  Yes it does!

Sorry for the extreme length of my post, but I was looking for someone's working, full XOrg.conf file.  Since I now have one and someone else may be looking, here it is!

Sweet, sweet music :-({|= to my eyes :shock: 

mod187, I am curious how you got Automatix to clone the screen for you?  I used Automatix to install my Nvidia driver and Adept to install some Nvidia tools (one of which, "nvidia-settings," should make this whole thing for for each of us, but the software is pretty useless), but none fixed this issue for me.  mod187?

Thank you to tselliot for the Guide that got each of us moving on this!

---

### Post by Vlatko on 2006-08-10
i followed the guide to the bone. when i rebooted ubuntu started normally, i logged in and everything was working properly. however my tv screen is blank, its completely grey, if i move the mouse to the top right corner i can see the "x" cursor moving on the tv. only i have no picture, everything is grey though i can move the mouse around.

here's my xorg file. i'd appreciated if someone helped me out as this probably the last thing i need to set-up on my new ubuntu 6.06 install.

i use a s-video cabel, nvidia 6600gt.

---

### Post by Vlatko on 2006-08-11
anyone have any idea? i really gotta solve this..

---

### Post by Vlatko on 2006-08-11
i don't know if this helps but i can see the nVidia logo perfectly fine, then when the log on screen comes the tv goes grey.

---

### Post by naszi on 2006-08-13
Hi,

so after a couple of days i got my nvidia-card running on my toshiba notebook. Unfortunately tv-out is still not operating, i hope somebody can help me with that. After boot and loging in i have only black screen on the tv. Here is my xorg.conf:

---

### Post by christooss on 2006-08-19
Hello

Its working. Thanks for the howto. But..

Its not working perfectly. I have a little problem There is a two cm(one inch) black area around picture. How could I fix that?

---

### Post by christooss on 2006-08-19
Vlatko try this.

Set auto login. and than remove monitor cable and boot with TV only. It fixed my setting. 

And did you try seting a tv to different input?

---

### Post by ManfredU on 2006-08-20
I just discovered that I need to use Option "UseDisplayDevice" "TV" instead of Option "ConnectedMonitor" "TV" to select TV-0 instead of CRT-1. It looks like the newer drivers ignore the ConnectedMonitor option and use UseDisplayDevice instead.

---

### Post by BitTorrentBuddha on 2006-08-21
Is there a way to make it an exact clone of what I see on the monitor?

---

### Post by Vlatko on 2006-08-22
> **christooss said:**
> Vlatko try this.

Set auto login. and than remove monitor cable and boot with TV only. It fixed my setting. 

And did you try seting a tv to different input?
thnx for the tip. well i tried what you said and ubuntu booted and i had tv out, only it was black and white. i also have that same 2cm black bar on the right side of the screen.

anyway tv out works but if i boot with both monitor and tv, the tv doesn't work anymore. this is really frustrating. 

[QUOTE=christooss]And did you try seting a tv to different input?[/QUOTE]
not sure what you mean with this?

---

### Post by mrashley on 2006-08-24
First off, I want to say thank you to tseliot for doing this particular HOWTO. It's kind of you to put in your time like this.

Now for anyone still watching this thread, I'm having trouble with my FX5200.

This is my Xorg.conf

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

Section "ServerLayout"
    Identifier     "Simple Layout"
    Screen         "Screen[0]"
    Screen         "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard" "CorePointer"
    InputDevice    "Configured Mouse" "CoreKeyboard"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
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
    Load           "bitmap"
    Load           "ddc"
#       Load    "dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
#       Load    "v4l"
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
    Identifier     "Monitor[0]"
    HorizSync       28.0 - 75.0
    VertRefresh     43.0 - 172.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier "Monitor[1]" #TV
    HorizSync 30-50
    VertRefresh 60
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    screen 0
#       Option  "TVStandard"    "PAL" #(or PAL, NTSC-J, etc.)
#       Option  "TVOutFormat"   "SVIDEO"
#       Option  "TVOverScan"    "0.5"
#       Option  "RenderAccel"   "1"
EndSection

Section "Device"
        Driver          "nvidia"
        Identifier      "Device[1]"
        Screen 1
        Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc
        Option          "TVStandard" "NTSC-M" #or NTSC etc
        Option          "ConnectedMonitor" "Monitor[1]"
#       BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci
EndSection

Section "Screen"

#       SubSection "Display"
#               Depth           16
#               Modes           "1024x768" "800x600" "640x480"
#       EndSubSection
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
        Device "Device[1]"
        Identifier "Screen[1]"
        Monitor "Monitor[1]"
        DefaultDepth 24
        SubSection "Display"
               Depth 24
               Modes "1024x768_60"
        EndSubSection
EndSection

```

The last 100 lines of my Xorg.0.log file.

```
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xdd000000 - 0xdd000fff (0x1000) MX[B]
        [7] -1  0       0xdd800000 - 0xdd87ffff (0x80000) MX[B]
        [8] -1  0       0xde000000 - 0xde0003ff (0x400) MX[B]
        [9] -1  0       0xde800000 - 0xde800fff (0x1000) MX[B]
        [10] -1 0       0xdf000000 - 0xdf000fff (0x1000) MX[B]
        [11] -1 0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [12] -1 0       0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
        [13] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [14] -1 0       0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
        [15] -1 0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [16] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [17] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [18] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [19] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x0000b800 - 0x0000b80f (0x10) IX[B]
        [23] -1 0       0x0000e000 - 0x0000e07f (0x80) IX[B]
        [24] -1 0       0x0000e100 - 0x0000e1ff (0x100) IX[B]
        [25] -1 0       0x0000d800 - 0x0000d807 (0x8) IX[B]
        [26] -1 0       0x00005100 - 0x0000511f (0x20) IX[B]
        [27] -1 0       0x00005500 - 0x0000550f (0x10) IX[B]
        [28] -1 0       0x00005000 - 0x0000500f (0x10) IX[B]
        [29] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [30] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
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
(**) Option "CorePointer"
(**) Generic Keyboard: Core Pointer
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
(WW) Generic Keyboard: does not have core pointer capabilities
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer" "False"
(**) Option "CoreKeyboard" "False"
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/bin/X(CreateConnectionBlock+0x4a) [0x806d7d2]
3: /usr/bin/X(main+0x5cf) [0x806e22b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d0aea2]
5: /usr/bin/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

```

When I

```
start -- -verbose 5 -logverbose 5
``` 

My TV flickers. My monitor briefly shows a themeless X windows backdrop complete with "X" mouse cursor.

My TV is left with half a screen of what looks like grey wool stitching. 

Any ideas? Anyone? Please?

---

### Post by christooss on 2006-08-25
Why do you have so much commented options? 

#       Load    "v4l" and others use my xorg.conf


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
	Option		"XkbLayout"	"si"
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

Section "Monitor"
	Identifier "Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync 31.5-80 
        	VertRefresh 56.3-75 
EndSection

 Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite"
   	Option          "TVStandard" "PAL-G"
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
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
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

Section "ServerLayout" 
   	Identifier  "Simple Layout" 
       	Screen 0 "Screen[0]" 
       	Screen 1 "Screen[1]" RightOf "Screen[0]" 
   	InputDevice "Configured Mouse" "CorePointer" 
   	InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by yakyu on 2006-08-26
hi all,

finally got the setup to work the way i wanted!!! i.e. dual monitor spanning from left (monitor) to right (tv) so that i can play some tv program on the right for my wife and still work on the left.

here's the xorg.conf for your interest:

note: i had to manual install 1.0-8774. the one came with ubuntu won't work.

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Aug  1 21:11:12 PDT 2006

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
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

#	FontPath	"/usr/share/X11/fonts/cyrillic"
	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
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
#	Load	"dri"
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

Section "Monitor"
    Identifier     "Monitor[0]"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device[1]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "RenderAccel" "true"
#    Option         "ConnectedMonitor" "CRT"
    Option         "UseDisplayDevice" "CRT"
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

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "COMPOSITE"
    Option         "TVStandard" "NTSC-M"
#    Option         "ConnectedMonitor" "TV"
    Option         "UseDisplayDevice" "TV"
    SubSection     "Display"
        Depth       24
        Modes      "640x480"
    EndSubSection
EndSection

```

enjoy!

al

---

### Post by Grog140 on 2006-08-31
Sorry if it was explained before, I simply do not have time to read 27 pages, lol!

This guide worked perfect for gnome without XGL/Compiz on.

With XGL/Compiz I can move my curser to the other screen but it is just a black screen with my curser as an X.

Could anyone point me in the right direction?

---

### Post by daller on 2006-09-02
I've created a wiki-page based on THIS thread:

[https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition)

---

### Post by daller on 2006-09-02
I have a little problem, though...

I have my TV connected to my laptop.

Everything works as it should, but the TV blanks when I close the lid!

...It would be nice to be able to watch TV without the light from the laptop.

Another problem:

Kicker (the taskbar) shows on the TV, whenever I browse around in Konqueror... Why??

---

### Post by luciferblack on 2006-09-02
Worked great for me!

I have a PCI-E GeForce 6600 running on Dapper 6.06 with Nvidia 8762 driver.

I ran a standard RCA type cable to my tv (since it's older and has no S-Video input) from the Nvidia adapter which is plugged into the S-Video output on my card and it works fine.  :)

I selected Composite for video type on the TV (since it has no S-Video input).

Thanks for the easy to follow guide!

---

### Post by naszi on 2006-09-02
Hi!

I followed the guide but could not get my tv-out to work.
I tried a lot of things, nothing worked. All i could figure out was that when i set BusID in the 2nd device-section, X crashes, it first tries 3 modes to set my display on the computer but result is always that upper half of screen is full white, lower half black. Thats all, nothing on the tv.

Any ideas what i should do?

i attach my config and the log.

---

### Post by daller on 2006-09-02
I have a black border, 5cm thick all around the picture on the TV...

How do I correct this?

---

### Post by ridermiller on 2006-09-04
Hey all.

I followed the initial post step by step. Rebooted my machine and it won't load the X Server.

I did do sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

So, I was wondering, since I can only use the terminal when Ubuntu boots up, how can I replace the .conf with the backup?

I'm a complete newbie, by the way. :(

Thanks for the help.

---

### Post by naszi on 2006-09-04
Hi,

It should work to copy back, if you change source to destination and vice versa, like:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

cp stands for "copy" then "from" and "to"
sudo is a tool to run commands even if You are not "root" user but do know the "root" password...but You already have experience with that...

Check Your log file Xorg.0.log in /var/log/, maybe it helps (Do this before You copy things back, and run X, because then it overwrites it)

Bye!

> **ridermiller said:**
> Hey all.

I followed the initial post step by step. Rebooted my machine and it won't load the X Server.

I did do sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

So, I was wondering, since I can only use the terminal when Ubuntu boots up, how can I replace the .conf with the backup?

I'm a complete newbie, by the way. :(

Thanks for the help.

---

### Post by ridermiller on 2006-09-04
> **naszi said:**
> Hi,

It should work to copy back, if you change source to destination and vice versa, like:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf



Thank you SO much! :mrgreen: 

I think I'll step back from s-video for a sec...heh

---

### Post by TSP on 2006-09-05
For those who have problems try coment out this line, something like this

```
# Option          "TVOutFormat" "Composite" 
```

Reboot and try. this work for me, i made many test (twinview, tv-out, etc) and no matters what i putt there (composite, SVIDEO) the tv wont work.

PS:Please add this option in the guide, it would be great for many users ;)

BTW thanks for this :D

---

### Post by tseliot on 2006-09-09
> **daller said:**
> I have a little problem, though...

I have my TV connected to my laptop.

Everything works as it should, but the TV blanks when I close the lid!

...It would be nice to be able to watch TV without the light from the laptop.

Another problem:

Kicker (the taskbar) shows on the TV, whenever I browse around in Konqueror... Why??

Try commenting out DPMS in your xorg.conf.

Save the file, log out, press CTRL+ALT+Backspace and log in

---

### Post by tseliot on 2006-09-09
> **TSP said:**
> For those who have problems try coment out this line, something like this

```
# Option          "TVOutFormat" "Composite" 
```

Reboot and try. this work for me, i made many test (twinview, tv-out, etc) and no matters what i putt there (composite, SVIDEO) the tv wont work.

PS:Please add this option in the guide, it would be great for many users ;)

BTW thanks for this :D

If you look carefully you will see that that option is already there

---

### Post by daller on 2006-09-09
> **tseliot said:**
> Try commenting out DPMS in your xorg.conf.

Save the file, log out, press CTRL+ALT+Backspace and log in

It didn't help! (Commenting out DPMS! and restarting X)

I also have a problem with a border all around the picture on the TV... About 3 cm wide.

Here's my xorg.conf: [www.dallerweb.dk/ubuntu/xorg.conf](www.dallerweb.dk/ubuntu/xorg.conf)

---

### Post by tseliot on 2006-09-09
> **daller said:**
> 
I also have a problem with a border all around the picture on the TV... About 3 cm wide.

Here's my xorg.conf: [www.dallerweb.dk/ubuntu/xorg.conf](www.dallerweb.dk/ubuntu/xorg.conf)

That might depend on the resolution and refresh rate

---

### Post by jazzgossen on 2006-09-14
I followed these instructions, and it works great!

One thing though: I can't set the resolution of the TV to anything but 1024x768, but I'd rather have 800x600. 

The sections that have to do with the TV are posted below. The only mode I've specified for the TV is  "800x600_60", but still it only uses 1024x768 at 60 Hz.

Any ideas why?

```
Section "Monitor"
    #Identifier     "TV"
    Identifier "Monitor[1]"
    HorizSync   30-50 #100?
    VertRefresh 60    #100?
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "S-VIDEO" #or S-VIDEO etc 
   	Option          "TVStandard" "PAL-B" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:2:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "800x600_60" 
       	EndSubSection    
EndSection

Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" LeftOf "Screen[0]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection
```

---

### Post by daller on 2006-09-14
> **tseliot said:**
> That might depend on the resolution and refresh rate

Which resolutions and refresh-rates should I try?

I've tried 1024x768_60
I've tried 1024x768_50
I've tried 800x600_60
I've tried 800x600_50

It's kind of old... about 10 years, I think!

The brand is "Telefunken" (a german brand) if that tells you anything...

---

### Post by gustavp on 2006-09-14
Hi, finally got my dualscreen to work with my tv, but now everything opens on my second screen (tv). But the taskbar is on my first screen.

How can I edit this?
xorg.conf:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 7600GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"

	Option "TwinView" "true"
	Option "TwinViewOrientation" "RightOf"
	Option "ConnectedMonitor" "crt,TV"
	Option "TVOutFormat" "S-VIDEO"
	Option "TVStandard" "PAL"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1280x1024, 800x600; 1027x768, 800x600; 1280x1024, NULL; 1024x768, NULL"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 7600GT]"
	Monitor		"SyncMaster"
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
```

And I think my normal screen is also on a refresh rate of 50;
screen resolution says: 2080x1024, refresh rate: 50.
Can I tune these seperatly?

Tnx!

---

### Post by daller on 2006-09-14
> **gustavp said:**
> 

Can I tune these seperatly?

Tnx!

I would give up on twinview, and setup 2 independant x-sessions.

See this:

[https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition)

---

### Post by ZlotZ on 2006-09-16
I'm using Kubuntu 6.06 Dapper, and the tutorial worked just the way it should for me =D

But there are 3 things annoying me, and I think it's possible to solve them... Here they are:

- Every time the mouse touched the right side of Screen 0, it would go to the Screen 1... This was very annoying ! I couldn't live with it. So I removed the  'RightOf "Screen[0]"' part. Now the Screen[1] displays just fine, but the cursor never goes out of Screen[0] when I touch the borders. This is just what I wanted ! Now I just need to know a way to pass the cursor to Screen[1]. Is there any command that does this trick ? I'm planning on setting the command to one of my multimedia keys on my keyboard, so it'll be fairly easy to switch between the screens.

- Speaking of Keyboard multimedia keys... I had configured them with xmodmap, and they work perfectly without the dual screen. With the dual screen, their commands are not executed. Not even "Print Screen", wich used to launch KSnapShot by default. Keys are recognized, but KDE doesn't run their commands. What could be the solution to this ?

- I start a movie on gmplayer on Screen[1], and I switch it to full screen. Fine, but when I go back to Screen[0] and give focus to another application, the kicker bar on Screen[1] and the mplayer control panel are displayed above the movie being played ! Any suggestions to solve this one ?


Thanks for the help !

---

### Post by daller on 2006-09-16
> **ZlotZ said:**
> I'm using Kubuntu 6.06 Dapper, and the tutorial worked just the way it should for me =D

But there are 3 things annoying me, and I think it's possible to solve them... Here they are:

- Every time the mouse touched the right side of Screen 0, it would go to the Screen 1... This was very annoying ! I couldn't live with it. So I removed the  'RightOf "Screen[0]"' part. Now the Screen[1] displays just fine, but the cursor never goes out of Screen[0] when I touch the borders. This is just what I wanted ! Now I just need to know a way to pass the cursor to Screen[1]. Is there any command that does this trick ? I'm planning on setting the command to one of my multimedia keys on my keyboard, so it'll be fairly easy to switch between the screens.

- Speaking of Keyboard multimedia keys... I had configured them with xmodmap, and they work perfectly without the dual screen. With the dual screen, their commands are not executed. Not even "Print Screen", wich used to launch KSnapShot by default. Keys are recognized, but KDE doesn't run their commands. What could be the solution to this ?

- I start a movie on gmplayer on Screen[1], and I switch it to full screen. Fine, but when I go back to Screen[0] and give focus to another application, the kicker bar on Screen[1] and the mplayer control panel are displayed above the movie being played ! Any suggestions to solve this one ?


Thanks for the help !

1. - Thanks, that's just what I'm going to do, also!

2. Use KeyTouch! - Very easy to use! [https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)

3. I also have that problem! (tried to kill kicker in that session - but didn't persist!)

---

### Post by tseliot on 2006-09-16
> **daller said:**
> Which resolutions and refresh-rates should I try?

I've tried 1024x768_60
I've tried 1024x768_50
I've tried 800x600_60
I've tried 800x600_50

It's kind of old... about 10 years, I think!

The brand is "Telefunken" (a german brand) if that tells you anything...

Try both 1024x768_50 and 800x600_50

---

### Post by daller on 2006-09-16
> **tseliot said:**
> Try both 1024x768_50 and 800x600_50

Try them both? - How?

1024x768_50;800x600_50 ???

I've already tried the 4 posted resolutions/refresh-rates, but haven't combined them, if that's what you mean!

---

### Post by tseliot on 2006-09-16
> **daller said:**
> Try them both? - How?

1024x768_50;800x600_50 ???

I've already tried the 4 posted resolutions/refresh-rates, but haven't combined them, if that's what you mean!

I mean: try one and then if that doesn't work try the other.

Use a 50hz refresh rate

---

### Post by naszi on 2006-09-17
Hi,

X crashes when i follow this guide, seems to have a problem with the tv-0 maximum pixel clock.

thanks,
András

---

### Post by jaccki on 2006-09-17
hi, really great work with this how-to. It works fine for me, but I have one annoying problem with keyboard. For example: when i press alt-f2(mouse focused on monitor) the "run program" window will appear on monitor, when i prees this one more time(after i run program or pressed esc) it will appear on tv, another hit and window appears back on monitor....and so on. Another example: when i use krusader(on crt) and press f7 to create a folder(then enter) the folder is created but focus goes to tv's desktop from krusader and i have to click back on krusader's window to continue working with it.

Those things don't happen when i use my original,unchanged xorg.conf. Please tell me if you have the same, because i've been looking for solution and didn't find any. And if you have any idea of how to fix this i would be very greatfull.

ps. sorry about my english ;)

---
Debian (etch)
KDE 3.54
NVIDIA FX5200 (SVIDEO)

---

### Post by kcleong on 2006-09-18
As Daller mentioned I'm also getting a small border in my Philips 25" CRT TV, the tv-out guide works perfect. I think the problem is the HorizSync rate (maybe also the VertRefresh?), these value(s) must be fine-tuned to get a full screen. 

My values from the guide:
```
    
    HorizSync 30-50
    VertRefresh 60

```

I would like to experiment with these rates, but I don't want to damage my tv ,is that possible? What are the optimal rates or which should I try, for a full screen on my CRT TV?

---

### Post by r8dhex on 2006-09-20
For those people having problems with TV-OUT using this method (2 screens; not twinview):

If you're using the newer nvidia drivers, the ConnectedMonitor option has changed.

```

Section "Device"
        #DVI Connection
        Identifier     "Device[0]"
        Driver         "nvidia"
        BusID          "PCI:1:0:0"
        **Option         "ConnectedMonitor" "DFP,TV"**
        **Option         "UseDisplayDevice" "DFP"**
        Screen        0
EndSection

Section "Device"
        #TV Connection
        Identifier     "Device[1]"
        Driver         "nvidia"
        BusID          "PCI:1:0:0"
        Option         "TVStandard" "NTSC-M"
        Option         "TVOutFormat" "SVIDEO"
        **Option         "ConnectedMonitor" "DFP,TV"**
        **Option         "UseDisplayDevice" "TV"**
        Screen        1
EndSection

```

The changes are marked in bold. For ConnectedMonitor, you have to list the devices that are plugged in, valid values are DFP,CRT,TV. Then UseDisplayDevice would specify which of the displays the device should use.

I managed to get this working on the latest nvidia drivers in the repository (1.0.8762).

---

### Post by christooss on 2006-09-21
What does dfp stands for?

---

### Post by r8dhex on 2006-09-21
DFP - Digital Flat Panel, corresponds to the DVI connection on your card

TV - Tele-Vision - this is where your TV plugs in

CRT - Cathode Ray Tube, if you use the traditional VGA connector

---

### Post by Rga1Rules on 2006-09-22
Hi, So I've been trying to get this to work for a couple days, X just crashes saying no screen found... i was wondering if anyone could take a look at my xorg.conf file and tell me whats wrong with it?

Thanks
     Grant

---

### Post by tseliot on 2006-09-22
> **Rga1Rules said:**
> Hi, So I've been trying to get this to work for a couple days, X just crashes saying no screen found... i was wondering if anyone could take a look at my xorg.conf file and tell me whats wrong with it?

Thanks
     Grant

```
Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option 		"ConnectedMonitor" "CRT"
	Option		"UseDisplayDevice" "CRT"
	screen 0
EndSection

Section "Device" 
	Driver "nv" 
	Identifier "Device[1]" 
	Screen 1  
	Option "TVOutFormat" "Composite" #or SVIDEO etc 	Option "TVStandard" "NTSC-M" #or NTSC etc 
	Option "ConnectedMonitor" "TV"
	Option "UseDisplayDevice" "TV" 
	BusID "PCI:2:0:0" 
EndSection
```

Device[1] should use the "nvidia" driver instead of "nv"

---

### Post by brent09 on 2006-09-25
Hi,
...I need help too.

I have an PCI-E EVGA 7600 GT KO with a Benq FP92G+ connected by DVI.  I also have a Toshiba TV connected to my stereo reciever (Kenwood VR-707) which is then also connected by composite cable to a s-video to composite video signal adapter plugged into the video card.  I am on an installation of 64bit Ubuntu (AMD Athlon 64 3200+), and I'm running Compiz.
Hopefully that doesn't throw too many unknowns into the mix.

I am getting no display to my TV whatsoever.  After following the steps in the first post and getting no results I tried searching through this thread a bit to try a few suggestions, but have not read the thread in entirety. Nothing seemed to change my situation.  As soon as the NVIDIA splash screen comes up, the TV goes blank.

my xorg.conf is attached.

Thanks in advance. ;)

---

### Post by brent09 on 2006-09-27
bump

No takers on this one???

---

### Post by Mguel on 2006-09-30
Maybe a bit off topic...

Is there a way of having the functionality to have the tv-out disabled and shift from monitor to tv-out (activating it) similar to how the Func+F3/5 work on notebooks. I installed kubuntu recently on a notebook, and I noticed that the switch/toggle output display is really what I would prefer since I use TV-OUT only to watch movies, and I don't work on my PC when watching movies :P

Cheers

---

### Post by pt123 on 2006-09-30
> **ManfredU said:**
> I just discovered that I need to use Option "UseDisplayDevice" "TV" instead of Option "ConnectedMonitor" "TV" to select TV-0 instead of CRT-1. It looks like the newer drivers ignore the ConnectedMonitor option and use UseDisplayDevice instead.

I got the tvout by using this guide
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

Also for those people wanting to remove the black border around the TV, open Nvidia Settings in Applications > System Tools

Then under devices choose TV-0 and under TV OverScan increase it till the borders are gone.

---

### Post by tseliot on 2006-10-01
> **brent09 said:**
> Hi,
...I need help too.

I have an PCI-E EVGA 7600 GT KO with a Benq FP92G+ connected by DVI.  I also have a Toshiba TV connected to my stereo reciever (Kenwood VR-707) which is then also connected by composite cable to a s-video to composite video signal adapter plugged into the video card.  I am on an installation of 64bit Ubuntu (AMD Athlon 64 3200+), and I'm running Compiz.
Hopefully that doesn't throw too many unknowns into the mix.

I am getting no display to my TV whatsoever.  After following the steps in the first post and getting no results I tried searching through this thread a bit to try a few suggestions, but have not read the thread in entirety. Nothing seemed to change my situation.  As soon as the NVIDIA splash screen comes up, the TV goes blank.

my xorg.conf is attached.

Thanks in advance. ;)
Try this guide:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by daller on 2006-10-01
What do you think about this guide:

[https://help.ubuntu.com/community/NvidiaTVOutNewbieEditionExperimental](https://help.ubuntu.com/community/NvidiaTVOutNewbieEditionExperimental)

???

It really cuts the setup-time in half!

Anything that should be changed?

---

### Post by hackbarth on 2006-10-11
Warning: this only worked for me after I changed 

Screen 1 "Screen[1]" RightOf "Screen[0]" 

for

Screen 1 "Screen[1]" rightof "Screen[0]"

---

### Post by raintheory on 2006-10-17
Okay I'm running XGL/Beryl on my Toshiba Satellite P15 S420 (nVIDIA GeFORCE FXgo 5100), I've followed this and when I restart I can see the nVIDIA splash screen on boot, and after login I just have a gray screen on the TV.  I can get the pointer over there but it's an X instead of an arrow, and I have no way to open anything on that screen...   Any ideas?

Here is my xorg.conf:

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
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   	Option          "TVStandard" "NTSC" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor" 
	Identifier	"Monitor[1]" #TV 
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

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

Section "ServerLayout" 
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Configured Mouse" "CorePointer" 
   InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks

---

### Post by raintheory on 2006-10-17
Just an update here...   I got twinview working using this guide that was posted ( [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut) ) and it works great.

However, the default resolution for my laptop is 1280x800, and setting the twinview up changes my laptops resolution to 1024x768 (in effect I lose a bunch of my desktop icons off of the right side of the screen).

](*,) 

Any ideas?

---

### Post by raintheory on 2006-10-18
Okay what I've done as a work-around is renamed the xorg.conf that makes TV-Out work (although changes my laptops res) to "xorg.conf-alternate", then created a small script that issues the following commands:

```

mv /etc/X11/xorg.conf-alternate /etc/X11/xorg.conf-current; 
mv /etc/X11/xorg.conf /etc/X11/xorg.conf-alternate; 
mv /etc/X11/xorg.conf-current /etc/X11/xorg.conf;

```

When I run this script it simply alternates between the two xorg.conf files. I have to restart x after running the script to enable tv-out (which makes the laptops res funny, as mentioned previously), and run it again to switch back...

Any idea what I can add to the script to have it automatically restart x rather than having to ctrl-alt-bksp?

---

### Post by tseliot on 2006-10-20
> **raintheory said:**
> Just an update here...   I got twinview working using this guide that was posted ( [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut) ) and it works great.

However, the default resolution for my laptop is 1280x800, and setting the twinview up changes my laptops resolution to 1024x768 (in effect I lose a bunch of my desktop icons off of the right side of the screen).

](*,) 

Any ideas?

My thread is not about Twinview. try this one instead:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by raintheory on 2006-10-20
> **tseliot said:**
> My thread is not about Twinview. try this one instead:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

Thanks!

---

### Post by Juzz on 2006-10-20
Does anyone know how to modify the way that the image is laid onto the TV?
I mean - on my TV the image is slimmer on top than on bottom, and in the middle is a noticable mark of the slimming.
I'd like for it to be as wide on the top as on the bottom.
Can I do anything to achieve that?

---

### Post by barcode_linux on 2006-10-22
Thank you for writing this how-to and thanks for all the contributions to it!
I am a Gentoo user who wanted a 2 display setup and found this one.
After reading the thread completely and testing for about 5 hours, I was able to get a sucessful setup with 2 DIFFERENT displays so I could do work(or play however you look at it) on one ( 1280x1024 ) display and the wife could watch a movie on the TV ( 1024x768 ) to the left me.
To ensure that I can make a contribution, I am enclosing my xorg.conf file.  It turns out that> Option      "ConnectedMonitor" "CRT,TV"
        Option      "UseDisplayDevice" "CRT" was a real show stopper.  Anyways, here is my xorg.conf:
> Section "Files"


    #FontPath   "/usr/share/fonts/local/"
    FontPath    "/usr/share/fonts/misc/"
    FontPath    "/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath    "/usr/share/fonts/75dpi/"
    FontPath    "/usr/share/fonts/100dpi/"
    FontPath    "/usr/share/fonts/corefonts"

EndSection

# **********************************************************************
# Module section -- this is an optional section which is used to specify
# which run-time loadable modules to load when the X server starts up.
# **********************************************************************

Section "Module"

    Load        "dbe"
    Load        "glx"
#    Load       "ddc"
    Load        "type1"
    Load        "freetype"
    Load        "extmod"
#    Load       "synaptics"

#    Load "dri"

EndSection


# **********************************************************************
# Server flags section.  This contains various server-wide Options.
# **********************************************************************

Section "ServerFlags"

     Option     "AllowMouseOpenFail" "true"
#     Option     "AIGLX" "true"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier  "Keyboard1"
    Driver      "kbd"

    Option      "AutoRepeat"    "500 5"
    Option      "XkbModel"      "pc104"
    Option      "XkbLayout"     "us"
    Option      "XkbRules"      "xorg"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier  "Mouse1"
    Driver      "mouse"

    Option      "Device"        "/dev/psaux"
    Option      "Protocol"      "ImPS/2"
    Option "ZAxisMapping" "4 5"

EndSection

Section "InputDevice"
    Identifier  "Mouse2"
    Driver      "mouse"
    Option      "Protocol"      "ImPS/2"
    Option      "Device"        "/dev/input/mice"
    Option      "ZAxisMapping" "4 5"
EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier  "Monitor[0]"
    #Option      "DPMS"

    VertRefresh 60
    HorizSync   28 - 110

    ModeLine "1280x800" 83.91 1280 1312 1624 1656 800 816 824 841
    ModeLine "1600x900" 173.86 1600 1672 2032 2176 900 902 914 940 +hsync +vsync
    Modeline "1280x720" 75 1280 1336 1472 1664 720 725 730 751
    Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
    Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
    ModeLine "1366x768" 88.03 1366 1424 1680 1816 768 770 782 808
    ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
    Modeline "720x576" 14.881 720 781 829 960 576 606 610 646 interlace +hsync +vsync
    ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
    ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
    ModeLine "960x600" 60 960 968 1048 1264 600 601 603 625 +HSync +VSync
    ModeLine "1088x612" 81.57 1088 1136 1376 1472 612 614 626 652 +hsync +vsync
    ModeLine "1792x1344" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    ModeLine "1792x1344" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
    ModeLine "1856x1392" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
    ModeLine "1856x1392" 288.0 1856 1984 2208 2560 1392 1393 1396 1500 -hsync +vsync
    ModeLine "1920x1440" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
    ModeLine "1920x1440" 297.0 1920 2064 2288 2640 1440 1441 1444 1500 -hsync +vsync
    ModeLine "1800x1440" 230 1800 1896 2088 2392 1440 1441 1444 1490 +HSync +VSync
    ModeLine "1800x1440" 250 1800 1896 2088 2392 1440 1441 1444 1490 +HSync +VSync
    Modeline "1280x768" 81.59 1280 1280 1384 1688 768 769 774 791

EndSection

Section "Monitor"
    Identifier "Monitor[1]" #TV
    HorizSync 30-50
    VertRefresh 60
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
        Identifier  "Device[0]"
        Driver      "nvidia" # do not remove vesa
        BusID       "PCI:0:6:0"
        Option      "ConnectedMonitor" "CRT,TV"
        Option      "UseDisplayDevice" "CRT"
        Screen 0
EndSection

Section "Device"
        Driver          "nvidia"
        Identifier      "Device[1]"
        Screen 1
       #Option          "TwinView" "true"
        Option          "TVOutFormat" "SVIDEO" #or Composite etc
        Option          "TVStandard" "NTSC-M" #or PAL etc
        Option         "ConnectedMonitor" "CRT,TV"
        Option         "UseDisplayDevice" "TV"
        BusID           "PCI:0:6:0" #adjust using 'lspci' or cat /proc/pci
EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

# The Identifier, Device and Monitor lines must be present

Section "Screen"
        Identifier  "Screen[0]"
        Device      "Device[0]"
        Monitor     "Monitor[0]"
 #   Option "AddARGBGLXVisuals" "true"

# The favoured Depth and/or Bpp may be specified here

    DefaultDepth 24

    SubSection "Display"
        Depth           8
        ViewPort        0 0
        Modes           "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           16
        ViewPort        0 0
        Modes           "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           24
        ViewPort        0 0
        Modes           "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection


EndSection

Section "Screen"
        Device "Device[1]"
        Identifier "Screen[1]"
        Monitor "Monitor[1]"
        DefaultDepth 24
        SubSection "Display"
               Depth 24
               Modes "1024x768_60"
        EndSubSection
EndSection

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Simple Layout"
       Screen 0 "Screen[0]"
       Screen 1 "Screen[1]" LeftOf "Screen[0]"
    InputDevice "Mouse1" "SendCoreEvents"
    InputDevice "Mouse2" "SendCoreEvents"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection  Hope this helps!

---

### Post by Juzz on 2006-10-22
> **Juzz said:**
> Does anyone know how to modify the way that the image is laid onto the TV?
I mean - on my TV the image is slimmer on top than on bottom, and in the middle is a noticable mark of the slimming.
I'd like for it to be as wide on the top as on the bottom.
Can I do anything to achieve that?
Is there really nothing to be done about that?

---

### Post by jazzgossen on 2006-10-23
That to me sounds like something you should correct for on the TV. Or perhaps it's a refresh rate problem? You could try to lower the refresh rate on the output signal to the TV.

---

### Post by daller on 2006-10-23
> **Juzz said:**
> Is there really nothing to be done about that?

I have a "similar" problem.

A black border round 3 cm's wide all around the screen (like the picture isn't stretched enough!)

I've changed everything changeable, and still that border!

---

### Post by Juzz on 2006-10-23
> **daller said:**
> I have a "similar" problem.

A black border round 3 cm's wide all around the screen (like the picture isn't stretched enough!)

I've changed everything changeable, and still that border!
You can try to set the Overscan value - for mine I had to go up to 12 to get the corners touch.
I was able to do that through the NVidia X Settings.

> But about my problem with the slimmer picture at the top - can't a top notch OS like linux do something to correct that.
I seem to remember that my old Amiga computer could correct that sort of thing...
I got a solution to that problem from another user at MythTVTalk forums:
```
Option "TVOverScan" "0.58"
```

---

### Post by LooGoo99 on 2006-10-31
Just tried it all and it works beautifully. Just a remark and a question!

The only thing that didn't work out-of-the-box was the rightclick-shortcut for Kubuntu to play it on the second screen (as explained on the second page of this thread). By making this change, it worked:

```
[Desktop Action PlayOnTV]
Exec=[COLOR="Red"]DISPLAY=0:1[/COLOR] mplayer [COLOR="Red"]-fs[/COLOR] %F
Name=Play this movie on TV
Icon=yast_tv
```

Only problem I have is that the KDE panel is displayed on the TV when watching the movie. I'd like to be able to watch a movie on the TV and continue working on my monitor. But with the first click I make on the monitor, the KDE panel pops up on the tv. Do you know of a way to prevent this?

#Addendum: I found an answer#
You can set the KDE Panel (Kicker) to Autohide. I had to do it this way (odd but works):
1. With a right click on Kicker on your monitor (NOT your tv), open up the Panel configuration.
2. Change it so that it will hide automatically. After saving, the Panel now autohides on BOTH screens.
3. Now repeat step 1, and remove the Autohide setting (return it to its default value). After saving, the Panel on the monitor stays visible and the Panel on the TV still autohides.

Now you can watch movies AND continue working at the same time, without the annoying Kicker.

---

### Post by marx2k on 2006-11-03
This application breaks my xorg.conf

Also I am using the latest beta drivers for this 6800 card and it is not detecting the TV until I actually USE that program to detect the TV... and if I tell the program to run it in a seperate X-window, it has to reatart X, but then, like I said.. it breaks the xorg.conf and I have to copy a backup

---

### Post by marx2k on 2006-11-03
AH! putting

Option "ConnectedMonitor" "CRT,TV"
Option "UseDisplayDevice" "TV"

in the TV device section and "CRT" in the CRT device section is what did it for me! THANK YOU!

Now I just need to figure out how to get it to NOT be black and white

---

### Post by g_rael on 2006-11-07
[B]
lspci 
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Hello all, thought I'd post my working config after much fiddling...
Can't be sure which things did and didn't work, but some basics:
Screen (n) links through to the device and screen sections, note the [Section [ServerLayout"], which I wrote as per the nvidia spec, (involved removing some "0"'s from our thread author's starting point.
Don't put multiple refresh rates on the TV vert refresh, or at least consider the TV's in your country.
Don't forget to use your correct PAL-? or NTSC? system.
Identifiers follow the above hierachy, but their names are relatively arbitary... so long as you link them through the hierachy:
   
      serverlayout
       |             |
  screen             screen
|       |           |       | 
monitor device    monitor  device

[Section "Monitor"] and [Section "Device"] seem to be refered to by the 
[Section "Screen"] portion.


It's easier fiddling once it's working !:KS 
[/B]

```

Section "ServerLayout"
    Identifier     "Simple Layout"
    Screen      0  "CRT"
    Screen      1  "TV" RightOf "CRT"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

**section cut for clarity and to save thread space **

Section "Monitor"
    Identifier     "CRT"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "TV"
    HorizSync       30 - 50
    VertRefresh     60
EndSection

Section "Device"
    Identifier     "DevCRT"
    Driver         "nvidia"
    Option "ConnectedMonitor" "CRT, TV"
    Option "UseDisplayDevice" "CRT"
    Screen 0
    BusID           "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "DevTV"
    Driver         "nvidia"
    Screen 1
    Option "ConnectedMonitor" "CRT, TV"
    Option "UseDisplayDevice" "TV"
    BusID           "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "CRT"
    Device         "DevCRT"
    Monitor        "CRT"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "TV"
    Device         "DevTV"
    Monitor        "TV"
    DefaultDepth    24
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-B"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```
8)

---

### Post by frogotronic on 2006-11-12
> Now you have to add the TV-OUT as a device below your Device[0] and add all the options listed below. Make it look EXACTLY like this example:

```
Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-G" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection
```

You might want to change 2 things in the example above:
1)You can change "Composite" to  “SVIDEO” (according to the type of video cable you use)
2)You can change your TVstandard from  “PAL-G” to “NTSC-M” or "NTSC-J" according to your tv.



I have a question about the BusID on my system.  Here is my output from lspci:

```
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
0000:02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
0000:02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
0000:02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
0000:07:00.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)
```

Is my BusID for my video card "PCI:1:0:0"?

Thanks,
CH

---

### Post by frogotronic on 2006-11-12
> **cement_head said:**
> I have a question about the BusID on my system.  Here is my output from lspci:

```
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
0000:02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
0000:02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
0000:02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
0000:07:00.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)
```

Is my BusID for my video card "PCI:1:0:0"?

Thanks,
CH


Okay, crashed my XServer.

Basic Question: Can I set up Twinview AND TV-out at the same time?

---

### Post by wilberfan on 2006-11-25
Figuring this out myself is going to be waaaaay beyond this n00b's abilities...but I'm curious:

The only display I get on my TV is the bootsplash text and Kubuntu usplash screens...   So, clearly, there is a signal getting from the video card to the TV--at least some of the time.

The screen is completely black once Ubuntu starts up...

:confused: 

That probably means adjusting something in my xorg.conf file??

---

### Post by frogotronic on 2006-11-26
> **wilberfan said:**
> Figuring this out myself is going to be waaaaay beyond this n00b's abilities...but I'm curious:

The only display I get on my TV is the bootsplash text and Kubuntu usplash screens...   So, clearly, there is a signal getting from the video card to the TV--at least some of the time.

The screen is completely black once Ubuntu starts up...

:confused: 

That probably means adjusting something in my xorg.conf file??

At a quick glance, I'd say that you don't have enough choices for your TV display & only being at 24bit depth is pretty high (deep).  Also, why do you specify the screen size in your monitor1 section.  I haven't gone through the whole file, but looks as if you just need to check that all the identifiers (strings/names) are consistent from section to section.

-CH

---

### Post by pairajacks on 2006-11-26
DDC on an old TV? Is that the problem?

After following the code provided, I'm still not getting anything on my TV (just my CRT works). My log file does not have any errors or warnings (except for a 4L video card driver. The motherbd has a 6150 GPU, so I *think* I can disregard this for now) 

Does anything special have to be done for this to work on an plain old TV using a composite RCA connection? (I did use the Option "TVOutFormat" "COMPOSITE"). The reason I ask is, because it's an old TV (1980's), I wouldn't expect it to have any smarts. 

I'm seeing the file (xorg.conf) change after running (startx). I get comments that say Horiz and Vert syncs will be set by DDC. It moves things around and comments some code. I tried setting Option "DDC" "false"  but no effect.](*,) 

(I'm on Fedora Core 5)

---

### Post by gobbluth on 2006-11-27
I apologize in advance if this problem has already been addressed, but I did search the thread quite a bit before posting. Everything worked except one seemingly trivial thing: When I log in, a desktop with a blue background and standard panel on the bottom (using KDE) is displayed on the TV, and my regular desktop is displayed on my laptop. The problem is there is no way for me to get the mouse to reach the TV, it won't scroll off the laptop monitor. I'm on a Dell Inspiron 9300 with a 6800 Go I believe. Here is my xorg.conf:

[xorg.conf.txt]("http://www.angelfire.com/d20/room/xorg.conf.txt")

Thanks to anyone who can help!

---

### Post by jradke on 2006-11-28
All my hours of futile attempts only yields me a black X screen. I can see my mouse cursor if I move it over to the other screen but that's it. 

](*,) I have tried 8-9 Howto's and methods now and this is the closest I get! I've tried many of the variations that others have described and this is where I've left it:

:~$ dmesg | grep -i nvidia
[17179584.116000] nvidia: module license 'NVIDIA' taints kernel.
[17179584.368000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9629  Wed Nov  1 19:30:07 PST 2006
:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

No related errors in Xorg.0.log
cat /var/log/Xorg.0.log | grep -i nvidia > Xorg.0.log

Please, please, help!

---

### Post by JELO on 2006-11-29
Hi, I followed the tutorial and it's working.  Previously I had been using the option in nvidia settings and it was totally screwing with things.
I'm running edgy with a 6600.  I'm getting the desktop on the TV, everything is peachy except for one thing.  I the tool bar doens't work, so I can't open anything.  I can move the mouse around fine and what not.
I do have Beryl installed and running, could this be a problem?
Thanks

---

### Post by jradke on 2006-11-29
I have beryl installed but disabled while trying to get this tv-out thing work'n. I also have a 6600, are you doing this with the svideo port to the tv? or the dvi/vga interface?

Did you have to do anything special to get a desktop setup on the TV screen?

I only get a black screen with my mouse cursor as an X. Did you ever encounter this problem? Can you post your xorg.conf for me and/or look mine over on the previous post?

Cheers,

-JGR

---

### Post by JELO on 2006-11-29
I've been messing around with the config file to no avail.
Here it is

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:48:08 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"

EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Proview MA982K"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:4:0:0"
    Screen          0
#added these
Option "ConnectedMonitor" "Monitor0"
Option "NoLogo" "true
Option          "TripleBuffer" "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:4:0:0"
    Screen          1
   	Option          "TVOutFormat" "SVIDEO" 
   	Option          "TVStandard" "NTSC" 
   	Option          "ConnectedMonitor" "Monitor1" 
EndSection

Section "Screen"
# Enable 32-bit ARGB GLX Visuals
	Option "AddARGBGLXVisuals" "True"
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
	Option "DisableGLXRootClipping" "True"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60"
    EndSubSection
EndSection

I did find out why my terminal and what not quit working, using the nvidia-settings was completly generating a new config file, put the beryl back in and everything works.  Except now i'm not getting a toolbar on the TV and of course the mouse clicking doesn't seem to work, cursor moves.  I tried editing a few things again to match the tutorial.  I imagine it might be something with my modules or server layout.

---

### Post by mlwalla on 2006-11-30
ok, I'm stumped.  I followed the directions in the guide and it seems like everything *should* work but I still just get a blank tv screen.
Here's my xorg.conf```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
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
   Identifier  "Simple Layout" 
       Screen 0 "Screen[0]" 
       Screen 1 "Screen[1]" RightOf "Screen[0]" 
   InputDevice "Configured Mouse"  
   InputDevice "Generic Keyboard"  
   InputDevice "Synaptics Touchpad"	
EndSection

Section "Files"

	#FontPath	"/usr/share/X11/fonts/cyrillic"
	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
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
	#Load	"glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "glx"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier "Monitor[0]" #LCD
	Option		"DPMS"
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
   	Identifier      "Device[1]" 
   	Driver          "nvidia"
	Screen 1 
   	Option          "TVOutFormat" "SVIDEO" #or COMPOSITE etc 
   	Option          "TVStandard" "NTSC-M" #or PAL-G etc
   	Option          "ConnectedMonitor" "TV" 
	BusID		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200"
    EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "800x600_60" 
       	EndSubSection    
EndSection


```

and here is my Xorg.0.log
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Guy 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 30 00:56:34 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Synaptics Touchpad"
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
(II) PCI: 00:00:0: chip 8086,1130 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,244c card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244a card 8086,4541 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 8086,4541 rev 02 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0112 card 1028,00a4 rev b2 class 03,00,00 hdr 00
(II) PCI: 02:03:0: chip 125d,1998 card 1028,00a4 rev 10 class 04,01,00 hdr 00
(II) PCI: 02:06:0: chip 1668,0100 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 02:0f:0: chip 104c,ac42 card d000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 02:0f:1: chip 104c,ac42 card d800,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 02:0f:2: chip 104c,8027 card 1028,00a4 rev 00 class 0c,00,10 hdr 80
(II) PCI: 08:04:0: chip 8086,1229 card 1668,1100 rev 08 class 02,00,00 hdr 00
(II) PCI: 08:08:0: chip 11c1,0448 card 1668,2400 rev 01 class 07,80,00 hdr 00
(II) PCI: 0d:00:0: chip 168c,001a card 1186,3b08 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
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
	[0] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,16), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[4] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[5] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[8] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[9] -1	0	0x0000f400 - 0x0000f4ff (0x100) IX[B]
	[10] -1	0	0x0000f800 - 0x0000f8ff (0x100) IX[B]
	[11] -1	0	0x0000fc00 - 0x0000fcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xfbffffff (0xa000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x23ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 8: bridge is at (2:6:0), (2,8,8), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[2] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (2:15:0), (2,9,12), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 9 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
(II) Bus 9 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
(II) Bus 9 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x21ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 13: bridge is at (2:15:1), (2,13,16), BCTRL: 0x0500 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) Bus 13 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0x22000000 - 0x23ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV11 [GeForce2 Go] rev 178, Mem @ 0xfc000000/24, 0xe0000000/27
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
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xebffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf4000000 - 0xf400ffff (0x10000) MX[B]
	[1] -1	0	0xf8ffec00 - 0xf8ffecff (0x100) MX[B]
	[2] -1	0	0xf8e00000 - 0xf8efffff (0x100000) MX[B]
	[3] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B]
	[4] -1	0	0xf6ff8000 - 0xf6ffbfff (0x4000) MX[B]
	[5] -1	0	0xf6ffd800 - 0xf6ffdfff (0x800) MX[B]
	[6] -1	0	0xf6ffe000 - 0xf6ffffff (0x2000) MX[B]
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[11] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B]
	[12] -1	0	0x0000ecc0 - 0x0000ecff (0x40) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000bce0 - 0x0000bcff (0x20) IX[B]
	[15] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf4000000 - 0xf400ffff (0x10000) MX[B]
	[1] -1	0	0xf8ffec00 - 0xf8ffecff (0x100) MX[B]
	[2] -1	0	0xf8e00000 - 0xf8efffff (0x100000) MX[B]
	[3] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B]
	[4] -1	0	0xf6ff8000 - 0xf6ffbfff (0x4000) MX[B]
	[5] -1	0	0xf6ffd800 - 0xf6ffdfff (0x800) MX[B]
	[6] -1	0	0xf6ffe000 - 0xf6ffffff (0x2000) MX[B]
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[11] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B]
	[12] -1	0	0x0000ecc0 - 0x0000ecff (0x40) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000bce0 - 0x0000bcff (0x20) IX[B]
	[15] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
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
	[4] -1	0	0xf4000000 - 0xf400ffff (0x10000) MX[B]
	[5] -1	0	0xf8ffec00 - 0xf8ffecff (0x100) MX[B]
	[6] -1	0	0xf8e00000 - 0xf8efffff (0x100000) MX[B]
	[7] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B]
	[8] -1	0	0xf6ff8000 - 0xf6ffbfff (0x4000) MX[B]
	[9] -1	0	0xf6ffd800 - 0xf6ffdfff (0x800) MX[B]
	[10] -1	0	0xf6ffe000 - 0xf6ffffff (0x2000) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B]
	[18] -1	0	0x0000ecc0 - 0x0000ecff (0x40) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[20] -1	0	0x0000bce0 - 0x0000bcff (0x20) IX[B]
	[21] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
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
	[4] -1	0	0xf4000000 - 0xf400ffff (0x10000) MX[B]
	[5] -1	0	0xf8ffec00 - 0xf8ffecff (0x100) MX[B]
	[6] -1	0	0xf8e00000 - 0xf8efffff (0x100000) MX[B]
	[7] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B]
	[8] -1	0	0xf6ff8000 - 0xf6ffbfff (0x4000) MX[B]
	[9] -1	0	0xf6ffd800 - 0xf6ffdfff (0x800) MX[B]
	[10] -1	0	0xf6ffe000 - 0xf6ffffff (0x2000) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B]
	[18] -1	0	0x0000ecc0 - 0x0000ecff (0x40) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[20] -1	0	0x0000bce0 - 0x0000bcff (0x20) IX[B]
	[21] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf4000000 - 0xf400ffff (0x10000) MX[B]
	[5] -1	0	0xf8ffec00 - 0xf8ffecff (0x100) MX[B]
	[6] -1	0	0xf8e00000 - 0xf8efffff (0x100000) MX[B]
	[7] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B]
	[8] -1	0	0xf6ff8000 - 0xf6ffbfff (0x4000) MX[B]
	[9] -1	0	0xf6ffd800 - 0xf6ffdfff (0x800) MX[B]
	[10] -1	0	0xf6ffe000 - 0xf6ffffff (0x2000) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B]
	[21] -1	0	0x0000ecc0 - 0x0000ecff (0x40) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000bce0 - 0x0000bcff (0x20) IX[B]
	[24] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[25] 0	0	0xfd0003b0 - 0xfd0003bb (0xc) IS[B]
	[26] 0	0	0xfd0003c0 - 0xfd0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce2 Go at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.01.44.b4
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 Go at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA Default Flat Panel (DFP-0)
(--) NVIDIA(0): NVIDIA Default Flat Panel (DFP-0): 162.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): NVIDIA Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (126, 126); computed from "UseEdidDpi" X config option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "NTSC-M"
(**) NVIDIA(1): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing SVIDEO output
(**) NVIDIA(1): TV Standard string: "NTSC-M"
(II) NVIDIA(1): NVIDIA GPU GeForce2 Go at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 32768 kBytes
(--) NVIDIA(1): VideoBIOS: 03.11.01.44.b4
(II) NVIDIA(1): Detected AGP rate: 4X
(--) NVIDIA(1): Interlaced video modes are not supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce2 Go at PCI:1:0:0:
(--) NVIDIA(1):     NVIDIA Default Flat Panel (DFP-0)
(--) NVIDIA(1): NVIDIA Default Flat Panel (DFP-0): 162.0 MHz maximum pixel
(--) NVIDIA(1):     clock
(--) NVIDIA(1): NVIDIA Default Flat Panel (DFP-0): Internal Dual Link LVDS
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[1] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf4000000 - 0xf400ffff (0x10000) MX[B]
	[7] -1	0	0xf8ffec00 - 0xf8ffecff (0x100) MX[B]
	[8] -1	0	0xf8e00000 - 0xf8efffff (0x100000) MX[B]
	[9] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B]
	[10] -1	0	0xf6ff8000 - 0xf6ffbfff (0x4000) MX[B]
	[11] -1	0	0xf6ffd800 - 0xf6ffdfff (0x800) MX[B]
	[12] -1	0	0xf6ffe000 - 0xf6ffffff (0x2000) MX[B]
	[13] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000ecb8 - 0x0000ecbf (0x8) IX[B]
	[20] -1	0	0x0000ecc0 - 0x0000ecff (0x40) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[22] -1	0	0x0000bce0 - 0x0000bcff (0x20) IX[B]
	[23] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
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
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?

``` 
The only error I see is ```
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
```
Is this a hardware problem? Anything obviously wrong in xorg.conf?  

I tell ya, after a grueling ordeal just to get the proprietary nvidia driver working (after trying every xorg configuration in the known universe I upgraded my BIOS), it is really frustrating to now have trouble configuring the tv-out ](*,) 
All input appreciated, and thanks much.

---

### Post by JELO on 2006-11-30
You might could try NTSC by itself, when I was trying it with the -M on the end mine was coming up blank.

---

### Post by gobbluth on 2006-12-01
Just wanted to check back in to say I figured out the issue I was having. I had not put the "RightOf Screen[0]" line in my xorg.conf. Sorry for the superfluous post.

---

### Post by mlwalla on 2006-12-02
woohoo! I too figured out the problem I was having...  For starters my svideo-to-composite cable was miscolored (the yellow s-video jack went to the red audio composite jack) so that fixed the problem I posted about.  Still I only finally got tv-out to work by changing my tv resolution in xconfig to 640x480 and taking out the ```
optio "ConnectedMonitor" "TV"
``` when I enter 800x600 all I get is a white screen...

All is good, the only small problem left is that on my tv there is a small black border (,aybe 3/4 inch on the sides and 1/2 inch top and bottom), and the very left edge of the desktop seems to fall under the border (covers all but about one pixel of my cursor).  Any ideas on what causes this or how to fix it?  Definitely live-withable, but hey if I can tweak just a little more to solve that'd be sweet!  Thanks all.

---

### Post by hmm on 2006-12-05
Hi! I just want to thank you! I got my tv-out working without any problems.

I use this script to open my movies directly on TV (so i have to right click movie and choose my script from "scripts"-list.)

```

#!/bin/sh
# opens movies to secondary monitor
video_file=""$PWD""/$1""
if [ -d "$1" ]
then 
	exit 0
else
	gmplayer -display :0.1 -fs "$video_file"&
fi

```

There can be a better solution but i have used this one :)

---

### Post by PartisanEntity on 2006-12-05
Probably a silly question, but are these instructions also applicable to laptops?

---

### Post by mlwalla on 2006-12-05
They should work just the same for laptops, at least they did for me.  Just remember that your LCD might have different values for resolution and refresh rate than a CRT monitor (in fact, I left the refresh rate lines out of my xorg.conf for Monitor[0] with no problems, but ymmv)

---

### Post by Alain21 on 2006-12-10
Hi, I did everything so far ... it seem to work except that on my TV I dont have a desktop .... it is just the plain X gray bkg with the big X 

should i need 2 instance of gdm ?

---

### Post by rotten777 on 2006-12-17
I've followed the guide only to get a blank TV screen.

xorg config
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:48:08 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen[0]"
    Screen 1 "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor[0]"
    VendorName     "Samsung"
    ModelName      "SyncMaster 213T"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor[1]" #TV!
    HorizSync       30-50
    VertRefresh     60
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GT"
    screen 0
    #Option          "ConnectedMonitor" "DFP" 
EndSection

Section "Device" 
    Driver          "nvidia" 
    Identifier      "Device[1]" 
    screen 1 
    Option          "TVOutFormat" "COMPOSITE" #or SVIDEO etc 
    Option          "TVStandard" "NTSC" #or NTSC etc 
    #Option          "ConnectedMonitor" "TV" 
    #BusID           "PCI:5:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "metamodes" "1600x1200 +0+0; 1280x1024 +0+0; 1152x864 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 640x480 +0+0; 1600x1200_60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024"
    EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "640x480_60" 
       	EndSubSection    
EndSection

```



xorg log file
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux linux 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 17 20:48:45 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/share/fonts/X11/TTF/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/OTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/CID/" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(**) RgbPath set to "/usr/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "0"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1565,3402 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1565,3402 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1565,3402 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1565,3402 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1565,3402 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0053 card 1565,3402 rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1565,5401 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1565,5401 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1565,2501 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:09:0: chip 1102,0004 card 1102,2002 rev 04 class 04,01,00 hdr 80
(II) PCI: 01:09:1: chip 1102,7003 card 1102,0040 rev 04 class 09,80,00 hdr 80
(II) PCI: 01:09:2: chip 1102,4001 card 1102,0010 rev 04 class 0c,00,10 hdr 80
(II) PCI: 01:0a:0: chip 1106,3044 card 1565,4200 rev 80 class 0c,00,10 hdr 00
(II) PCI: 05:00:0: chip 10de,0092 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfe700000 - 0xfe7fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe600000 - 0xfe6fffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe5fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfe400000 - 0xfe4fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfe300000 - 0xfe3fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xcfffffff (0x20000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(5:0:0) nVidia Corporation GeForce 7800 GT rev 161, Mem @ 0xfc000000/24, 0xb0000000/28, 0xfd000000/24, I/O @ 0x9f00/7
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
(II) Active PCI resource ranges:
	[0] -1	0	0xfe9fe000 - 0xfe9fe7ff (0x800) MX[B]
	[1] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[2] -1	0	0xfe9ff000 - 0xfe9ff7ff (0x800) MX[B]
	[3] -1	0	0xfebfa000 - 0xfebfafff (0x1000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfe0ff (0x100) MX[B]
	[7] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[12] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[13] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[15] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[16] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[17] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[18] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[19] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[20] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[27] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[29] -1	0	0x00009f00 - 0x00009f7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe9fe000 - 0xfe9fe7ff (0x800) MX[B]
	[1] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[2] -1	0	0xfe9ff000 - 0xfe9ff7ff (0x800) MX[B]
	[3] -1	0	0xfebfa000 - 0xfebfafff (0x1000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfe0ff (0x100) MX[B]
	[7] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[12] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[13] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[15] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[16] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[17] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[18] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[19] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[20] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[27] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[29] -1	0	0x00009f00 - 0x00009f7f (0x80) IX[B](B)
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
	[4] -1	0	0xfe9fe000 - 0xfe9fe7ff (0x800) MX[B]
	[5] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[6] -1	0	0xfe9ff000 - 0xfe9ff7ff (0x800) MX[B]
	[7] -1	0	0xfebfa000 - 0xfebfafff (0x1000) MX[B]
	[8] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfe0ff (0x100) MX[B]
	[11] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[18] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[19] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[21] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[32] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[33] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[35] -1	0	0x00009f00 - 0x00009f7f (0x80) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9629
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9629
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9629  Wed Nov  1 19:31:54 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Assigning device section with no busID to primary device
(--) Assigning device section with no busID to primary device
(WW) NVIDIA: More than one matching Device section found: Device[1]
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9fe000 - 0xfe9fe7ff (0x800) MX[B]
	[5] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[6] -1	0	0xfe9ff000 - 0xfe9ff7ff (0x800) MX[B]
	[7] -1	0	0xfebfa000 - 0xfebfafff (0x1000) MX[B]
	[8] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfe0ff (0x100) MX[B]
	[11] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[18] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[19] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[21] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[32] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[33] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[35] -1	0	0x00009f00 - 0x00009f7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9fe000 - 0xfe9fe7ff (0x800) MX[B]
	[5] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[6] -1	0	0xfe9ff000 - 0xfe9ff7ff (0x800) MX[B]
	[7] -1	0	0xfebfa000 - 0xfebfafff (0x1000) MX[B]
	[8] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfe0ff (0x100) MX[B]
	[11] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[21] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[22] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[24] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[25] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[26] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[27] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[28] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[29] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[35] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[36] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[37] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[38] -1	0	0x00009f00 - 0x00009f7f (0x80) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "MetaModes" "1600x1200 +0+0; 1280x1024 +0+0; 1152x864 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 640x480 +0+0; 1600x1200_60 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7800 GT at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.70.02.13.07
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7800 GT at PCI:5:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200+0+0"
(II) NVIDIA(0):     "1280x1024+0+0"
(II) NVIDIA(0):     "1152x864+0+0"
(II) NVIDIA(0):     "1024x768+0+0"
(II) NVIDIA(0):     "832x624+0+0"
(II) NVIDIA(0):     "800x600+0+0"
(II) NVIDIA(0):     "640x480+0+0"
(II) NVIDIA(0):     "1600x1200_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (94, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[1] 0	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
	[2] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfe9fe000 - 0xfe9fe7ff (0x800) MX[B]
	[8] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[9] -1	0	0xfe9ff000 - 0xfe9ff7ff (0x800) MX[B]
	[10] -1	0	0xfebfa000 - 0xfebfafff (0x1000) MX[B]
	[11] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[12] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[13] -1	0	0xfebfe000 - 0xfebfe0ff (0x100) MX[B]
	[14] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] 0	0	0x00009f00 - 0x00009f7f (0x80) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000dd00 - 0x0000dd7f (0x80) IX[B]
	[25] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[26] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[28] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[29] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[30] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[31] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[32] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[33] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[34] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[35] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[36] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[37] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[38] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[39] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[40] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[41] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[42] -1	0	0x00009f00 - 0x00009f7f (0x80) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200+0+0"
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc105)" };
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

```

---

### Post by jboehm on 2006-12-18
> **tseliot said:**
> Remove XGL

For people with Grey Problem on TV-OUT using XGL.  Try this

Option "TVStandard" "HD480i"
# Option "TVStandard" "NTSC-M"

My Grey problems went away.  There is a pun in there some where

Jon

---

### Post by 1ns4nity on 2006-12-28
Hi. I´ve been trying for the past 2 days to get my GeFOrce FX 5200´s tv out to work on Xubuntu. Ive followed the guide and many other suggestions made by other users in this thread but I am still not able to get anything showing on my tv out.

Basically all my TV does it blink black and blue (without anything plugged in its blue).

Please help me if you can to diagnose what is wrong? Thanks soo so so much in advance...this is driving me crazy :(

This is my log file
> 

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux ubuntumyth 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 28 21:02:16 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3116 card 1106,3116 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 109e,036e card 107d,6606 rev 11 class 04,00,00 hdr 80
(II) PCI: 00:0b:1: chip 109e,0878 card 107d,6606 rev 11 class 04,80,00 hdr 80
(II) PCI: 00:11:0: chip 1106,3147 card 1106,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:2: chip 1106,3038 card 0925,1234 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:3: chip 1106,3038 card 0925,1234 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1458,a002 rev 40 class 04,01,00 hdr 00
(II) PCI: 00:13:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
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
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdde00000 - 0xdfefffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcdc00000 - 0xddcfffff (0x10100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:11:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xdddfe000/12
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xde000000/24, 0xd0000000/27, BIOS @ 0xdfee0000/17
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[1] -1	0	0xdddff000 - 0xdddfffff (0x1000) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[6] -1	0	0xdddfe000 - 0xdddfefff (0x1000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[11] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[1] -1	0	0xdddff000 - 0xdddfffff (0x1000) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[6] -1	0	0xdddfe000 - 0xdddfefff (0x1000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[11] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
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
	[4] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[5] -1	0	0xdddff000 - 0xdddfffff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xdddfe000 - 0xdddfefff (0x1000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
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
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Found 2 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[5] -1	0	0xdddff000 - 0xdddfffff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xdddfe000 - 0xdddfefff (0x1000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[5] -1	0	0xdddff000 - 0xdddfffff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xdddfe000 - 0xdddfefff (0x1000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[22] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT,TV"
(**) NVIDIA(0): Option "UseDisplayDevice" "CRT"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x83e
(**) NVIDIA(0): ConnectedMonitor string: "CRT,TV"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): GPU Architecture: 0x30
(II) NVIDIA(0): GPU Implementation: 0x34
(II) NVIDIA(0): GPU Revision: 0xb1
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(0): Bus detected as AGP
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing constraints for  : GeForce FX 5200
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0): 
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0): 
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     HP (CRT-0)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): HP (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for HP (CRT-0) ---
(--) NVIDIA(0): EDID Version                 : 1.0
(--) NVIDIA(0): Manufacturer                 : HWP
(--) NVIDIA(0): Monitor Name                 : HP
(--) NVIDIA(0): Product ID                   : 2830
(--) NVIDIA(0): 32-bit Serial Number         : 81556680
(--) NVIDIA(0): Serial Number String         : 
(--) NVIDIA(0): Manufacture Date             : 1998, week 15
(--) NVIDIA(0): DPMS Capabilities            : Standby Suspend Active Off
(--) NVIDIA(0): Prefer first detailed timing : No
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 280mm x 210mm
(--) NVIDIA(0): Valid HSync Range            : 31 kHz - 68 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 60 Hz - 85 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 108.0 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):   640  x 480  @ 75 Hz
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   800  x 600  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 75 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Standard Timings:
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   1280 x 1024 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 108.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1328
(--) NVIDIA(0):     HSyncEnd, HTotal : 1440, 1688
(--) NVIDIA(0):     VRes, VSyncStart : 1024, 1025
(--) NVIDIA(0):     VSyncEnd, VTotal : 1028, 1066
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   1024 x 768  @ 85 Hz
(--) NVIDIA(0):     Pixel Clock      : 94.50 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1024, 1072
(--) NVIDIA(0):     HSyncEnd, HTotal : 1168, 1376
(--) NVIDIA(0):     VRes, VSyncStart : 768, 769
(--) NVIDIA(0):     VSyncEnd, VTotal : 772, 808
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   800  x 600  @ 85 Hz
(--) NVIDIA(0):     Pixel Clock      : 56.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 800, 832
(--) NVIDIA(0):     HSyncEnd, HTotal : 896, 1048
(--) NVIDIA(0):     VRes, VSyncStart : 600, 601
(--) NVIDIA(0):     VSyncEnd, VTotal : 604, 631
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   640  x 480  @ 85 Hz
(--) NVIDIA(0):     Pixel Clock      : 36.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 640, 696
(--) NVIDIA(0):     HSyncEnd, HTotal : 752, 832
(--) NVIDIA(0):     VRes, VSyncStart : 480, 481
(--) NVIDIA(0):     VSyncEnd, VTotal : 484, 509
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for HP (CRT-0) ---
(--) NVIDIA(0): 
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): TV modes supported by this encoder:
(II) NVIDIA(0):   1024x768; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI,
(II) NVIDIA(0):     PAL-N, PAL-NC
(II) NVIDIA(0):   800x600; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   720x576; Standards: PAL-BDGHI, PAL-N, PAL-NC
(II) NVIDIA(0):   720x480; Standards: NTSC-M, NTSC-J, PAL-M
(II) NVIDIA(0):   640x480; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   640x400; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   400x300; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   320x240; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0):   320x200; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC
(II) NVIDIA(0): Option "UseDisplayDevice" "CRT" converted to "CRT-0".
(II) NVIDIA(0): Frequency information for HP (CRT-0):
(II) NVIDIA(0):   HorizSync   : 31.000-68.000 kHz
(II) NVIDIA(0):   VertRefresh : 60.000-85.000 Hz
(II) NVIDIA(0):     (HorizSync from EDID)
(II) NVIDIA(0):     (VertRefresh from EDID)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for HP (CRT-0) ---
(II) NVIDIA(0): "nvidia-auto-select"   : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1600x1024"            : 1600 x 1024 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1600x1024_60"         : 1600 x 1024 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x1024"            : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x1024_60"         : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x960"             : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x960_60"          : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x800"             : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x800_60"          : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768"             : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768_60"          : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864"             : 1152 x  864 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1152x864_75"          : 1152 x  864 @  75.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768"             : 1024 x  768 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_85"          : 1024 x  768 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_75_0"        : 1024 x  768 @  75.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_75"          : 1024 x  768 @  75.0 Hz  (from: EDID)
(II) NVIDIA(0): "1024x768_70"          : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_60"          : 1024 x  768 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "840x525"              :  840 x  525 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d60"           :  840 x  525 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "832x624"              :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "832x624_75"           :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "800x600"              :  800 x  600 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_85_0"         :  800 x  600 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_85"           :  800 x  600 @  85.1 Hz  (from: EDID)
(II) NVIDIA(0): "800x600_75"           :  800 x  600 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_72"           :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_60"           :  800 x  600 @  60.3 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x512"              :  800 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x512d60"           :  800 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450"              :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450d60"           :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x400"              :  720 x  400 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "720x400_85"           :  720 x  400 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "700x525"              :  700 x  525 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "700x525d60"           :  700 x  525 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512"              :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d60"           :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"              :  640 x  480 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_85"           :  640 x  480 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_75"           :  640 x  480 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_73"           :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480d60"           :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_60_0"         :  640 x  480 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"           :  640 x  480 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "640x400"              :  640 x  400 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x400_85"           :  640 x  400 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x400d60"           :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384"              :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384d60"           :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x350"              :  640 x  350 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x350_85"           :  640 x  350 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "576x432"              :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75"           :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"              :  512 x  384 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d85"           :  512 x  384 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"           :  512 x  384 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"           :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"           :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"              :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"           :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"              :  400 x  300 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d85"           :  400 x  300 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"           :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"           :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"           :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "360x200"              :  360 x  200 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "360x200d85"           :  360 x  200 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"              :  320 x  240 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d85"           :  320 x  240 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"           :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"           :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"           :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x200"              :  320 x  200 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x200d85"           :  320 x  200 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x175"              :  320 x  175 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x175d85"           :  320 x  175 @  85.3 Hz DoubleScan  (from: X Server)


---

### Post by 1ns4nity on 2006-12-28
```


(II) NVIDIA(0): --- End of ModePool for HP (CRT-0): ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "1024x768":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1024, 768]
(II) NVIDIA(0):     HP (CRT-0): "1024x768"
(II) NVIDIA(0):         Size          : 1024 x 768
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1024 x 768
(II) NVIDIA(0):         Position      : [0, 0, 1024, 768]
(II) NVIDIA(0): MetaMode "800x600":
(II) NVIDIA(0):     Bounding Box: [0, 0, 800, 600]
(II) NVIDIA(0):     HP (CRT-0): "800x600"
(II) NVIDIA(0):         Size          : 800 x 600
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 800 x 600
(II) NVIDIA(0):         Position      : [0, 0, 800, 600]
(II) NVIDIA(0): MetaMode "640x480":
(II) NVIDIA(0):     Bounding Box: [0, 0, 640, 480]
(II) NVIDIA(0):     HP (CRT-0): "640x480"
(II) NVIDIA(0):         Size          : 640 x 480
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 640 x 480
(II) NVIDIA(0):         Position      : [0, 0, 640, 480]
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "CRT,TV"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "COMPOSITE"
(**) NVIDIA(1): Option "UseDisplayDevice" "TV"
(==) NVIDIA(1): Using HW cursor
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing COMPOSITE video output
(==) NVIDIA(1): Video key set to default value of 0x101fe
(**) NVIDIA(1): TV Standard string: "PAL-B"
(II) NVIDIA(1): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 131072 kBytes
(II) NVIDIA(1): GPU Architecture: 0x30
(II) NVIDIA(1): GPU Implementation: 0x34
(II) NVIDIA(1): GPU Revision: 0xb1
(--) NVIDIA(1): VideoBIOS: 04.34.20.69.00
(--) NVIDIA(1): Found 2 CRTCs on board
(II) NVIDIA(1): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(1): Bus detected as AGP
(II) NVIDIA(1): Detected AGP rate: 4X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(II) NVIDIA(1): 
(II) NVIDIA(1): Mode timing constraints for  : GeForce FX 5200
(II) NVIDIA(1): Maximum mode timing values   :
(II) NVIDIA(1):     Horizontal Visible Width : 8192
(II) NVIDIA(1):     Horizontal Blank Start   : 8192
(II) NVIDIA(1):     Horizontal Blank Width   : 4096
(II) NVIDIA(1):     Horizontal Sync Start    : 8184
(II) NVIDIA(1):     Horizontal Sync Width    : 504
(II) NVIDIA(1):     Horizontal Total Width   : 8224
(II) NVIDIA(1):     Vertical Visible Height  : 8192
(II) NVIDIA(1):     Vertical Blank Start     : 8192
(II) NVIDIA(1):     Vertical Blank Width     : 256
(II) NVIDIA(1):     Veritcal Sync Start      : 8191
(II) NVIDIA(1):     Vertical Sync Width      : 15
(II) NVIDIA(1):     Vertical Total Height    : 8193
(II) NVIDIA(1): 
(II) NVIDIA(1): Minimum mode timing values   :
(II) NVIDIA(1):     Horizontal Total Width   : 40
(II) NVIDIA(1):     Vertical Total Height    : 2
(II) NVIDIA(1): 
(II) NVIDIA(1): Mode timing alignment        :
(II) NVIDIA(1):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(1):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(1):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(1):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(1):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(1):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(1): 
(--) NVIDIA(1): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(1):     HP (CRT-0)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): HP (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): 
(--) NVIDIA(1): --- EDID for HP (CRT-0) ---
(--) NVIDIA(1): EDID Version                 : 1.0
(--) NVIDIA(1): Manufacturer                 : HWP
(--) NVIDIA(1): Monitor Name                 : HP
(--) NVIDIA(1): Product ID                   : 2830
(--) NVIDIA(1): 32-bit Serial Number         : 81556680
(--) NVIDIA(1): Serial Number String         : 
(--) NVIDIA(1): Manufacture Date             : 1998, week 15
(--) NVIDIA(1): DPMS Capabilities            : Standby Suspend Active Off
(--) NVIDIA(1): Prefer first detailed timing : No
(--) NVIDIA(1): Supports GTF                 : No
(--) NVIDIA(1): Maximum Image Size           : 280mm x 210mm
(--) NVIDIA(1): Valid HSync Range            : 31 kHz - 68 kHz
(--) NVIDIA(1): Valid VRefresh Range         : 60 Hz - 85 Hz
(--) NVIDIA(1): EDID maximum pixel clock     : 108.0 MHz
(--) NVIDIA(1): 
(--) NVIDIA(1): Established Timings:
(--) NVIDIA(1):   640  x 480  @ 60 Hz
(--) NVIDIA(1):   640  x 480  @ 75 Hz
(--) NVIDIA(1):   800  x 600  @ 60 Hz
(--) NVIDIA(1):   800  x 600  @ 75 Hz
(--) NVIDIA(1):   1024 x 768  @ 75 Hz
(--) NVIDIA(1): 
(--) NVIDIA(1): Standard Timings:
(--) NVIDIA(1):   1024 x 768  @ 60 Hz
(--) NVIDIA(1): 
(--) NVIDIA(1): Detailed Timings:
(--) NVIDIA(1):   1280 x 1024 @ 60 Hz
(--) NVIDIA(1):     Pixel Clock      : 108.00 MHz
(--) NVIDIA(1):     HRes, HSyncStart : 1280, 1328
(--) NVIDIA(1):     HSyncEnd, HTotal : 1440, 1688
(--) NVIDIA(1):     VRes, VSyncStart : 1024, 1025
(--) NVIDIA(1):     VSyncEnd, VTotal : 1028, 1066
(--) NVIDIA(1):     H/V Polarity     : +/+
(--) NVIDIA(1):   1024 x 768  @ 85 Hz
(--) NVIDIA(1):     Pixel Clock      : 94.50 MHz
(--) NVIDIA(1):     HRes, HSyncStart : 1024, 1072
(--) NVIDIA(1):     HSyncEnd, HTotal : 1168, 1376
(--) NVIDIA(1):     VRes, VSyncStart : 768, 769
(--) NVIDIA(1):     VSyncEnd, VTotal : 772, 808
(--) NVIDIA(1):     H/V Polarity     : +/+
(--) NVIDIA(1):   800  x 600  @ 85 Hz
(--) NVIDIA(1):     Pixel Clock      : 56.25 MHz
(--) NVIDIA(1):     HRes, HSyncStart : 800, 832
(--) NVIDIA(1):     HSyncEnd, HTotal : 896, 1048
(--) NVIDIA(1):     VRes, VSyncStart : 600, 601
(--) NVIDIA(1):     VSyncEnd, VTotal : 604, 631
(--) NVIDIA(1):     H/V Polarity     : +/+
(--) NVIDIA(1):   640  x 480  @ 85 Hz
(--) NVIDIA(1):     Pixel Clock      : 36.00 MHz
(--) NVIDIA(1):     HRes, HSyncStart : 640, 696
(--) NVIDIA(1):     HSyncEnd, HTotal : 752, 832
(--) NVIDIA(1):     VRes, VSyncStart : 480, 481
(--) NVIDIA(1):     VSyncEnd, VTotal : 484, 509
(--) NVIDIA(1):     H/V Polarity     : -/-
(--) NVIDIA(1): 
(--) NVIDIA(1): --- End of EDID for HP (CRT-0) ---
(--) NVIDIA(1): 
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): TV modes supported by this encoder:
(II) NVIDIA(1):   1024x768; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI,
(II) NVIDIA(1):     PAL-N, PAL-NC
(II) NVIDIA(1):   800x600; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   720x576; Standards: PAL-BDGHI, PAL-N, PAL-NC
(II) NVIDIA(1):   720x480; Standards: NTSC-M, NTSC-J, PAL-M
(II) NVIDIA(1):   640x480; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   640x400; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   400x300; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   320x240; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   320x200; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1): Option "UseDisplayDevice" "TV" converted to "TV-0".
(II) NVIDIA(1): 
(II) NVIDIA(1): --- Modes in ModePool for NVIDIA TV Encoder (TV-0) ---
(II) NVIDIA(1): "nvidia-auto-select"   : 1024 x  768 @  60.0 Hz  (from: NVIDIA Predefined)
(II) NVIDIA(1): "1024x768"             : 1024 x 768; for use with TV standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N, PAL-NC (from: NVIDIA Predefined)
(II) NVIDIA(1): "800x600"              : 800 x 600; for use with TV standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N, PAL-NC (from: NVIDIA Predefined)
(II) NVIDIA(1): "720x576"              : 720 x 576; for use with TV standards: PAL-BDGHI, PAL-N, PAL-NC (from: NVIDIA Predefined)
(II) NVIDIA(1): "640x480"              : 640 x 480; for use with TV standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N, PAL-NC (from: NVIDIA Predefined)
(II) NVIDIA(1): "400x300"              : 400 x 300; for use with TV standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N, PAL-NC (from: NVIDIA Predefined)
(II) NVIDIA(1): "320x240"              : 320 x 240; for use with TV standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N, PAL-NC (from: NVIDIA Predefined)
(II) NVIDIA(1): "320x200"              : 320 x 200; for use with TV standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N, PAL-NC (from: NVIDIA Predefined)
(II) NVIDIA(1): --- End of ModePool for NVIDIA TV Encoder (TV-0): ---
(II) NVIDIA(1): 
(II) NVIDIA(1): Assigned Display Device: TV-0
(II) NVIDIA(1): Requested modes:
(II) NVIDIA(1):     "640x480"
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1): MetaMode "640x480":
(II) NVIDIA(1):     Bounding Box: [0, 0, 640, 480]
(II) NVIDIA(1):     NVIDIA TV Encoder (TV-0): "640x480"
(II) NVIDIA(1):         Size          : 640 x 480
(II) NVIDIA(1):         Offset        : +0 +0
(II) NVIDIA(1):         Panning Domain: @ 640 x 480
(II) NVIDIA(1):         Position      : [0, 0, 640, 480]
(II) NVIDIA(1): Virtual screen size determined to be 640 x 480
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(1): Saved console TV mode: 3
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfffff00 - 0xdfffffff (0x100) MX[B]
	[7] -1	0	0xdddff000 - 0xdddfffff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[12] -1	0	0xdddfe000 - 0xdddfefff (0x1000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): CRT-0 assigned CRTC 0
(II) NVIDIA(0): TV-0 assigned CRTC 1
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) NVIDIA(1): kernel module enabled successfully
(II) NVIDIA(1): Memory mapped
(II) NVIDIA(1): Interrupts enabled
(II) NVIDIA(1): Setting mode "640x480"
(II) NVIDIA(1): Not allocating video overlay for second X screen sharing this
(II) NVIDIA(1):     GPU
(II) NVIDIA(1): First mode initialized
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Visuals set up
(II) NVIDIA(1): Pixmap depths set up
(II) NVIDIA(1): GLX visuals set up
(II) NVIDIA(1): Framebuffer set up
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(II) NVIDIA(1): Default colormap initialized.
(II) NVIDIA(1): Palette loaded
(II) NVIDIA(1): Screen initialization complete
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbVariant" "intl"
(**) Generic Keyboard: XkbVariant: "intl"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
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
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us(intl)+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/input/mice"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!


```


And my config file is:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
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
    Screen      0  "Screen[0]"
    Screen     1    "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    #InputDevice    "stylus" "SendCoreEvents"
    #InputDevice    "cursor" "SendCoreEvents"
    #InputDevice    "eraser" "SendCoreEvents"
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
    FontPath        "/usr/share/fonts/X11/misc"
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "intl"
    Option         "XkbOptions" "lv3:ralt_switch"
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
    Identifier     "Monitor[0]"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
 #TV
    Identifier     "Monitor[1]"
    HorizSync       30-50
    VertRefresh     60
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    Screen 0
    BusID "PCI:1:0:0"
    Option "ConnectedMonitor" "CRT,TV"
    Option "UseDisplayDevice" "CRT"
EndSection

Section "Device"
 #adjust using lspci or cat /proc/pci
    Identifier     "Device[1]"
    Driver         "nvidia"
    BusID "PCI:1:0:0"
    Screen 1
    Option         "TVOutFormat" "COMPOSITE" # or SVIDEO etc
    Option         "TVStandard" "PAL-B" # or NTSC etc
    #Option         "ConnectedMonitor" "Monitor[1]" # or NTSC etc
    #Option "IgnoreEDID" "True"
    Option "ConnectedMonitor" "CRT,TV"
    Option "UseDisplayDevice" "TV"
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    16
    #Option         "TwinView" "true"
    #Option         "TwinViewOrientation" "Clone"
    #Option         "TVOutFormat" "COMPOSITE"
    #Option         "TVStandard" "PAL-M"
    #Option         "SecondMonitorHorizSync" "30-50"
    #Option         "SecondMonitorVertRefresh" "60"
    #Option         "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "640x480"
    EndSubSection
EndSection



```

---

### Post by fattmox on 2007-01-04
Found this article very helpful

Running Edgy Eft on Dell C840 with a GeForce 440 Go.

Up and running in minutes.

Thanks.

---

### Post by JELO on 2007-01-14
Well, I had it working for awhile.  I recently ran updates and everything went wrong.  Managed to get X working again and the tv out sort of.  Not to my liking though, I basically just have a clone on my tv.  Before I had it so my tv was separate, could open movies up directly to my tv etc.  Whenever I try doing the RightOf option in xorg.conf, x crashes on restart and I have to change the file back the way it was.   I'm running the latest beryl and nvidia beta drivers as described in this guide [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by obryant on 2007-02-13
I'm a total linux newb. I just followed the directions verbatim and it worked. (Edgy Eft with geForce 5200)

Thanks

---

### Post by RudolfMDLT on 2007-02-22
Thanks man! this worked great!:guitar:

---

### Post by medeshago on 2007-02-25
Can't get it to work. No picture on the TV.

xorg.conf:

```
Section "ServerLayout" 
   	Identifier  "Simple Layout" 
       	Screen 0 "Screen[0]" 
       	Screen 1 "Screen[1]" RightOf "Screen[0]" 
   	InputDevice "Configured Mouse"  
   	InputDevice "Generic Keyboard" 
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
    FontPath        "/usr/share/fonts/X11/misc"
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "latam"
    Option         "XkbOptions" "lv3:ralt_switch"
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
	Identifier "Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync 31.5-80 
        	VertRefresh 56.3-75 
EndSection

 Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "NTSC" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:5:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection


```


Xorg.0.log

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux nosotros 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 26 14:35:52 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1462,7135 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1462,7135 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1462,7135 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1462,7135 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1462,7135 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1462,b010 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1462,7135 rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1462,7135 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1462,7135 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1462,7135 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 05:00:0: chip 10de,01df card 1462,0345 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfd800000 - 0xfd8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(5:0:0) nVidia Corporation unknown chipset (0x01df) rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
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
(II) Active PCI resource ranges:
	[0] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[1] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[2] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[3] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[4] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[5] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[6] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[10] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[11] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[12] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[13] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[14] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[15] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[21] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[22] -1	0	0x0000ea00 - 0x0000eaff (0x100) IX[B]
	[23] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[24] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[1] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[2] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[3] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[4] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[5] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[6] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[10] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[11] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[12] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[13] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[14] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[15] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[21] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[22] -1	0	0x0000ea00 - 0x0000eaff (0x100) IX[B]
	[23] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[24] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
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
	[4] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[16] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[17] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[18] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[19] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[20] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[21] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[27] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[28] -1	0	0x0000ea00 - 0x0000eaff (0x100) IX[B]
	[29] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[30] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[16] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[17] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[18] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[19] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[20] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[21] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[27] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[28] -1	0	0x0000ea00 - 0x0000eaff (0x100) IX[B]
	[29] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[30] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[19] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[30] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[31] -1	0	0x0000ea00 - 0x0000eaff (0x100) IX[B]
	[32] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[33] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GS at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.43.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GS at PCI:5:0:0:
(--) NVIDIA(0):     ViewSonic E70f+-4 (CRT-0)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): ViewSonic E70f+-4 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "Monitor[1]"
(**) NVIDIA(1): Option "TVStandard" "NTSC"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing COMPOSITE video output
(**) NVIDIA(1): TV Standard string: "NTSC"
(WW) NVIDIA(1): Unknown TV Standard "NTSC"; defaulting to "NTSC-M"
(II) NVIDIA(1): NVIDIA GPU GeForce 7300 GS at PCI:5:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.72.22.43.00
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7300 GS at PCI:5:0:0:
(--) NVIDIA(1):     ViewSonic E70f+-4 (CRT-0)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): ViewSonic E70f+-4 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: TV-0
(WW) NVIDIA(1): No valid modes for "1024x768_60"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfe029000 - 0xfe029fff (0x1000) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f007 (0x8) IX[B]
	[22] -1	0	0x0000f100 - 0x0000f10f (0x10) IX[B]
	[23] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[24] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[25] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[26] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[27] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[33] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[34] -1	0	0x0000ea00 - 0x0000eaff (0x100) IX[B]
	[35] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[36] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[37] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
```

---

### Post by nosleep on 2007-02-26
Hi, only got "No video signal" on TV so far.  

On boot there is picture on TV, but when Ubuntu starts it lost and I got TV message  "No video signal".  If I try to boot with "vesa" drivers picture on TV is OK.

This is my xorg.conf:

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
	Option		"XkbLayout"	"hr"
#	Option		"XkbVariant"	"hr"
#	Option		"XkbOptions"	"lv3:ralt_switch"
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


##=================================================================================


Section "Monitor"
	Identifier "Monitor[0]" #CRT
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
EndSection


Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-B" #or NTSC etc 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
	Option 		"ConnectedMonitor" "Monitor[0]"
   	Screen 1 
EndSection


Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
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
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

and this is the log

```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux htpc 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 26 21:06:03 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(==) |-->Input Device "Generic Keyboard"
(WW) The core keyboard device wasn't specified explicitly in the layout.
	Using the first core keyboard device.
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3168 card 1106,3168 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b168 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1106,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,3177 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 15bd,3000 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1106,0102 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0170 card 10b0,0b02 rev a3 class 03,00,00 hdr 00
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
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 MX 460] rev 163, Mem @ 0xe4000000/24, 0xd0000000/27, 0xd8000000/19
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[1] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[1] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
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
	[4] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[22] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 460 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.00.45.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 460 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "Monitor[0]"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "Composite"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing COMPOSITE video output
(**) NVIDIA(1): TV Standard string: "PAL-B"
(II) NVIDIA(1): NVIDIA GPU GeForce4 MX 460 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 65536 kBytes
(--) NVIDIA(1): VideoBIOS: 04.17.00.45.00
(II) NVIDIA(1): Detected AGP rate: 4X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce4 MX 460 at PCI:1:0:0:
(--) NVIDIA(1):     CRT-0
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: TV-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1024x768"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xd807ffff (0x80000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] 0	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe6001000 - 0xe60010ff (0x100) MX[B]
	[8] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "1024x768"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "hr"
(**) Generic Keyboard: XkbLayout: "hr"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
    xkb_keycodes             { include "xfree86+aliases(qwertz)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+hr" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

---

### Post by pixel8 on 2007-03-02
hi all, just to say this worked 1st time for me just following the (excellent) guide, thank you tseliot.

running Edgy with an FX5200, using S-Video out port.

---

### Post by Ph00p on 2007-03-02
Sorry if this has already been posted here, but is it easy to connect and disconnect the tv or is this a permanent thing?

---

### Post by peekj on 2007-03-04
I have my TV-Out working just fine except for one thing that I hope someone can help with:

The image on the TV does not fill out the entire screen. here's about 1.5 inches on the left that are purely black as well as about 0.5 inches on the top, right, and bottom that are unused. Now, on a monitor it's easy to adjust the screen position but my TV has no such controls.

Can I adjust this in software? Maybe in the xorg.conf? I don't want to use nvtv because I haven't had a good experience with it. Is there any other way to do this? I'd like to use all the screen real estate if possible.

Thanks!

---

### Post by codecks on 2007-03-16
I can't get it working. I followed the guide tried some modifications but nothing works. As soon as I try to use the TV-Out it Ubuntu doesn't start anymore.I hope someone can point me out in the right direction.

Here's my xorg.conf

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
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

#Section "ServerLayout"
#    Identifier     "Default Layout"
#    Screen         "Default Screen" 0 0
#    InputDevice    "Generic Keyboard"
#    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
#    InputDevice    "Synaptics Touchpad"
#EndSection

Section "ServerLayout"
	Identifier "Simple Layout"
		Screen 0 "Screen[0]"
		Screen 1 "Screen[1]" RightOf "Screen[0]"
	InputDevice "Configured Mouse" "CorePointer"
	InputDevice "Generic Keyboard" "CoreKeyboard"
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
    FontPath        "/usr/share/fonts/X11/misc"
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
    Option         "XkbOptions" "lv3:ralt_switch"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor[0]" #crt
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier "Monitor[1]" #TV
    HorizSync 30.0 - 50.0
    VertRefresh 60.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    screen 0
EndSection

Section "Device"
	Identifier "Device[1]"
	Driver "nvidia"
	Screen 1
	Option "TVOutFormat" "COMPOSITE"
	Option "TVStandard" "PAL-B"
	Option "ConnectedMonitor" "TV"
	BusID  "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    16
    Option         "ExactModeTimingsDVI" "TRUE"
    Option         "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"

    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen"
	Device "Device[1]"
	Identifier "Screen[1]"
	Monitor "Monitor[1]"
	DefaultDepth 16
	SubSection "Display"
		Depth 16
		Modes "1024x768"
	EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

and here's my Xorg.0.log

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux ubuntu 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 16 18:26:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Generic Keyboard"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1a30 card 1179,0001 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2482 card 1179,0001 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2484 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 42 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,248c card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,248a card 1179,0001 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,2485 card 1179,0001 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,2486 card 1179,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0175 card 1179,0001 rev a3 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 104c,8023 card 1179,0001 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:08:0: chip 8086,1031 card 1179,0001 rev 42 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 1179,0617 card d000,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0b:1: chip 1179,0617 card d800,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0d:0: chip 1179,0805 card 1179,0001 rev 03 class 08,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xebf00000 - 0xefffffff (0x4100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,8), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfce00000 - 0xfcefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x23ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:11:0), (2,3,4), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x21ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (2:11:1), (2,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[1] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x22000000 - 0x23ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 420 Go] rev 163, Mem @ 0xfd000000/24, 0xec000000/26, 0xebf80000/19
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfcef6e00 - 0xfcef6fff (0x200) MX[B]
	[1] -1	0	0xfcef7000 - 0xfcef7fff (0x1000) MX[B]
	[2] -1	0	0xfcef8000 - 0xfcefbfff (0x4000) MX[B]
	[3] -1	0	0xfceff800 - 0xfcefffff (0x800) MX[B]
	[4] -1	0	0x24000000 - 0x240003ff (0x400) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xebf80000 - 0xebffffff (0x80000) MX[B](B)
	[7] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[10] -1	0	0x0000c980 - 0x0000c9ff (0x80) IX[B]
	[11] -1	0	0x0000ca00 - 0x0000caff (0x100) IX[B]
	[12] -1	0	0x0000cdc0 - 0x0000cdff (0x40) IX[B]
	[13] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[14] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[15] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[16] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[17] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[18] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfcef6e00 - 0xfcef6fff (0x200) MX[B]
	[1] -1	0	0xfcef7000 - 0xfcef7fff (0x1000) MX[B]
	[2] -1	0	0xfcef8000 - 0xfcefbfff (0x4000) MX[B]
	[3] -1	0	0xfceff800 - 0xfcefffff (0x800) MX[B]
	[4] -1	0	0x24000000 - 0x240003ff (0x400) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xebf80000 - 0xebffffff (0x80000) MX[B](B)
	[7] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[10] -1	0	0x0000c980 - 0x0000c9ff (0x80) IX[B]
	[11] -1	0	0x0000ca00 - 0x0000caff (0x100) IX[B]
	[12] -1	0	0x0000cdc0 - 0x0000cdff (0x40) IX[B]
	[13] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[14] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[15] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[16] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[17] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[18] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcef6e00 - 0xfcef6fff (0x200) MX[B]
	[5] -1	0	0xfcef7000 - 0xfcef7fff (0x1000) MX[B]
	[6] -1	0	0xfcef8000 - 0xfcefbfff (0x4000) MX[B]
	[7] -1	0	0xfceff800 - 0xfcefffff (0x800) MX[B]
	[8] -1	0	0x24000000 - 0x240003ff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xebf80000 - 0xebffffff (0x80000) MX[B](B)
	[11] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[16] -1	0	0x0000c980 - 0x0000c9ff (0x80) IX[B]
	[17] -1	0	0x0000ca00 - 0x0000caff (0x100) IX[B]
	[18] -1	0	0x0000cdc0 - 0x0000cdff (0x40) IX[B]
	[19] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[20] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[21] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[22] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[23] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[24] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[25] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
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
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcef6e00 - 0xfcef6fff (0x200) MX[B]
	[5] -1	0	0xfcef7000 - 0xfcef7fff (0x1000) MX[B]
	[6] -1	0	0xfcef8000 - 0xfcefbfff (0x4000) MX[B]
	[7] -1	0	0xfceff800 - 0xfcefffff (0x800) MX[B]
	[8] -1	0	0x24000000 - 0x240003ff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xebf80000 - 0xebffffff (0x80000) MX[B](B)
	[11] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[16] -1	0	0x0000c980 - 0x0000c9ff (0x80) IX[B]
	[17] -1	0	0x0000ca00 - 0x0000caff (0x100) IX[B]
	[18] -1	0	0x0000cdc0 - 0x0000cdff (0x40) IX[B]
	[19] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[20] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[21] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[22] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[23] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[24] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[25] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcef6e00 - 0xfcef6fff (0x200) MX[B]
	[5] -1	0	0xfcef7000 - 0xfcef7fff (0x1000) MX[B]
	[6] -1	0	0xfcef8000 - 0xfcefbfff (0x4000) MX[B]
	[7] -1	0	0xfceff800 - 0xfcefffff (0x800) MX[B]
	[8] -1	0	0x24000000 - 0x240003ff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xebf80000 - 0xebffffff (0x80000) MX[B](B)
	[11] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[19] -1	0	0x0000c980 - 0x0000c9ff (0x80) IX[B]
	[20] -1	0	0x0000ca00 - 0x0000caff (0x100) IX[B]
	[21] -1	0	0x0000cdc0 - 0x0000cdff (0x40) IX[B]
	[22] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[23] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[24] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[25] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[26] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[27] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[28] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[29] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ExactModeTimingsDVI" "TRUE"
(**) NVIDIA(0): Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failure reading maximum pixel clock value for display device
(EE) NVIDIA(0):     TV-0.
(II) NVIDIA(0): NVIDIA GPU GeForce4 420 Go at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.00.41.c7
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 420 Go at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     NVIDIA Default Flat Panel (DFP-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 100.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Mode Validation Overrides for NVIDIA Default Flat Panel
(II) NVIDIA(0):     (DFP-0):
(II) NVIDIA(0):     NoEdidDFPMaxSizeCheck
(II) NVIDIA(0):     NoVesaModes
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (76, 75); computed from "UseEdidDpi" X config option
(**) NVIDIA(1): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(1): RGB weight 565
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "COMPOSITE"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing COMPOSITE video output
(**) NVIDIA(1): TV Standard string: "PAL-B"
(II) NVIDIA(1): NVIDIA GPU GeForce4 420 Go at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 32768 kBytes
(--) NVIDIA(1): VideoBIOS: 04.17.00.41.c7
(II) NVIDIA(1): Detected AGP rate: 4X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce4 420 Go at PCI:1:0:0:
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1):     NVIDIA Default Flat Panel (DFP-0)
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 100.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: TV-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1024x768"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	0	0xebf80000 - 0xebffffff (0x80000) MX[B]
	[1] 0	0	0xec000000 - 0xefffffff (0x4000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfcef6e00 - 0xfcef6fff (0x200) MX[B]
	[8] -1	0	0xfcef7000 - 0xfcef7fff (0x1000) MX[B]
	[9] -1	0	0xfcef8000 - 0xfcefbfff (0x4000) MX[B]
	[10] -1	0	0xfceff800 - 0xfcefffff (0x800) MX[B]
	[11] -1	0	0x24000000 - 0x240003ff (0x400) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xebf80000 - 0xebffffff (0x80000) MX[B](B)
	[14] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[22] -1	0	0x0000c980 - 0x0000c9ff (0x80) IX[B]
	[23] -1	0	0x0000ca00 - 0x0000caff (0x100) IX[B]
	[24] -1	0	0x0000cdc0 - 0x0000cdff (0x40) IX[B]
	[25] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[26] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[27] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[28] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[29] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[30] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[31] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[32] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(EE) NVIDIA(0): The requested configuration of display devices is not
(EE) NVIDIA(0):     supported in the hardware.

Fatal server error:
AddScreen/ScreenInit failed for driver 0

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/X11R6/bin/X(AbortServer+0x23) [0x81a1603]
3: /usr/X11R6/bin/X(FatalError+0x66) [0x81a1b06]
4: /usr/X11R6/bin/X(InitOutput+0x883) [0x809fdd3]
5: /usr/X11R6/bin/X(main+0x276) [0x806e506]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d0f8cc]
7: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

FatalError re-entered, aborting
Caught signal 11.  Server aborting

```


This seems to be the error, dunno what it exactly means tho (did some googling but no real explanation)
```

(EE) NVIDIA(0): Failure reading maximum pixel clock value for display device
(EE) NVIDIA(0):     TV-0.

```

What happens is when I start ubuntu, the system shows a blank screen, then it "flicker's" 2 or 3 times (like if it is changing resolution) and then it hangs. From the moment I press a key, I got an X error message.

I'm running it on a laptop (Toshiba Satelite Pro 2100) with a GeForce4 420 GO graphic adapter.

Please help.

---

### Post by medeshago on 2007-03-16
This works perfectly using metacity but when i try to use it with beryl, i can't get it to work. Any solution to that?

---

### Post by BiggerGeek on 2007-03-21
I don't know if anyone is still watching this thread, but I am having problems getting video to display on the second device. I have two desktops, one on my crt and one on my tv. I can't get videos or programs to open on that display using the scripts people mentioned in this thread.

If i do 

mplayer -display :0.1 -fs $filename 

it says it cannot connect to the display. And sometimes, after I have been messing with it, certain programs will only open on my TV, like gedit. I am ideally trying to get mplayer and mythtv only to run on the tv only. Anyone know how I can check the numbering of the available displays or anything like that?

---

### Post by daller on 2007-03-22
> **BiggerGeek said:**
> I don't know if anyone is still watching this thread, but I am having problems getting video to display on the second device. I have two desktops, one on my crt and one on my tv. I can't get videos or programs to open on that display using the scripts people mentioned in this thread.

If i do 

mplayer -display :0.1 -fs $filename 

it says it cannot connect to the display. And sometimes, after I have been messing with it, certain programs will only open on my TV, like gedit. I am ideally trying to get mplayer and mythtv only to run on the tv only. Anyone know how I can check the numbering of the available displays or anything like that?

Please post your xorg.conf file inside a "CODE/CODE"

Your screens should be numbered in the ServerLayout like this:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0 "Default Screen"
        Screen 1 "Screen[SISUSBVGA]" RightOf "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

---

### Post by t-tbone on 2007-03-25
[img]http://ubuntuforums.org/images/smilies/eusa_clap.gif[/img]
Nvidia 6800 here doing s-video out to a Panasonic 42" plasma worked like a champ the first time with your instructions.  Thanks because this is about the fourth set I've tried until yours worked.

:guitar:

---

### Post by gforster on 2007-03-31
Thank you for your guide.  It helped me get the s-video working.  My problem is that the entire screen does not show up on the TV.  The right third and the bottom third are cut off.  I can't figure out the problem. I have tried everything I can think of (changing resolutions, etc.), but I am now stuck.  I cannot find information on this at all anywhere.  I really need to get his to work as I do presentations at school.  I can adjust the position of picture on the TV screen, but not the size.  Anybody have an idea?

---

### Post by avidesh on 2007-04-07
I don't see the entire desktop on TV only the top & bottom menu and the background.
Don't see any application windows on the TV screen, while on the CRT I see everything.
I have Geforce2 MX/MX 400, Ubuntu edgy, nvidia 71X legacy driver

How to fix this?

---

### Post by jetpeach on 2007-04-20
I am also look for a way to optimize the position of the screen on the TV - it does not fill it all and is screwed a little funny.
I have a geforce3 ti 200 so run the newer legacy driver, but i heard the newest uptodate driver allows screen positioning in it's gui config? could somebody who has adjusted their screen position post what happens in the xorg.conf files to move the screen?
thanks,
jet

---

### Post by FurryNemesis on 2007-04-26
Has anyone managed to get this working with an NVidia Geforce4 Go? I was very close yesterday but unfortunately my laptop screen greyed out with a timer and the TV that I was trying to hook it up to wouldn't play ball. I'm using Dapper and the Legacy driver from the repos as the one from the nvidia site won't compile at the moment. Will try again in the meantime and post relevant Xorg.conf+log if I fail.

---

### Post by FurryNemesis on 2007-04-26
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
	Load	"record"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"9"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7 8 9"
	Option		"Emulate3Buttons"	"false"
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 460 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Screen 0
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-I" #or NTSC etc 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor" #Laptop Screen
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 460 Go]"
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

Section "Screen" 
   	Device "NVIDIA Corporation NV17 [GeForce4 460 Go]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

Section "ServerLayout" 
   	Identifier  "Simple Layout" 
       	Screen 0 "Default Screen" 
       	Screen 1 "Screen[1]" RightOf "DefaultScreen" 
   	InputDevice "Configured Mouse" "CorePointer" 
   	InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Sawert on 2007-05-12
Have anyone that uses the "Workspace on a cube"-effect got this to work? If so, does the whole feature "on a cube" stops working? It should, because if you use this feature, like I do, I have four different workspaces on this cube and it would be a shame to loose this feature. If this means that I have to change xorg.conf every time I want to connect my computer to the TV, it's so not worth it, then the best way should be to clone the picture, like several people though about. I found another guide about that and if what I stated is facts, I'll try to clone it instead.

The problem I have had so far while cloning the screen is that the TV can't manage rezolutions higher than 1024 and that means that my desktop runs the same resolution. Why isn't there a simple feature to clone the screen in nvidia-settions, just like in Windows so the screen refrehses if you clone the screen.

---

### Post by Sirhanz on 2007-05-15
Hi I have a Matrox G450 I would like to configure for tv out. here is my xorg.conf, if someone would be so kind to just edit what i posted so that i may cut and paste for my eyes are very bad. Thanks in advance.         ```
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
    Load    "dbe"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "record"
    Load    "type1"
    Load    "v4l"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "usdvorak"
    Option        "XkbVariant"    "dvorak"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
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
    Identifier    "MatroxG450"
    Driver        "mga"
    BusID        "PCI:6:0:0"
    Option        "OldDmaInit"        "True"
EndSection

Section "Monitor"
    Identifier    "PHILIPS 109B"
    Option        "DPMS"
    HorizSync    30-100
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "MatroxG450"
    Monitor        "PHILIPS 109B"
    DefaultDepth    16
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

```

---

### Post by dimmanramone on 2007-05-17
Hi!

Even if I followed your guide...i still cannot make the TV-out to work...i think that i have done everything right, or at least i made some things right because i can see the arrow of the mouse on the TV, but i don't get any background and i cannot move any application there :S 

here is my xorg.conf:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor[1]" #TV
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor[0]" #CRT
    VendorName     "Unknown"
    ModelName      "DELL P992"
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          0
    Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"
    Option "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device[1]"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          1    
    Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
    Option          "TVStandard" "PAL-G" #or NTSC etc 
    Option          "ConnectedMonitor" "Monitor[1]" 
    Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"
    Option "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "metamodes" "TV: 800x600 +0+0; TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1600x1200_75 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


What can be wrong?

---

### Post by dimmanramone on 2007-05-17
Just realize that my xorg.conf was absolutely fine, the problem was from there, but that i have active the desktop effects...

Thx for the very good guide...

---

### Post by zion_da on 2007-05-18
hey guys , 
great How-to guide, my tvout function is working great in 2x x-screens on my FX5200 card.
(ubuntu feisty fawn, and newest nvidia drivers)

but only one problem, when beryl is activated i'm getting a menu delay of 2 seconds on each click
only after editing the xorg.conf file,

here's my xorg.conf file

[http://www.speedyshare.com/615908818.html](http://www.speedyshare.com/615908818.html)

what should i do ?

thanks in advanced!

Zion

---

### Post by ac82 on 2007-05-19
Hi! I've been using various Ubuntu distros along XP, never used any of them more than a week or two, but with Feisty, I've finally decided to start using only Ubuntu.
I've got a problem with tv-out on my Asus 6800gt 128mb agp (v9999gt). I've installed drivers through synaptic and everything works perfectly until I tried to enable tv-out. I have my tv connected to s-video port on my card, and I used nvidia-settings to enable tv as second screen(option: separate x-screen). I applied and saved changes to xorg.conf which then looked like this:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "IQT L70S"
    HorizSync       31.0 - 79.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 720x400 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

When I restarted, x wouldn't start, giving this announcement:```

(EE)NVIDIA(1): Unable to initialize the X Int10 module; the console may not be restored on your TV.
(EE)The requested configuration of display devices is not supported in the hardware.

Fatal server error: Add screen/ScreenInit failed for driver0
```

Please, could someone help me, 'cause this one really bugs me, and  Ubuntu is loosing points when it comes to usability (using tv as second screen on XP worked just fine).

---

### Post by cody50 on 2007-05-20
would someone have to do all of this if they just wanted to use the TV as the only screen?

---

### Post by jetpeach on 2007-05-21
no, i didn't, this guide was written December 3rd, 2005 and in Feisty it is simpler.
I use my nvidia with a TV as the only monitor and all i did to set up was install the nvidia drivers from their website (for some reason the proprietary drivers in the repositories don't work though), i just ran the binary, answered the questions, and then I was able to boot info KDE/Gnome (I always was able to have terminal access on the TV, that's how i downloaded/installed).

in any case, i think this thread has some very useful info in it still but since it is so old and long now, it's quite difficult to decipher what is old and what is new... It might be the case that this even "just works" with Feisty  if proprietary drivers are enabled by default.

---

### Post by 8086 on 2007-05-24
> **jetpeach said:**
> no, i didn't, this guide was written December 3rd, 2005 and in Feisty it is simpler.
I use my nvidia with a TV as the only monitor and all i did to set up was install the nvidia drivers from their website (for some reason the proprietary drivers in the repositories don't work though),

Thanks for the tip. I have upgraded from a fully functional dapper to feisty, and it is not able to give me Xorg output on the TV-out. I also have to do everything from console, but I haven't tried downloading the drivers from the Nvidia website. Will try that any minute now.
Seems that a lot changed with the drivers/setup that came with feisty. I installed the proprietary driver all over again (after the upgrade), but it complained about my configfile. This has changed:

In the Device section:
   Previously this worked: ```
Option ConnectedMonitor "TV-identifier"
```, where TV-identifier was the name of the Monitor section for the TV. Now it has a completely different meaning:
    ```
Option ConnectedMonitor "TV"
```, where TV is the *type* of the monitor. So if you have both a CRT and a tv attached you would write "CRT, TV". 

The ```
 Option "TvOutFormat" "S-VIDEO"
``` part now has changed to "```
 Option "TvOutFormat" "SVIDEO"
```. I had to do these changes to make Xorg stop complaining, but after all the complaints have disappeared I now only get a "FATAL: Module nvida not found"...

A lot of other programs might also be corrupted by the upgrade. Starting the command line bittorrent client (```
btdownloadcurses
``` gives me heaps of GZip errors:(

Will never trust the upgrade program again...

---

