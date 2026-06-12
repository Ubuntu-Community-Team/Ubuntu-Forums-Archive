---
title: "Canon iP1700 printer"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by sammasaurus on 2008-11-11
Hello.  I just installed Linux and am unable to use my printer, a Canon iP1700.  Their website lists no software (and I'm guessing drivers) for Linux.  Any ideas?

Canon's website: [http://software.canon-europe.com/products/0010384.asp](http://software.canon-europe.com/products/0010384.asp)

The printer does show up when I go to print from Open Office, but I get a message that says "error while printing."  I'm guessing this is because my driver is no longer on the comp (as I entirely reformated to get linux).

Also, I have my driver CD still, but I have no idea what to access or how to put it on my computer.  Er....

---

### Post by dracayr on 2008-11-11
use the ip2200 drivers from that page. (download the .tar.gz)

dracayr

---

### Post by sammasaurus on 2008-11-11
I can't find what you're talking about .. For some reason absolutely nothing comes up when I say my OS is linux.

---

### Post by sammasaurus on 2008-11-11
I followed these directions to no avail:

[http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/](http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/)

Any ideas?  The printer shows up on the page but the test page won't print, and I also still cannot print from OpenOffice.

---

### Post by sammasaurus on 2008-11-12
> **dracayr said:**
> use the ip2200 drivers from that page. (download the .tar.gz)

dracayr


Ok, so I've found the file and I also downloaded alien.  The .tar file is now extracted and sitting on my desktop, and I have no idea what to do.  I'd really appreciate your help here, I'm a full-time student and can't afford to not have a printer. :/

---

### Post by dracayr on 2008-11-14
install alien
after extracting, you should have some .rpm files. convert those to .deb files using ```
alien --to-deb *file.rpm*
``` then install the debs (via doubleclick or dpkg)

Then add the printer through CUPS ([http://localhost:631](http://localhost:631)) Choose iP1700 on USB#1 Choose iP2200 PPD

try to print test page again.

dracayr

---

### Post by sammasaurus on 2008-11-14
I have the .deb files on my desktop (two of them unpack as the same file name, so there are 4 .rpm files, 3 .deb files.  When I try to install one of the .deb files, it stops with the following error:

cnijfilter-ip2200_2.60-1_i386.deb

Warning: Skipping conversion of scrips in package cnijfilter-ip2200: postinst postrm
Warning: Use the --scrips parameter to include the scripts

Then I use package installer and I get
(Reading database ... 108921 files and directories currently installed.)
Unpacking cnijfilter-ip2200 (from .../cnijfilter-ip2200 2.60-1_i386.deb) ... 
dpkh: error processing /home/sam/Desktop/cnijfilter-ip2200_2.60-1_i386.deb (--install):
trying to overwriter `/usr/lib/bjlib/cifip2200.conf', which is also in package libcnbj-2.6
dpkg-deb: subprocess paste killed by signal (Broken pipe)

---

### Post by baAng on 2008-12-13
Hello all..

For your information, you can use iP1800 driver for iP1700. I've been  trying all those tips and solutions but i found this solutions is the best.

Actually, this driver is from Canon Australia with the .rpm format. Luckily, a kind hearted person has "alien"ed it for all.

**Step One**

Connect your printer (your printer must be connected in order to proceed)
and Install this [Common Filter]("http://www.box.net/shared/ouagas9zrg")

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

