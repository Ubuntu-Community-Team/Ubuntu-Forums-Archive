---
title: "instalation printer canon IP1700"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by rVan on 2008-07-23
i have printer canon pixma IP 1700, and i want to install the driver so that i can use the printer. but how to install them??
thanxx.

---

### Post by enlightenment now on 2008-07-23
> **rVan said:**
> i have printer canon pixma IP 1700, and i want to install the driver so that i can use the printer. but how to install them??
thanxx.

[https://answers.launchpad.net/ubuntu/+question/22555](https://answers.launchpad.net/ubuntu/+question/22555)

---

### Post by baAng on 2008-12-13
Hello all..

For your information, you can use iP1800 driver for iP1700. I've been  trying all those tips and solutions but i found this solutions is the best.

Actually, this driver is from Canon Australia with the .rpm format. Luckily, a kind hearted person has "alien"ed it for all.

**Step One**

Connect your printer (your printer must be connected in order to proceed)

[B]Step Two
[/B]
Install your package. Get it here
[cnijfilter-ip1800_2.70-2_i386.deb]("http://www.box.net/shared/x4avbcfzft") **(Gusty & Earlier)**
[cnijfilter-ip1800_2.70-2_i386-hardy.deb]("http://www.box.net/shared/4qnsdbmdl1") **(Hardy)**

You can install it through GDebi by double-clicking on them or by using this command through terminal

```
sudo dpkg -i /driver/download/location/file_name.deb
```

*This driver is subject to the terms of the Canon IJ Printer Driver License, which you must read and agree to before installing. It's the GNU General Public License v2 with additional copyright notices and disclaimers.*

**Step Three**

Configure your CUPS. go to this web interface [CUPS]("http://localhost:631/").

Click Administration --> Add Printers 
In this section, put your printer name (iP1800/iP1700), 
Location usb://Canon/iP1700 and Description is up to you.
In the second section, choose Canon --> Continue
In the last section, choose Canon iP1800 series Ver. 2.70 (en)

**Step Four**

Restart your CUPS by using this command

```
sudo /usr/sbin/invoke-rc.d  cupsys restart
```

Now, your iP1700/iP1800 printer is ready to eat papers 
:guitar:

---

### Post by elwood55 on 2008-12-16
I actually have an ip1800. I downloaded both drivers, but get the same error message trying to install either:

Dependency is not satisfiable:cnijfilter-common.

Found this filter at:
[http://caletalinux.blogspot.com/2007/07/canon-ip1800-drivers-en-ubuntu-feisty.html](http://caletalinux.blogspot.com/2007/07/canon-ip1800-drivers-en-ubuntu-feisty.html)

Installed common filter, then iP1800 filter, followed steps 3 & 4, printer works fine.

Thanks, baAng!

---

### Post by baAng on 2008-12-16
good to hear that ;D

---

### Post by cerabys on 2009-05-04
Yes these instructions work perfectly thank you so much both of you. I spent 2 days following instructions from different posts until I stumbled on this one because I just didn't want to give up. If anyone else is having trouble go to your synaptic manager, get rid of anything you installed previously regarding the canon filters and follow this post.

---

### Post by jtmedin on 2009-06-23
I also have a iP1700 + ubuntu 9.04. Am unable to get beyond cnijfilter-ip1800series* . Was unable to get the libxml1 pkg thru synaptic but found it on the web, that quited several errors but now I get a error return of 100 from a script. Anyone got any ideas? TIA

---

### Post by nipunshakya on 2012-04-11
> **baAng said:**
> Hello all..

For your information, you can use iP1800 driver for iP1700. I've been  trying all those tips and solutions but i found this solutions is the best.

Actually, this driver is from Canon Australia with the .rpm format. Luckily, a kind hearted person has "alien"ed it for all.

**Step One**

Connect your printer (your printer must be connected in order to proceed)

[B]Step Two
[/B]
Install your package. Get it here
[cnijfilter-ip1800_2.70-2_i386.deb]("http://www.box.net/shared/x4avbcfzft") **(Gusty & Earlier)**
[cnijfilter-ip1800_2.70-2_i386-hardy.deb]("http://www.box.net/shared/4qnsdbmdl1") **(Hardy)**

You can install it through GDebi by double-clicking on them or by using this command through terminal

```
sudo dpkg -i /driver/download/location/file_name.deb
```*This driver is subject to the terms of the Canon IJ Printer Driver License, which you must read and agree to before installing. It's the GNU General Public License v2 with additional copyright notices and disclaimers.*

**Step Three**

Configure your CUPS. go to this web interface [CUPS]("http://localhost:631/").

Click Administration --> Add Printers 
In this section, put your printer name (iP1800/iP1700), 
Location usb://Canon/iP1700 and Description is up to you.
In the second section, choose Canon --> Continue
In the last section, choose Canon iP1800 series Ver. 2.70 (en)

**Step Four**

Restart your CUPS by using this command

```
sudo /usr/sbin/invoke-rc.d  cupsys restart
```Now, your iP1700/iP1800 printer is ready to eat papers 
:guitar:


Sir, is there any procedure to get the driver work for 64 bit Ubuntu 11.04 with ip1700 printer?

---

