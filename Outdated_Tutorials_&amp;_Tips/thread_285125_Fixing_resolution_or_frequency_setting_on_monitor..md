---
title: "Fixing resolution or frequency setting on monitor."
date: 2006-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by TitanKing on 2006-10-26
As you all know, this is a topic that appears allot in these forums. After three days of tweaking I finally got mine to work properly and this after all  guides failed, I can now switch resolutions at the correct frequency on my Ubuntu machine.

The problem occured after I upgraded to the latest Nvidia drivers which was : 1.0.8762 

I was affected in the following ways, my BenQ FP91GX LCD would not run @ 60 Hz and it pulled the whole screen off center, I could not set it to a lower resolution nor could I set the Hz, and then finally I found got he solution. I thought I would share this cause all my friends had the exact same issues.  

This is how its done;

First make sure you your graphics drivers are installed ok, you can use your own method for determining this (search the forums). I simply type in terminal "~$ glxgears", if the gears you see is smoot then you most probably have your drivers correctly installed.

After above is done and you are assured that it is working, you need to do the following :

1.) Check your monitors manual or Google your exact same monitor model and locate the "Technical Specifications." (Each model has a unique set of values, you cant use any one elses except if they got the exact same LCD model.

2.) When you found it, look for values named Horizontal Frequency and Vertical Frequency. 

3.) Open the file /etc/X11/xorg.conf (~$ gksudo gedit /etc/X11/xorg.conf)
4.) Locate the section "Monitor" 
5.) Write the values you found in step 2 in the "Monitor" Section like so :

[PHP]
    HorizSync	   31-81
    VertRefresh    56-76
[/PHP]

6.) Locate in the same opened file xorg.conf section "Screen".

7.) You will note that there are a few subsections in the above "Screen" section named "Display", this subsections stores what resolutions you can view at which depth.

8.) We will need to change some values in the "Screen" section to allow us  to make resolution changes as well.

9.) Lets take "depth 24" first, you will see a line like this :

[PHP]Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350" [/PHP]  

10.) I only need a few of these resolution on my LCD display so I will be removing some resolution I dont need. You can add resolutions as well. This  is how I done this :

[PHP]Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"[/PHP]

11.) Ok, we will now tell xorg what frequencies we want it to allow us, we will now make further changes like so (LCD's works best @ 60 HZ so I want my Hz to run @ 60 Hz):

[PHP]Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"[/PHP]

12.) Note the "_60" I added next to each resolution, this stands for 60Hz, you can make yours diffrent frequencies that your screen can handle, it all doesnt have to be the same values and this would be correct for example : 

[PHP]Modes		"1280x1024_60" "1152x864_60" "1024x768_75" "800x600_60" "640x480_75"[/PHP]

**[COLOR="Red"]PS : SOME WRITE THIS AS "800x600_60.00" THIS IS WITH THE .00 ADDED, THIS DID NOT WORK FOR ME !!!! LEAVE OUT THE .00[/COLOR]** 

13.) Now you can repeat this process for all the different depths, if you do not wish to have all these depths simply remove those subsections you do not wish to have.

14.) Here is the changed portion of my xorg.conf file which allowed me freedom of resolution and frequency :

[PHP]
Section "Monitor"
    Identifier     "BenQ FP91GX"
    Option         "DPMS"
    HorizSync	   31-81
    VertRefresh    56-76
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "BenQ FP91GX"
    DefaultDepth    24

SubSection "Display"
	Depth		1
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		4
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		8
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		15
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		16
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		24
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60" 
EndSubSection

EndSection 
[/PHP]

15.) After you have made the changes we need to restart the Graphics Engine by hitting CNTRL + SHIFT + Backspace, wait a few seconds for it to restart . 

16.) You should now be able to set resolutions and frequencies from the GUI  > System > Preferences > Change Resolution.

17.) Well Done !

18.) For your Information, here is the output of my complete xorg.conf file :

[PHP]# nvidia-xconfig: X configuration file generated by nvidia-xconfig
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
    Identifier     "BenQ FP91GX"
    Option         "DPMS"
    HorizSync	   31-81
    VertRefresh    56-76
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "BenQ FP91GX"
    DefaultDepth    24

SubSection "Display"
	Depth		1
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		4
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		8
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		15
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		16
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60"
EndSubSection
SubSection "Display"
	Depth		24
	Modes		"1280x1024_60" "1152x864_60" "1024x768_60" "800x600_60" "640x480_60" 
EndSubSection

EndSection
[/PHP]

---

