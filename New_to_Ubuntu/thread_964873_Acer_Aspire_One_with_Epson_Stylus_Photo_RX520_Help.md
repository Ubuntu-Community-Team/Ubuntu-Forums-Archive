---
title: "Acer Aspire One with Epson Stylus Photo RX520 Help"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by loafer3003 on 2008-10-31
Hi, 
Could anyone advice how to get the Epson Stylus Photo RX520 to work with Acer One. When the printer is plugged into the USB, detecting hardware etc. it asked for driver, selected make Epson, the gave a list of printers but no Styles Photo RX520. (There is one that says only Stylus Photo and another Stylus Photo RX7xx - cannot remember what the last two numbers are).
So ran a check online to see if there are drivers available for Linux - Linpus. The following is what I came up with:

1)Epson Site (UK)
[http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=vRaxNXeC8zgSFwIM6P5kaxaNNOMyHiS7isSgPaJ3SQIU003D&tc=6](http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=vRaxNXeC8zgSFwIM6P5kaxaNNOMyHiS7isSgPaJ3SQIU003D&tc=6)
After downloading it to Linpus, extracted it and double-click on the extracted file, came up with:
Can't open file "/mnt/home/Downloads/epson31411eu/Linux Driver.html":
Archive format is not recognized!

PROBLEM

2)Went through the Ubuntu Forums and ran a search on any topics related to the Epson Stylus RX520. Luckily came up with some leads:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX520](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX520)
I am lost with the links to download driver, being a newbie I have no idea  which one to download:
**Driver packages for:** x86 32 bit (RPM for LSB 3.2), x86 32 bit (DEB for LSB 3.2), x86 32 bit (RPM for LSB 3.1), x86 32 bit (DEB for LSB 3.1), x86 64 bit (RPM for LSB 3.2), x86 64 bit (DEB for LSB 3.2), x86 64 bit (RPM for LSB 3.1), x86 64 bit (DEB for LSB 3.1), How to install)
Generic instructions for: CUPS, LPD, LPRng, PPR, PDQ, no spooler

Then at the bottom of the page there is:
gutenprint  (driver home page)
Top Quality Printer Drivers for inkjets, dye sublimation printers, and PCL lasers
Supplier: Gutenprint project
License: GPL (free software) 	 
  	User support:  	Gutenprint mailing list at SourceForge (voluntary) 	 
  	Color output  Type: CUPS Raster 	 
  	Text: 
Line art:  	||||||||||||||||||||  90 
||||||||||||||||||||  90  	 Graphics: 
 Photo:  	||||||||||||||||||||  100 
||||||||||||||||||||  100  	 System load: 
 Speed:  	Unknown
||||||||||||||||||||  60 	 
 Download:  Driver packages: x86 32 bit (RPM for LSB 3.2), x86 32 bit (DEB for LSB 3.2), x86 32 bit (RPM for LSB 3.1), x86 32 bit (DEB for LSB 3.1), x86 64 bit (RPM for LSB 3.2), x86 64 bit (DEB for LSB 3.2), x86 64 bit (RPM for LSB 3.1), x86 64 bit (DEB for LSB 3.1) (How to install)

QUESTION: Which one is the driver for Acer Aspire One running on Linpus Linux?

3)One of the treads in the forum lead me to:
[http://avasys.jp/hp/menu000000900/hpg000000859.htm](http://avasys.jp/hp/menu000000900/hpg000000859.htm)
Then, Linux > Driver Download > All-in-Ones 
Scroll down to Check OS of operation: Clicked on the first link:
Test Page came up, hit print.....nothing happens
Clicked on second link:
Test Page came up, hit print.....nothing happens

Went down to Form for download:
*Model*
- Image Scan! for Linux & Photo Image Print System
(Selected - Epson Stylus Photo RX520/RX530)

- Image Scan! for Linux & Photo Image Print System Lite
(None Selected - Model not listed)

*Distribution* : Others (drop-down menu showed no Linpus)
*Distribution Version* : Others
*Your country/region* : UK
*Connection environment for using all-in-ones* : Print/scan with local printer or scanner
*Location for the product* : Individuals(documents) - 1st time
                             Individuals(graphics/image) - 2nd time
NEXT

Printer Driver
Download for Epson Stylus Photo RX520/RX530 for CUPS
RPM package 	Filesize / md5sum
pips-sprx520-cups-2.6.3-1.i386.rpm 	1,276,972 bytes
257f036de26601375c5f1b04056ad650
 
Source file 	Filesize / md5sum
pips-sprx520-2.6.3.tar.gz 	2,348,839 bytes
fe42d117a2d2518e5fcdb31e07764b27
 
Installation method 	Filesize
Please refer to the readme-sprx520-cups 	13,467 bytes
 
Download for Epson Stylus Photo RX520/RX530 for LPR
RPM package 	Filesize / md5sum
pips-sprx520-2.6.3-1.i386.rpm 	1,666,697 bytes
cbbb3837d624d94f6d9d472bb005ee6a
 
Source file 	Filesize / md5sum
pips-sprx520-2.6.3.tar.gz 	2,348,839 bytes
fe42d117a2d2518e5fcdb31e07764b27
 
Installation method 	Filesize
Please refer to the readme-sprx520 	22,448 bytes
 
&#8593;PAGE TOP
Scanner Driver
Download for Epson Stylus Photo RX520/RX530 (for gcc 3.4 or later)
RPM package 	Filesize / md5sum
iscan-2.11.0-1.c2.i386.rpm 	363,497 bytes
5009513b7fb5ce13d63bf908bc674d59
 
Source file 	Filesize / md5sum
iscan_2.11.0-1.tar.gz 	1,458,880 bytes
76991cb47dc8ff1269e47d4bce3d41b5
 
Installation method 	Filesize
Please refer to the userg_revG_e.pdf 	695,737 bytes
 
Download for Epson Stylus Photo RX520/RX530 (for gcc 3.2/3.3)
RPM package 	Filesize / md5sum
iscan-2.11.0-1.i386.rpm 	363,030 bytes
e0d0cf9a90475b3991d28bb4d4581ab1
 
Source file 	Filesize / md5sum
iscan_2.11.0-1.tar.gz 	1,458,880 bytes
76991cb47dc8ff1269e47d4bce3d41b5
 
Installation method 	Filesize
Please refer to the userg_revG_e.pdf

----------------------------------------------------------
I am stuck here. Don't know which one (or all?) to download?
And Advice is much appreciated. Thanks

---

