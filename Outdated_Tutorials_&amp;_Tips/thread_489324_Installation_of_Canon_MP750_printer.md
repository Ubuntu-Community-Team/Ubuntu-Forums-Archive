---
title: "Installation of Canon MP750 printer"
date: 2007-07-01
forum: Outdated Tutorials &amp; Tips
---

### Post by herman moolenaar on 2007-07-01
I just installed my MP750 printer in Ubuntu 7.04. The printer part of the MP750 is the same as the PIXMA IP4300. My printer is connected to a Windows XP machine and from there shared on the network. The information presented here is a combination of information I collected from other sites:

download the driver from: 
1) [http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx](http://www.canon.com.au/products/printers/colour_bj_printers/ip4300_support.aspx). The driver consists of 2 RPM's: cnijfilter-common* and cnijfilter-ip4300*.
2) sudo -s
3) apt-get update 
4) apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common
5) alien -d -i cnijfilter-common-2.70-1.i386.rpm
6) alien -d -i -c cnijfilter-ip4300-2.70-1.i386.rpm 
7) apt-get --reinstall install libpng3
8) ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3 
9) ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3 
10) ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1 
11) ldconfig 
12) /etc/init.d/cupsys restart 
13) Next add the new printer. In Ubuntu, this is accessed in System|Preferences|Printing. Select Canon as the manufacturer, click on "Install Driver..." and select /usr/share/ppd/custom/canonip4300.ppd. Now select "iP4300 Ver.2.70" under "Model". Select "Standard" for the driver (this should be the only option). Make sure the connection is correct.

Success!

---

