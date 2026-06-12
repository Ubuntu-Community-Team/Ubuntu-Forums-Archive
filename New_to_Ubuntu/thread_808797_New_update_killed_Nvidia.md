---
title: "New update killed Nvidia"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by kavon89 on 2008-05-26
I updated Heron with the system updater today (about 60Mb with a new wine update too) and noticed one of the updates said "linux.... somthing about a new kernel". I went ahead and updated my system and restarted as per request of the updater. Now my video/nvidia is broken.

```
kavon@kavon-thinkpad:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

How do I fix this? I need my graphics working asap. :/

---

### Post by drs305 on 2008-05-26
You might try installing/reinstalling nvidia-glx-new . The package says this is for newer cards. For older cards, it says nvidia-glx-legacy. It could be your drivers were dropped during the update. I don't remember having to reinstall anything on the update, but it's worth a try. I'll try to do some searching of the forum for an answer.

---

### Post by philinux on 2008-05-26
nvidia-glx-new did get updated today.

Why that should break things I've no idea. All ok here.

---

### Post by drs305 on 2008-05-26
Another post suggested hitting escape during the grub loading and then selecting the previous kernel. That worked for the nvidia user who was having problems (although not the same ones) with the new kernel.

Good luck.

Added: Hey, I went back to give credit to the suggester, and it was PHILINUX (see above) :lolflag:

---

### Post by philinux on 2008-05-26
Thanks though the problem has moved on by people saying reinstall the video drivers. But thats bad news for an update.

I hope people are reporting this via launchpad.

Must away to bed. Snooze .......

---

### Post by davidsrsb on 2008-05-26
Nvidia frequently relegate an older card from new to legacy
There is not much ubuntu can do about this.

---

### Post by madpeople on 2008-05-27
Hi I installed ubuntu 8.04 (release ending in 16) yesterday on a spare computer hooked up to my TV.

it all seemed to be going well, it had installed the nvidia driver after a popup appeared at the top, and everything was good. (had the extra effects turned on too)

then another popup appeared saying there were 102 updates, so I installed them, it said to restart, so i did.

I now had a 8.04 version ending with 17.
and when i tried to use this, i got a black screen (i think i also got it with the 16 version too now)

i used the restore mode to fix the X config, and i now had video, but it wasn't using the nvidia driver, which meant the gfx card wouldn't produce the right output for my screen (the default driver has the screen shifted off the edge of the screen on one side, and a black bar on the other, the nvidia one doesn't).

so i try downloading the driver from nvidia's website, but it says to remove all previous versions of their driver, i'm not sure how to do this, so i format the hdd and re-install ubuntu.
i then install the 102 updates and try the nvidia install.
it tells me that X is running and must be closed, i'm not sure how to do this so (after figuring out x = graphics) i start in restore mode and enter as root and run the nvidia install and it complains there are things missing and it can't get them (because the network isn't connected, and i don't know how to turn it on from command line).

after looking on these forums, i find a link to envy, i tried using envy to install the driver, it succeeds but now i have a black screen.

so i try using it to install an older driver, that worked, but still results in a black screen.

something in the update results in incompatibility with the nvidia drivers.

what should i do?

the machine is a
p4 1.7 Ghz
GeForce FX5900
3*256Mb SD ram
connected to internet via my lan (it is using a 10mbit Ethernet card)
(yeah, it's old, but i'm only using it as a dvd player and as a backup facility for my other computers)
:confused:

(sorry for long post)

i should probably mention i am good with computers, but new to ubuntu and linux, so you probably want to explain actions simply to me (i haven't figured out how to exit a "man" page in the terminal without just closing the terminal), but you can talk about more complex ideas

---

### Post by drarem on 2008-05-27
I have a thread on this exact thing; I had to go back to .16 in the grub menu to have nvidia working.

---

### Post by madpeople on 2008-05-27
just did a clean install again, this time i only installed a few of the updates, i left out the following:
jockey-common
jockey-gtk
libhal-storage1
libhal1
linux-generic
linux-headers-2.6.24-17
linux-headers-2.6.24-17-generic
linux-headers-generic
linux-image-2.6.24-17-generic
linux-image-generic
linux-restricted-modules-2.6.24-17-generic
linux-restricted-modules-generic
linux-ubuntu-modules-2.6.24-17-generic
xserver-xorg-video-intel

and i can't use the nvidia drivers which ubuntu suggests.
so it might be something else causing the problems?

PmDematagoda asked someone else for this, i don't know whether it would be useful
```
cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by Sinkingships7 on 2008-05-27
@ Kavon: The reason your drivers aren't working anymore is because they don't seem to get along with your new kernel. You updated from 2.6.24-16 to 2.6.24-17.

Reboot your system, and when grub starts to load, press Esc. Choose the generic 2.6.24-16 kernel.

Now your graphics card should work again.

To only use the older kernel, you can uninstall the new one via synaptic, or simply edit your boot/grub/menu.lst file.

If you need help, say so and someone will guide you through it.

---

### Post by kavon89 on 2008-05-27
Ok, I went ahead and booted up in the -16 instead of -17 kernel in Grub. It still said that it had to run in low graphics mode. So I went ahead and did:

```
sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm start
```

in the TTY thing, and I have a proper resolution, but the Nvidia menu is gone from the Applications>System Tools and moved itself to System>Adminstration. glxgears won't run and the Nvidia settings application complains that it isn't in use and tells me to run nvidia-xconfig as sudo.

I went ahead and stopped the gdm again and ran the command. and it told me:

```
Validation Error: Data Incomplete /etc/X11/xorg.conf.
Device configuration section "Configured Video Device" must have driver line.
```

I started gdm again and i'm back to low graphics 800x600 mode. Here is the current xorg.conf, what should I do now? :(

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Delever on 2008-05-27
Well, steps that helped me after kernel update (I am using beta nVidia driver):

To generate new xorg, I ran:

sudo dpkg-reconfigure -phigh xserver-xorg

Then logged out to restart X.

Killed gdm

sudo /etc/init.d/gdm stop

Then nvidia installer was able to modify xorg.conf properly. That *may* be true in your case too.

Then, restart:

sudo shutdown -r now

---

### Post by kavon89 on 2008-05-27
> **Delever said:**
> Well, steps that helped me after kernel update (I am using beta nVidia driver):

To generate new xorg, I ran:

sudo dpkg-reconfigure -phigh xserver-xorg

Then logged out to restart X.

Killed gdm

sudo /etc/init.d/gdm stop

Then nvidia installer was able to modify xorg.conf properly. That *may* be true in your case too.

Then, restart:

sudo shutdown -r now

That didn't work out. :( I feel like I've been doing the same commands over and over. How do I fully reinstall the nvidia drivers? I initally installed them menually from the website. I also restricted nv and nvidia and now I tried restricting nvidia_new in the restricted modules thing becase I had an issue earlier.

---

### Post by Delever on 2008-05-27
1. Rename your downloaded file which ends with .run to nvidia.run and place to your home directory (i.e. /home/delever)

2. Install libraries for compiling things:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

3. Reset xorg.conf to basic state (if you need some settings in xorg, make backup of it before running this):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

4. Log out, Log in. Resolution may have changed.

5. Turn off Gnome Display Manager, this will send you to console.
```
sudo /etc/init.d/gdm stop
```

6. Log in there.

7. Run nvidia installer:
```
sudo sh nvidia.run
```

8. Follow instructions, let it modify xorg.conf when it asks.

9. Start GDM again:
```
sudo /etc/init.d/gdm start
```

(I posted this on other thread, found out these steps myself with trial and error, so I still need some info to know if they really work)

EDIT: it worked, so you may try as well :)

---

### Post by kavon89 on 2008-05-27
> **Delever said:**
> 1. Rename your downloaded file which ends with .run to nvidia.run and place to your home directory (i.e. /home/delever)

2. Install libraries for compiling things:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

3. Reset xorg.conf to basic state (if you need some settings in xorg, make backup of it before running this):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

4. Log out, Log in. Resolution may have changed.

5. Turn off Gnome Display Manager, this will send you to console.
```
sudo /etc/init.d/gdm stop
```

6. Log in there.

7. Run nvidia installer:
```
sudo sh nvidia.run
```

8. Follow instructions, let it modify xorg.conf when it asks.

9. Start GDM again:
```
sudo /etc/init.d/gdm start
```

(I posted this on other thread, found out these steps myself with trial and error, so I still need some info to know if they really work)

EDIT: it worked, so you may try as well :)

This didn't work. I followed exactly and even tried restricting "nv nvidia" in the restricted file like before to get it to work out (i unrestricted it when i started this install).

I can't believe I ruined my entire system by clicking that stupid Update button. I'm loosing hope here.

---

### Post by Delever on 2008-05-27
> **kavon89 said:**
> This didn't work. I followed exactly and even tried restricting "nv nvidia" in the restricted file like before to get it to work out (i unrestricted it when i started this install).

I can't believe I ruined my entire system by clicking that stupid Update button. I'm loosing hope here.

None of those steps failed?

If so, next thing I suggest (if you are using nvidia card older than GeForce 9600), is to get program which automates driver installation:

Run ubuntu in Failsafe GNOME session.

```
sudo apt-get install envyng-gtk
```

Then run it from Applications->System tools->EnvyNG, select NVIDIA, and click APPLY.

---

### Post by kavon89 on 2008-05-27
I have tried uninstalling and reinstalling the Nvidia drivers through EnvyNG.

I have tried using kernel version .16, .16 recovery and used xfix as someone in IRC suggested.

I have tried using kernel version .17 recovery xfix option also suggested in IRC.

When I tried your way, no problems seemed to arise at all. The linux-headers thing said it was already installed for .17. Install went flawlessly as I had already installed the Nvidia drivers manually.

I haven't played much with the /etc/default/linux-restricted-modules-common file, to restrict nv or nvidia or nvidia_new. I had originally had restricted nv and nvidia to keep the system from using the wrong driver and I was fine and dandy before.

What should I do?

---

### Post by Delever on 2008-05-27
"restrict nv" should be added if you tried installing driver using nvidia installer.

Other than that, I have no more ideas. In what state is your desktop now?

---

### Post by kavon89 on 2008-05-27
I changed it to:

```
DISABLED_MODULES="nv"
```

Reinstalled and still have no luck. It puts my resolution to 800x600 and tells me it's running in low graphics mode when I install the driver and when I use nvidia's reconfigure command.

Using  sudo dpkg-reconfigure -phigh xserver-xorg  and starting gdm gets me back to a resoltuion that doesn't drive me nuts and is my regular, 1280x800.

Here is the xorg.conf when I have a proper resolution. Maybe all I need to do is add a line so it uses the nvidia driver properly?

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
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	InputDevice	"Synaptics Touchpad"
EndSection
```

I think I need to add these kinds of lines into that to get the nvidia running? How do I copy and paste this with nano or do I have to write it on paper?


Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

---

