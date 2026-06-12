---
title: "How can I download this driver for my HD 4850 graphics card?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by psyoptic on 2008-10-22
I've been looking for a way to get the drivers for my graphics card, which is a Radeon HD 4850. I read somewhere that it's located in the Ubuntu repositories, but I'm not exactly sure what that is.

The driver I'm looking for is mentioned in this phoronix article if that helps. [http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1](http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1)

---

### Post by jamesrl on 2008-10-22
You have two options.  You can use the latest (free as in beer) propietary closed-source ati drivers from here:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

or you can use the closed-source (originally wrote *open-source*) drivers in the repositories.
To do go to the command prompt and install via the command:
(in ubuntu restricted repo)
```
sudo apt-get install xorg-driver-fglrx
```

If you don't have the repositories, make sure you have 
```

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

```
in your /etc/apt/source.list (to edit type sudo nano /etc/apt/sources.list)

---

### Post by LowSky on 2008-10-22
install Envy, then Launch the program it will install the proprietary driver for yout ATI graphics card.

---

### Post by psyoptic on 2008-10-22
> **jamesrl said:**
> You have two options.  You can use the (free as in beer) propietary closed-source ati drivers from here:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

or you can use the open-source drivers in the repositories, though often they don't work as well.

I want the open source drivers because they are supported with Intrepid Ibex. Do you know how I can access the repositories?

> **LowSky said:**
> install Envy, then Launch the program it will install the proprietary driver for yout ATI graphics card.

Envy doesn't work, I've tried.

---

### Post by jamesrl on 2008-10-22
See edit to my previous post as well as:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Also, I think I was wrong above about open-source/closed-source.

All drivers with fglrx in the name are closed-source binaries,
xserver-xorg-video-ati is the (inferior) open-source alternative.
You can install the versions in the repository, or the latest binary version from the website manually.
Envy (install envyng-gtk or envyng-qt in the package manager) is a program that is supposed to download and automatically install the proprietary latest version from ATI/nvidia website.

---

### Post by psyoptic on 2008-10-22
> **jamesrl said:**
> or you can use the closed-source (originally wrote *open-source*) drivers in the repositories.
To do go to the command prompt and install via the command:
(in ubuntu restricted repo)
```
sudo apt-get install xorg-driver-fglrx
```

I typed in that command. Now what should I do?

---

### Post by Nxion on 2008-10-22
This might help also
[URL="http://ubuntuguide.org/wiki/Ubuntu:Hardy#RadeonHD_driver_.28ATI_only.29"]
http://ubuntuguide.org/wiki/Ubuntu:Hardy#RadeonHD_driver_.28ATI_only.29[/URL]
[URL="http://www.phoronix.com/scan.php?page=article&item=842&num=1"]
http://www.phoronix.com/scan.php?page=article&item=842&num=1[/URL]

---

### Post by danilo74 on 2008-10-23
Hi all,

I'm not sure I'm posting my problem in the right thread (I'm new to linux, ubutntu, communities etc.).

I installed the ati 8.10 drivers following the guide in
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

that was indicated in many threads as the guide to follow to install drivers for the Radeon HD 4850.

I followed the guide and installed the driver (in manual mode because in many threads was indicated as the way to follow) but after reboot I have a complete black screen at login. After running the recovery mode and executing Xfix I can login again and apparently the driver is installed and in use but not enabled (that according to the guide is the correct situation, if I understand correctly).


Unfortunaly anyway if I run:

fglrxinfo

I obtain:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

I checked how to remove the mesa drivers but none of the situations described in the guide apply to my case.

Does someone have any idea how can I fix the problem?

Thanks a lot in advance for any help.

PS:
My system is:
Motherboard: Asus M3A78-EM 780G
Processor  : AMD Phenom X4 9550 2.2GHz
Graphic    : PCI-e Asus Radeon HD4850 512MB
OS         : Ubuntu 8.04 Hardy

---

### Post by danilo74 on 2008-10-23
RADEON HD 4850 WORKING. The driver works correctly following the manual mode installation: (ubuntu way not working)

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The problem was that the monitor I was using had a wrong EDID and the ATI driver requires a correct one to have DVI output otherwise it switches automatically to analog (VGA).

Sorry for the false alarm.

I still have the problem that when I start xawtv the screen goes black and only way to recover is to reset the computer.


Hi all,

I'm not sure I'm posting my problem in the right thread (I'm new to linux, ubutntu, communities etc.).

I installed the ati 8.10 drivers following the guide in
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

that was indicated in many threads as the guide to follow to install drivers for the Radeon HD 4850.

I followed the guide and installed the driver (in manual mode because in many threads was indicated as the way to follow) but after reboot I have a complete black screen at login. After running the recovery mode and executing Xfix I can login again and apparently the driver is installed and in use but not enabled (that according to the guide is the correct situation, if I understand correctly).


Unfortunaly anyway if I run:

fglrxinfo

I obtain:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

I checked how to remove the mesa drivers but none of the situations described in the guide apply to my case.

Does someone have any idea how can I fix the problem?

Thanks a lot in advance for any help.

PS:
My system is:
Motherboard: Asus M3A78-EM 780G
Processor  : AMD Phenom X4 9550 2.2GHz
Graphic    : PCI-e Asus Radeon HD4850 512MB
OS         : Ubuntu 8.04 Hardy[/QUOTE]

---

