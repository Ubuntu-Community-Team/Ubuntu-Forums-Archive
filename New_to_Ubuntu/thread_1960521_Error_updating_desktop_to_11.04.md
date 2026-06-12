---
title: "Error updating desktop to 11.04"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by forestfields on 2012-04-17
Hi All

Made mistake of clicking 'update' button on my update manager to update which recommended I update to 11.04 (was using 10.04)

This didn't work so when you reboot machine (netbook) it says 'fail' at 'starting load fallback graphic devices' and then hangs at 'stopping userspace bootsplash'

I used (limited) command line knowledge and info on Ubuntu forums to try to complete the install and hit the following:
apt-get -f install
...after this operation 393kb additional diskspace will be used Y/N

I hit Y then it says:

dkpg:error processing /var/cache/apt/archives/xdiagnose_1.6_all.deb (--unpack): trying to overwrite /usr/share/apport/apport-gpu-error-intel.py, which is also in package xserver-xorg-video-intel 3:2.9down2.14.0+git20110220.9599fde6-0ubuntu0sarvatt~natty
Errors were encountered while processing:
/var/cache/apt/archives/xdiagnose_1.6_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can't get past it and I've tried to look at the bug report on this 824023 but it makes no sense to me. 



Help would be great ta

---

### Post by fleamour on 2012-04-17
I think it was a bug that you were able to update at all.  You were using 10.04 (LTS) which should only update to 12.04 (LTS.)  On the normal (non Long Term Support) channel you should upgrade to 10.10.

Cheerz.

---

### Post by mörgæs on 2012-04-17
If you are new to Buntu you might save a lot of time by doing a fresh install of 11.10 rather than fixing a broken upgrade.

---

### Post by forestfields on 2012-05-02
I just stuck with the first one I tried. I've tried to install 11.10 and 12.04 now from USB but it doesn't seem to be booting from the USB drive. I can see the USB and select it from the Boot menu but it doesn't actually boot and then it just hangs on the Ubuntu loading screen then I am unable to do anything other then turn it off. 

All that seems to be missing from completing the intstall of 11.04 is xdiagnose. Is there any way I can complete this upgrade and then worry about installing a different version of Ubuntu? 

Pretty stuck at the mo..

---

### Post by mörgæs on 2012-05-02
How did you create the USB stick? 
Does it boot in another computer?

---

### Post by forestfields on 2012-05-04
Yes, got the usb working and did fresh install of 12.04, now only thing is missing is that there isn't correct monitor resolution option available for my netbook (1024x600) - is something missing?

---

