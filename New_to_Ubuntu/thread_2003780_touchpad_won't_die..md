---
title: "touchpad won't die."
date: 2012-06-14
forum: New to Ubuntu
---

### Post by solitario on 2012-06-14
I followed the instructions here, several times:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

When I restart, the touchpad is disabled, sometimes enabled.

This was after the same inconsistent results with the "Touchpad-indicator" program I downloaded through the software manager.

Any advice on how to permanently disable the touchpad without tearing apart the hardware is appreciated.

Thanks.

P.S. Here are the results of running xinput list.

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]

---

### Post by limpdisk on 2012-06-16
Don't know what Ubuntu version you're using but on my 10.04 laptop I open up the Configuration Editor by holding down the left-side 'alt' key and pressing F2.

In the small window, type "gconf-editor" (without the quotes) and click 'run'.

In the new window, expand the 'desktop' folder by clicking on small icon on its left.  Expand the 'gnome' folder clicking on its icon. Drop down and expand the 'peripherals' folder.

Click on the 'touchpad' folder. In the window to the right, drop down to 'touchpad_enabled'.  If the small square to the right has a check mark in it, click on the square to remove it.

Close out Configuration Editor.

Hope this helps

---

### Post by solitario on 2012-06-20
Hi limpdisk.
Unfortunately I couldn't find the Configuration Editor.
I also did a sudo gconf-editor which turned up nothin.
I'm on Ubuntu 12.04 LTS.

Anyone? I do a lot of typing and my accidentally tapping the touchpad is really slowing me down. Muchos thanks.

---

### Post by solitario on 2012-06-21
got it. (at least I think)

I added this command, replacing "15" with the device number of my touchpad:
xinput set-prop 15 "Device Enabled" 0

AND

Followed [this tutorial]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") so as to run the above script on start up.

thanks.

---

