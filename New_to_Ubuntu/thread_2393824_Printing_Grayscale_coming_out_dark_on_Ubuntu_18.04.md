---
title: "Printing Grayscale coming out dark on Ubuntu 18.04."
date: 2018-06-08
forum: New to Ubuntu
---

### Post by dim+ on 2018-06-08
Problem: Printing coming out Dark in version 18.04 of L/K/X/Ubuntu

Systems tested: L/X/Ubuntu 16.04 and L/X/K/Ubuntu 18.04.

Printer settings
Media Size: A4
Color Model: Grayscale
Color Precision: Normal
Media Type: Plain Paper
Print Quality: Standard
Resolution: Automatic

Tested hardware
Desktop Dell Optiplex 745
IBM ThinkPad T61 Notebook
Epson Stylus TX123 Printer

I also installed Epson drivers, made 2 down-grid kernel and 1 kernel upgrade, replaces the 6 Libre office by 5, and lastly, as a blind shot, I removed all the packages related to print drivers of the new version (Ubuntu 18.04) and installed the same Packages from the previous version (Ubuntu 16.04), no results yet.


Someone with the same problem?
Any idea how to fix this?

[[IMG]https://www.4shared.com/img/CkY6AvJkee/s25/1648b8f59a8/impresso[/IMG]](https://www.4shared.com/photo/CkY6AvJkee/impresso.html)

---

### Post by dim+ on 2018-07-11
There is also manual option, brightness control, contrast, saturation and others, in the last case.

[[IMG]https://www.4shared.com/img/JDPKEST7ee/s25/1648b958f80/teste_impresso[/IMG]]("https://www.4shared.com/photo/JDPKEST7ee/teste_impresso.html")

The Ubuntu 18.04 comes with printer-driver-gutenprint 5.2.13-2, does anyone know how to force the use of the printer-driver-gutenprint 5.2.11 version of Ubuntu 16.04?

---

### Post by Claus7 on 2018-07-12
Hello,

sometimes if I chose to print greyscale, then the result was no printing at all - the printer printed an empty paper, yet I do not own a printer like yours.

Now, about your question, I guess that you could download the package you want from here:
[https://packages.ubuntu.com/xenial/printer-driver-gutenprint](https://packages.ubuntu.com/xenial/printer-driver-gutenprint)

and try to install it, yet it might not work due to dependency problems. You could check it out in a virtual machine, if you do not want to brick your system.

Ah! &welcome to the forums!

Regards!

---

### Post by dim+ on 2018-07-12
> **Claus7 said:**
> Hello,

sometimes if I chose to print greyscale, then the result was no printing at all - the printer printed an empty paper, yet I do not own a printer like yours.

Now, about your question, I guess that you could download the package you want from here:
[https://packages.ubuntu.com/xenial/printer-driver-gutenprint](https://packages.ubuntu.com/xenial/printer-driver-gutenprint)

and try to install it, yet it might not work due to dependency problems. You could check it out in a virtual machine, if you do not want to brick your system.

Ah! &welcome to the forums!

Regards!

Thanks Claus7, I hadn't tested print colorful, has no color ink here, it's empty, just black, I left the printer for RGB color, and Printed correctly, it was not as dark as in Grayscale mode.

I ended up getting install on Ubuntu 18.04 the old version of the driver Gutenprint (printer-driver-Gutenprint v 5.2.11), had not achieved before because I was doing the wrong way, replacing all the print packets by the old version but only It was necessary to replace the packages (printer-driver-Gutenprint v 5.2.13 and Libgutenprint2 v 5.2.13).


First I removed the packages (printer-driver-Gutenprint v 5.2.13 and Libgutenprint2 v 5.2.13), then installed via terminal the packages (printer-driver-Gutenprint v 5.2.11 and Libgutenprint2 v 5.2.11), and finally locked the two files to not update (sudo Apt-mark hold printer-driver-gutenprint and sudo apt-mark hold libgutenprint2).

[[IMG]https://www.4shared.com/img/qpNMsplOda/s25/164a10d9010/printtest2[/IMG]]("https://www.4shared.com/photo/qpNMsplOda/printtest2.html")


As I always print on Grayscale, I made some prints with two images, a light gray and another dark gray, I realized that the (Driver Gutenprint v 5.2.11 does not print light gray when it is in RGB Color mode, and the driver Gutenprint v 5.2.13 prints very dark When it's in Grayscale mode.


conclusion, for those who print colorful the ideal seems to be the (Driver Gutenprint v 5.2.13) because it does not ignore the light gray, I do not have color ink here, do not know if the (printer-driver-Gutenprint v 5.2.11) would use the colored ink to print the light gray, and for Who prints on Grayscale the ideal seems to be the (Driver Gutenprint v 5.2.11) because it does not make the image darker.

[[IMG]https://www.4shared.com/img/YUHa_Trtda/s25/164a10d6130/printtest1[/IMG]]("https://www.4shared.com/photo/YUHa_Trtda/printtest1.html")


Remembering that this is tested on the printer Epson Stylus TX123, it is not general rule, but the steps here maybe help someone, as I print only in Grayscale mode, my problem solved with the installation of the (Driver Gutenprint v 5.2.11).

---

