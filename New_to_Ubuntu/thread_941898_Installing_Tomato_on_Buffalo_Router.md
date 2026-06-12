---
title: "Installing Tomato on Buffalo Router"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by ssdurn on 2008-10-08
I am trying to install Tomato onto my WBR-G54 router.

The tomato install notes tell me to either install from the routers firmware - this fails, or to run a .bat file, which wont work 'cos it's a windows file.

Any suggestions? I am sure I'm missing something obvious!

TIA

---

### Post by MrWES on 2008-10-08
so you went to your router via [http://192.168.1.1](http://192.168.1.1) and went to the upgrade firmware tab?

---

### Post by ssdurn on 2008-10-08
Yes, and browsed to the tomato.trx file, and clicked the upgrade button, and I keep getting an error message saying there has been a download error and to try again...

There are special directions for Buffalo routers on the readme.htm included in the tomato package: 

[INDENT][COLOR="RoyalBlue"]Installing from Buffalo's firmware

WARNING: Be aware that you may not be able to re-install the original firmware back if Buffalo only has the encrypted version of the firmware available for your router.

    * Push and hold the reset button on the router for a few seconds to reset the configuration.
    * Plug your computer directly to the router. This will not work over a wireless connection.
    * Set your computer's ethernet card settings to: IP=192.168.11.2, mask=255.255.255.0, gateway=192.168.11.1.

          In Windows, you can set this by going to Control Panel, Network Connections, right-click your ethernet card, click Properties, then select "Internet Protocol (TCP/IP)", then click Properties, click "Use the following IP address". You can leave the DNS settings blank. 

    * Make sure the red diagnostic light isn't lit on the router, unplug the power cable to the router, wait a few seconds, then re-plug.
    * Double-click on the whr_install.bat file
    * You only have a 5 second window to do this, so if it doesn't work, unplug and try again.
    * After uploading, wait. It still needs about 2 minutes to flash the image. [/COLOR][/INDENT]

This includes using the .bat file I am  having problems with.

---

### Post by MrWES on 2008-10-09
Were you doing this over a wireless or hard wired connection? Sounds like you bricked the router. Can you get ahold of the original firmware to flash it back?

---

