---
title: "NVDIA driver kernel module mismatch"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by monkeymoo on 2008-05-01
I recently installed the new NVIDIA driver as previously X wouldn't load and I was stuck with the command line, and it was the best solution I could think of (I'm sure most of you can think of better ones). 
I downloaded it from their website: NVIDIA-Linux-x86_64-173.08-pkg2.run, I have 64bit Gutsy installed so this seemed like the right one to choose. 

So from the command line I used, ```
sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run
``` to install it. 
Everything seemed to go fine with the install, and I said yes to it auto-configuring my xorg file. After it had finished it exited to the command line again. I typed ```
startx
``` and my desktop loaded up and I was very happy with myself (to soon) as everything worked marvellously and looked great. Even compiz was working, although I turned it off as I'm not too keen on the effects, but it shows the graphics driver was working well. 

The bad news came when I booted up the computer next day. Again X didn't start and I was left at the command line, not what I expected. I tried startx again and I got this error message. > Error: API mismatch, this NVIDIA driver component has version 173.08, but the NVIDIA kernel module's version does not match. Please make sure that the kernel module and all NVIDIA components have the same version.

Now I read the NVIDIA driver readme and it does mention that you need to re-install the driver if you change the kernel as otherwise they won't match, but I haven't changed the kernel at all, all I did was shut down and boot the next day! 

So what I did was to reinstall the driver again. After that everything was working fine again. Problem is, every time I reboot get this error and I have to reinstall the driver to get going. I don't really want to have to do the installation every time I boot my computer so a better solution would be hugely appreciated. 

My kernel is: Linux SD39P2 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux and my GPU is GeForce 8500 GT. And I'm happy to provide any other info that is relevant, just ask.

---

### Post by monkeymoo on 2008-05-01
I'm happy to consider alternative ways of getting things to work without using the NVIDIA manual install driver if there is one. 

Anything?

---

### Post by skymera on 2008-05-01
Ok this is how i do it.
Works flawless every time

Go to the the terminal and type:

```
 sudo aptitude install envyng-gtk 
```

the go Applications -> System Tools -> EnvyNG
Follow the steps and restart.

If you have wrong resolution open the terminal and type:

```
 sudo nvidia-xconfig 
```

---

### Post by monkeymoo on 2008-05-01
> **skymera said:**
> Ok this is how i do it.
Works flawless every time

Go to the the terminal and type:

```
 sudo aptitude install envyng-gtk 
```

the go Applications -> System Tools -> EnvyNG
Follow the steps and restart.

If you have wrong resolution open the terminal and type:

```
 sudo nvidia-xconfig 
```

Thanks, but when I do ```
 sudo aptitude install envyng-gtk 
```

I get > Couldn't find any package whose name or description matched "envyng-gtk"

---

### Post by Nepherte on 2008-05-01
Envy is only in the hardy repositories. Download the envy package for the correct ubuntu version here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
and install the deb package.

---

### Post by monkeymoo on 2008-05-01
Thanks. I got the envy.deb and followed the install instructions. Then I started up the envy GUI and told it to install the nvidia driver. It did it's thing and didn't report an error. I said yes to letting it set up the Xorg.conf file and then yes to the suggested restart. 

On restart I thought it was going to work when the fullscreen nvidia logo splashed onto the screen, but then it disappeared and left me with the command line. 
Tried "startx" and no go. 

So I manually installed the nvidia driver again and here I am, back where I started. 

Any other ideas?

---

### Post by martrn on 2008-05-01
I dunno if this will answer your question or not. I have only just found out today myself this...

Have a look at your /etc/X11/xorg.conf  file
If it contains a complete pile of tosh, you need to put it back to the origional, how it was.  Hopefull you will have a backup in your /etc/X11 folder.

If you are using gdm you need to turn bullet proof x off
[http://people.ubuntu.com/~bryce/BulletProofX/]("http://people.ubuntu.com/~bryce/BulletProofX/")

If you are using kdm this don't use bullet proofx, cool.

I don't know if its bullet proof x causing your probs or not or if it is, this only applys if it is.

---

### Post by monkeymoo on 2008-05-01
> **martrn said:**
> I dunno if this will answer your question or not. I have only just found out today myself this...

Have a look at your /etc/X11/xorg.conf  file
If it contains a complete pile of tosh, you need to put it back to the origional, how it was.  Hopefull you will have a backup in your /etc/X11 folder.

If you are using gdm you need to turn bullet proof x off
[http://people.ubuntu.com/~bryce/BulletProofX/]("http://people.ubuntu.com/~bryce/BulletProofX/")

If you are using kdm this don't use bullet proofx, cool.

I don't know if its bullet proof x causing your probs or not or if it is, this only applys if it is.

Thanks. My /etc/X11/xorg.conf seems to be pretty reasonable (below). 
I don't know anything about that bulletproofx thing, or how to check if I'm using it and how to turn it off if I am. Any hints? 


> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed Apr  2 08:22:13 PST 2008

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
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
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
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
        Modes      "1440x900" "1024x768" "800x600"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


---

### Post by martrn on 2008-05-01
The only other thing I can find is from nvidia, and it states:
(I am cutting and pasting, visit to find out more)....
[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Please note: unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.

I have no idear apart from that.
Sorry.

---

### Post by monkeymoo on 2008-05-01
That sounds like it might be useful. 

I'm pretty sure I have the first 3 *'s covered, but the last one and the stuff after that I certainly haven't done myself. I will check it out. 

Thanks for your help.

---

### Post by bodhi.zazen on 2008-05-01
> Error: API mismatch, this NVIDIA driver component has version 173.08, but the NVIDIA kernel module's version does not match. Please make sure that the kernel module and all NVIDIA components have the same version.

This error message results when you have both the open source (nv) (nvidia-glx or nvidia-new-glx) drivers installed as well as the Nvidia Proprietary driver.

To resolve the issue you need to remove the open source drivers and re-install the nvidia driver.

You may or may not need to black list the nvidia-glx-new, better just remove it.

nvidia-glx-new has a nasty bug, has bee reported long ago but remains unresolved.

```
sudo apt-get remove --purge nvidia-gls nvidia-new-glx
sudo rm -f /lib/linux-restricted-modules/.nvidia_new_installed
```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

To black list modules, if needed (you should not need to do this if you remove the drivers as above).

```
sudo nano /etc/default/linux-restricted-modules-common
```

Add this to he DISABLED_MODULES line to make it look like this:-

```
DISABLED_MODULES="nv nv_new"
```

Now reboot

Then re-install the nvidia driver (using the nvidia script or envy).

Reboot -> gksu nvidia-settings

---

### Post by monkeymoo on 2008-05-01
Many thanks martrn and bodhi.zazen. The key seems to be purging those old packages and deleting the old files. 
Everything seems to be working fine now, even after restarting! 

Your help was much appreciated!

---

