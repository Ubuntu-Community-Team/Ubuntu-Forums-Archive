---
title: "poor screen resolution after update"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by gecomle on 2008-11-19
I have installed some updates last week. After restart the 1280x1024 resolution does not appear any more in System>Preferences>Screen Resolution.

 I tried to edit /etc/X11/xorg.conf, adding following lines:
  SubSection "Display"
                Modes      "1280x1024"
        EndSubSection

Thus, now my "screen" section of /etc/X11/xorg.conf looks like:
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	 SubSection "Display"
                Modes      "1280x1024"
        EndSubSection
	Device		"Configured Video Device"
EndSection

However, no change took place even after reboot. Anyone can help me? Thanks!

---

### Post by puppywhacker on 2008-11-19
Hi,

You also need in the monitor section a line for the 1280x1024

this could be caused by not loading the new restricted-drivers for your video card. Like for my ATI I use the fglrx drivers.

like it suggest in the xorg.conf you could reconfigure X11 by running this.

sudo dpkg-reconfigure -phigh xserver-xorg

Goodluck

---

### Post by gecomle on 2008-11-20
Unfortunatelly, it did NOT help.

I can add the following information: my video board is "Intel G33/G31 Express Chipset Family". This I know from Windows, which is on the same disk.

Any other idea?

---

