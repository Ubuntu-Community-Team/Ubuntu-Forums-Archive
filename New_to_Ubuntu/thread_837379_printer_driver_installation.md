---
title: "printer driver installation"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by fredfelter on 2008-06-22
Please be gentle; this is "absolute beginner talk" and I definitely qualify.
Ubuntu 8, Thinkpad t22, Canon MF4270

I received the appropriate driver as a tar.gz > expanded it to 2 folders, a documents and sources folder > the sources folder contains 2 files that I am supposed to install, a common and a 1b. Instructions say to "run make at the top level directory of this package source tree as follows: $ make gen; su; make install"

How do I "run make at the top level ..."? Do I add the names of the files to that command? Do I run that command with the file open? In other words what exactly do I do to initiate the installation?

Thanks in advance.

---

### Post by UltraMathMan on 2008-06-22
In short, the package you downloaded needs to be built from the source code. I looked up the printer model on openprinting.org and found a link to a .deb package which should be much easier for you to install. [Canon drivers]("http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One+Printers&series=Laser+Multifunction&model=Laser+imageCLASS+MF4140%2fMF4150&menu=Download") select the Linux Printer Driver (UFR II) Ver.1.70E one (number 7). 

When you unarchive it open the 32-bit driver and then the debian folder - simply double click on the .deb files to install them.

-Hope this helps :)

FYI: [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-MF4270]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-MF4270")

---

### Post by fredfelter on 2008-06-22
Thanks a million UltraMathMan - that did the trick.

If I may ask how did you recognize the download as a Debian package? It looks like the same package description as the one I was using.
And secondly briefly, what would I needed to have done to install the package I was using? I assume some day I'll run into an installation that will offer me no easy Debian double click alternative.

This inspires me to continue learning to use Linux.

---

### Post by UltraMathMan on 2008-06-22
The other linux package was marked (source) - Debian packages end in .deb, although in this case I just happened to get lucky since there was no outward indiaction that it contained deb and rpm files.

To build from source you need the build-essentials package. I'd also recommend grabbing the checkinstall package to use over makeinstall as that will bundle and install the code as a .deb package, which makes for easier removal should the need arise.

Generally the procedure is something like:
1. Navigate to the highest level of the folder you unarchive (in the terminal via cd /path to folder/)

2. Type ./configure && make

3. Type sudo checkinstall -D

Most packages are available either via Ubuntu's package management system or as a downloadable .deb, there are only a handful I can recall absolutely needing to install from source.

Good luck :)

---

### Post by alexcuervo on 2009-04-24
For 64bit users there is a good guide here
For the printer part
[http://queleimporta.com/installing-canon-imageclass-mf4270-on-ubuntu-64-bit/]("http://queleimporta.com/installing-canon-imageclass-mf4270-on-ubuntu-64-bit/")

For the scanner part:
[http://queleimporta.com/installing-canons-imageclass-mf4270-scanner-on-ubuntu-64-bit/]("http://queleimporta.com/installing-canons-imageclass-mf4270-scanner-on-ubuntu-64-bit/")

---

### Post by Francewhoa on 2009-05-23
Click here for [*HOWTO: Install Canon ImageCLASS MF4270 Multifunction driver.*]("http://ubuntuforums.org/showthread.php?t=1140724")

---

