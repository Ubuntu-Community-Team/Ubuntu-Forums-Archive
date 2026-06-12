---
title: "Dual Monitor"
date: 2006-08-20
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-08-20
[img]http://www.oneposter.com/UserData/Poster/Poster_5674.jpg[/img]**[SIZE="6"]How to Dual Monitor.[/SIZE]**


[SIZE="3"]I will focus on light desktops: Fluxbox, Openbox, and IceWM with two monitors.This works well with KDE, GNOME, and XFCE as well.[/SIZE]

[color=darkred][size=2]_Note_: This how-to works on Dapper, Edgy, and Feisty Fawn with the newest nVidia beta drivers.[/color][/size]

_Note_: I wrote a simple bash script to start your dual monitors from a GUI.

See here:

[[size=2][color=blue]Dual Monitor GUI[/color][/size]](http://ubuntuforums.org/showthread.php?t=271045)

Edit: I changed the names of the servers the names of the servers in the script. I will edit my example xorg.conf example in this post. I left the attached xorg.conf as is as this is a template only. 

This is NOT another how to on twinview or xcinerama.
If that is what you want, see here:

[How to Twinview](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=twinview)

[Twinview Options](http://wiki.arslinux.com/Twinview)

[How to Xinerama](https://help.ubuntu.com/community/XineramaHowTo)

Twinview/xicnerama work well enough with the "big three" (KDE/Gnome/XFCE), but I am interested in a lighter weight desktop (Fluxbox, Openbox, IceWM).

**Here is a nice How-to on "dual monitors"** [Dual Monitors](http://doc.gwos.org/index.php/DualMonitors)
_Note_: This wiki page is a more detailed overview of multiple monitors, configuration of X, and is an adaptation from the Gentoo wiki.

What do I mean the by Dual monitor? Two "independent" monitors. The mouse can move freely beetween the monitors, but you can not drag a window  or application from one window to another. (Twinview/xcinerama is described as "One large monitor").

Preamble;
> 1. **Graphic card = nVidia**. If others want to add OK, but I only know so much. With that said, most of this should work with just about any graphics card.

Edit: [color=darkred]Here is a link of ATI cards:[/color]
[Dual Monitor set up with ATI AIW9600](http://www.ubuntuforums.org/showthread.php?&t=317682)
[color=blue] Thank you to **XPuntu**[/color]

2. I boot to the command line (CLI) and start these window managers from the command line (not KDM/GDM/XDM). I will include examples of start scripts. These scripts work better for me at least partially because I do not know how to configure GDM/KDM/WDM/XDM to start the dual monitor X server.

If you, like most, boot to GDM/KDM/WDM/XDM you do NOT need to change the way you boot. Use Ctrl-Alt-F1 to get to your CLI on tty1.

3. Twinview is the server configuration that gives 1 large desktop across two monitors and is the most "popular" configuration. This "How to" focuses on setting up what I call Dual Monitors, but Twinview remains the default behavior so you may have the best of both worlds and change between the two configurations at will (requires a re-start of X, and thus your desktop manager to change).

4. I will use Dual monitors for Fluxbox/Openbox/IceWM. This is two independent monitors. You can move the mouse freely between the monitors, but not drag windows between them (as you can in Twinview).

5. The main reason for the "Dual monitor" approach  is Twinview/xcinerama is it does not always work well. Panels may be stretched across two windows (Fluxbox, IceWM), applications may start in the middle of the two screens, Background images are variable, etc..

6. The majority of this How  to is configuration of X in /etc/X11/xorg.conf. There is, however, no automatic configuration tool.

7. In this How to, all commands to be entered either at the terminal or CLI start with a #.

8. I advise writing xorg.conf from within X using gedit (copy and paste). You can cut-and paste to vi or nano if you prefer.

9. You must know the technical specifications for your monitors. If you do not know this, Google now and write down the address of the relevant web site (you will need it later).

10. You will be able to cut-and-paste most of my xorg.conf. when following this How to, but some sections must be configured BY YOU. in addition you may desire a few different options.

11. This xorg.conf will give you three options for X: Twinview, Dual monitors, and a third to start a single monitor.

12 I posted my current Ubuntu xorg.conf  at the bottom of this How to so you may see what the finished product will look like.


**[SIZE="2"]Overview of how it works:[/SIZE]**
From the CLI, to start a window manager
```
# startx /usr/bin/name_of_window_manager -- :2 -layout SERVER_NAME
```
1. Note the space between startx and /usr/bin/...
2. Use full path to the window manager.
3. The -layout option tells X which server configuration to use. The server configurations are in xorg.conf (/etc/X11/xorg.conf) [See below].
4. The -- :2 option starts X on a virtual terminal. Just like the CLI, you can run multiple instances of X at the same time, up to 4, more if you tweak your configuration.

Ctrl-alt-F7 for first instance of X 
Ctrl-alt-F8 for second instance of X

Numbering of screens starts with 0.
Thus the first X session is 0. The first monitor is also 0 The second monitor is 1.
Thus :0.0 refers to the first monitor on the first X session.
:0.1 is the second monitor on the first X session.
:1.0 is the first monitor of the second X session......

**[SIZE="2"]Paths to various window managers:[/SIZE]**
> Fluxbox:   /usr/bin/fluxbox
Openbox:	/usr/bin/openbox
IceWM:	/usr/bin/icewm-session
XFCE: 	/usr/bin/xfce4-session
GNOME:	/usr/bin/gnome-session
KDE:		/usr/bin/startkde

**[SIZE="2"]A quick note on other "light" desktop environments:[/SIZE]** Fluxbox has a nice menu and transparency options and in my opinion is best. IceWM is also very nice, lots of settings and configuration options. Openbox is about as bare bones as I get. Each has it's advantages. There are how-to's on the Ubuntu and Debian forums for these window managers.

There is a very nice How-to for Icewm on the Debian forums (Thank you Lou):

[Debian How to IceWM](http://forums.debian.net/viewtopic.php?t=5450&highlight=configure+icewm&sid=d98a2e6680fc6ef6276446ed4225d6b8)

**[SIZE="2"]The "problems" with twinview/xcinerama and light desktops are:[/SIZE]** With wallpapers and panels stretched across both screens (not as problematic in Gnome, KDE, XFCE, or IceWM) and windows opening in the middle of the two monitors , split across both screens. You can make a large, dual monitor wallpaper with GIMP. **[SIZE="2"]Advantage of Twinview [/SIZE]**is you can drag windows between both monitors.

**[SIZE="2"]Most of these problems are solved with using what I am calling "Dual monitors", but you lose the ability to drag windows between monitors.[/SIZE]**

**[SIZE="2"]On the subject of panels: [/SIZE]**You can of course launch kicker, gnome-panel, or the XFCE panel. These all work, although I have had problems with kicker outside of KDE.

There are several light panels and If I have the energy I will write (briefer) how to's on some of these panels. fbpanel is, again in my opinion, the best and most easily customized (fbpanel is NOT related to fluxbox) and it allows transparency. perlpanel is also VERY NICE, but no transparency. pypanel is nice and also allows transparency BUT it does not seem to work for me (crashes) with multiple monitors .

**[SIZE="4"]OK, now for the hard stuff. [/SIZE]**

The bad news is you will have to configure X for yourself. The good news is you can follow this template.

First, install the nVidia driver and configure X for twinview with the Nvidia driver. This part is fairly straight forward and is covered elsewhere both in the Ubuntu forums and elsewhere. This will give you a "basic" xorg.conf on which to build. This approach should work with other graphics cards and drivers just fine (no guarantees....). The idea is to start with a working xorg.conf  using twinview/xicnerama and whatever drivers/settings work with your monitors, keyboard, and mouse. (the open drivers for nVidia card do not work with my card, thus I use the nVidia driers).

I will also not cover installation or configuration of Fluxbox, openbox, icewm, XFCE, panels, etc in any further detail.

**[SIZE="4"]Now the fun begins:[/SIZE]**

1. Backup your xorg.conf
```
# cd /etc/X11
# sudo cp xorg.conf xorg.conf.org # .org for "original" working copy
```

2. Edit xorg.conf. As is, xorg.conf  is not well commented. We will change that.
```
# sudo gedit /etc/X11/xorg.conf
```
Note: I used gedit as it seem popular on Ubuntu. I use leafpad. Use what editor you like.

**[SIZE="4"]I have posted my entire xorg.conf below (as a text file) and will go through each section here.[/SIZE]**

[SIZE="2"]Section 1: Starting comments.[/SIZE] This is a representation of our hardware. Change it to reflect yours. For example your mouse may be USB rather then a PS2 port, what are your monitors and where do they sit?, etc. You will find some of the information in your existing xorg.conf, this serves as a quick reference.

> ##############################################################################################
#
# X O R G . C O N F
#
#  My ... Hardware:
#
#
#   .---. .---.             1 - 'IBM P202'
#   | 1 | | 2 |             2 - 'DELL P1110'
#   ø---ø ø---ø
#     |     |
#     |     |
# .--+-------+--.
# |  | card  |  |        card - '7600gt' aka 'e-GeForce 7600-GT'
# |  +-------+  |	 bus ID - PCI:1:0:0
# |             |
# |             |
# |             |
# |  +-------+  |
# |__|PS_Port|__|
#    |       |
#   kbd    mouse          kbd - 'microsoftmulti'
#                       mouse - 'ExplorerPS/2'
#
#
#  to start an xserver with a special layout:
#
#    startx /usr/bin/fluxbox -- :1 -layout LAYOUTNAME
#
#  available layouts:
#
#    TWINVIEW  - uses nvidia-driver-xinerama support
#    **DUAL      - 2 seperated screens  <-- EDIT NOTE NAME CHANGE**
#    **FAIL      - uses a single monitor  <-- EDIT NOTE NAME CHANGE**
#

[SIZE="2"]Note: This section looks much nicer as a text file then on the Ubuntu forums. [/SIZE]

[SIZE="2"]Section 2: Files section.[/SIZE] Do not cut and paste my files section. Use your current section as is.

> # **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************
# This section is unique to each version of Linux
# **********************************************************************

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

[SIZE="2"]Section 3: Server flags, modules, and extensions.[/SIZE] This section sets the global options for the X server. You should be able to use mine cut-and-paste. Make note or your original settings.

> # **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"
	Option		"DefaultServerLayout"  "twinview"
	Option		"AllowDeactivateGrabs" "true"
	Option		"AllowClosedownGrabs" "true"
	Option		"AllowMouseOpenFail" "true"
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"
	Load "dbe"  	# Double buffer extension
	SubSection "extmod"
	Option "omit xfree86-dga"   # don't initialise the DGA extension
	EndSubSection
	Load "type1"
	Load "freetype"
	Load "glx"
	Load "record"
	Load "evdev"
	Load "xtrap"
#	Load "extmod"
#	Load "v41"
#	Load "speedo"
#	Load "bitmap"
#	Load "ddc"
#	Load "dri"
#	Load "int10"
#	Load "vbe"
EndSection

#Section "Extensions"
#	Option "Composite" "Enable"
#EndSection


[B]DO NOT forget the following line in Server Flags.
Option      "DefaultServerLayout" "twinview" [/B]

Several Modules are included for reference, but commented out. Use them (uncomment) if you need them. If you are unsure, leave this section alone.

[SIZE="2"]Section 4: Input section.[/SIZE] This configures your keyboard and pointer (mouse/touchpad). Do not cut and paste mine but rather use your own sections as is.

> ##############################################################################################
#
# I N P U T - SECTION
#
#  keyboards and mice are handled here
#
##############################################################################################

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************
Section "InputDevice"
	Identifier	"Keyboard1"
	Driver		"kbd"
	Option		"AutoRepeat"    "500 30"
	Option		"XkbRules"      "xorg"
	Option		"XkbModel"      "microsoftmulti"
	Option		"XkbLayout"     "us"
#	Option		"XkbVariant"    ""
#	Option		"XkbOptions"    ""
EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"
	Identifier	"Mouse1"
	Driver		"mouse"
	Option		"Device" "/dev/input/mice"
	Option		"CorePointer"
	Option		"Protocol" "ExplorerPS/2"
	Option		"Emulate3Buttons" "False"
	Option		"Buttons" "7"
	Option		"ZAxisMapping" "4 5 6 7"
EndSection

[SIZE="2"]Section 5: Monitor section.[/SIZE] Again, use my sections as a template, but update:
> VendorName
ModelName
HorizSync
VertRefresh

to reflect your monitors.

Also update the web site where you found your sepcs in the comments sections. (Section 1).

> ##############################################################################################
#
# DELL P110 = Monitor 1
#
# sepcs at [http://www.Add_your_monitor's_web_site_here](http://www.Add_your_monitor's_web_site_here).
#
##############################################################################################

Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"DEL"
	ModelName	"DELL P1110"
	HorizSync	29-121
	VertRefresh	50-180
EndSection


#
##############################################################################################
#
# IBM P202 = Monitor 2
#
# sepcs at [http://www .Add_your_monitor's_web_site_here](http://www .Add_your_monitor's_web_site_here).
#
##############################################################################################

Section "Monitor"
	Identifier	"Monitor2"
	VendorName	"IBM"
	ModelName	"IBM P202"
	HorizSync	30-107
	VertRefresh	50-160
	Option		"DPMS"
EndSection

[SIZE="2"]Section 6: Server section.[/SIZE]This sets up options for X. It sets up 3 devices and (X server) layouts, each setup is different. The setups are twinview, dualscreen, and Dell. I encourage you to change the name of "DELL" to the name of your first monitor.
> # **********************************************************************
# Server section
# **********************************************************************

# **********************************************************************
# Graphics device section
# **********************************************************************

#
##############################################################################################
#
# T W I N V I E W - S E T U P (NVIDIA)
#
#  Monitor1 and Monitor2 are both connected to the same (nvidia) videocard
#  activates the nvidia-twinview-mode
#
#    advantage: opengl on both windows
#    disadvantage: cant get 1600x1200 on each monitor, it seems that both
#                     screen must have same refreshrates
#                  no xv for mplayer

Section "Device"
	Identifier	"twinview"
	VideoRam	256000
	VendorName	"nVidia Corporation"
	BoardName	"Video device"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"TwinView"
	Option		"MetaModes" "1600x1200,1600x1200"
	Option		"TwinViewOrientation" 	"LeftOf"
	Option		"SecondMonitorHorizSync""UseEdidFreqs"
	Option		"SecondMonitorVertRefresh" "UseEdidFreqs"
	Option		"HWCursor"		"On"
	Option		"UseEdidFreqs"		"true"
	Option		"NvAGP" "1"
#	Option		"NoLogo"		"true"
#	Option		"RenderAccel"		"true"
#	Option		"CursorShadow"		"true"
#	Option		"XvmcUsesTextures"	"true"
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

Section "Screen"
	Identifier	"twinviewscreen"
	Device		"twinview"
	Monitor		"Monitor1"
 
   DefaultDepth 24
   
    Subsection "Display"
        Depth       8
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"
	Identifier	"TWINVIEW"
	Screen		"twinviewscreen"
	InputDevice	"Mouse1" "CorePointer"
	InputDevice	"Keyboard1" "CoreKeyboard"
Endsection

#
##############################################################################################
#
#  D U A L M O N I T O R - S E T U P (NVIDIA)
#
#  crt0 and crt1 are both connected to the grafic card. we create a pseudo
#  device that points to the same graficcard.
#
#  advantage: we can get 1600x1200 on both displays, both screens can have
#             different refresh resolutions, rates, depths etc etc
#             xv works again (brightness etc for mplayer)
#             opengl on both monitors
#  disadvantage: no exchange of windows between those 2 screens.
#


Section "Device"
	Identifier     "Videocard1"
	VideoRam  256000
	VendorName  "nVidia Corporation"
	BoardName   "Video device"
	Driver     "nvidia"
	BusID       "PCI:1:0:0"
	Screen 0
        Option "HWCursor" "On"
        Option "UseEdidFreqs" "true"
        Option "NvAGP" "1"
EndSection

Section "Device"
	Identifier     "Videocard2"
	VideoRam  256000
	VendorName  "nVidia Corporation"
	BoardName   "Video device"
	Driver     "nvidia"
	BusID       "PCI:1:0:0"
	Screen 1
        Option "HWCursor" "On"
        Option "UseEdidFreqs" "true"
        Option "NvAGP" "1"
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

Section "Screen"
    Identifier  "Screen 0"
    Device      "Videocard1"
    Monitor     "Monitor1"
 
   DefaultDepth 24
   
    Subsection "Display"
        Depth       8
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "Videocard2"
    Monitor     "Monitor2"
 
   DefaultDepth 24
   
    Subsection "Display"
        Depth       8
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"
**     Identifier      "DUAL"     <--- EDIT NOTE NAME CHANGE**   
     Screen      0  "Screen 0" 0 0
     Screen      1  "Screen 1" LeftOf "Screen 0"
     InputDevice     "Mouse1" "CorePointer"
     InputDevice     "Keyboard1" "CoreKeyboard"
EndSection

#
##############################################################################################
#
#  D E L L P1110 - S E T U P
#
#  setup to have a xserver on the iiyama display alone
#
# device for crt0


Section "ServerLayout"
**	Identifier  "FAIL"     <--- EDIT NOTE NAME CHANGE**
	Screen      0 "Screen 0"
	InputDevice     "Mouse1" "CorePointer"
	InputDevice     "Keyboard1" "CoreKeyboard"
#	Option      "Offtime" "10"
EndSection

Watch your:
1. Amount of  video ram. You may have more or less.
2. VendorName.
3. BusID. Do not use mine, but check the BusID in your xorg.conf..
4. Metamodes. I use a resolution of 1600x1200. You man need to reduce this to reflect your monitors and preferences. ? "1280x1024,1280x1024". I believe you can have different resolutions on each monitor if you like ie "1600x1200,1280x1024"
5. Default depth. I use 24, you may want to change this.
6. You may need to change TwinViewOrientation to "Rightof"
7. If you do not want to see (or do not use) the nVidia logo uncomment the "noLogo" line. I left it for now so you will have confirmation you are using the nVidia driver.
8. Ditto with other options.
9. In your modes sections you can use modlines if you like. If you do not know what a modline is, do not worry about it for now. 
10 NOTE DUALSCREEN and DELL are ALL-CAPS.

Save your changes and exit gedit.

Back up your new xorg.conf.
```
# sudo cp xorg.conf xorg.conf.bak
```

You should be good to go.


**[SIZE="4"]Now the moment of truth !![/SIZE]**

To start a desktop:
```
# startx /usr/bin/path_to_window_manager -- :2
```
This will start you in the default, **twinview mode**.

**For fluxbox with dual monitors use the layout flag:**
```
# startx /usr/bin/fluxbox -- :2 **-layout DUAL**
```
**EDIT Note name change.**

**Welcome to Fluxbox on Dual monitors.**

To start fluxbox, Single Monitor::
```
# startx /usr/bin/fluxbox -- :2 **-layout FAIL**
```
**EDIT Note name change.**

This will start fluxbox with a single monitor.

**[size=3]EDIT These scripts are outdated and are incorporated in the bash script.[/size]**

I left these scripts as examples.

**[SIZE="2"]Scripts:[/SIZE]**

As I said, I launch my windows managers from the CLI, no KDM/GDM/XDM here.

If you boot to say GDM you, no problem. just Ctrl-Alt-F1 to tty1, log in, viola.

My start scripts will not interfere in any way with GDM if you boot to GDM. GDM runs on display :0.0, all my script start on higher displays.

I am afraid you will have to look elsewhere if you want to configure KDM/GDM/XDM.

Note: I use xscreensaver and numlockx for all sessions. Either install these applications or comment out the lines.

Note: With openbox I use fbpanel. (Trying to wean myself of panels as I know they are not needed, esp with *Box or IceWM [Unlike Gnome/KDE], but they are so pretty and have configured the clocks just tthe way I like.....)
Again either install fbpanel or comment out the appropriate lines.
For your convince I included other panels in the openbox script, if you want any particular panel just remove the hash mark. XFCE panel does not need multiple enteries, the others do.

Add the following aliases to ~./.bashrc :
```
#Start scripts
alias startflux='/home/your_user_name/.config/fluxbox/autostart.sh &'
alias startopen='/homeyour_user_namei/.config/openbox/start &'
alias startice='/home/your_user_name/.config/icewm/start &'
```

You need to log out and then back in fro these to take effect.

Save these script in ~/.config

>  Fluxbox: (Fluxbox only needs one script)
 ~/.config/fluxbox/autostart.sh

Openbox:
~/.config/openbox/autostart.sh
~/.config/openbox/autostart.sh

IceWM
 ~/.config/icewm/autostart.sh
 ~/.config/icewm/autostart.sh

Here are the scripts:

**Fluxbox (Only one needed for Fluxbox) :**
autostart.sh
```
#!/bin/sh
DISPLAY=:1.0 /usr/bin/xscreensaver &
DISPLAY=:1.0 /usr/bin/numlockx on &
/usr/bin/startx /usr/bin/fluxbox -- :1 **-layout DUAL**
```
**EDIT Note name change.**

**Openbox (Both scripts needed) :**
start
```
 #!/bin/sh
startx /home/your_user_name/.config/openbox/autostart.sh -- :3 **-layout DUAL**
```
**EDIT Note name change**

autostart.sh
```
#!/bin/sh

#Screensaver and numberlock
/usr/bin/xscreensaver &
/usr/bin/numlockx &

# Set BG image
DISPLAY=:3.0 /usr/bin/fbsetbg -f /path_to_your_BG_Image.jpg
DISPLAY=:3.1 -f /path_to_your_BG_Image.jpg

# Start a panel
DISPLAY=:3.0 /usr/bin/fbpanel &
DISPLAY=:3.1 /usr/bin/fbpanel &
# /usr/bin/xfce4-panel & #XFCE only needs this one line.
# /usr/bin/perlpanel &
# DISPLAY=:3.1 /usr/bin/perlpanel &
# /usr/bin/kicker & # I had problems running kicker outside of KDE

#Start Openbox
/usr/bin/openbox & DISPLAY=:3.1 /usr/bin/openbox
```

**Icewm (Both scripts needed) :**
start
```
 #!/bin/sh
startx /home/your_user_name/.config/icewm/autostart.sh -- :4 -layout DUAL
```
**EDIT Note name change.**

autostart.sh
```
#!/bin/sh
/usr/bin/numlockx &
DISPLAY=:4.0 /usr/bin/xscreensaver &
/usr/bin/icewm-session & DISPLAY=:4.1 /usr/bin/icewm-session
```

NO I COULD NOT USE A SINGLE SCRIPT FOR EITHER OPENBOX OR ICEWM. I tried. If you know of a better solution (each gave a different set of errors) PLEASE POST.

I tried configuring GDM, but was unable to pass all these options to X from GDM. Did not try KDM/WDM/XDM.

With these scripts in place you can start the window managers from the command line with a simplified command:

**Fluxbox :**
```
# startflux
```

**Openbox :**
```
# startopen
```

**Icewm :**
```
# startice
```

Closing notes: As I said, you can run more then one window manager at a time. Why you  ask?

Because we can (in Linux, not Windows). My wife likes KDE, I prefer Fluxbox. She prefers a much lower resolution and dual monitors give her a headache. Why GDM if she uses KDE? She likes the picture better and I have not configured KDM with the same picture. Go figure, just another example of mix and match Linux.

Solution: > She logs into GDM -> KDE and "owns" the first virtual X session. She uses a much lower resolution.

I use tty1 and can start Fluxbox on the second virtual X session. I have dual monitors at a high resolution. 

We do not have to log each other on and off or constantly change the resolution or window manager.

If you are concerned about security, lock the terminal or password protect your xscreensaver.

To do this, change the "defaultServerLayout" in your server flags section of xorg.conf to 

> Option "DefaultServerLayout" "NAME_OF_YOUR_SINGLE_MONITOR_SERVER" #Change this to the name of your third server layout.


**Finally, acknowledgment of my mentors:**

[je_fro](http://www.justlinux.com/forum/showthread.php?t=143803)

[darkshed](http://darkshed.net/files/rcs/misc/xorg.conf)

[Lou](http://forums.debian.net/viewtopic.php?t=5450&highlight=configure+icewm&sid=d98a2e6680fc6ef6276446ed4225d6b8)

**[SIZE="4"]ENJOY[/SIZE]**

[img]http://www.laiwa.com/cache/3/1/531045_70x70.gif[/img] [color=navy]bodhi.[/color][color=darkgray]zazen[/color]

**Here is a WORKING COPY of my xorg.conf as a text file:**

---

### Post by bodhi.zazen on 2006-08-24
bump.

There is a second post in these forums which is my mistake (clicked submit rather then preview).

Requested the other post (copy) be removed.

Posted this note to put this one on the top.

---

### Post by dsyn on 2006-09-16
Thought I would post my working version of xorg.conf and this link: [http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

This article and the link(above) really helped out a lot with understanding the dual monitor setup process.

thanks bodhi.zazen

---

### Post by CromagDK on 2006-09-20
Ok, i dont get this to work. I get error "no screens found"
I have an idea that i either missed something or the 2 identical screens makes the error. Or i am just blind :)

Would apriciate cause im REALLY looking for this :) 
I use a nvidia 6800 if that helps.
xorg.conf here:

```
# ************************************************** ********************
# Files section. This allows default font and rgb paths to be set
# ************************************************** ********************

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

# ************************************************** ********************
# Server flags section.
# ************************************************** ********************

Section "ServerFlags"
Option "DefaultServerLayout" "twinview"
Option "AllowDeactivateGrabs" "true"
Option "AllowClosedownGrabs" "true"
Option "AllowMouseOpenFail" "true"
EndSection

# ************************************************** ********************
# Module section -- this section is used to specify
# which dynamically loadable modules to load.
# ************************************************** ********************

Section "Module"
Load "dbe" # Double buffer extension
SubSection "extmod"
Option "omit xfree86-dga" # don't initialise the DGA extension
EndSubSection
Load "type1"
Load "freetype"
Load "glx"
Load "record"
Load "evdev"
Load "xtrap"
# Load "extmod"
# Load "v41"
# Load "speedo"
# Load "bitmap"
# Load "ddc"
# Load "dri"
# Load "int10"
# Load "vbe"
EndSection

#Section "Extensions"
# Option "Composite" "Enable"
#EndSection

################################################## ############################################
#
# I N P U T - SECTION
#
# keyboards and mice are handled here
#
################################################## ############################################

# ************************************************** ********************
# Core keyboard's InputDevice section
# ************************************************** ********************

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

# ************************************************** ********************
# Core Pointer's InputDevice section
# ************************************************** ********************

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




################################################## ############################################
#
# IBM P260 = Monitor 1
#
# 
#
################################################## ############################################

Section "Monitor"
Identifier "Monitor1"
VendorName "IBM"
ModelName "IBM P260"
HorizSync 29-121
VertRefresh 50-180
EndSection


#
################################################## ############################################
#
# IBM P260 = Monitor 2
#
# 
#
################################################## ############################################

Section "Monitor"
Identifier "Monitor2"
VendorName "IBM"
ModelName "IBM P260"
HorizSync 29-121
VertRefresh 50-180
EndSection


# ************************************************** ********************
# Server section
# ************************************************** ********************

# ************************************************** ********************
# Graphics device section
# ************************************************** ********************

#
################################################## ############################################
#
# T W I N V I E W - S E T U P (NVIDIA)
#
# Monitor1 and Monitor2 are both connected to the same (nvidia) videocard
# activates the nvidia-twinview-mode
#
# advantage: opengl on both windows
# disadvantage: cant get 1600x1200 on each monitor, it seems that both
# screen must have same refreshrates
# no xv for mplayer

Section "Device"
Identifier "twinview"
VideoRam 256000
VendorName "nVidia Corporation"
BoardName "Video device"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 0
Option "TwinView"
Option "MetaModes" "1600x1200,1600x1200"
Option "TwinViewOrientation" "Rightof"
Option "SecondMonitorHorizSync""UseEdidFreqs"
Option "SecondMonitorVertRefresh" "UseEdidFreqs"
Option "HWCursor" "On"
Option "UseEdidFreqs" "true"
Option "NvAGP" "1"
# Option "NoLogo" "true"
# Option "RenderAccel" "true"
# Option "CursorShadow" "true"
# Option "XvmcUsesTextures" "true"
EndSection


# ************************************************** ********************
# Screen sections
# ************************************************** ********************

Section "Screen"
Identifier "twinviewscreen"
Device "twinview"
Monitor "Monitor1"



	DefaultDepth	24

	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

************************************************** ********************
# ServerLayout sections.
# ************************************************** ********************

Section "ServerLayout"
Identifier "TWINVIEW"
Screen "twinviewscreen"
InputDevice "Mouse1" "CorePointer"
InputDevice "Keyboard1" "CoreKeyboard"
Endsection

#
################################################## ############################################
#
# D U A L M O N I T O R - S E T U P (NVIDIA)
#
# crt0 and crt1 are both connected to the grafic card. we create a pseudo
# device that points to the same graficcard.
#
# advantage: we can get 1600x1200 on both displays, both screens can have
# different refresh resolutions, rates, depths etc etc
# xv works again (brightness etc for mplayer)
# opengl on both monitors
# disadvantage: no exchange of windows between those 2 screens.
#


Section "Device"
Identifier "Videocard1"
VideoRam 256000
VendorName "nVidia Corporation"
BoardName "Video device"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 0
Option "HWCursor" "On"
Option "UseEdidFreqs" "true"
Option "NvAGP" "1"
EndSection

Section "Device"
Identifier "Videocard2"
VideoRam 256000
VendorName "nVidia Corporation"
BoardName "Video device"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 1
Option "HWCursor" "On"
Option "UseEdidFreqs" "true"
Option "NvAGP" "1"
EndSection


-----

# ************************************************** ********************
# Screen sections
# ************************************************** ********************

Section "Screen"
Identifier "Screen 0"
Device "Videocard1"
Monitor "Monitor1"

DefaultDepth 24

Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 32
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
EndSection

Section "Screen"
Identifier "Screen 1"
Device "Videocard2"
Monitor "Monitor2"

DefaultDepth 24

Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 32
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
EndSection

# ************************************************** ********************
# ServerLayout sections.
# ************************************************** ********************

Section "ServerLayout"
Identifier "DUALSCREEN"
Screen 0 "Screen 0" 0 0
Screen 1 "Screen 1" LeftOf "Screen 0"
InputDevice "Mouse1" "CorePointer"
InputDevice "Keyboard1" "CoreKeyboard"
EndSection

#
################################################## ############################################
#
# IBM P260 - S E T U P
#
# setup to have a xserver on the P260 display alone
#
# device for crt0


Section "ServerLayout"
Identifier "P260"
Screen 0 "Screen 0"
InputDevice "Mouse1" "CorePointer"
InputDevice "Keyboard1" "CoreKeyboard"
# Option "Offtime" "10"
EndSection

```

---

### Post by bodhi.zazen on 2006-09-20
First, do you have the nvidia drivers installed?

[Nvidia drivers](http://www.nvidia.com/object/unix.html)

If so, try the attached file.

The default will start twinview. Do you know how to test the other configurations?

```
startx --:2 -layout DUALSCREEN
```

and

```
startx --:2 -layout P260
```

---

### Post by CromagDK on 2006-09-21
Hi again. I tried the conf. but still same problem.

I will post something you might find usefull somehow. 

cromag@Zippy:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:

Xorg.0.log:

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Zippy 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 21 11:48:48 2006
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 243 of section Screen in file /etc/X11/xorg.conf
	"**************************************************" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor

Thank you for the helt so far :)

/CromagDK

---

### Post by bodhi.zazen on 2006-09-21
I will try to look at it again tonight.

In the mean time, I started this thread advising you start with a working copy of xorg.conf with twinview. Could you post your original xorg.conf (the one you backed up) with twinview working? I you would be so kind as to post as an attachment as it makes this thread hard to read with long xorg.conf files posted. :cool:

If you do not have twinview working, follow the links at the start of my post and get twinview up first. :)

---

### Post by CromagDK on 2006-09-21
argh sorry it got this late. My own punishment. Well. I'll post the working twinview xorg.conf here as an attachment. I can see this 1st page of the thread is kinda huge now. :(

hope this can solve the issue. Twinview was the one where you could mode windows across monitors as far as i remember. And that i am able to do.

//CromagDK

---

### Post by bodhi.zazen on 2006-09-22
Does this work (twinview only, but modified).

---

### Post by CromagDK on 2006-09-22
Im not sure ehm... My twinview works fine? Want me to check with your conf if twinview works with that to ?

Edit well, it works. Just the wrong side. I have to go left to go to the screen on the right :P And kb layout is weird.

//CromagDK

---

### Post by bodhi.zazen on 2006-09-24
Try this:

The default is still twinview.

To start another setting:```
startx --:2 -layout DUALSCREEN
```

And:```
startx --:2 -layout IBM
```

To change the default edit> # ************************************************** ********************
# Server flags section.
# ************************************************** ********************

Section "ServerFlags"
Option "DefaultServerLayout" "twinview"
Option "AllowDeactivateGrabs" "true"
Option "AllowClosedownGrabs" "true"
Option "AllowMouseOpenFail" "true"
EndSection

And change the "DefaultServerLayout" to "DUALSCREEN" or "IBM".

---

### Post by CromagDK on 2006-09-24
I tried the new attachment, and it doesnt work. I have attached the log file if it helps anything.

/CromagDK

---

### Post by bodhi.zazen on 2006-09-24
LOL try this. What about:```
startx --:2 -layout DUALSCREEN
```

---

### Post by CromagDK on 2006-09-26
Still no, but this times its regarding:

waiting for x server to shut down FreeFontPath /usr/share/X11/fonts/misc/ 

refcount is 2; should be 1; fixing.

And then theres just a command line prompt.

---

### Post by bodhi.zazen on 2006-10-01
Try this command```
/usr/bin/startx /usr/bin/fluxbox -- :2
```

Should at least give you fluxbox with twinview.

For Dual monitors:```
/usr/bin/startx /usr/bin/fluxbox -- :2 -layout DUALSCREEN
```

FYI: I have written a Bash script and will put the finishing touches on it in the next few days.

The good news is it evokes a graphical menu where you can select your window manager (Fluxbox, Gnome, IceWM, KDE, Openbox, and XFCE)monitor configuration (Twinview, Dual Monitiors, and a single (failsafe) monitor.

The other good news is I have simplified the  start scripts.....

I need to modify the xorg.conf a little, just use consistent (and simpler) names of servers.

I will likely start a new thread dedicated to the script.... 8-)

---

### Post by CromagDK on 2006-10-03
> **bodhi.zazen said:**
> Try this command```
/usr/bin/startx /usr/bin/fluxbox -- :2
```

Should at least give you fluxbox with twinview.

For Dual monitors:```
/usr/bin/startx /usr/bin/fluxbox -- :2 -layout DUALSCREEN
```

FYI: I have written a Bash script and will put the finishing touches on it in the next few days.

The good news is it evokes a graphical menu where you can select your window manager (Fluxbox, Gnome, IceWM, KDE, Openbox, and XFCE)monitor configuration (Twinview, Dual Monitiors, and a single (failsafe) monitor.

The other good news is I have simplified the  start scripts.....

I need to modify the xorg.conf a little, just use consistent (and simpler) names of servers.

I will likely start a new thread dedicated to the script.... 8-)



Well, yesh, i just thought that in Dualscreen you would NOT be able to drag windows from one screeb to another. (?) Well i can. And in Fluxbox the bottom bar is shared between the to screens. not sure if its supposed to hehe :)

Just a bit of info :)

CromagDK

---

### Post by bodhi.zazen on 2006-10-04
FYI: I posted a bash script to start your dual monitors.

I went with a separate post because this one is long enough.

**I will edit this how-to when the other is available**

Look for How to bash script dual monitors. There may be a 24-48 hour delay from this post.

---

### Post by Nesousx on 2006-11-01
Hey,



I tried to set up the dual Monitor according to your HOWTO, but it doesn't work.. I can't figure out what I missed / messed up.

Thanks a lot for your support.

Im using Ubuntu.
Nvidia Geforce 7900GT PCI express
Syncmaster 930BF as main screen
LG3200t, hdtv as second screen



You can find your "xorg.conf" edited according to my config.



And here is the logfile from Xorg:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux nesousx-desktop 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Wed Nov  1 13:45:21 2006
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined InputDevice "Mouse1" referenced by ServerLayout "TWINVIEW".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor


```

Edit> Added mz working old dual screen xorg.conf.

---

### Post by bodhi.zazen on 2006-11-02
> **Nesousx said:**
> Hey,...

I tried to set up the dual Monitor according to your HOWTO, but it doesn't work.. I can't figure out what I missed / messed up.


1. Look at the contents of /var/log/Xorg.93.log

2. You have a mismatch between your configured mouse and keyboard and server sections.

Using twinview as an example:

Keyboard:
> # **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************
Section "InputDevice"
**    Identifier     "Generic Keyboard"**
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
EndSection

Mouse:
> # **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"
**    Identifier     "Configured Mouse"**
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection


Twinview Server Section:
> # **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"
	Identifier	"TWINVIEW"
	Screen		"twinviewscreen"
**[color=red]	InputDevice	"Mouse1" "CorePointer"[/color]**
**[color=red]	InputDevice	"Keyboard1" "CoreKeyboard"[/color]**
Endsection

Try this:
Replacement Twinview server section:
Twinview Server Section:
> # **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"
	Identifier	"TWINVIEW"
	Screen		"twinviewscreen"
**[color=blue]	InputDevice	"Configured Mouse" "CorePointer"[/color]**
**[color=blue]	InputDevice	"Generic Keyboard" "CoreKeyboard"[/color]**
Endsection

I have not had the time to look through your entire xorg.conf. The log file should give you a clue as to other problems.

If you are still having problems, re-post your xorg.conf, as an attachment please, and I will try to debug. However, I may not have time before the weekend, at the earliest (sorry :( ).

---

### Post by Nesousx on 2006-11-05
Cheers ^^

It works :)

---

### Post by rharriso on 2008-08-19
Wow, good job guys. This worked perfectly. Ubuntu is really catching up with proprietary OS's feature for feature.

---

### Post by bvidinli on 2008-12-23
for normal dual head monitor, with xinerama on ati,

open console,
run followings:

aticonfig --initial=dual-head --screen-layout=right
aticonfig --dtop=horizontal --overlay-on=0
aticonfig  --xinerama=on


this will setup an xorg.conf with dual head, one large desktop, you can drag a windows from one monitor to another...

---

