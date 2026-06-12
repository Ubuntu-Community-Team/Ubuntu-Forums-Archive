---
title: "Broadcom 4318 Wireless on Hardy"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by adamgram on 2008-05-20
I'm trying to get the Broadcom 4318 Wireless Card to work on this laptop.  I have Ubuntu 8.4 installed with the Ubuntu Restricted extras downloaded and installed.  

In System -> Administration -> Hardware Drivers, the Broadcom B43 driver is listed as in use with the box for 'enabled' NOT checked.  Checking the box prompts a screen to enable and when pressed the status becomes 'Needs Computer Restart'.  If I close the window and reopen it, however, the status reverts back to 'In Use', and after a restart of the computer this behavior is no different.

I did do some things that may have caused or complicated this problem by following the instructions found here

[http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom+Corporation+BCM4318+](http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom+Corporation+BCM4318+)[Airforce+54g]+802.11g+Wireless+LAN+Controller

I initially completed the procedure described above using the step 2 as listed (for the wrong wireless card) and when that didn't work, I realized what I did and followed the instructions for the alternate step 2 as described in the link.  Several errors and attempted fixes later, I really don't know what is going on with my system, as I'm really not sure what the initial procedure was doing in the first place.  

Any help would be greatly appreciated, and and subsequent explanation of how these things work would be appreciated as well.

Oh yeah, one more thing that might help or be another problem altogether:  When I check for updates in the update manager I get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks in advance

---

### Post by adamgram on 2008-05-20
FINALLY!  It works now.  Link below for anyone else with this problem.  Careful with the quoted text, it's abbreviated at one part

[http://ubuntuforums.org/showthread.php?t=738216](http://ubuntuforums.org/showthread.php?t=738216)

---

