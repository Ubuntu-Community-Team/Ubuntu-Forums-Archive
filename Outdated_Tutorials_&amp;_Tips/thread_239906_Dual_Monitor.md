---
title: "Dual Monitor"
date: 2006-08-20
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-08-20
**[SIZE="6"]How to Dual Monitor.[/SIZE]**

[SIZE="3"]I will focus on light desktops: Fluxbox, Openbox, and IceWM with two monitors.This works well with KDE, GNOME, and XFCE as well.[/SIZE]

This is NOT another how to on twinview or xcinerama.
If that is what you want see here:

[http://www.ubuntuforums.org/showthread.php?t=221174&highlight=twinview](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=twinview)

[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

Twinview/xicnerama work well enough with the "big three" (KDE/Gnome/XFCE), but I am interested in a lighter weight desktop (Fluxbox, Openbox, IceWM).

What do I mean the by Dual monitor? Two "independent" monitors. The mouse can move freely beetween the monitors, but you can not drag a window  or application from one window to another. (Twinview/xcinerama is described as "One large monitor").

Preamble;
> 1. Graphic card = nVidia. If others want to add OK, but I only know so much. With that said, most of this should work with just about any graphics card.

2. I boot to the command line (CLI) and start these window managers from the command line (not KDM/GDM/XDM. I will include examples of start scripts. These scripts work better for me at least partially because I do not know how to configure GDM/KDM/WDM/XDM to start the dual monitor X server.

If you, like most, boot to GDM/KDM/WDM/XDM you do NOT need to change the way you boot. Use Ctrl-Alt-F1 to get to your CLI on tty1.

3. Twinview is the server configuration that gives 1 large desktop across two monitors and is the most "popular" configuration. This "How to" focuses on setting up what I call Dual Monitors, but Twinview remains the default behavior so you may have the best of both worlds and change between the two configurations at will (requires a re-start of X, and thus your desktop manager to change).

4. I will use Dual monitors for Fluxbox/Openbox/IceWM. This is two independent monitors. You can move the mouse freely between the monitors, but not drag windows between them (as you can in Twinview).

5. The main reason for the "Dual monitor" approach  is Twinview/xcinerama is it does not always work well. Panels may be stretched across two windows (Fluxbox, IceWM), applications may start in the middle of the two screens, Background images are variable, etc..

6. The majority of this How  to is done with "proper" configuration of X in /etc/X11/xorg.conf. There is, however, no automatic configuration tool.

7. In this How to, all commands to be entered either at the terminal or CLI start with a #.

8. I advise writing xorg.conf from within X using gedit (copy and paste). You can cut-and paste to vi or nano if you prefer.

9. You must know the technical specifications for your monitors. If you do not know this, Google now and write down the address of the relevant web site (you will need it later).

10. You will be able to cut-and-paste most of my xorg.cong later in this post, but some sections must be configured BY YOU. in addition you may desire a few different options.

11. This xorg.conf will give you three options for X: Twinview, Dual monitors, and a third to start a single monitor.

12 I posted my current Ubuntu xorg.conf  at the bottom of this How to.


**[SIZE="2"]Overview of how it works:[/SIZE]**
From the CLI, to start a window manager
```
startx /usr/bin/name_of_window_manager -- :2 -layout SERVER_NAME
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
> fluxbox:   /usr/bin/fluxbox
openbox: /usr/bin/openbox
icewm: /usr/bin/icewm-session
xfce:  /usr/bin/xfce4-session
gnome:  /usr/bin/gnome-session
KDE: /usr/bin/startkde

**[SIZE="2"]A quick note on other "light" desktop environments:[/SIZE]** Fluxbox has a nice menu and transparency options and in my opinion is best. IceWM is also very nice, lost of settings and configuration options. Openbox is about as bare bones as I get. Each has it's advantages. There are how-to's on the Ubuntu and Debian forums for these window managers.

There is a very nice How-to for Icewm on the Debian forums:

[http://forums.debian.net/viewtopic.php?t=5450&highlight=configure+icewm&sid=d98a2e6680fc6ef6276446ed4225d6b8](http://forums.debian.net/viewtopic.php?t=5450&highlight=configure+icewm&sid=d98a2e6680fc6ef6276446ed4225d6b8)

**[SIZE="2"]The "problems" with twinview/xcinerama and light desktops are:[/SIZE]** With wallpapers and panels stretched across both screens (not as problematic in Gnome, KDE, XFCE, or IceWM) and windows opening in the middle of the two monitors , split across both screens. You can make a large, dual monitor wallpaper with GIMP. **[SIZE="2"]Advantage of Twinview [/SIZE]**is you can drag windows between both monitors.

**[SIZE="2"]Most of these problems are solved with using what I am calling "Dual monitors", but you lose the ability to drag windows between monitors.[/SIZE]**

**[SIZE="2"]On the subject of panels: [/SIZE]**You can of course launch kicker, gnome-panel, or the XFCE panel. These all work, although I have had problems with kicker outside of KDE.

There are several light panels and If I have the energy I will write (briefer) how to's on some of these panels. fbpanel is, again in my opinion, the best and most easily customized (fbpanel is NOT related to fluxbox) and it allows transparency. perlpanel is also VERY NICE, but no transparency. pypanel is nice and also allows transparency BUT it does not seem to work for me (crashes) with multiple monitors .

**[SIZE="4"]OK, now for the hard stuff. [/SIZE]**

The bad news is you will have to configure X for yourself. The good news is you can follow this template.

First, install the nVidia driver and configure X for twinview with the Nvidia driver. This part is fairly straight forward and is covered elsewhere both in the Ubuntu forums and elsewhere. this will give you a "basic" xorg.conf on which to build. This approach should work with other graphics cards and drivers just fine (no guarantees....) start with a working xorg.conf  using twinview/xicnerama and whatever drivers/settings work with your monitors, keyboard, and mouse. (the open drivers for my nVidia card do not work with my card, thus I use the nVidia driers).

I will also not cover installation or configuration of Fluxbox, openbox, icewm, XFCE, panels, etc in any further detail.

**[SIZE="4"]Now the fun begins:[/SIZE]**

1. Backup your xorg.conf
```
# cd /etc/X11
# sudo cp xorg.conf xorg.conf.org
```

2. Edit xorg.conf. As is, xorg.conf  is not well commented. We will change that.
```
# sudo gedit /etc/X11/xorg.conf
```

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
#    twinview    - uses nvidia-driver-xinerama support
#    dell      - use only the DELL P1110-display
#    dualscreen  - 2 seperated screens
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


DO NOT forget the following line in Server Flags.
Option      "DefaultServerLayout" "twinview" 

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
# sepcs at [http://www](http://www).
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
#  specs at : http:
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

[SIZE="2"]Section 6: Server section.[/SIZE]This sets up options for X. It sets up 3 devices and (X server) layouts, each setup is different. The setups are twinview, dualscreen, and Dell. I encourage you to change the name of "dell" to the name of your first monitor.
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
     Identifier      "DUALSCREEN"
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
	Identifier  "DELL"
	Screen      0 "Screen 0"
	InputDevice     "Mouse1" "CorePointer"
	InputDevice     "Keyboard1" "CoreKeyboard"
#	Option      "Offtime" "10"
EndSection

Watch your:
1. Amount of  video ram. You may have more or less.
2. VendorName.
3. BusID. Do not use mine, but check the BusID in your xorg.conf..
4. Metamodes. I use a resolution of 1600x1200. You man need to reduce this to reflect your monitors and preferences. ? "1280x1024,1280x1024". I believe you can have different resolutions on eachmonitor if you like ie "1600x1200,1280x1024"
5. Default depth. I use 24, you may want to change this.
6. You may need to change TwinViewOrientation to "Rightof"
7. If you do not want to see the nVidia logo uncomment the "noLogo" line. I deft it for now so you will have confirmation you are using the nVidia driver.
8. Same with other options.
9. In your modes sections you can use modlines if you like. If you do not know what a modline is, do not worry about it for now. 
10 NOTE DUALSCREEN and DELL are ALL-CAPS.

Save your changes and exit gedit.

Back up your new xorg.conf.
```
# sudo cp xorg.conf xorg.conf.bak
```

You should be good to go.


Now the moment of truth !!

To start a desktop:
```
# startx /usr/bin/path_to_window_manager -- :2 This will start you in twinview.
```


For fluxbox with dual monitors use the layout flag:
```
# startx /usr/bin/fluxbox -- :2 -layout DUALSCREEN
```

Welcome to Fluxbox on Dual monitors.

Scripts:

As I said, I launch my windows managers from the CLI, no KDM/GDM/XDM here.

If you boot to say GDM you, no problem. just Ctrl-Alt-F1 to tty1, log in, viola.

My start scripts will not interfere in any way with GDM if you boot to GDM. GDM runs on display :0.0, all my script start on higher displays.

I am afraid you will have to look elsewhere if you want to configure KDM/GDM/XDM.

Note: I use xscreensaver and numlockx for all sessions. Either install these applications or comment out the lines.

Note: With openbox I use fbpanel.
Again either install fbpanel or comment out the appropriate lines.
for your convince I included other panels in the openbox script, if you want any particular panel just remove the hash mark. XFCE panel does not need multiple enteries, the others do.

Add the following aliases to ~./.bashrc :
```
#Start scripts
alias startflux='/home/your_user_name/.config/fluxbox/autostart.sh'
alias startopen='/homeyour_user_namei/.config/openbox/start'
alias startice='/home/your_user_name/.config/icewm/start' 
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

Fluxbox :
```
#!/bin/sh
DISPLAY=:1.0 /usr/bin/xscreensaver &
DISPLAY=:1.0 /usr/bin/numlockx on &
/usr/bin/startx /usr/bin/fluxbox -- :1 -layout DUALSCREEN
```

Openbox
start
```
 #!/bin/sh
startx /home/your_user_name/.config/openbox/autostart.sh -- :3 -layout DUALSCREEN
```

autostart
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
# /usr/bin/xfce4-panel &
# /usr/bin/perlpanel &
# DISPLAY=:3.1 /usr/bin/perlpanel &
# /usr/bin/kicker & # I had problems running kicker outside of KDE

#Start Openbox
/usr/bin/openbox & DISPLAY=:3.1 /usr/bin/openbox
```

Icewm
start
```
 #!/bin/sh
startx /home/your_user_name/.config/icewm/autostart.sh -- :4 -layout DUALSCREEN
```

autostart
```
#!/bin/sh
/usr/bin/numlockx &
DISPLAY=:4.0 /usr/bin/xscreensaver &
/usr/bin/icewm-session & DISPLAY=:4.1 /usr/bin/icewm-session
```


Closing notes: As I said, you can run more then one window manager at a time. Why you  ask?

My wife likes KDE, I prefer Fluxbox. She prefers a much lower resolution and dual monitors give her a headache.

Solution: > She logs into GDM -> KDE and "owns" the first virtual X session. She uses a much lower resolution.

I use tty1 and can start Fluxbox on the second virtual X session. I have dual monitors at a high resolution. 

We do not have to log each other on and off or constantly change the resolution.

If you are concerned about security, lock the terminal or password protect your xscreensaver.

> To do this, change the "defaultServerLayout" in your server flags section of xorg.conf to 

Option "DefaultServerLayout" "DELL" #Change this to the name of your third server layout.

ENJOY

Here is my file (as text):

[QUOTE] 

---

### Post by bodhi.zazen on 2006-08-23
This is an incomplete, accidental post ans should be deleted.

Please see my other post which is complete:
[http://www.ubuntuforums.org/showthread.php?t=240150](http://www.ubuntuforums.org/showthread.php?t=240150)

---

