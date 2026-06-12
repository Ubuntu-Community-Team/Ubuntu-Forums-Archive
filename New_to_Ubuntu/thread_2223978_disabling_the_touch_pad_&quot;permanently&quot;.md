---
title: "disabling the touch pad &quot;permanently&quot;"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by ross4 on 2014-05-13
I 've figured out how to disable my touch pad using xinput but this only lasts until I shut down the computer. When I start it up again, I have to go to the command line and re-enter the appropriate command. How can I get this to be a permanent thing, at least until I want to re-activate the pad?  Not sure if it is relevant but the details on my machine follow my salutation.  Regards, Ross Toshiba Laptop Satellite 500 Intel Pentium III processor 1.10 GHz, 512 MB of RAM, available hard drive space 26.7 GB Video Card: NVIDIA GeForce4 440 Go

---

### Post by squakie on 2014-05-13
Try:

sudo apt-get install synaptics <press enter>  - remember the "s" on the end or you'll get the package manager instead

This will install a touchpad package.  I also thought the setting you were looking for (turning off tap) was already an option under mouse and then touchpad.

---

### Post by coastwatcher on 2014-05-15
With Xubuntu 12.04, "[COLOR=#000000]sudo apt-get install synaptics" tells me that it cannot find any such package, and suggests that I install tpconfig instead.  I did that, but I cannot find anything that will drive a stake through the heart of my touchpad.

If I disable the touchpad in Settings -> Settings Manager -> Mouse and Touchpad, the change does not take effect until I log off and back on (that looks like a bug, but I really don't know.)  Then when I suspend the machine by closing the lid or by a Suspend menu item, the touchpad is reactivated when I open the lid and unlock the session, so I have to go use the Settings and then logoff and back on again to get rid of the touchpad.

There doesn't seem to be a separate module that I could blacklist at boot time to keep the touchpad from ever being recognized.  The code to support the touchpad seems to be in the same module as the code for the USB mouse, which I need to keep.  Am I going to be reduced to hacking code out of the mouse driver and building a custom kernel?  That seems more like the Slackware way than the Ubuntu way. <grin>


[/COLOR]

---

### Post by buzzingrobot on 2014-05-15
Check the BIOS setup to see if the touchpad can be disabled there.

---

