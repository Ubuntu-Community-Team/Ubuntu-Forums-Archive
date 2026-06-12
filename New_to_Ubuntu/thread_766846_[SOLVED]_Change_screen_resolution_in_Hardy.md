---
title: "[SOLVED] Change screen resolution in Hardy"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by kestrel1 on 2008-04-25
I have a clean install of Ubuntu 8.04 (Hardy Heron) & the maximum screen resolution that I can get is 800 X 600.
I tried 
```
sudo dpkg-reconfigure xserver-xorg
```
as this used to work in Ubuntu 7.10, but I don't get an option to change the screen resolution as I used to.
I have tried adding modes to the xorg.conf file, but I get a 'no signal' message on my monitor. I go to a command prompt (ctrl,alt,F1) & type in the command above & I can get back to my original desktop 800 X 600, this is starting to annoy me now. I expect I am being a complete P brain, but could someone help me out.
Many thanks

---

### Post by kestrel1 on 2008-04-25
Bump

---

### Post by philinux on 2008-04-25
System>Prefs>Screen Resolution.

See if that works. It's the preferred method now. xorg.conf is now only a stub file.

---

### Post by nemodot on 2008-04-25
I think he already tried that...

I have the exact same problem. I'll submit to this thread for the solution.

---

### Post by kestrel1 on 2008-04-25
Sorry, forgot to mention that I had already done that one. Max resolution is the same 800 x 600.
I installed the restricted drivers for my Nvidia card & the max resolution I got then was even worse 640 x 480
Any other thoughts?

---

### Post by Rabindranath on 2008-04-25
What graphics card do you have? If it is NVIDIA, you can also change it through System > Preferences > NVIDIA X Server Settings.

---

### Post by philinux on 2008-04-25
In hardy there is now a thing called xfix, you issue the command from recovery mode in grub.

---

### Post by nemodot on 2008-04-25
I've found the solution!

Look on the Synaptic manager the "nvidia settings" and install it. Then look for it on System->Admin. It worked for me

---

### Post by philinux on 2008-04-25
Good news. Which graphics card have you got?

---

### Post by ff78 on 2008-04-25
I'm having similar issues on my machine as well, so this is quite relevant to me and my nVidia GeForce 6100.

---

### Post by hurtstotalktoyou on 2008-04-25
This appears to be a problem with the monitor detection, not the video card driver.  Here's what I did:

1.  Go to System > Administration > Hardware Drivers and make sure your proprietary video card driver is disabled (the box should be unchecked).  Don't worry, you'll enable it later; just not now.  Reboot if necessary.

2.  Go to System > Preferences > Screen Resolution and choose the highest available resolution (usually 800x600).  This will allow you to navigate through Ubuntu more easily than at the lower resolutions associated with the proprietary driver.

3.  Go to System > Preferences > Main Menu > Applications > Other and make sure the "Screens and Graphics" box is checked.

4.  Go to Applications > Other > Screens and Graphics and select the option which best describes your display (LCD or CRT, etc.).  Do *not* use the "detect" function.  Also, do *not* choose "Plug 'n' play".

5.  Now go back to System > Administration > Hardware Drivers and enable your proprietary video card driver.  You will have to reboot for sure this time.

Even after these steps, I still am having trouble with the login screen, which does not display properly.  However, after logging in you should have little or no trouble getting higher resolutions.

**Does anyone know how to fix the login screen resolution?**

---

### Post by MFelkins on 2008-04-25
That did it. And I have a very old GeForce 2 mx/mx 400 with a wopping 32 mg of ram. I am using my 2048 x 1024 Flat screen at 2048 x 2048 and it looks good.

Thanks again:smile::smile:

---

### Post by nemodot on 2008-04-25
> **ff78 said:**
> I'm having similar issues on my machine as well, so this is quite relevant to me and my nVidia GeForce 6100.

Like i said, nvidia users: Install "nvidia-settings" from synaptic and then go to System-> NVIDIA X server Settings. Look the screenshot i uploaded.

---

### Post by nemodot on 2008-04-25
> **ff78 said:**
> I'm having similar issues on my machine as well, so this is quite relevant to me and my nVidia GeForce 6100.


Like i said, nvidia users, install "nvidia-settings" from synaptic. Then look for it in system->admin. and you'll be able to change the resolution.

I worked for me, i have a pretty noisy geforce 6600gt

---

### Post by kestrel1 on 2008-04-26
Thanks to 'hurtstotalktoyou' That sorted it out.
I think that the logon screen res needs to be in the /etc/X11/xorg.conf file as a mode, but not sure how to sort that one. I got it working on Ubuntu 7.10, so will have a dig & see if I can find the info.
Will post back if I find it.

---

### Post by xandox on 2008-04-27
The Solution to the Login Resolution can be found at [http://ubuntuforums.org/showthread.php?t=753376](http://ubuntuforums.org/showthread.php?t=753376)

First open the xorg.conf in your favourite text editor

```
sudo gedit /etc/X11/xorg.conf
```

and you should see the folling section called Screen. in the "Display" subsection there is a Modes entry and a Virtual entry in my case it was:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	**1600	1200**
		Modes		"1152x864@75"	"1280x1024@75"	"1024x768@60"	"1024x768@70"	"1280x1024@60"	"1024x768@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
```

The Virtual entry **should** be the same as the first Resolution in the Modes entry. Unfortunaty this doesn't happen. So in my case I changed it from "1600	1200" to "1152	864"

This is what my entry looked like after the edit:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	**1152	864**
		Modes		"1152x864@75"	"1280x1024@75"	"1024x768@60"	"1024x768@70"	"1280x1024@60"	"1024x768@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
```

After you've made the edit, save and reboot. Then you should see your login in it's restored state.

---

### Post by kestrel1 on 2008-04-27
I was getting close, then Xandox came up with the solution. Anyway, saved me some more work. Thanks Xandox

---

### Post by sailor2001 on 2008-04-27
most simple way   /usr/applications/screen & graffics

---

### Post by Skip Da Shu on 2008-04-28
> **hurtstotalktoyou said:**
> 
3.  Go to System > Preferences > Main Menu > Applications > Other and make sure the "Screens and Graphics" box is checked.


I upgraded one of my Xubuntu remote boxes and my "screens and graphics" option under settings is gone... any idea how to do the step 3 above in Xubuntu to get it back?

---

### Post by Killer Cop on 2008-04-28
Same problem with my nVidia card.

> **nemodot said:**
> I've found the solution!

Look on the Synaptic manager the "nvidia settings" and install it. Then look for it on System->Admin. It worked for me

I'll try that one when I get home.

---

### Post by Beatnikboy on 2008-04-29
I am also having nvidia display problems but have now managed to get the preferred resolution using the screens and graphic utility.

However, when I go system>admin>Nvidia x server settings a box pops up stating:
" You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I then typed sudo nvidia-xconfig in the terminal and get :
sudo: nvidia-xconfig: command not found.

What am I doing wrong?

---

### Post by xandox on 2008-04-29
> **Skip Da Shu said:**
> I upgraded one of my Xubuntu remote boxes and my "screens and graphics" option under settings is gone... any idea how to do the step 3 above in Xubuntu to get it back?

Rather than enabling the "Screen and Graphics" in the Menu you can use this command in terminal.

```
sudo displayconfig-gtk
```

I've had the same problem with Ubuntu Studio. The "Screen and Graphics" isn't in the "Main Menu" Preferences.

Doing this should open the "Screen and Graphics" utility. Then just continue from step for of hurtstotalktoyou's solution.

---

### Post by kestrel1 on 2008-04-29
> **Beatnikboy said:**
> I am also having nvidia display problems but have now managed to get the preferred resolution using the screens and graphic utility.

However, when I go system>admin>Nvidia x server settings a box pops up stating:
" You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I then typed sudo nvidia-xconfig in the terminal and get :
sudo: nvidia-xconfig: command not found.

What am I doing wrong?
I suspect you haven't got the Nvidia X server settings installed. To install type this in a terminal box:
```
sudo apt-get install nvidia-settings
```
The nvidia-xconfig command should then be found.

---

### Post by aaeeiio on 2008-04-29
My problem persists even after following nemodot's and hurtstotalktoyou's advice... I have Geforce 6600gt and an Acer AL1714 LCD screen.

> I suspect you haven't got the Nvidia X server settings installed. To install type this in a terminal box:
Code:

sudo apt-get install nvidia-settings

The nvidia-xconfig command should then be found. 

I have it installed and the command seems to be executed as it should, but the same error message comes again when trying to launch nvidia x server settings. In "hardware drivers" it says the newest Nvidia drivers are installed and in use.

The problem occured when updating from 7.10 to 8.04. Before it worked all fine.

---

### Post by kestrel1 on 2008-04-29
Can you post your /etc/X11/xorg.conf file. This may give a clue.

---

### Post by aaeeiio on 2008-04-29
/etc/X11/xorg.conf:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:2:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

There are files called xorg.conf.1, xorg.conf.2 and xorg.conf.3 as well... I don't know if it should be like that.

---

### Post by brigadoon on 2008-04-29
I had a NVIDIA driver with the same problem. My solution can be found at...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

I hope it helps.

---

### Post by aaeeiio on 2008-04-29
> **brigadoon said:**
> I had a NVIDIA driver with the same problem. My solution can be found at...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

I hope it helps.

Too bad I don't really understand your description of the solution. :???: (I'm a Linux noob.) And my problem isn't about black bars, but the resolution.

---

### Post by kestrel1 on 2008-04-29
What is your current screen res & what do you want it to be?
If it is what I think it is, your current resolution is set to 800 x 600, if that is the case & you want it higher, say 1024 x 768 enter that in the following line in your xorg.conf file:
```
Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"
```
So the first entry would be 1024x768@72

---

### Post by djamu on 2008-04-29
Hey aaeeiio unless you got 2 graphical cards in there ( and even then they should have different bus ID's ) this is never going to work.
I'll explain 

if you look at > Section device  ( you have it twice !! )
in the first you specify > driver "nvidia" ( leave that, that's ok )

completely remove the 2nd > Section device ( the complete section )
where you say > driver "nv" ( this is also an nvidia driver but the open source one, which you probably don't want )

Did you merge 2 xorg.conf files ?


> **aaeeiio said:**
> /etc/X11/xorg.conf:

```


.
.
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
EndSection
.
.
.
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:2:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection

```


with 8.04 beta you just had to run nvidia-xconfig, but seems that doesn't work anymore ( the very reason why I ended up here ), because my perfect good xorg.conf all of a sudden stopped working, guess the latest update ( yesterday ) aint good ..... so for now, only advice I can give you is to use my tuned xorg.conf that i'll attach here & run the "screens & graphics" applet to fix the resolution ( should work )

of what I know > nvidia-xconfig is the way the developers want to configure the screen + driver  ( that's why that screen & graphics applet is hidden )... so until there's a fix for nvidia-xconfig > here's my xorg... 

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

# xorg.conf (X.Org X Window System server configuration file)
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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
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
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by Skip Da Shu on 2008-04-29
> **xandox said:**
> Rather than enabling the "Screen and Graphics" in the Menu you can use this command in terminal.

```
sudo displayconfig-gtk
```

I've had the same problem with Ubuntu Studio. The "Screen and Graphics" isn't in the "Main Menu" Preferences.

Doing this should open the "Screen and Graphics" utility. Then just continue from step for of hurtstotalktoyou's solution.

Duh... The light should of gone on when I found out that this is what "Screens & Graphics" executes.  Thanx for getting me back on the path.  My immediate problem wasn't really what this thread was about but more around how X11vnc reacts to machines that have been rebooted w/o a monitor on them and that all seems to tie back to xorg.conf.  I've actually got the original two machines that were giving me grief working as desired from remote via edits to xorg-conf (modified resolution & scan rate entries, less of them and added the virtual entry)

But I'm glad to have this as it allows me to "realtime" display what is actually running including the driver being used.  I just tried it on both a Xubuntu v7.10 and v8.04 machine.  Works like a champ. It shows the v8.04 machine at 1280x1024@61Hz, using vesa driver (61?... was supposed to be 60 but close 'nuff for me) which is what is in xorg.conf and working.  

Thanx Xandox,
Skip

---

### Post by jimoz on 2008-04-29
Thanks for your help.

Screen res spot on now, had some trouble with nvidia drivers in gutsy, working beautifully now. One note - did have some trouble with the login screen, couldnt get it to display at native 1280x800 - tried manipulating xorg.conf etc but would not work. Turns out, if you just switch login to plain, and then back again, it sorts the login res out for you. See this link:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/16472](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/16472)

---

### Post by tjpatton on 2008-04-30
> **kestrel1 said:**
> Sorry, forgot to mention that I had already done that one. Max resolution is the same 800 x 600.
I installed the restricted drivers for my Nvidia card & the max resolution I got then was even worse 640 x 480
Any other thoughts?

This is very frustrating because I have the same situation here.  Odd thing is that when I had 7 it recognized the card and LCD, but that's not happening in 8.  All the drivers have been installed, but yet when I attempt to change the resolution it's a no go.  For some odd reason it wants to recognize my Dell LCD as a CRT.  WTF is that all about?  I've read over all of your postings but I'm still coming up empty.  Tough looking at a monitor that is 640 x 480.  Tim

---

### Post by bouss on 2008-04-30
Problem is in ati as well (changing resolution from system menu has no affect)... anyone can help on that too?

---

### Post by kestrel1 on 2008-04-30
Have you used the Screens & Graphics application?
Go through this ppost by hurtstotalktoyou: [http://ubuntuforums.org/showthread.php?t=766846&page=2](http://ubuntuforums.org/showthread.php?t=766846&page=2)

---

### Post by kestrel1 on 2008-04-30
Have you used the Screens & Graphics application?
Go through this post by hurtstotalktoyou: [http://ubuntuforums.org/showthread.php?t=766846&page=2](http://ubuntuforums.org/showthread.php?t=766846&page=2)

---

### Post by bouss on 2008-04-30
Changes in screen and graphics menu are not saved and when system restarts all changes are lost. The real problem is that system > preferences > screen resolution changes don t take effect even if the system asks you whether to keep new settings or not (as if something changed). This is weird and I hope someone can give some working solution. I hate having all my buttons moving left and right changing resolutions...

---

### Post by tjpatton on 2008-04-30
I FINALLY got it to work using hurtstotalktoyou method.  Thanks Mr. Hurt.  I didn't get it to work the first time because when he said "Don't us plug & play" I took him literally and didn't touch it.  Duh...  After I did it all came into play.  The welcome page is a bit screwed up with the sign on down in the right hand corner, but I really don't care about that.  As opposed to seeing Ubuntu I see Ubunt.  Works for me, see ya later Bill Gates!

---

### Post by kestrel1 on 2008-04-30
tjpatton:
To get the login screen sorted you need to reconfigure your xorg.conf file & it is fairly easy to do.
Try this:
```
sudo gedit /etc/X11/xorg.conf
```
Once your xorg.conf file opens scroll down the page until you reach a section like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1152	864
		Modes		"1152x864@75"
	EndSubSection
```
behind Virtual you need to change the values to be the same as your current screen res. If you notice above 'Modes' is set to 1152x864@75 That is the current screen res. Changing 'Virtual to be the same as your first 'Modes' entry that should sort it out. Note: you only need the numbers, see 'Virtual' above for example. Don't forget to save the file.
I think a simple logout will sort the settings out.
Hope that helps.

---

### Post by aaeeiio on 2008-05-01
Problem is still unsolved. I'll try to explain how it went...

I replaced the xorg.conf according to djamu's advice, after which I got the option to change resolution through "screens and graphics" to the normal 1280x1024. It said it needed a restart, so I did it. The login screen appeared at the proper high resolution, which made me hopeful, but when logged in the picture was totally messed up. :confused: The cursor and everything else appeared simultaneously like six times. I could barely navigate through the menus by memory but couldn't read the texts... I took a screenshot, but in it all appears as if it worked normal.

I tried restarting through recovery mode, and from there used something like "fix X server". When I was logged in I could succesfully switch the resolution to 1280x1024. Although the display was just defined as "plug 'n play" and the nvidia driver wasn't in use, I was happy it worked decently again.

Too bad that upon restart I get the same old error, which in English would be something like "The display and video card could not be defined. The display settings need to be set manually." :neutral: And, as always, manually setting it up won't help at all, and I'm back in the grainy 800x600...

Maybe I'm doing something silly. Any help?

---

### Post by aaeeiio on 2008-05-01
> **kestrel1 said:**
> What is your current screen res & what do you want it to be?
If it is what I think it is, your current resolution is set to 800 x 600, if that is the case & you want it higher, say 1024 x 768 enter that in the following line in your xorg.conf file...

I tried this as well, but nothing changed.

---

### Post by djamu on 2008-05-01
to aaeeiio

if your unable to get in your desktop > ctrl+alt+F1 can be a livesaver 
to get back to your desktop > ctrl+alt+F7, to reset the display server without having to reboot ctrl+alt+backspace  ( not delete but the one above return, assuming your not on a laptop), can you post some specs too? ( grahical card type / monitor type / keyboard layout language )
can you repost your current xorg.conf? ( the one that got altered after inserting mine )
as said in the future everyone should use the nvidia-xconfig command which seems to be broken ... ( since 2 days ), worked fine in the beta, my original xorg.conf was generated by it.. 
tell me what screen resolution you want it to be, i'll make you a working xorg.conf

are you using a dual screen setup ?
you can install the EnvyNG package which makes sure you have all the tools installed, i'll take a look why the new standard tool isn't working properly anymore...

---

### Post by djamu on 2008-05-01
K I figured it out


short howto, should work for everyone & the fix is as unlikey as it is logical..
( this will NOT work for very old monitors )
because of the seemingly broken plug'n play I suddenly thought that rebooting the computer will not solve the fact that the monitor doesn't provide correct info... ( the monitor provides the grahical card with it's features, rebooting will not correct that, but completely powering off the monitor -pulling out the powerplug- will > plug'n play )

Do not use that screens & grahics stuff again after this.. just forget that it exists, instead use > System > Preferences > Screen resolution ( your monitor will work plug & play ) or the nvidia-settings panel

so here's what i did...
make sure you install proprietary drivers first > reboot >  put my minimal xorg.conf in /etc/X11/ > Halt the computer > remove all powerplugs ( also from the monitor !!! ) let it settle for a minute so all caps decharge properly > reconnect power plug from monitor > reconnect power from computer > boot > FIXED

:KS

for sake of completeness i'll add my xorg.conf again here ( you might need to change the keyboard layout )

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load            "v4l"
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
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

 have fun

:lolflag:

---

### Post by bouss on 2008-05-02
What about us with ati cards? Any idea to make it use the resolution we want and make system > screen resolution menu work properly?

P.S. Though the addition of virtual+resolution worked for me giving me a stable resolution every time I start the computer. Screen is EIZO F520, graphic card is ATI Radeon 9250.

---

### Post by aaeeiio on 2008-05-02
> **djamu said:**
> to aaeeiio

if your unable to get in your desktop > ctrl+alt+F1 can be a livesaver 
to get back to your desktop > ctrl+alt+F7, to reset the display server without having to reboot ctrl+alt+backspace  ( not delete but the one above return, assuming your not on a laptop), can you post some specs too? ( grahical card type / monitor type / keyboard layout language )
can you repost your current xorg.conf? ( the one that got altered after inserting mine )
as said in the future everyone should use the nvidia-xconfig command which seems to be broken ... ( since 2 days ), worked fine in the beta, my original xorg.conf was generated by it.. 
tell me what screen resolution you want it to be, i'll make you a working xorg.conf

are you using a dual screen setup ?
you can install the EnvyNG package which makes sure you have all the tools installed, i'll take a look why the new standard tool isn't working properly anymore...

At the moment I need to boot through recovery mode and "fix X server" every time in order to get the proper resolution.

```
# xorg.conf (X.Org X Window System server configuration file)
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
	Option		"XkbLayout"	"fi"
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
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Graphics card is nVidia Geforce 6600GT, my display is a 17" LCD (1280x1024) and I use the Finnish/Scandinavian keyboard layout.
I have only one screen.

And I can't follow your latest advice, djamu. For some reason I see no component (the graphics card) listed at all in system > admin > proprietary drivers, although I previously did. I removed some nVidia driver stuff through Synaptic to try and see if it changes anything, so I suppose it has to do with that. Now I just don't know how to get it back. :???:  I'm slightly losing my hope with this whole hassle.

"Proprietary drivers are not used in this computer."
[[IMG]http://img370.imageshack.us/img370/5070/kuvakaappauslaiteajuritpy8.th.png[/IMG]](http://img370.imageshack.us/my.php?image=kuvakaappauslaiteajuritpy8.png)

---

### Post by Skip Da Shu on 2008-05-02
I've been working on an xorg.conf that I can just copy and use on 8 different Xubuntu v8.04 machines, a Xubuntu v7.10 machine and an Ubuntu v7.10 desktop.

I'm not quite there yet but getting close...  so far this works on a couple makes of mobos with Nvidia GE6100 onboard video and Intel GMA X3100 onboard video (Gigabyte boards) with any of 3 different LCD panels I've tried.

```

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280  1024
		Modes	"1280x1024@60"	"1024x768@70"	"800x600@72"	"640x480@75"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by djamu on 2008-05-03
to Skip Da Shu:

This will work on every machine since it uses the VESA driver.. so alas no hardware acceleration ( no OpenGL / Compiz goodness )


to aaeeiio:

1 question though, in some cases an onboard graphical card ( on the motherboard ) might interfere with the added one, make sure you disable it in the BIOS. ( you can try re-enabling it later on )

To make sure you got everything installed > install ( thru synaptic ) the EnvyNG  ( envyng-gtk for ubuntu gnome / envyng-qt for kubuntu kde ) package 
after installation ( also include any updates available ) click > application > system tools > EnvyNG > choose latest driver ( ATI / NVIDIA ) install > reboot > if things still don't work conclude with following my previous post , & you should be set...

If after this things still don't work ( including resetting the monitor by unplugging the power )....  well in linux there's nothing unfixable, but if your new to linux you might be fixed quicker doing a brand new install... ( after the unplugging stuff ), maybe an important config file got altered unknowing to you.... 




:-)

---

### Post by Skip Da Shu on 2008-05-03
> **djamu said:**
> to Skip Da Shu:

This will work on every machine since it uses the VESA driver.. so alas no hardware acceleration ( no OpenGL / Compiz goodness )
:-)

Badness for me!  ;-) With the exception of the 1 Ubuntu desktop these are remote dedicated number crunchers and don't have monitor, keyboard, mouse on them most of the time...just X11vnc server running on them for remote access.  So my primary mission is to make VNC happy.  In the past I've had the remote screen res change on me using the hardware drives depending on whether the machine last booted with monitor connected or not... Still trying to figure out WHY that is.

I'll try changing the vesa driver to one of the nvidia drivers on the desktop just for grins (nvidia 410 chipset with GE6100) although the user of that machine doesn't play 3D games (and is still complaining that Ubunutu will not let her play "Party Poker" online!)

Thanx, Skip

---

### Post by aaeeiio on 2008-05-04
I'm still stuck in 800x600 after installing the drivers through EnvyNG, rebooting and (when found it won't work) then replacing xorg.conf and halting the computer and then removing the (power and VGA) cables for a good while.

Oddly system > admin > prop. drivers still won't show anything, although I did install the drivers.

I suppose I'll start backing up files to do a clean reinstall. Anyhow I appreciate your effort, djamu.

---

### Post by rohan21 on 2008-05-04
i have the same issue my resolution is 800 by 600. i installed nvidia-settings and then changed the resoluton to 1024 by 768 and clicked apply- i got the right resoution but when i choose to save the file - it doesn't allow me to do so saying that it cannot save the backup file -- so i have to change my resolution every time i login --- any help is very much appreciated

---

### Post by kestrel1 on 2008-05-04
rohan21: You need to run the NVidia settings as a root user, so that you have access to write to the correct folder. to do this type the following in a terminal window:
```
sudo nvidia-settings
```
Then you can save the file & you should be okay.

---

### Post by Normank on 2008-05-04
Many thanks
worked for me also.

---

### Post by djamu on 2008-05-04
I just updated kernel to 2.6.24-17 > screen jumped back to 800x600 on reboot.
After halting, disconnecting all power cords ( both computer & VGA ) & reboot, resolution was normal again. 

I'll post a bug report if anyone can confirm this, seems there's really something wrong with the plug'n play detection.  ( i'm using the minimal xorg.conf posted earlier )

Problem is that if it's the Nvidia driver, it's unlikely there will be a fix....

:neutral:  it's just a minor bug, but annoying enough...

---

### Post by aaeeiio on 2008-05-05
I installed 8.04 from fresh and now all works smoothly. Reinstalling the whole system wasn't such a big task after all.

I will now however think twice about updating when 8.10 comes out...

---

### Post by winzar on 2008-05-07
Demonstrating my complete incompetence with things Linux/ Unix...  But seriously trying to learn to escape from the MS hegemony.

I've just installed Xubuntu on an aging Toshiba Satelite Pro 4600 and I have the same problem as others with the default 800x600 resolution.
HurtsToTalkToYou has been exceedingly generous with his instruction.
Now here's where I show my incompetence:
Where do I find the 

System > Preferences >

or 

System > Administration >

I'm in the regular login.  Does that make a difference?  If so how do I log in as Administrator?

Thank you all for yor patience.

---

### Post by philinux on 2008-05-07
You'll have to poke about in xubuntu's menus system>prefs is gnome ie ubuntu.

---

### Post by Skip Da Shu on 2008-05-07
> **winzar said:**
> Demonstrating my complete incompetence with things Linux/ Unix...  But seriously trying to learn to escape from the MS hegemony.

I've just installed Xubuntu on an aging Toshiba Satelite Pro 4600 and I have the same problem as others with the default 800x600 resolution.
HurtsToTalkToYou has been exceedingly generous with his instruction.
Now here's where I show my incompetence:
Where do I find the 

System > Preferences >

or 

System > Administration >

I'm in the regular login.  Does that make a difference?  If so how do I log in as Administrator?

Thank you all for yor patience.

These two Ubuntu menus are covered in Xubuntu with 

Applications -> Settings -> Settings Manger

and / or

Applications -> System

I had the same Ubuntu to Xubuntu xlate problem when I first "converted" and still run into it more than I'd like to admit.

Lemme know if you need something more specific.

Skip

---

### Post by Motorhead Kaze on 2008-07-01
**[COLOR="Purple"][SIZE="4"]Hurtstotalktoyou[/SIZE][/COLOR]**, OH WOW you RULE!

After a reinstall of Hardy, I lost my dual monitor setup and Ubuntu just would NOT see my second monitor, and I could not get it off cloned output, even after my edits in xorg.conf.  It was the god-flabergasting propriety driver that was keeping Ubuntu/Hardy from recognizing that second monitor.

It is 11pm, and I have spent roughly 10 hours of the day trying MANY things to get my dual monitors to work.  You did it, whether it was your original idea or not, your post is what I found.

Big thanks to you.

---

### Post by BLTicklemonster on 2009-01-24
Skip Da Shu, thank you. I had a pci-3 video card in my machine, but my son was having a tough time playing some games on his onboard card on his machine, so I gave up my card and went back to the onboard Nvidia gf6100 and could only get 640x480 out of nvidia "uncool" drivers, and 800x600 with vesa. Thanks to you I can get 1024x768. It's not as good as before, but with my flat panel, it's a lot better for sure! I'm ordering a new pci-e card tomorrow, so in the meantime this fix you posted for xorg.conf did the trick. Shame the thank you button is only set for like 5 minutes (something the admins ought to reconsider if you ask me).

---

### Post by CrazyG on 2009-01-25
Thanks to all who contributed to this thread, I have fixed my screen resolution in Hardy to the correct resolution using the Nvidia X Server Settings.  My login resolution was huge, so I just changed to the plain login and this works.

I have a ViewSonic G75f CRT, the manual recommends 1024X768 with refresh rate of 75.  I currently have 1024X768 with refresh rate of 88, which is ok, it is still under the maximum refresh rate for this monitor.  It wouldn't allow me to choose 75 for the refresh rate.

---

### Post by Skip Da Shu on 2009-01-26
> **CrazyG said:**
> ...edited out....
I have a ViewSonic G75f CRT, the manual recommends 1024X768 with refresh rate of 75.  I currently have 1024X768 with refresh rate of 88, which is ok, it is still under the maximum refresh rate for this monitor.  It wouldn't allow me to choose 75 for the refresh rate.
I believe is you change this portion of your xorg.conf:
```
SubSection "Display"
		Depth	24
		Virtual	1280  1024
		Modes	"1280x1024@60"	

```
Replacing - 
"60" w/ "75" 
"1024" w/ "768", 
"1280" with "1024"  

it'll come up in a default resolution of 1024x768@75.

Will require at least a logout/login to take effect (maybe a reboot, not sure and too early in morning for brain to think this out).

---

### Post by fixitdude on 2010-01-02
The automated screen setup is OK, but only if the developers make a easy to find and use tool for changing it manually.

Like for instance, I am setting up a friends computer at home using my large monitor, he has a small one so I want to do everything at his resolution so when I got over there with the computer it's ready to go and all icons on the desktop are in the right places.

IT'S A PAIN!!!

So here's some answers after hours of messing around:

If you lost "Monitor and Display" in KDE, or don't have the "System Settings" menu, you need to install the Kubuntu stuff and it suddenly appears. The normal "kde" install doesn't supply it, as if you won't ever need it, WHATEVER!

Just install this package (you can use Synaptic to do this too):

sudo apt-get install kubuntu-desktop

If it asks, you want to use the "kdm" manager, not "gdm".

And if you don't see "System Settings" on your menu after installing Kubuntu, try this

sudo apt-get install systemsettings

Now go to "System Settings" --> "Monitor and Display" then set things as you like.

Another thing I found that will put manual setting stuff into /etc/X11/xorg.conf is this, but don't use it to "test" you can only say "OK" and then reboot so it loads the new xorg.conf:

sudo displayconfig-gtk

I would only use the last one as a last resort, and save a copy of your xorg.conf before you use it just in case.

The below little command might save you, it should reset the xorg.conf and also don't forget you can hit "ESC" at boot, get to the grub menu, boot as "recovery" and select "xfix", that might help too.

sudo dpkg-reconfigure -phigh xserver-xorg

If the developers are listening please make changing screen res easy for ALL users.

Good luck. I was pulling my hair out on this one.

---

