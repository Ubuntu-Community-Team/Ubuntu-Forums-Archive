---
title: "Epsom printer compatibility"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by wolfrowan on 2012-03-21
Hi.  I just bought an epson workforce 545/645 series 4-in-one printer.  Is this compatible with Ubuntu?  And if so, how would I install it.  I don't have a working cd drive.  Thanks so much in advance.   Rowan

---

### Post by Cheesemill on 2012-03-21
According to [http://www.openprinting.org/printer/Epson/Epson-WorkForce_545_Series](http://www.openprinting.org/printer/Epson/Epson-WorkForce_545_Series) it works perfectly.

Drivers are available here:
[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Search for 'workforce 545' and it will give you a list of printer and scanner drivers. Just download the correct .deb files (32 or 64 bit) and double click on them to install :)

---

### Post by plucky on 2012-03-21
> **wolfrowan said:**
> Hi.  I just bought an epson workforce 545/645 series 4-in-one printer.  Is this compatible with Ubuntu?  And if so, how would I install it.  I don't have a working cd drive.  Thanks so much in advance.   Rowan

Try plugging it into a USB socket, power on, and see if it installs.


Good Luck

---

### Post by wolfrowan on 2012-03-25
Hi Cheesemill,
Thanks for your advice about installing an epson workforce545 driver.  I went to those sites, double clicked on what I think is the right one, but my computer just sits and thinks about something else.  Nothing happens.  Did I have to do something else first?   Rowan

---

### Post by GregA on 2012-03-26
Instead of double-clicking (as in windows), just place your mouse arrow over the file (or click on it once to "select" it).   Then right-click the file, and you should get a popup that presents an option to "open file with" . . . . finally, you should see the option "gdebi" (an alternate package manager).  

Gdebi will install the "deb" automagically for you.  Do the same for the universal scanner driver (from Epson).   

Also, install "Simple Scan" (if it's not already installed).   Simple scan  doesn't actually require the Epson scanner driver, it will use the "Xsane" scanning program which works fine with these printers.

---

### Post by George W. Tush on 2012-08-14
I also have the Epson Workforce 645.  The printing worked instantly on Xubuntu 12.04 without any input from me.  I plugged it in.  It worked.

However, the computer and the scanner do not find one another.  

When I try to scan, the scanner says "Communication error.  Make sure the computer is connected, then try again."  I know it is connected because it prints.  

Image Scan says, "Could not send command to the scanner.  Check the scanner's status." 

Simple Scan says, "Failed to scan.  Unable to connect to scanner."

If anyone can nudge me to the solution, I will thank you profusely.

---

### Post by plucky on 2012-08-15
> **George W. Tush said:**
> I also have the Epson Workforce 645.  The printing worked instantly on Xubuntu 12.04 without any input from me.  I plugged it in.  It worked.

However, the computer and the scanner do not find one another.  

When I try to scan, the scanner says "Communication error.  Make sure the computer is connected, then try again."  I know it is connected because it prints.  

Image Scan says, "Could not send command to the scanner.  Check the scanner's status." 

Simple Scan says, "Failed to scan.  Unable to connect to scanner."

If anyone can nudge me to the solution, I will thank you profusely.

I don't have your printer/scanner,but I think it would be worth installing **sane-utils** which I believe is not installed by default.

If that doesn't work,try installing **xsane** and see if that finds your scanner.

Good Luck

---

### Post by George W. Tush on 2012-08-16
plucky, you are the god of all things Ubuntu.  It worked!

Thank you for your pluperfect suggestion. 

All hail plucky!

---

### Post by uzzo2 on 2012-09-04
I just bought one of these today, I got the printer installed but am having trouble with the scanner also. I have xsane and sane-utils installed, with xsane I'm getting an "error during read:error during device I/O".

The driver from epson won't install either, I get a "Error- Dependency is not satisfiable : iscan-data" message from it.

---

### Post by anewguy on 2012-09-04
As an aside to one of the posts earlier about using gdebi:  If the file is a .deb file, it should open automatically using the software center at which point it is like installing/removing any package via the software center.  No need for any extra packages.

---

### Post by uzzo2 on 2012-09-04
I think I got it figured out folks, I downloaded the core package. But there was a data package that had to be downloaded as well, works great now! This is at the very bottom of the FAQ page.

"If you're compiling from source you need both the core package (iscan) and data package (iscan-data) source tarballs. For details, please refer to README of each source package."

This is the core package:  (iscan_2.29.1-5~usb0.1.ltdl7_i386.deb)

And here is the data package:  (iscan-data_1.17.0-2_all.deb)

You get them both here:  

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18458&DSCCHK=68d0637c914e0c59181d4bdb01e1c1a8ed5d186d](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18458&DSCCHK=68d0637c914e0c59181d4bdb01e1c1a8ed5d186d) 

These are the Ubuntu drivers for 8.10 and later versions only!

---

### Post by abexman on 2012-11-24
Just got this printer and trying to install on Ubuntu 12.04. Printer driver seemed to install OK. But the two scan deb files I am getting a message like "Dependency is not satisfiable: iscan (>=2.21.0)"

Any ideas what I am doing wrong?

UPDATE: Looks like it may be working even though the drivers did not installl

---

### Post by pdc on 2012-11-25
so we take it that you are using an Epson 545? Is that correct?

from here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5)

......the Epson download site ..............

one can see that [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb[/COLOR] is available 

(as is a 64bit driver............)

(I believe dlt7 is for later kernels.................)

would this version of iscan work for you?

---

