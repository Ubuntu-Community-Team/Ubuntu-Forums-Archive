---
title: "Hardy Xconf"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by jtclicker on 2008-05-04
I'm strill trying to get my nvidia driver to work... I've read that hardy changed the way X11/xconf works. Can anyone point me a to a page that explains how? I'm trying to understand what could have gone wrong with the upgrade from Gustsy to Hardy

---

### Post by philinux on 2008-05-04
What's your specs, mine installed itself almost apart from desktop effects.

---

### Post by jtclicker on 2008-05-04
I'm running geofrce4 MX440. I load the restricted driver, activate it and reboot. Before the loggin screen the monitor turns off. I then start in recovery mode and auto reconfig the xconf. Xconf that works is
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

Xconf that fails on boot after initialising the nvidia driver is

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
	Option		"Emulate3Buttons"	"true"
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

---

### Post by jtclicker on 2008-05-04
anyone any ideas? I'm struggling with this, so could do with a pointer to how the hardy xconf has changed from gutsy or any specific ideas??

---

### Post by NewDisciple on 2008-05-04
I believe that "nvidia" must be edited to be "nv".
Edit with text editor and reboot.

---

### Post by graben3 on 2008-05-04
> **jtclicker said:**
> I'm strill trying to get my nvidia driver to work... I've read that hardy changed the way X11/xconf works. Can anyone point me a to a page that explains how? I'm trying to understand what could have gone wrong with the upgrade from Gustsy to Hardy

I just installed ubuntu Hardy a couple days ago and I used Envy to install the nvidia drivers correctly for me. This program is in synaptic software channels.

There are 2 versions on envy one for the old cards and one for the new cards. My card is a gt 7600 so I choosed the new one (EnvyNG). It installed all drivers fine.

Then I lauched the nvidia display utility to configue my screens, Xinerama dont work anymore so I onfigured them in twinview and it works with 3d accel /compiz on both screens.

When you lauchch the nvidia app, dont forget to edit the menu command and add gksudo before the existing command because it wont save anything in your xorg.conf unless you do so.

---

### Post by jtclicker on 2008-05-04
Thanks guys I'll try these and report back

---

### Post by jtclicker on 2008-05-04
HMM Envy crashed on startup, and changing the driver to 'nv' didn't do anything. But I'll follow through the Envy path, see if i can get it to work

---

### Post by glennric on 2008-05-04
You don't want "nv" you want "nvidia" to use the proprietary nvidia drivers and not the open source drivers.

---

### Post by jtclicker on 2008-05-04
that is what I've been using and it is failing at boot. I posted the xconf in the first post, I'm basically trying anything and everything to repair the damage updating to Hardy did!

---

### Post by 67GTA on 2008-05-04
The new xorg wasn't ready for a LTS release. It has left several people cold. I have Hardy on two machines with Nvidia graphics. They both worked flawlessly with the last 3 releases. Now with Hardy, I could not get anything past 800x600 res. I had to use Envy to install the drivers, and manually edit xorg.conf to get my native resolutions. Not good...

---

### Post by jtclicker on 2008-05-04
well, I got envy to work, rebooted and then the monitor went offline during the reboot, same as with the gui...
here is the xorg.conf as done by envy...

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
 
Is this a bug in Hardy?? Should I report it? Is anyone working on it?

---

### Post by philinux on 2008-05-04
This is mine using ubuntu's nvidia driver.

```
 cat /etc/X11/xorg.conf
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
	Option		"XkbLayout"	"gb"
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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by 67GTA on 2008-05-04
It is a bug with the new xorg. You need to file a bug report with your hardware/graphics card info on launchpad. The bug with my desktop card was fixed after posting my info on launchpad. No one has even looked at the bug I posted for my laptop card. Maybe someone will help.

---

### Post by jtclicker on 2008-05-04
Phil, That is basically what I have when I use the ubuntu restricted driver but it falls over at boot. I've seen old problems like this where the xconf was pointing to the wrong video bus, but that kind of instruction isn't in the new Hardy xconf

---

### Post by jtclicker on 2008-05-04
> **67GTA said:**
> It is a bug with the new xorg. You need to file a bug report with your hardware/graphics card info on launchpad. The bug with my desktop card was fixed after posting my info on launchpad. No one has even looked at the bug I posted for my laptop card. Maybe someone will help.

Thanks Ill post a bug

---

### Post by 67GTA on 2008-05-04
The old dpkg tools were taken out of the Hardy build,(dpkg-reconfigure xserver-xorg) will no longer work. The only tool given to us now is ```
displayconfig-gtk
```. It is useless if your driver isn't being detected correctly(ecspecially nvidia).

---

### Post by starcannon on 2008-05-04
I run Nvidia on most of my machines, I got it up and running in Hardy the same way I have in all previous versions of Ubuntu, you'll need to download drivers for your particular card from here:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Then follow the directions on this page.

 [http://ubuntuforums.org/showthread.php?p=4873702#post4873702](http://ubuntuforums.org/showthread.php?p=4873702#post4873702)

Thats how I set up 2 Hardy Desktops and 2 Hardy Laptops. 1 has a 6600gt another has twin 7950gt's sli'd together, and the laptops both run 8400m gs cards. I will be doing a geforce2 go card this week, I expect it will go in the same way.

GL

---

### Post by jtclicker on 2008-05-04
Thanks, yes I found that early in my quest and it didn't work!

> **starcannon said:**
> I run Nvidia on most of my machines, I got it up and running in Hardy the same way I have in all previous versions of Ubuntu, you'll need to download drivers for your particular card from here:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Then follow the directions on this page.

 [http://ubuntuforums.org/showthread.php?p=4873702#post4873702](http://ubuntuforums.org/showthread.php?p=4873702#post4873702)

Thats how I set up 2 Hardy Desktops and 2 Hardy Laptops. 1 has a 6600gt another has twin 7950gt's sli'd together, and the laptops both run 8400m gs cards. I will be doing a geforce2 go card this week, I expect it will go in the same way.

GL

---

### Post by starcannon on 2008-05-04
Can you post the xorg.conf from your attempt, I'm a little puzzled, this is the method I use on my bunch of nvidia machines and it never fails, so I either forgot to post part of my method, or something failed.

If when your done with the steps I listed want to have the nvidia driver go back through your xorg.conf then type ```
sudo nvidia-xconfig
``` at a command line, I always back up the old xorg.conf file and remove it then let nvidia build one from scratch.

I'll hang in there with you till its solved if you like.

---

### Post by jtclicker on 2008-05-04
starcannon thanks, I'll try it in the morning

---

### Post by ibbill on 2008-05-04
this is how I did my after a lot of frustration I may add not sure why  Hardy Heron would cause this. As Gutsy worked fine

[http://ubuntuforums.org/showthread.php?t=766846&highlight=nvidia&page=2](http://ubuntuforums.org/showthread.php?t=766846&highlight=nvidia&page=2)

---

### Post by jtclicker on 2008-05-04
> **ibbill said:**
> this is how I did my after a lot of frustration I may add not sure why  Hardy Heron would cause this. As Gutsy worked fine

[http://ubuntuforums.org/showthread.php?t=766846&highlight=nvidia&page=2](http://ubuntuforums.org/showthread.php?t=766846&highlight=nvidia&page=2)

thanks same problem, monitor turned off at boot. I'm not actually seeing anyone else reporting this exact problem...

---

### Post by jtclicker on 2008-05-05
Hi Starcannon, followed your steps and got the same problem and the same xconf, I'm using the very latest driver


Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
Option "AddARGBGLXVisuals" "True"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
EndSection
Section "Module"
Load "glx"
EndSection

---

### Post by jtclicker on 2008-05-05
sorry, wrong xconf
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
    Driver         "keyboard"
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
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

