---
title: "Epson XP-310 printer/scanner"
date: 2015-01-04
forum: New to Ubuntu
---

### Post by cats2 on 2015-01-04
[SIZE=3]I'm new to Linux, although I have worked with Unix.
I am trying to get my Epson XP-310 combo printer/scanner to work with my new Ubuntu 14.04.  It worked fine with Ubuntu Studio 13.04.

Now my Compaq Presario laptop recognizes the printer and the printer responds, but all I get is blank pages.  Most likely a driver issue, right?

So I searched the forums and found this link  [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)  where I am offered these downloads:
=========================================================================================================
[/SIZE][TABLE="class: searchResTbl"]
[TR]
[TH="align: left"][SIZE=3]Product Name
[/SIZE][/TH]
[TH="align: left"][SIZE=3]Category            
[/SIZE][/TH]
[TH="align: left"][SIZE=3]Operation System
[/SIZE][/TH]
[TH="align: left"][SIZE=3]Version[/SIZE][/TH]
[TH="align: left"][SIZE=3]     Module Name
[/SIZE][/TH]
[TH="align: left"][SIZE=3]Language
[/SIZE][/TH]
[TH="align: left"][SIZE=3]     Release Date
[/SIZE][/TH]
[TH][SIZE=3]
[/SIZE][/TH]
[/TR]
[TR]
[TD][SIZE=3]XP-310 Series
[/SIZE][/TD]
[TD][SIZE=3]Printer Driver[/SIZE][/TD]
[TD][SIZE=3]Linux
[/SIZE][/TD]
[TD][SIZE=3]1.4.4
[/SIZE][/TD]
[TD][SIZE=3]     ESC/P-R Driver  (generic driver)
[/SIZE][/TD]
[TD][SIZE=3]All language
[/SIZE][/TD]
[TD][SIZE=3]     10-31-2014
[/SIZE][/TD]
[TD][SIZE=3]                          
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=3]XP-310 Series
[/SIZE][/TD]
[TD][SIZE=3]Printer Driver[/SIZE][/TD]
[TD][SIZE=3]Linux                            
[/SIZE][/TD]
[TD][SIZE=3]1.0.0[/SIZE][/TD]
[TD][SIZE=3]     ESC/P Driver (full feature)
[/SIZE][/TD]
[TD][SIZE=3]All language
[/SIZE][/TD]
[TD][SIZE=3]     05-30-2013
[/SIZE][/TD]
[TD][SIZE=3]                          
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=3]XP-310 Series
[/SIZE][/TD]
[TD][SIZE=3]Scanner Driver       
[/SIZE][/TD]
[TD][SIZE=3]Linux
[/SIZE][/TD]
[TD][SIZE=3]Ver. 2.30.0/1.33.0[/SIZE][/TD]
[TD][SIZE=3]     core package&data package
[/SIZE][/TD]
[TD][SIZE=3]All language
[/SIZE][/TD]
[TD][SIZE=3]     11-26-2014
[/SIZE][/TD]
[TD][SIZE=3]                          
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=3]XP-310 Series
[/SIZE][/TD]
[TD][SIZE=3]Scanner Driver[/SIZE][/TD]
[TD][SIZE=3]Linux
[/SIZE][/TD]
[TD][SIZE=3]latest[/SIZE][/TD]
[TD][SIZE=3]     network plugin package
[/SIZE][/TD]
[TD][SIZE=3]All language
[/SIZE][/TD]
[TD][SIZE=3]     12-12-2013
[/SIZE][/TD]
[/TR]
[/TABLE]
[SIZE=3]=========================================================================================================

I downloaded them all, just to take a look.  This is what I got.

/home/cat1/Downloads/epson-inkjet-printer-escpr_1.4.4-1lsb3.2_amd64.deb
/home/cat1/Downloads/epson-inkjet-printer-escpr_1.4.4-1lsb3.2_i386.deb
/home/cat1/Downloads/epson-inkjet-printer-escpr-1.4.4-1lsb3.2.i486.rpm
/home/cat1/Downloads/epson-inkjet-printer-escpr-1.4.4-1lsb3.2.src.rpm
/home/cat1/Downloads/epson-inkjet-printer-escpr-1.4.4-1lsb3.2.tar.gz
/home/cat1/Downloads/epson-inkjet-printer-escpr-1.4.4-1lsb3.2.x86_64.rpm

I have no idea what these files are or what to do with them.  Do I need all of them, or only certain ones for my system?
I would guess that I ned at least one printer driver and one scanner driver, but that's just a guess, since I really don't know what I'm looking at.
(I recognize tar.gz as a compressed folder, but the other extensions are unfamiliar.)

After downloading, what do I do next?  

Thank you all for any help you can offer.[/SIZE]

CatS

---

### Post by codingman on 2015-01-04
Trash all the .rpm files as Ubuntu does not require them, instead it uses .deb files.

Do you have CUPS installed? If not, install it, and go to [COLOR=#FFFFCC][FONT=Trebuchet MS] [http://localhost:631](http://localhost:631)
[/FONT][/COLOR]You may be able to get some information from the CUPS web interface.

---

### Post by kerry_s on 2015-01-04
first:
sudo apt-get install lsb

then open a terminal where you have the deb, i'll guess your Downloads/
cd ~/Downloads
sudo dpkg -i epson-inkjet-printer-escpr_1.4.4-1lsb3.2_amd64.deb
or if your not running a 64 bit install:
sudo dpkg -i epson-inkjet-printer-escpr_1.4.4-1lsb3.2_i386.deb

now just use the printer manager to add the printer it will find the drivers you just installed.

---

### Post by Mike_Walsh on 2015-01-04
Hi, cats2.

If you want the scanner to work, too, then you'll need to download the scanner and data package as well. 

For the scanner, you'll need either the i386. deb, or the amd_64.deb. [COLOR=#000000]You'll want the iscan 2.30.0-1~0.1.ltdl7_amd64 OR i386.deb scanner package, AND the iscan-data_1.33.0-1_all.deb data package. 

They will both install through the Software centre, by double-clicking on them in your Downloads folder. [/COLOR][COLOR=#ff0000]IT IS MOST IMPORTANT[/COLOR][COLOR=#000000] that you install the data package first, as the scanner package needs to be able to 'read' the data package, in order to install itself correctly.

Hope that helps.

Regards,

Mike. [/COLOR];)

---

### Post by kerry_s on 2015-01-04
yeah, i don't bother with the scanner. when i scan i use the controls on the printer. mines an epson xp-410 uses the same drivers though.

---

### Post by JeQhdMD on 2015-01-04
Just a quick note - - Ubuntu only uses the deb (short for "debian") type of package versus the rpm package format used by Red Hat, Suse and others.   What I like to do is to install the "gdebi" package manager program.   It can be found using the Ubuntu Software Center or another great package manager (program for installing linux packages) called Synaptic.   Installing both will give the most flexibility.

I use gdebi to install "stand-alone" deb packages (those found in non-Ubuntu sources such as Sourceforge or Open Printing ([http://www.openprinting.org/printers](http://www.openprinting.org/printers)) . . . where many folks also go to find print/scanner drivers.

Just download the deb file you want to your folder of choice (the default "downloads" folder is fine).   Then access that folder via the file manager (Nautilus or Files app), and RIGHT-click the deb file.   The right click menu will give you the option to use gdebi to handle the install (provided of course you've already installed it).   That's all you actually need to do . . . you will have a deb file for the printer, and another deb file for the scanner.   Even if you use a hardware method to use the scanner, I would suggest to install the scanner driver anyway, as you'll have more options for multi-page scans and quality settings.

PS - - I also like the scanner application called "Simple Scan" . . . it's in the Ubuntu Software Center.

---

### Post by pdc on 2015-01-08
so cats2: are you still hanging in there?

Somehow; you got off on the wrong track in your post;

the full feature driver for this XP-310 is the [SIZE=5]epson-inkjet-printer-201303w_1.0.0-1lsb3.2_amd64.deb[/SIZE] (for a 64bit system)

________________________________________

you get it from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=22524&DSCCHK=be2881cd731a22e340ed2e96eb71ee0725faab96](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=22524&DSCCHK=be2881cd731a22e340ed2e96eb71ee0725faab96) 

and if you click to download, your system may well offer to OPEN the file with gdebi installer or ubuntu software centre: either way, the system is offering to install the package for you as soon as it downloads it; if possible, accept that offer;

you may have to go to Printers in the Menu; and ADD A NEW PRINTER but with the epson driver installed, your system should find the XP-310

___________________________________

tell us though, is it usb connected?

---

