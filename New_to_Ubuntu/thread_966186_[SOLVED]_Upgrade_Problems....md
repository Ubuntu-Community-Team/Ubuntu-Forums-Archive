---
title: "[SOLVED] Upgrade Problems..."
date: 2008-11-01
forum: New to Ubuntu
---

### Post by hatman on 2008-11-01
Upgraded, or attempted to upgrade from Hardy to Intrepid via Update Manager... too about 30 seconds to download updates (odd I thought, the one at work took a helluva lot longer) and then it set off... Went to work and came back, rebooted PC and now it wont do much...

Comes up in low graphics mode - not picked up my nvidia card, when running "System - Nvidia X Server Settings" I get an error saying "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

So I run sudo (and also gksudo) nvidia-xconfig in a terminal and nothing happens, it just pops another prompt in there...

Try to start x and nothing happens...

When running update manager I get:-

"Not all updates can be installed

Run a partial upgrade, to install as many updates as possible

This can be caused by:
A previous upgrade that didn't complete
Problems with some of the installed software
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu"

So I click on partial upgrade and then the following box pops up:

"Cannot upgrade

An upgrade from 'intrepid' to 'hardy' is not supported with this tool"

Trying to check the Repos in Synaptic and it always says they've changed and to hit reload, so I hit reload and it downloads the new information and then go to look at the repos again and it comes up again that they've changed and need to hit reload again, ad infinitum so can't check the repos using synaptic...

I don't want to have to remove everything and start from scratch again like I did with the upgrade to Hardy...

ta...

EDIT: Read through a few more threads and tried to sort it out with replies in those threads (X Server problems specifically) but now I can only get 600x480 resolution...

Ready for throwing in the towel and going back to XP, seem to be going round in circles, problems like this need to be sorted if we ever want Ubuntu to go mainstream...

---

### Post by Pro-reason on 2008-11-01
If you are having problems updating your Hardy installation to Intrepid, then do a clean installation of Intrepid.  It's the easiest option.  You will know, from booting from the live CD, whether Intrepid will work or not.

If you wish to fix your current installation, then you'd probably be best advised to run some commands to install the right video drivers.  Something like the following should do it:

```

sudo apt-get install envyng-gtk envyng-core
sudo envyng -t

```

You should also make sure that Intrepid is installed properly.  It seems likely that not all the packages downloaded, due to a connection problem.  The following might fix it:

```

sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by hatman on 2008-11-01
> **Pro-reason said:**
> If you are having problems updating your Hardy installation to Intrepid, then do a clean installation of Intrepid.  It's the easiest option.  You will know, from booting from the live CD, whether Intrepid will work or not.

If you wish to fix your current installation, then you'd probably be best advised to run some commands to install the right video drivers.  Something like the following should do it:

```

sudo apt-get install envyng-gtk envyng-core
sudo envyng -t

```

Damn! This didn't work.. still on 640x480, comes up as failed to load... 

> **Pro-reason said:**
> 
The following might fix it:

```

sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
Brilliant! Thanks for this, worked a treat, just got to sort out the video drivers now...

---

### Post by hatman on 2008-11-01
OK, almost all sorted, the upgrade worked perfectly after the instructions above were run.

The graphics instructions didnt work, so after the system had fully upgraded I removed all references to nVidia within synaptic and then ran the commands above.  It *appeared* to work but alas it hasnt worked fully... I'm no longer stuck to 640x480 or 800x600 but am running in my normal resolution of 1280x1024, however the graphics are still not 100%.  Looking in System --> Hardware Drivers shows no proprietary drivers as being loaded and on boot up I get the following error and options:

"UBUNTU IS RUNNING IN LOW GRAPHICS MODE
The following error was encountered.
You may need to update your configuration to solve this
(EE) Problem parsing the config file
(EE) Error parsing the config file

What would you like to do?
Run Ubuntu im low graphics mode for just this session
Reconfigure graphics
Troubleshoot the error"

Obviously I've run in low graphics mode cos I dont really have a clue when it comes to reconfiguring the graphics and fear I may make matters worse!

Anyway, the contents of my Xorg.conf file (if it helps) is:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Jan 22 19:53:46 PST 2008

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
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by Pro-reason on 2008-11-01
You should probably choose the option to reconfigure or troubleshoot.  I doubt you'll make it any worse than it is.

Here's some insurance:

Open a terminal and do this:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.kindaworks

```

That creates a back-up.  If you somehow mess up the video configuration completely, you should be able to restore it with the following:

```

sudo mv /etc/X11/xorg.conf.kindaworks /etc/X11/xorg.conf 

```

---

### Post by hatman on 2008-11-06
Tried both re-configuring and troubleshooting but both to no avail.  It works after a fashion (well, at least it's not stuck on 640x480 or 800x600) so I'll probably leave it as is and take this as an opportunity to get a larger hdd and start from scratch...

---

### Post by hatman on 2008-11-10
Just to update, I did an update during the week that (I think) included some changed files to do with nVidia.  After rebooting it started working on it's own, but the title bar was missing on all wiondows.  That only needed a change to the config in CCSM and now everything is up and running perfectly.. Still gonna upgrade hdd tho'...

---

