---
title: "Installing drivers for printer"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by loseby on 2012-05-15
I found out by right clicking you can extract the divers ( tar.gz file ) and have done that.I unzipped them onto the desktop and they are all in a folder called cnijfilter-mg6100series-3.40-1-rpm I opened this folder and dragged the install.sh into the terminal window as below and get this error. 

> william@Z77XUD5H:~$ '/home/william/Desktop/cnijfilter-mg6100series-3.40-1-rpm/install.sh' 
An error occurred. A necessary package could not be found in the proper location.
william@Z77XUD5H:~$ 


what am I doing wrong  ..... no bloody idea about terminal

---

### Post by BaffledMollusc on 2012-05-16
Edit 2: You don't need to install a driver; it's already available. Click on System Settings (the spanner and gear icon in launcher), click on "Printing", then click on "Add". Add your printer. At the appropriate point select the driver under Canon->PIXMA MG 6100. 

Edit: Are you sure you need to install these drivers? Most linux distributions ship with a *lot* of drivers by default. I'm having a hard time finding out for sure, but it looks like the MG6100 printer driver should come with Ubuntu 12.04 (see [https://bugs.launchpad.net/baltix/+bug/959043](https://bugs.launchpad.net/baltix/+bug/959043)). Anyway, if you definitely can't print, and *do* need to install the driver separately, keep reading:

Hi,

Your main problem is that you're trying to install an RPM package rather than a DEB package. 

Very roughly speaking, there are two ways of packaging software in the linux world - RPMs, used by Red Hat, Fedora etc, and DEBs, used by Debian, Ubuntu etc.

This thread seems to lay out the steps you need: [http://ubuntuforums.org/showthread.php?t=1656821](http://ubuntuforums.org/showthread.php?t=1656821)

One note: Where the above thread says "double click on the appropriate .deb file (386 or amd)" that's because you'll find four drivers in the "packages" directory:

cnijfilter-common_3.40-1_amd64.deb
cnijfilter-common_3.40-1_i386.deb
cnijfilter-mg6100series_3.40-1_amd64.deb
cnijfilter-mg6100series_3.40-1_i386.deb

If you installed a 64-bit version of ubuntu you'll need to double click on the two _amd64 packages; if you installed a 32-bit version of Ubuntu you'll need the two _i386 versions.

I haven't actually done the install, so I don't know if it works. Post again if you have problems!

---

### Post by loseby on 2012-05-16
the thing is its wireless so I am pretty sure that is why it wont pick it up


I might try actually connecting the print via cable firstly and see what happens.


edit...ok, that worked roughly  :-)

Printer is a 6150 and has a bottom tray but that wont work....have to put paper in at the back whick defeats the purpose of the printer ie. lack of space and opening the back takes up room if doesnt have 

I wont be doing that much printing so I guess I can just move it to the floor next the computer when I need to print 


thanks you

---

### Post by loseby on 2012-05-17
ok...have worked out what I will be doing for a temp solution

It wont be the perfect result but it will do. Have installed libre on a win7 pc and will use that. ie. will save files to a USB stick on 12.04 and plug that into the windows machine

thats easier then moving the printer  :-)

---

### Post by loseby on 2012-05-18
ok.....have just managed a test page print


It uses the drivers for the 6100 but only rear paper feed


just put in 10.1.1.7 as the address  ......   well thats what shows when you connect to the router

---

### Post by BaffledMollusc on 2012-05-19
Good to know! Hopefully this'll help other people searching for info on the same printer :-)

---

