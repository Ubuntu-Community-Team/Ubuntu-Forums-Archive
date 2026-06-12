---
title: "Loading Epson NX230 Drivers into Ubuntu 10.04"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by Old Stang on 2012-09-23
Searched the site and found some help with loading drivers... went to this site
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)  downloaded the .rpm and .deb files. 

Performed the following from the command line... seemed to load OK 

losee@Losee-desktop:~$ # rpm -i /losee/Download Temp/Epson NX230 Drivers/epson-inkjet-printer-201108w-1.0.0-1lsb3.2.i486.rpm
losee@Losee-desktop:~$ # dpkg -i /losee/Download Temp/Epson NX230 Drivers/epson-inkjet-printer-201108w_1.0.0-1lsb3.2_i386.deb
losee@Losee-desktop:~$ 

Went to the CUPS site to register the printer (NX230) and load the .ppd.gz file... that seems to go OK.

When I try to print a Test Page from either the CUPS site or directly from the System/Administration/Printing... menu, I get the following printer configuration error:

**Missing Printer Driver**
Printer 'NX230' requires the '/opt/epson_inkjet_printer_filter' program but it is not currently installed. 

I believe that program file is part of the .rpm, but not sure. Obviously I either failed to load something properly or I need to find that file and load it. At this point I am spinning in circles and likely doing more harm than good.

Note that I had an Epson NX515 connected wirelessly and it worked fine until it suddenly gave up the ghost. Initially this NX230 POS "kinda" worked using a Ubuntu driver for another Epson model available locally through the settings tab, but color registration was off... so today I decided to "fix it right"... what a mistake. 

Though I am new to Linux, I am familiar with using a command line having  started with computers when OS required the use of DOS... but its been a  loooooong time. :wink:

Any assistance/ direction is appreciated... including instruction on how  to wipe the printer install slate clean and start from square one.

Thanks,
Marc

---

### Post by Old Stang on 2012-09-24
> **Old Stang said:**
> Searched the site and found some help with loading drivers... went to this site
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)  downloaded the .rpm and .deb files. 

Performed the following from the command line... seemed to load OK 

losee@Losee-desktop:~$ # rpm -i /losee/Download Temp/Epson NX230 Drivers/epson-inkjet-printer-201108w-1.0.0-1lsb3.2.i486.rpm
losee@Losee-desktop:~$ # dpkg -i /losee/Download Temp/Epson NX230 Drivers/epson-inkjet-printer-201108w_1.0.0-1lsb3.2_i386.deb
losee@Losee-desktop:~$ 

Went to the CUPS site to register the printer (NX230) and load the .ppd.gz file... that seems to go OK.

When I try to print a Test Page from either the CUPS site or directly from the System/Administration/Printing... menu, I get the following printer configuration error:

**Missing Printer Driver**
Printer 'NX230' requires the '/opt/epson_inkjet_printer_filter' program but it is not currently installed. 

I believe that program file is part of the .rpm, but not sure. Obviously I either failed to load something properly or I need to find that file and load it. At this point I am spinning in circles and likely doing more harm than good.

Note that I had an Epson NX515 connected wirelessly and it worked fine until it suddenly gave up the ghost. Initially this NX230 POS "kinda" worked using a Ubuntu driver for another Epson model available locally through the settings tab, but color registration was off... so today I decided to "fix it right"... what a mistake. 

Though I am new to Linux, I am familiar with using a command line having  started with computers when OS required the use of DOS... but its been a  loooooong time. :wink:

Any assistance/ direction is appreciated... including instruction on how  to wipe the printer install slate clean and start from square one.

Thanks,
Marc

**[SIZE=3]Bueller?  ... anyone?[/SIZE]**

---

### Post by Old Stang on 2012-09-26
Let me rephrase: How can I load the drivers so that I don't get the listed error message (see previous post) and enable me to use my printer?
 
Thanks.

---

### Post by stoneage on 2012-09-26
You don't need the .rpm since it isn't intended for Debian based systems like Ubuntu. 

Since the file epson_inkjet_printer_filter is supplied by the drivers package you downloaded, my first guess would be that something didn't go right. The spaces in the file path are a slight worry.

First of all the .deb file you downloaded seems to be the correct one if you have a 32 bit install of Ubuntu. If not download this one:- [epson-inkjet-printer-201108w_1.0.0-1lsb3.2_amd64.deb ]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-amd64/epson-inkjet-printer-201108w_1.0.0-1lsb3.2_amd64.deb")
Try right clicking on the package file and choose 'Open with GDebi Package installer', or the Software Centre if it is installed on 10.04 (it may be worded differently on 10.04) and see what happens.

---

### Post by Old Stang on 2012-09-27
> **stoneage said:**
> You don't need the .rpm since it isn't intended for Debian based systems like Ubuntu. 

Since the file epson_inkjet_printer_filter is supplied by the drivers package you downloaded, my first guess would be that something didn't go right. The spaces in the file path are a slight worry.

First of all the .deb file you downloaded seems to be the correct one if you have a 32 bit install of Ubuntu. If not download this one:- [epson-inkjet-printer-201108w_1.0.0-1lsb3.2_amd64.deb ]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-amd64/epson-inkjet-printer-201108w_1.0.0-1lsb3.2_amd64.deb")
Try right clicking on the package file and choose 'Open with GDebi Package installer', or the Software Centre if it is installed on 10.04 (it may be worded differently on 10.04) and see what happens.

Stoneage,

I can't thank you enough. You were correct on several points...
the 32 bit .deb file was the right one;
my install was somehow flawed;
the 'Open with GDebi installer' worked like a champ!

All is well in my printer world now. Thank you! :D

Regards,
Marc

---

