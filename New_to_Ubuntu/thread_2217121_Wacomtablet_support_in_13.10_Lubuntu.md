---
title: "Wacom/tablet support in 13.10 Lubuntu?"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by dkfrantz on 2014-04-15
Hello,

I have recently installed Lubuntu 13.10 on a Motion LE1700 tablet and the WACOM pen works, however I cannot find any way to change the settings or calibrate the pen.  Everything I can find on the subject is about Ubuntu and doesn't seem to apply to Lubuntu as none of the settings they are talking about in Ubuntu are in Lubuntu.  I've tried searching around but am only finding responses for older versions of installs and nothing seems to really apply to Lubuntu anyways.  

I just want to:

Calibrate the pen
Set pressure to work as right click (if possible)

Its very hard to get to the edges of the screen without calibration.  Thanks in advance.

---

### Post by dkfrantz on 2014-04-16
I went ahead and reinstalled xinput-calibrator and got it working by running it in the terminal window as the option for it in System Tools > Calibrate Touchscreen only brings up a blank term window.  Command was "xinput_calibrator".

It gives me coordinates to use in a file called 99-calibration.conf that is supposedly located in /etc/X11/xorg.conf.d/ , however no such directory exists.  So I found that on *ubuntu , the directory is located at /usr/share/X11/xorg.conf.d/ .  Progress.  No file called 99-calibration.conf exists so I create it.  Reboot.  Defaults are still all wrong and its not using the snippet given to me by the xinput_calibrator script.  So I'm looking to verify that I am using the right info in the 99-calibration.conf and don't have something wrong.

xinput list:
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]

The xinput_calibrator snippet:
Section "InputClass"
    Identifier    "calibration"
    MatchProduct    "!!Name_Of_TouchScreen!!"
    Option    "MinX"    "98"
    Option    "MaxX"    "24591"
    Option    "MinY"    "12"
    Option    "MaxY"    "18454"
EndSection


What I changed:
Section "InputClass"
    Identifier    "calibration"
    MatchProduct    "Serial Wacom Tablet stylus"
    Option    "MinX"    "98"
    Option    "MaxX"    "24591"
    Option    "MinY"    "12"
    Option    "MaxY"    "18454"
EndSection


Do I have everything correct here or did I put something wrong?  Thanks

---

### Post by pdc on 2014-04-16
we have been using a 680 recently; but it now works adequately so I haven't attempted to adjust things

googling suggests such things as this linux mint post [http://forums.linuxmint.com/viewtopic.php?f=109&t=108973](http://forums.linuxmint.com/viewtopic.php?f=109&t=108973) 

and I guess you worked through such posts as this [http://www.thefanclub.co.za/how-to/how-ubuntu-1204-touchscreen-calibration](http://www.thefanclub.co.za/how-to/how-ubuntu-1204-touchscreen-calibration)

and this [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration) and of course this [http://www.freedesktop.org/wiki/Software/xinput_calibrator/](http://www.freedesktop.org/wiki/Software/xinput_calibrator/)

___________________

sounds like detailed work needed; do post back to us as your research will be really helpful for others

---

### Post by dkfrantz on 2014-04-21
Thanks for the response.

The links you provide have conflicting information in them.  Granted, one is for Mint and one for Ubuntu but it seems like both should work the same.  Here's the conflicting info:

> 

[LIST]
[*] 		Once you have determined the x and y co-ordinate information, you need to add it to the X11 configuration files, for the **evdev** driver, the default installed driver used for handling Touchscreen input events.
[*] 		The X11 configuration for the Touchscreen can be found in the **&#8203;/usr/share/X11/xorg.conf.d/10-evdev.conf **file.
[/LIST]

conflicts with

> 
The wiki is wrong telling you to modify the evdev touchscreen snippet in  /usr/share/X11/xorg.conf.d/10-evdev.conf.  Custon user .conf's belong  in /etc/X11/xorg.conf.d.  You may have to create that xorg.conf.d  directory (mkdir).  The /usr/share/X11/xorg.conf.d location is for the  Distribution.

I can confirm that I have tried putting this info in both 10-evdev.conf and 99-calibration.conf in the /usr/share/X11/xorg.conf.d/ directory and no changes are saved in either case.  Even after a restart, the default values for the screen calibration remain exactly the same.  Plus I can put absurd numbers in both which should result in the Wacom pen not acting correctly (small field) and it still works just as it did previously.

I will try creating the directory in /etc/ and see if it makes any difference next I suppose.

---

