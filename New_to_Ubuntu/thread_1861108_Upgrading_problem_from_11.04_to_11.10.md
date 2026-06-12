---
title: "Upgrading problem from 11.04 to 11.10"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Ymurti on 2011-10-15
Please I need help. I had Ubuntu 11.04 on my laptop and yesterday I tried to upgrading to 11.10   As it was late I went to sleep while the packages were been downloaded. When I awoke the mouse was not working the computer had frozen. So I press the power for some time and turned off the laptop. When I tried to turn on again it comes till the point where I can choose between Ubuntu and windows (I have it installed with Ubuntu in my laptop) When I choose Ubuntu it does not launch my desktop. I have Ubuntu in a pen drive and I loaded it on my laptop. I used Disk Utility and tried to check and repair the filesystem but I got an error message. I took a Screenshot and here it is.

---

### Post by roger_1960 on 2011-10-15
Hi

Mmm  how long were you alseep for, the upgrade can take several hours.  I think you may have to erase the ubuntu partition (not the others) using gparted and then install ubuntu into the space created. (gparted is included in the ubuntu live iso)  Hopefully you already have your data backed up or on the NTFS partition?

In future, the safest way to upgrade from on version to the next (assuming you dont want a clean install) is to first burn the iso file to USB (or CD), run the live version from USB /CD and chose the "upgrade keeping existing data" option.  If you can, have an internet connection (wired) at the same time.

---

