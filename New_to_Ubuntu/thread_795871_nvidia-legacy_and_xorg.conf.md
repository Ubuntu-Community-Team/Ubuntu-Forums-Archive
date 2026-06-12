---
title: "nvidia-legacy and xorg.conf"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by ricardisimo on 2008-05-15
I'm losing screen resolution by the hour, for some reason. [By the way, I'm going with "Absolute Beginners" here because I've been on Kubuntu for exactly a day, despite many years on Ubuntu. I don't think you need to be too detailed, in other words.]

When I installed yesterday, my screen res was at something like 1400*1280 (is that about right?) which is just how I like it. Today I logged in and found the screen at 1040*786 (or thereabouts), and started investigating. After tinkering a while, I rebooted now I'm maxed out at 640*480, at least according to my Monitor & Display settings.

I've tried "sudo dpkg-reconfigure -phigh xserver-xorg", but only get
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080515191738
```
Here's what is actually in xorg.conf - 
```
# The usual commented out stuff...
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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

I didn't expect to see "Configured Video Device" nor "Configured Monitor", but rather a list of specific settings.

Here's my lspci for the card:```
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
```
I can tell you from past experience that I require the nvidia-legacy driver for this card, and I have installed it via adept, but can't seem to select it anywhere. The only two that will even be considered as options are "nv" or "nvidia" (non-legacy).

Any help at all would be greatly appreciated.

P.S. - I can't find where, in Kubuntu system settings, I would activate both ALT keys as 3rd-level selectors, rather than just the right ALT. This came to mind just now glancing at my xorg.conf. Thanks again.

---

### Post by EXCiD3 on 2008-05-15
have you tried using ```
sudo nvidia-xconfig
```

---

### Post by ricardisimo on 2008-05-15
```
sudo: nvidia-xconfig: command not found
```
Is this a module or app I can install via adept?

---

### Post by EXCiD3 on 2008-05-15
This app is part of the nvidia driver I think. It should be installed on your system if you have the nvidia driver installed correctly. How about ```
sudo nvidia-settings
```

---

### Post by Victormd on 2008-05-15
to use nvidia-config, you have to install the nvidia package and I think the easiest way is through Envy-NG

---

### Post by ricardisimo on 2008-05-15
```
sudo: nvidia-settings: command not found
```

Now I can't configure my hardware via Monitor & Display. Where would I find Envy-NG? Thanks again.

---

### Post by EXCiD3 on 2008-05-15
Your nvidia driver isnt correctly installed. You can install EnvyNG through Synaptic or in terminal ```
sudo apt-get install envyng-gtk
```It will be located in Applications->System Tools->EnvyNG and you can reinstall the nvidia driver there.

More info on EnvyNG: [http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)

---

### Post by ricardisimo on 2008-05-16
Error: EnvyNG couldn't carry out the task you chose because of the following error:
```
    choice(sys.argv[1], sys.argv[2])
  File "pulse.py", line 33, in choice
    objects.maninstall3('nvidia', 'oldest')
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 156, in maninstall3
    task.nvidiaInstall()
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 1076, in nvidiaInstall
    check.checkntry(packages)
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 306, in checkntry
    raise Exception(error)
Exception: ('\nEnvyNG ERROR: The following packages cannot be installed:',)
```
So now what?

---

### Post by EXCiD3 on 2008-05-16
Hmmm, thats interesting. Open terminal and try "sudo apt-get install -f" as it looks like Envy could not install the required packages for compiling the nvidia driver.

You should also try "*sudo envy --uninstall-all*" before trying Envy again.

---

### Post by ricardisimo on 2008-05-16
Well, something interesting happened. While I was waiting for responses on this issue I installed all of the restricted codecs and such for mp3s, DVDs, etc. and after these installed, I had to reboot. When I rebooted I was at a higher res... not the one I was looking for, but certainly better than 640*480. I was pleased, but then tried installing nvidia-legacy via Monitors & Display. I rebooted, and I'm right back where I started. I'm going to try fixing and/or uninstalling Envy as you suggested. 

Is there a way to just manually edit xorg.conf?

---

### Post by EXCiD3 on 2008-05-16
I never asked, which video card are you running and which version of ubuntu?

You can manually edit the xorg for this although you will want to make sure you have the correct refresh rates so that you dont screw up your monitor.

Here is an example of what the sections related to your videocard and monitor should look like when configured for the nvidia driver:

```
Section "Monitor"
    Identifier    "Philips 190S"
    Option        "DPMS"
        Option        "HorizSync"    "30-82"
        Option        "VertRefresh"    "56-76"
EndSection

Section "Device"
    Identifier    "nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
    Driver        "nvidia"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
    Monitor        "Philips 190S"
    Defaultdepth    24
    Option        "AddARGBGLXVisuals"    "True"
    SubSection "Display"
        Depth    1
        Modes        "1280x1024_60"    "1280x1024"    "1152x864"    "1024x768"    "832x624"    "800x600"    "720x400"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    4
        Modes        "1280x1024_60"    "1280x1024"    "1152x864"    "1024x768"    "832x624"    "800x600"    "720x400"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    8
        Modes        "1280x1024_60"    "1280x1024"    "1152x864"    "1024x768"    "832x624"    "800x600"    "720x400"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    15
        Modes        "1280x1024_60"    "1280x1024"    "1152x864"    "1024x768"    "832x624"    "800x600"    "720x400"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    16
        Modes        "1280x1024_60"    "1280x1024"    "1152x864"    "1024x768"    "832x624"    "800x600"    "720x400"    "640x480"
    EndSubSection
    SubSection "Display"
        Depth    24
        Modes        "1280x1024_60"    "1280x1024"    "1152x864"    "1024x768"    "832x624"    "800x600"    "720x400"    "640x480"
    EndSubSection
EndSection
```To get the screen modes for you computer run this in terminal:```

xrandr -q
```Then you can use the "cvt -v" command to generate the lines for your xorg. 

It will look something like this: ```
$ cvt -v 1440 900 60.0Hz
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
**Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync**
```

Then i think you can add the to xorg...Its definitely better if we can just figure out what is causing the nvidia driver from installing correctly. As you can probably see its not easy to configure it manually. ;)

---

### Post by ricardisimo on 2008-05-16
Thank you for still being awake.

I'm on Kubuntu 8.04, and here's what "sudo lshw" has to say about my graphics card:
```
*-display UNCLAIMED
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 4000]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: c1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=248 maxlatency=1 mingnt=5
```
I recall my monitor being generic, with a refresh at roughly 60. Not exactly hard science, but that's what I remember. Thanks again.

---

### Post by EXCiD3 on 2008-05-16
For now you may want to try adding this line to your xorg.conf:
```

Section "Device"
    Identifier    "Configured Video Device"
        Driver          "nv"
EndSection

```Restart the xserver (ctrl-alt-backspace) and see what your resolution looks like.

I dont mind being up this late, i usually am anyways ;) if you want, feel free to contact me via IM. We might be able to find a solution quicker that way. I'm probably going to go to bed soon.

---

### Post by EXCiD3 on 2008-05-16
You may want to try compiling the nvidia driver by hand since you had trouble with Envy. Here is a quick tutorial on how to do this: [http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/](http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/)

---

### Post by ricardisimo on 2008-05-16
Fortunately kate (or kubuntu itself) auto-saves previous version of system files like xorg.conf, and I found the oldest version and saved it as xorg.conf. So now I', at 1280x1024 which is close to what I'd like, but still no cigar. Mind you, at least I can bear to stare at the screen, which is good.

Here's the current xorg.conf:
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
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```
What's with the "Configured" stuff? Bizarre, if you ask me. Thanks again. I'm at work for the next several hours, unfortunately. If you're up, hats off to you.

---

### Post by EXCiD3 on 2008-05-16
The "Configured" stuff is just a way of naming the video devices and monitors. Mine has Screen0 instead. For some reason you have no Modes section in your xorg. You probably need this in order to get the correct resolution. If you know the correct resolution for your screen you could probably add it as a mode manually without using any of the nvidia-xconfig or nvidia-settings tools.

---

### Post by ricardisimo on 2008-05-16
Crap... I think it was 1400x1280, but I'm not sure. Does that sound right to you?

---

### Post by ricardisimo on 2008-05-16
And what's the "syntax", if you will, for it in my xorg.conf?

---

### Post by EXCiD3 on 2008-05-16
I would try under section Screen adding this and modifying it for the screen resolution you think is right:

```
Defaultdepth    24
SubSection "Display"
    Depth    24
    Modes        "1280x1024"
EndSubSection
```

If i had to take a guess id say 1400 x 1050 or 1600x1280 based on your 1280x1024 resolution that you currently have.

---

### Post by ricardisimo on 2008-05-16
It would appear that "sudo dpkg-reconfigure -phigh xserver-xorg" has been greatly neutered, if not completely castrated. I can't fathom why, but clearly someone figured I wouldn't still have a legacy card by now.

Sadly, I do, so now I'm on my own. Odd feeling, really.

---

### Post by RWells on 2008-05-16
I have been struggling with very simular problems, so I would love to see this resolved.

I downloaded 8.04 the day it was released, and have been trying to install it since that day,sometime lastnight around midnight it worked.

I now have Ubuntu Hardy Heron 8.04 installed and fully operational on one of three machines.
I have absolutely no idea what I did to fix it, I just thrashed around changing things and downloading stuff and so on.

Here is what I think.

Ubuntu 8.04 is supposed to have better hardware support and thinks it knows what is best for your system. However this new and improved system with better hardware support is a work in progress and is not complete.


I am pretty sure the solution to your problem will be a combination of getting the nvidia driver installed AND getting the correct monitor installed, I  don't think you will have any luck with generic or plug and play monitor.

I have had zero luck manually edditing xorg.conf, for somereason that always generated a error warning at the top of the xorg.conf.

and dpkg-reconfigure -phigh xserver-xorg has resulted in a black screen every time.

Rusty

---

### Post by EXCiD3 on 2008-05-16
Hopefully the 8.04.1 release will fix these problems. Unfortunately it appears that everyone with a legacy card is having trouble with Hardy. The best option I can think of is to go back to a previous version of Ubuntu which worked with your card. :( They still package software for Gutsy and Feisty, you just dont get the most recent software.

One thing you can do to help is to file bug reports about the nvidia-legacy driver on [http://launchpad.net](http://launchpad.net)

---

### Post by ricardisimo on 2008-05-16
It's more than a bit troublesome... one of the selling points to Ubuntu and Linux in general is that you can keep your hardware alive longer, but for me it's turning out to be quite the opposite. As it is, I had to finally break down and buy an Atheros wireless card, because my RaLink wouldn't work past Feisty (and rather poorly there, at that), and now I might have to buy a new graphics card as well.

This is interesting: > There are presently two Legacy GPU driver series. The 1.0-71xx series supports TNT, TNT2, GeForce 256, and GeForce2 GPUs. The 1.0-96xx series supports GeForce2 MX, GeForce3, GeForce4, and Quadro4 GPUs. For a complete list of the GPUs supported in each of the Legacy GPU driver series, see the lists below.  This is from the [nVidia web page on Legacy drivers]("http://www.nvidia.com/object/IO_32667.html"). I can swear that this was absolutely NOT the case with Feisty. This may be the cause of the problem. Let's see if I can get the proper "Legacy" up and running. I will report back.

---

### Post by EXCiD3 on 2008-05-16
Unfortunatley this is yet another reason holding users back in Windows territory because lots of things simply do not work. :( If its all the same you can always continue using feisty and compile software from source if you want a newer version. Another thing to consider is switching distros. Ubuntu is great for many, but not all. Some distros may have better support for your wireless and video drivers. Ubuntu seems to have hit some roadbumps with the last couple of releases.

---

### Post by ricardisimo on 2008-05-16
Envy-NG appears to have done the job this time, but 1280x1024 is still the upper limit, despite the fact that my xorg.conf lists "1600x1200" quite clearly in "Modes" under "Screen". And nothing resembling 1400xanything. Still, what I've got looks good.

I wonder if the problems everyone is having comes from trying to force the other "Legacy" driver to be used. I'm using the regular nvidia-glx right now, which was NOT the case under Feisty.

---

### Post by EXCiD3 on 2008-05-16
That could be that it is forcing the wrong driver. Does your nvidia-settings work now? You might be able to use it to configure now if the driver is installed correctly.

---

### Post by Victormd on 2008-05-17
> **ricardisimo said:**
> Envy-NG appears to have done the job this time, but 1280x1024 is still the upper limit, despite the fact that my xorg.conf lists "1600x1200" quite clearly in "Modes" under "Screen". And nothing resembling 1400xanything. Still, what I've got looks good.

I wonder if the problems everyone is having comes from trying to force the other "Legacy" driver to be used. I'm using the regular nvidia-glx right now, which was NOT the case under Feisty.

One thing that I've noticed, and even on the beginning of this thread, is that you tried to install envyng-gtk, but that's for ubuntu. If you're using Kubuntu, you should install envyng-qt... but I don't think many people make that distinction...

---

### Post by ricardisimo on 2008-05-17
> **Victormd said:**
> One thing that I've noticed, and even on the beginning of this thread, is that you tried to install envyng-gtk, but that's for ubuntu. If you're using Kubuntu, you should install envyng-qt... but I don't think many people make that distinction...

No, I saw that in Synaptic and chose the right one. The problem was that I was certain that I would be running the old "Legacy" driver, but not only are their now two "Legacies", apparently the GEForce4 MX has been bumped up a rung in the process. No idea how that works.

Does anyone know if the "nv" driver still being worked on, or is it pretty much as is for the rest of its life?

---

### Post by EXCiD3 on 2008-05-17
It doesnt look like there has been much work put into their 2D driver at all since '07. I bet if they felt it was pretty much stable and complete they would scrap the project and put their developers to work on the 3D driver seeing as its the one everyone wants.

---

### Post by ricardisimo on 2008-05-21
I take it all back... sort of. I did in fact get 1280x1024 working properly in Kubuntu, but then I returned to Ubuntu, mostly for reasons of personal preference, past experience, etc.

Now I cannot get any resolution above 1024x768 to work properly. 1280x1024 will run via EnvyNG and nvidia-settings, but application titlebars float off the top of the screen, and text in the terminal won't even appears on screen at all. Also, everything loads extremely slowly when booting up or restarting X. Very strange. I'd appreciate some tips.

Here's my xorg.conf right now (which is hopefully roughly what it was at install):
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Jan 22 19:53:46 PST 2008

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
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "altgr-intl"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
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
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```
Thanks in advance.

---

