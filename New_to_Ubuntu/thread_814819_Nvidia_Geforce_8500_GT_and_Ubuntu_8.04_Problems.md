---
title: "Nvidia Geforce 8500 GT and Ubuntu 8.04 Problems"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by pancakelizard on 2008-06-01
I've enclosed a copy of my xorg.conf file. It is currently the best performance with my video card that I can get.

I have been searching and troubleshooting for hours and can not get my Nvidia 8500 GT to work fully with a fresh install of Ubuntu 8.04 that I made today.

I have tried installing through Envy and through the restricted drivers as well as in the Appearance tab in the System menu. Whenever I reboot X, the screen is cut off half-way and I am forced to go to the terminal (CTRL+ALT+F1) and apt-get remove the nvidia-glx-new drivers.

I have also downloaded version 173.14.05 from Nvidia's website and did a terminal install of that with the resolution only being allowed to go to 640*480.

I have the 64 bit version of Hardy Heron
A Nvidia Geforce 8500 GT
And a Dell 2005FPW Widescreen Monitor - Connected through DVI.

Among other things, I am trying to achieve a resolution of 1680*1080 @ 60 (max my monitor supports) with the best visual effects enabled using Nvidia drivers.

I've tried different versions of drivers, Envy, etc and can not get this to work.

Please help!

---

### Post by Will240 on 2008-06-01
I have almost exactly the same problem but with Dell Inspiron 1520 and 128MB NVIDIA® GeForce® 8400M GS.

---

### Post by KenBW2 on 2008-06-01
I had the same problem with my nvidia card/drivers after upgrading from Gusty. One day it just refused to work. Alas I ended up being forced to make a new installation of ubuntu :(

---

### Post by pancakelizard on 2008-06-01
There has to be something besides a complete reinstall of the operating system...

---

### Post by pancakelizard on 2008-06-01
Bump!

---

### Post by JordanII on 2008-06-01
I'm having the same problem with the NVIDIA GeForce 6150 LE. I really need it fixed. :(

---

### Post by Xiong Chiamiov on 2008-06-01
> **pancakelizard said:**
> I've enclosed a copy of my xorg.conf file. It is currently the best performance with my video card that I can get.

I have been searching and troubleshooting for hours and can not get my Nvidia 8500 GT to work fully with a fresh install of Ubuntu 8.04 that I made today.

I have tried installing through Envy and through the restricted drivers as well as in the Appearance tab in the System menu. Whenever I reboot X, the screen is cut off half-way and I am forced to go to the terminal (CTRL+ALT+F1) and apt-get remove the nvidia-glx-new drivers.

I have also downloaded version 173.14.05 from Nvidia's website and did a terminal install of that with the resolution only being allowed to go to 640*480.

I have the 64 bit version of Hardy Heron
A Nvidia Geforce 8500 GT
And a Dell 2005FPW Widescreen Monitor - Connected through DVI.

Among other things, I am trying to achieve a resolution of 1680*1080 @ 60 (max my monitor supports) with the best visual effects enabled using Nvidia drivers.

I've tried different versions of drivers, Envy, etc and can not get this to work.

Please help!
You're using the Vesa drivers in that xorg.conf, which are the failsafe ones.  I know you said you installed the NVIDIA drivers directly from them, but can you double-check with [this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329")?  Make sure that you choose the option for it to write a new xorg.conf, and if that's not working, can you post the contents of that please?

---

### Post by pancakelizard on 2008-06-01
I will try but I have the 64bit version installed and according to the link, all that is listed was 32 bit drivers.

---

### Post by Xiong Chiamiov on 2008-06-01
Ah, you'll need [this page]("http://www.nvidia.com/object/linux_amd64_display_archive.html") then.  I'll update that post accordingly.

---

### Post by philinux on 2008-06-01
What does system>admin>hardware drivers report?

---

### Post by pancakelizard on 2008-06-01
I followed the instructions and enclosed a copy of the new xorg.conf file in the post.

The Nvidia X server now works and shows that the driver is installed but the option to make the resolution higher than 640*480 is not there!

---

### Post by Xiong Chiamiov on 2008-06-01
I'm trying to compare your xorg to mine to see what important differences there are.  So then, try changing this:
```

SubSection     "Display"
        Depth       24
    EndSubSection

```
to this:
```

SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

```
Of course, your resolutions are probably different than mine, but we just want to see if we get more options then.

---

### Post by pancakelizard on 2008-06-01
I made the changes and after rebooting, the options were not there to select the diferent resolutions. However there are still listed in the xorg.conf file.

---

### Post by Xiong Chiamiov on 2008-06-01
I'm not sure if this will help or not, but try adding these two lines to the "Screen" section:
```

Option         "AddARGBGLXVisuals" "True"
Option         "AddARGBVisuals" "True"

```

---

### Post by pancakelizard on 2008-06-01
That didn't work either :(

---

### Post by Xiong Chiamiov on 2008-06-01
You might try a few other depths, as shown [here]("http://ubuntuforums.org/showpost.php?p=5095455&postcount=13").

---

### Post by pancakelizard on 2008-06-01
Did the also for 16 and 24 bit, also added the 8 bit and nothing.
Any other ideas?

Why is this so difficult again?
I noticed I don't have drivers for my monitor, would that make a difference? Although it doesn't seem there are Linux based drivers for my monitor.

---

### Post by Xiong Chiamiov on 2008-06-01
I suppose we should make sure that the NVIDIA driver really is running.  You can check in the restricted drivers setting somewhere (sorry, not that familiar with GNOME).

I'm not sure the effect that different monitors has.  Mine I believe is supported, but I don't really know.  Since you are getting something, it's not a problem with your monitor (mine is rather picky about what resolutions it will accept, and I was stuck for a while with a black screen).

It's difficult because it's Linux.  Even if this is Ubuntu, it's still Linux.  Some things are much easier, but many are just more difficult than in Windows.

---

### Post by pancakelizard on 2008-06-01
After I made the changes from the link you posted, I noticed that the driver is no longer listed in the Restricted Drivers list anymore.

There isn't an option to enable or disable this driver.

Ideas?

---

### Post by Xiong Chiamiov on 2008-06-01
Mm, which link, the first one or the second?

I'm not sure if it'll show up after installing manually or not, but it should display somewhere.  For me (in KDE) it shows up in the Monitor section of the system settings.

---

### Post by pancakelizard on 2008-06-02
The link with the 64-bit drivers.

The drivers report as being installed in the Nvidia X Server however the resolution problem is still occuring.

One user suggested a reinstall of the OS, I did that and reloaded the drivers and nothing worked.

I've run out of ideas as far as getting this to work, so anymore help is greatly apprecaited.

---

### Post by durand on 2008-06-02
Well, it works on my 8600 card so Im assuming that this will work for you as well.

Install the new drivers and an autoconfiguration program:
```
sudo aptitude install nvidia-glx-new nvidia-xconfig
```
then configure it:
```
sudo nvidia-xconfig
```
As reference, this is what my file looks like:

[PHP]# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "extmod"
	#    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "v4l"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: 1280x1024@60 +0+0; CRT: nvidia-auto-select +1280+0, DFP: 1280x960@60 +0+0; CRT: 1280x800 @1280x1024 +1280+0, DFP: 1280x1024@75 +0+0; CRT: nvidia-auto-select +1152+0, DFP: 1152x864@75 +0+0; CRT: nvidia-auto-select +1024+0, DFP: 1024x768@60 +0+0; CRT: nvidia-auto-select +1024+0, DFP: 1024x768@70 +0+0; CRT: nvidia-auto-select +1024+0, DFP: 1024x768@75 +0+0; CRT: nvidia-auto-select +832+0, DFP: 832x624@75 +0+0; CRT: nvidia-auto-select +800+0, DFP: 800x600@60 +0+0; CRT: nvidia-auto-select +800+0, DFP: 800x600@75 +0+0; CRT: nvidia-auto-select +800+0, DFP: 800x600@72 +0+0; CRT: nvidia-auto-select +800+0, DFP: 800x600@56 +0+0; CRT: nvidia-auto-select +640+0, DFP: 640x480@75 +0+0; CRT: nvidia-auto-select +640+0, DFP: 640x480@72 +0+0; CRT: nvidia-auto-select +1280+0, DFP: 1280x800 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "RandRRotation" "on"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1280x1024@75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
[/PHP]

As you can see, it has a whole lot more options than your xorg file and all automatically added...

---

### Post by reiki on 2008-06-02
try running sudo nvidia-settings
when the applet starts highlight where it says your monito and press the button that says "Acquire EDID" and tell it to write to the configuration file.

Are you by any chance using the DVI cable connection between your graphics card and monitor?

---

### Post by durand on 2008-06-02
> Are you by any chance using the DVI cable connection between your graphics card and monitor?
Would that make any difference? Works fine here.

---

### Post by pancakelizard on 2008-06-02
Same problem but allowing 800x600. I did all recommended steps on this page.

Here is the new xorg.conf

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
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:2:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 2005FPW (Digital)"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-75.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1680x1050@60"	"1680x1050@75"	"1600x1024@60"	"1920x1200@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by pancakelizard on 2008-06-02
Update:
I installed Kubuntu 8.04 and the same thing happens, I can't get a resolution above 640*480.

---

### Post by pancakelizard on 2008-06-03
Bumping for more suggestions / help.

---

### Post by Artemis3 on 2008-06-03
I think your xorg.org is wrong, if you have driver vesa; you are not using nvidia. Also try following [my guide](http://ubuntuforums.org/showpost.php?p=4131809&postcount=9) with a clean ubuntu install.

Here is how my section "device" looks like:

```
Section "Device"
        Identifier      "video_card"
        Driver          "nvidia"
        Busid           "PCI:3:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection
```

Be very careful with Busid, this is normally not needed and most of the time, you can simply omit this line. To find out the correct Busid, use the lspci command.

What monitor do you have? Most monitors send the information to the driver and you normally don't need to specify it anymore, but you can try doing a correct monitor config in the section "Monitor". If this is a laptop with external or secondary monitor, unplug them before turning on the machine.

Here is mine for example:

```
Section "Monitor"
        Identifier      "P910+"
        Horizsync       30-107
        Vertrefresh     50-150
        Option          "DPMS"
EndSection
```

In your monitor manual (or the internet) you may find this Horizontal sync and Vertical refresh values.

Let me suggest you comment away all those modelines (just add # in the beginning of each line), this will also lead to change your section "Screen", here is mine for example:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "video_card"
        Monitor         "P910+"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1792x1344"     "1600x1200"     "1280x960"      "1152x864"      "1024x768"      "896x672"       "800x600"       "640x480"       "576x432"       "512x384"       "448x336"       "400x300"       "320x240"
        EndSubSection
EndSection
```

Of course you don't need that many resolutions, i just have fun doing "zoom" with ctrl alt +, and your monitor might probably require different resolutions (consult the manual).

---

### Post by hotweiss on 2008-06-03
This should fix it:

Download the new driver:

[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

---

### Post by pancakelizard on 2008-06-03
> **hotweiss said:**
> This should fix it:

Download the new driver:

[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

I've already done this and it is not working.
One thing I was wondering is, I have a 64 bit processor and using the 64 bit of Ubuntu - during the installation, a question to install 32 components is asked and I always say 'yes'. 
Should I say no?

---

### Post by durand on 2008-06-03
Isn't there a 64 bit version?

---

### Post by pancakelizard on 2008-06-03
Of the drivers and yes that's what I downloaded and used.
What I was asking was should the 32 bit components that I am prompted to install during the installation be ignored?

---

### Post by durand on 2008-06-03
Maybe someone else can answer that :( I'm not familiar with 64bit desktops.

---

### Post by pancakelizard on 2008-06-03
... I did state from the beginning I'm using the 64 bit version :P

---

### Post by hotweiss on 2008-06-03
> **pancakelizard said:**
> ... I did state from the beginning I'm using the 64 bit version :P

Here's something I found:

[http://translate.google.ca/translate?u=http%3A%2F%2Fwiki.ubuntu-forum.de%2Findex.php%2FNvidia_installieren&sl=de&tl=en&hl=en&ie=UTF-8](http://translate.google.ca/translate?u=http%3A%2F%2Fwiki.ubuntu-forum.de%2Findex.php%2FNvidia_installieren&sl=de&tl=en&hl=en&ie=UTF-8)

Try adding these steps:

> sudo apt-get install build-essential xserver-xorg-dev linux-headers-`uname-r` 

> sudo aptitude install libc6-i386 

You can also try this:

[http://ubuntuforums.org/showpost.php?p=4970051&postcount=2](http://ubuntuforums.org/showpost.php?p=4970051&postcount=2)

...and this:

[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

---

### Post by loxaXcracker on 2008-08-15
I got the exact same problem with my Nvidia 8500 GT 512mb (My pc is Hp Pavilion a6230). I can't get a resolution higher than 640xsomething (but the special effects are enabled) and when I install the latest drivers from Nvidia, my resolution goes a bit higher 800x600 (but all the effects are disabled and can't be enabled again). I've tried so many things so far and nothing worked. I am so disappointed in Nvidia and Linux (this is my first attempt to install Linux...). I guess all I can do is stick with my trusty vista. 
ps. I installed Ubuntu 8.04 Hardy.

---

### Post by Tomston on 2008-08-25
For anyone having problems with getting the best resolution and enabling visual effects - i just wasted 5 days before realising that it works finew with a VGA connection but not with DVI....

---

### Post by SMix on 2008-09-10
So I'm still a linux noob, and I want to see if I can perhaps help out here.  I have been struggling to get this Ubuntu 8.04 working with my NVIDIA GeForce 8500GT.  Granted You may be running the 64bit version, but I'm not sure if it will necessarily matter.  I know there is someone else who has seen this as well where they had a 32bit so I think at least for them this should work.  I got fed up and sent a log file to NVIDIA to see what they say and they gave me this link: 

[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

My instruction is going to be a bit of what they say, and a bit of what I did after it all.

(There part that you need to be sure of, check you have the certain packages, and that the others are gone.  When deleting the other files I hope you can do that part.  Just CTRL+ALT+F1 to terminal and sudo /etc/init.d/gdm stop, then delete the files.)

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist
If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled.
Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Now after doing all this, these are the steps I took:

1. CTRL+ALT+F1 out to a terminal if you aren't already.
2. Sudo /etc/init.d/gdm stop
3. sudo apt-get remove nvidia*
4. sudo apt-get install nvidia-glx-new-envy nvidia-glx-new-dev-envy
5. accept the install packages and dependencies
6. sudo nvidia-xconfig
7. I then saw a line about warning with mouse and keyboard and information regarding where the old xorg.conf file was backed up.
8. sudo /etc/init.d/gdm start

Upon starting Gnome displayed the NVIDIA logo, and then successfully logged on.  Upon logging on my display was at a normal size, and I was able to enable compiz effects.  If you try this and it works, please let me know.  I would love to find out I helped someone else get their system working right.  Especially since I don't know much of linux still.  Or if there are questions I will try and check on it to answer em!

---

### Post by EarendiL- on 2008-09-25
He Guys i have a problem with my Nvidia Geforce 8500 GT..it crasehs all the time..you know blue screen and these strange letters...this happens sometimes when i have Windos media player and i open VLC and it happens All the time that I open Warcraft3:FT...some months ago it only happened with Windows media player and World of Warcraft( now i don't play anymore so i don'tknow) but i could play Warcraft..As well ,sometimes I open Warcraft without Windows MEdia Player Running and it Usually crashes again...what can i do???i just downloaded the latest Drivers by nVidia.com so what else can be done????or should I buy a new One.?.Thanks in advance

---

