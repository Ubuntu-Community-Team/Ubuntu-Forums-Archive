---
title: "broken pipe while installing printer"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by sammasaurus on 2008-11-17
Hello!

I'm trying to install the drivers for/make functional a Canon ip1700 printer.  When I try to install the .deb files, I get a "broken pipe" on the second .deb I install.

[SIZE="1"]sam@Mr:~/Desktop$ sudo dpkg -i cnijfilter-ip2200_2.60-2_i386.deb
(Reading database ... 108994 files and directories currently installed.)
Unpacking cnijfilter-ip2200 (from cnijfilter-ip2200_2.60-2_i386.deb) ...
dpkg: error processing cnijfilter-ip2200_2.60-2_i386.deb (--install):
 trying to overwrite `/usr/lib/bjlib/cifip2200.conf', which is also in package libcnbj-2.6
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 cnijfilter-ip2200_2.60-2_i386.deb[/SIZE]




Question #1: What the heck does "Broken pipe" mean, anyway?
and more importantly, #2 how can I fix this, or how else could I do it?



Also, I have tried the following guides to no avail:
[http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/](http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/)
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700)
[http://blog.indodx.com/archives/how-to-install-canon-ip1700-printers-drivers-in-ubuntu.jsp](http://blog.indodx.com/archives/how-to-install-canon-ip1700-printers-drivers-in-ubuntu.jsp)



Any help would be greatly appreciated.

---

### Post by NewJack on 2008-11-17
I came across this in Linux Forums: [http://www.linuxforums.org/forum/peripherals-hardware/91563-need-driver-canon-ip1700-fedora-core-3-a.html](http://www.linuxforums.org/forum/peripherals-hardware/91563-need-driver-canon-ip1700-fedora-core-3-a.html)

Leads to this page: [http://software.canon-europe.com/software/0024301.asp?model=](http://software.canon-europe.com/software/0024301.asp?model=)

Which if you look down towards the bottom of the downloads, there is a guide that you may want to download and maybe that will help you get the drivers on the above page installed.

Good Luck

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

