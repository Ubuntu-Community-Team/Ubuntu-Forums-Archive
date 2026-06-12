---
title: "problems with screen resolution 1176x664"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by xvampssx on 2013-09-07
trying to get my screen resolution to 1176x664. I read some previous posts but nothing is actually solving my problem. I am running Nvidia GT 210 2gb/ panasonic 32" w/ HDMI connected, And Ubuntu 12.04.

I did however read up on this post and it seems to be what I am looking for, but I am having problems executing some of the solutions posted here.

====================================================================================

From: [http://ubuntuforums.org/showthread.php?t=2120886&highlight=1176x664](http://ubuntuforums.org/showthread.php?t=2120886&highlight=1176x664)

actual kernel directly deal with X, so its normal and prefered to not  use xorg.conf (which can bring troubles if not set corectly). To be  sure, run:

     Code:
     sudo rm /etc/X11/xorg.conf 
then , from synaptic:

(if not already installed: sudo apt-get install synaptic)
- purge all the installed nvidia packages
- install that ppa to get the latest nvidia driver
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
- update & install : nvidia-313
-deactivate that ppa & update again
- reboot
====================================================================================

I installed synaptic, but now how do I, purge and install from PPA for latest driver, then deactivate?

---

### Post by carlwsnyder on 2013-09-07
I hope the listed nvidia-313 package supports your nVidia GT-210 display card.

You purge all installed nVidia packages by:
[LIST]
[*] searching for nVidia with the Synaptic search Quick Filter
[*] right-clicking and selecting the Mark for Complete Removal selection
[*] Then click the Apply icon
[/LIST]
You can install the PPA from Synaptic as well by selecting the Settings >> Repositories >> Other Software tab >> Add >> deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main and exiting back to the main Synaptic window.  
[LIST]
[*] Now select the Reload icon
[*] Use the Quick Filter again to look for nvidia and find the proper driver for your video system
[*] Mark it with a right-click for installation
[*] Click the Apply icon
[/LIST]
I wouldn't deactivate the PPA in case there are updates needed.  You also don't need to re-boot, you only need to log out and log back in again.

---

