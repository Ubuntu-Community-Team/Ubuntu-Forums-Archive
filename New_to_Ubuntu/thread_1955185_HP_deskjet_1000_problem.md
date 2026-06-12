---
title: "HP deskjet 1000 problem"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by jrev on 2012-04-09
Hi,
I just bought an HP printer HP deskjet 1000-j110 serie connected via USB 
I tried it on 2 different computers running on Ubuntu 10.4
I checked the HPLIP driver  which is installed .
No noise is coming from the machine when I click on or off this machine the duty list is empty.
What shall I do ?
[http://www.zimagez.com/zimage/capture-impression-localhost.php](http://www.zimagez.com/zimage/capture-impression-localhost.php)
Thanks

---

### Post by Tamlynmac on 2012-04-09
Have you tried installing the HPLIP driver from [here]("http://hplipopensource.com/hplip-web/models/deskjet/deskjet_1000_j110_series.html")? I suggest you use the [wizard]("http://hplipopensource.com/hplip-web/install_wizard/index.html").

I've had a number of HP printers that required this downloaded HP driver for 9.04 & 10.04. Follow the instructions and don't forget to reboot both the printer & the PC after completion.

Good Luck & hope this helps.

---

### Post by daslinkard on 2012-04-10
jrev,

Are you connecting via USB or through Network, etc.?  I too have had much success in downloading from the HP web site as listed above.  Good luck!

---

### Post by jrev on 2012-04-10
I downloaded the hplip-3.12.2.run on my Desktop and went through the long installation process.
I then restarted  my computer and the printer to no success.
What did I forget ?

---

### Post by jrev on 2012-04-10
my first printer fjet 2400-series doesn't operate' any more ...

---

### Post by daslinkard on 2012-04-10
It seems that another user had success in this [post]("http://ubuntuforums.org/showthread.php?t=1810525") installing the printer you are trying to install.  The version they downloaded was hplip version 3.11.5.  Let me know what you find out.

---

### Post by jrev on 2012-04-11
I tried again on the second computer where the printer is due to be installed without any success.
Thanks for your help

---

### Post by ld114 on 2012-04-11
I had this problem on a Debian Squeeze installation with a different printer, and solved it by doing a complete re-installation of hplip from HP. The same option is available for Ubuntu 10.04 at:

[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

This installs the latest hplip, along with all the latest drivers.

---

