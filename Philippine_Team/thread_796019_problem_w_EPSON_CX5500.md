---
title: "problem w/ EPSON CX5500"
date: 2008-05-16
forum: Philippine Team
---

### Post by ricoglenndeuna on 2008-05-16
Please help me install Epson stylus cx5500 driver.

Ubuntu 7.10 / 8.04

:popcorn::):(:confused::confused:

thanks

---

### Post by jepong on 2008-05-16
di ba nya na autodetect?

---

### Post by pendletone on 2008-05-16
It seems that you're using a multifunction printer. Try this [link]("http://ohioloco.ubuntuforums.org/showthread.php?t=627471") it might help.

---

### Post by eilu on 2008-05-16
in my experience, epsons work better with guttenprint than cups. it's in the repos.

---

### Post by liphin204 on 2012-05-20
Guys, any idea why my Epson CX5500 scanner unable to work in Xsane when my Ubuntu is 12.04 64 bits? Previously I was using Ubuntu 12.04 TS 32 bits why I follow all the instruction posted in the web page but still failed. I though maybe because of my Epson CX5500 scanner not working at 32 bit Ubuntu, hence I change Ubuntu 12.04 TS to 64 bits.

Now still my Epson CX5500 scanner doesn't work at 12.04 TS 64 bit, and I follow all the instruction posted in the web, google search as many I can still doesn't making my scanner work at Xsane. I already run out of idea.  I though Epson CX5500 is the best scanner but it just not support in the stupid sane , xsane version.

below is the message after I type scanimage -L
> 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


why I type sudo sane-find-scanner, it does able to find the scanner:

> 

found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error]) at libusb:006:003


I don't know what the hell is going on. I have installed iscan 2.28.1 version, also edit the 
/etc/sane.d/dll.conf to read as epkowa,  don't know why still xsane cannot find my scanner. Anyone can help me?

---

### Post by Script Warlock on 2012-05-20
meron din ako nyan cx5500 dati working sa 8.04 pero dedo after 2yrs of use sa cyber shop. try ko tingnan yung naisave na driver baka pwede yun natin pagtyagaan. naemail mo na rin ba epson? [[COLOR="Blue"]eto[/COLOR]]("http://global.epson.com/newsroom/2011/news_20110331.html") kasi sabi nila para sa linux users.

---

### Post by jbantug on 2013-02-12
I encountered the same problem after I installed Ubuntu 12.04 LTS 64bit. One good thing that happened was that when I plugged in my CX-5500, Ubuntu detected it as a printer and enabled the printer driver. So I am left with the scanner problem only.  I researched in this forum. It led me to [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX). I input CX5500 and set OS to Linux. Note that CX5500 has no dash.  [INDENT]From the list, look for CX5500 scanner driver. You should find 2 items. Download both.  When you download core package and data package, you will be asked to accept the agreement. Accept it and you will be presented with another list. From the list, download the following: 

[LIST=1]
[*]iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
[*]iscan-data_1.22.0-1_all.deb
[*]userg_revQ_e.pdf
[/LIST]

[/INDENT]When you download the iscan plugin package, you will be asked asked again to accept the agreement. Accept it and you will be presented with another list. From the list, download iscan-plugin-cx4400_2.1.3-1_amd64.deb.  [INDENT]Of the 4 items you downloaded, the most important is userg_revQ_e.pdf. It has the installation guide. Note that the user guide is a guide for all kinds of installations. It does not care about Ubuntu version. Executing the commands as is might translate to different parsing procedure so to be safe, I installed the packages explicitly one by one. 

[/INDENT]Below are the commands I issued. Install data package, core package then plugin package.  

[LIST=1]
[*]sudo dpkg --install iscan-data_1.22.0-1_all.deb
[*]sudo dpkg --install iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
[*]sudo dpkg --install iscan-plugin-cx4400_2.1.3-1_amd64.deb
[/LIST]
[INDENT]
Depending on the updates you did to Ubuntu prior to installation of scanner driver, you might encounter errors related to dependencies.  When I encountered errors related to xlstproc dependency when installing the data package, I issued the command below. It worked. Try installing again the data package. It should work fine this time.  

sudo apt-get install xsltproc  

[/INDENT]When I encountered errors related to dependencies other then xsltproc, I issued the command below (as suggested by postings in this forum for such problem). I do not understand what it is supposed to do but it works so I'm fine with it. 

sudo apt-get -f install  
[INDENT]After this, launch "iscan" program. "Xsane" should be fine also. Even "simple scan" works.[/INDENT]

---

