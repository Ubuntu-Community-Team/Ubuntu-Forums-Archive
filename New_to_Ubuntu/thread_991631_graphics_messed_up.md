---
title: "graphics messed up"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by nintendorulz55 on 2008-11-24
i plugged my dell inspiron 1525 with intrepid ibex into my flat screen TV yesterday... it worked just fine, the problem came when i looked at my laptop. It looks like im in too big a resolution. I know thats not it, i've played with it a couple times and the only other options are way off. (i have it set to 1024x768). in hardy, there used to be a "screen" option under system -> preferences. Now that its not there, im not quite sure what to do... anyone have an answer?

---

### Post by GSF1200S on 2008-11-24
> **nintendorulz55 said:**
> i plugged my dell inspiron 1525 with intrepid ibex into my flat screen TV yesterday... it worked just fine, the problem came when i looked at my laptop. It looks like im in too big a resolution. I know thats not it, i've played with it a couple times and the only other options are way off. (i have it set to 1024x768). in hardy, there used to be a "screen" option under system -> preferences. Now that its not there, im not quite sure what to do... anyone have an answer?

Hello. Could you give us a little more data please? What video card do you have? If the resolution of the flat screen is larger than the laptop, it will do this. Depending on your video card and the associated driver, we should be able to set it up to recognize your configuration..

---

### Post by nintendorulz55 on 2008-11-24
video card-Intel Graphics Media Accelerator X3100

---

### Post by nintendorulz55 on 2008-11-24
bump

---

### Post by phidia on 2008-11-24
There is a wiki guide on dual screen set up [here]("https://help.ubuntu.com/community/XineramaHowTo"). Near the bottom of that page is info on intel cards.

---

### Post by loomsen on 2008-11-24
There's this handy little tool I recently stumbled upon.

[[img]http://www.ubuntu-pics.de/thumb/6303/screenshot_06_g2XaS3.png[/img]](http://www.ubuntu-pics.de/bild/6303/screenshot_06_g2XaS3.png)

```
sudo apt-get install gvidm
```

as soon as I hit enter the menu pops up under my pointer.

---

### Post by nintendorulz55 on 2008-11-24
> **loomsen said:**
> There's this handy little tool I recently stumbled upon.

[[img]http://www.ubuntu-pics.de/thumb/6303/screenshot_06_g2XaS3.png[/img]](http://www.ubuntu-pics.de/bild/6303/screenshot_06_g2XaS3.png)

```
sudo apt-get install gvidm
```

as soon as I hit enter the menu pops up under my pointer.

this did nothing.i installed, typed in "gvidm" hit enter, and the menu popped up, but nothing happened when i clicked anything. thanks for the help, its not not the answer im looking for.

---

### Post by nintendorulz55 on 2008-11-24
> **phidia said:**
> There is a wiki guide on dual screen set up [here]("https://help.ubuntu.com/community/XineramaHowTo"). Near the bottom of that page is info on intel cards.
I already did the dual screen (in a much easier way than described here..) my problem is the screwed up look my screen has after unplugging. I wouldnt call it so much a resolution problem.. everything looks a tiny bit bigger and its all fuzzy.

---

### Post by nintendorulz55 on 2008-11-24
i think ive found the problem. My resolution is set to 1024 x 768 when it should be set to 1080 x 1024 (i think). The problem is, thats not an option under system->prefernces->screen resolution. any ideas?

---

### Post by loomsen on 2008-11-24
Well then set it up correctly in your xorg.conf

If you manage to do, you'll as well be able to use gvidm... So you probably don't have 

> 
system->prefernces->screen resolution.


OK, no, you don't. Type
```

man xorg.conf
```

and say goodbye GUI!(You should configure you X-server while it's down anyway)

Here's my most recent xorg.conf for dualhead layout: 
TAKE IT AS A HINT, IT WON'T WORK IF YOU COPY AND PASTE.
```

######################################
#                                    #
#	 DUALHEAD   LAYOUT           #
#                                    #
######################################

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "dbe"
    Load           "record"
EndSection

###############################################
#####         INPUT            ################
###############################################

	## INPUT - MOUSE ##
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

	## INPUT - TOUCHPAD ##
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "True"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizTwoFigerScroll" "True"
    Option         "VertTwoFingerScroll" "True"
EndSection

	## INPUT - KEYBOARD ##
Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
EndSection

################################################
####          OUTPUT        ####################
################################################


########## LAPTOP --- SCREEN ##
	#######################
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    	DefaultDepth    24
    Option         "TwinView" "0"
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "Coolbits" "1"
    Option         "NoLogo" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

	#  LAPTOP - GRAFIKKARTE  #
	##########################
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

	#  LAPTOP - MONITOR  #
	######################
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    DisplaySize     381    238
#    HorizSync       30.0 - 110.0
#    VertRefresh     50.0 - 150.0
    Option         "DPMS"
    Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
#    Modeline "1440x900_100.00"  187.55  1440 1544 1704 1968  900 901 904 953  -HSync +Vsync
EndSection



########## FERNSEHER --- SCREEN ##
	##########################
Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TVStandard" "PAL-B"
#   Option		"PixmapCacheSize" "2500000"  ## deprecated
    Option         "AllowGLXWithComposite" "true"
#   Option		"XAANoOffscreenPixmaps"  ## deprecated, for older cards more recent
    Option         "AddARGBGLXVisuals" "true"
#    Option         "AllowIndirectPixmaps" "true" 
    Option         "Coolbits" "1"                    ## overclocking feature
    Option         "NoLogo" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60"
    EndSubSection
EndSection

	#  FERNSEHER - GRAFIKKARTE #
	############################
Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

	#  FERNSEHER - MONITOR  #
	#########################
Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    ###### FIXME #######
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

####################################################
	
	# SERVER HINTS #
	################
	
Section "ServerFlags"
    Option         "Xinerama" "0"
    Option	   "DoubleScan" "true"
    Option         "Pixmap" "32"
    Option         "GlxVisuals" "typical"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "true"
    Option         "DAMAGE" "true"
EndSection

Section "DRI"
     Group 	"video" 
     Mode 	0660
EndSection

```

---

