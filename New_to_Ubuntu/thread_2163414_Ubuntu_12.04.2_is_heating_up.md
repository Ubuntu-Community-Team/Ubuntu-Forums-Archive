---
title: "Ubuntu 12.04.2 is heating up"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by Shimaa m a on 2013-07-18
I've installed Ubuntu 12.04.2 x64 as a second OS with Windows 7 x64. 

These are the issues I've faced till now:
1- The system heated up with even nothing running with so loud fan noise, and it even crushed due to overheating during the installation and i had to uninstall and reinstall again.
2- The wireless connects and disconnects all the time, and even when it connects the wireless button is still red not blue.
3- When Ubuntu is staring up, a black screen is opened and stays there till I press the button responsible for brightness on the keyboard.

Isn't Ubuntu install open-source drivers that should work fine- for fan control or graphics at least to get beyond the installation part-? 
If i wanted to install the drivers come with the hardware, do i need just the wireless driver and it'll automatically download the rest or do i have to manually install them all
-and maybe a one to survive the driver installation and avoid heating up- ?

Hardware: 
hp pavilion g series 

Thanks in advance

---

### Post by su:bhatta on 2013-07-18
Welcome to the Ubuntu Forums!

Ubuntu does come with a set of open source drivers that should work out of the box...
HP website has a list of G series Laptops, can you please provide your model no. and/or the specific Intel HD graphics card it uses, and if possible the wireless card details...

At this point do you have a working Ubuntu installation with you?

 If you have, then you can bring up 'Softwares & Updates' from the dash i.e. the topmost launcher on the dock on the left of your screen and on the last tab find 'Additional Drivers' If any Proprietary drivers are listed you can download them and activate them to check how it works, you will have to restart, for the driver to start working.

Also, you can try the Ubuntu 13.04 AMD64 iso & instead of Installing try a 'Live Session' i.e. 'Try Ubuntu' and find out if 13.04 works out of the box with your system....

---

### Post by mastablasta on 2013-07-18
those come with nvidia here. if you have nvidia GPU with optimus you might need to install bumblebee.

---

### Post by su:bhatta on 2013-07-18
Yes,... 
Check out bumblebee project at:

[http://bumblebee-project.org/](http://bumblebee-project.org/)

---

### Post by su:bhatta on 2013-07-18
Also, if you have the Windows Wireless Driver with you, you can download 'Windows Wireless Drivers' from the Ubuntu Software Center & use the windows wireless driver that you have...

see if that removes the problem of wireless...

---

### Post by Shimaa m a on 2013-07-18
@ bhattabhishek
The laptop model is g6 1256-ee

Ubuntu is installed but I can't do  much work using it as it heats up and i can't download because of the wireless issue. 
I may try Ubuntu 13.04 but it has no LTS, will the "live session" show all the issues ? I mean if it worked fine, will it work exactly the same after installation?

---

### Post by su:bhatta on 2013-07-18
The Live session works like an installation only... so that should not be a problem....
are you having Nvidia Optimus? then you can try Bumblebee...

See if 13.04 solves the issue, if it does, you can use 13.04, upgrade to 13.10 by Jan '14  & then go for 14.04 LTS...which is to be supported for 5 years...

Good luck...
see how things work out..

---

### Post by su:bhatta on 2013-07-18
duplicate post, Please ignore...

Good luck...

---

### Post by mastablasta on 2013-07-20
well accordign to this: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02993732&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5170320](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02993732&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5170320) 
it has radeon GPU 
[TABLE="width: 540"]
[TR="bgcolor: #E7E7E7"]
[TD="align: left"][/TD]
[TD="class: columnReducedMargin, align: left"]AMD Radeon HD 6470M[/TD]
[/TR]
[/TABLE]
and 
[TABLE="width: 540"]
[TR="bgcolor: #E7E7E7"]
[TD="align: left"][/TD]
[TD="class: columnReducedMargin, align: left"]2.4 GHz Intel Core i5-2430M[/TD]
[/TR]
[/TABLE]

this probably makes it a hybrid. Suggets 13.04 (for better experience) and also because it's a hybrid you definatelly need to install AMD GPU drivers.

have a look here for some further informaiton: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

the drivers can be installed using the additional drivers software: [http://linuxg.net/how-to-install-additional-drivers-in-ubuntu-13-04-from-the-gui/](http://linuxg.net/how-to-install-additional-drivers-in-ubuntu-13-04-from-the-gui/)

you might try that first as this GPU might work in 12.04.2.

---

