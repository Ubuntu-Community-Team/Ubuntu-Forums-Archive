---
title: "HOW TO : Install Brother MFC8460N on Edgy"
date: 2007-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by edmondt on 2007-03-31
Just got the Brother MFC 8460N All-in-one printer and I wasn't sure it will work on ubuntu. After setting it up and hooking it to the network, I took the ip address assigned to the printer from my router, which was 192.168.0.109

Brother has drivers which supports this model, first I install brmfc8460nlpr-2.0.0-1.i386.deb from here:

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/brmfc8460nlpr-2.0.0-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/brmfc8460nlpr-2.0.0-1.i386.deb&lang=English_lpr)

Then install cupswrapperMFC8460N-2.0.0-1.i386.deb from here:

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC8460N-2.0.0-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC8460N-2.0.0-1.i386.deb&lang=English_gpl)

Next get the network fax driver, brmfcfaxlpd-1.0.0-1.i386.deb from here:

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb&lang=English_lpr)


After installing the drivers, go here and add your printer:

[http://localhost:631](http://localhost:631)

Under Administration, Add Printer enter name as:

Brother-MFC-8460N

Hit Continue...

Then Select LPD/LPR Host or Printer, and hit Continue...

Enter Device URI: lpd://192.168.0.109 (Your printer's ip address)

Continue...

On this page, when it ask which drivers, at the bottom click browse...

Navigate to:
/usr/share/cups/model

Select MFC8460N.ppd then click Add Printer.

It should ask for your username and password, just enter your admin username and password...

Your printer should be added, try to print a test page and see...


You can repeat the same thing for the fax printer... I haven't tried faxing directly using the driver, but I hope this little guide will be helpful for some.

---

### Post by dragonito on 2007-04-23
I have some problems with the installation.

First I installed the driver, no problem. Then i tried to install the wrapper and i got this error message:

"ERROR : Brother LPD filter is not installed."

I tried to install the Cups PPD driver directly with the gnome integrated printer configurator. No Problems. When i´m printing a testpage, the printer gots the data (its blinking) but nothing happens. After blinking the led is green.

The same procedure on my Laptop works fine, but my workpc won´t work.

Thanx a lot, hope you could help me

Robin

---

### Post by desperado666 on 2007-04-23
cant print with brother printer drivers under feisty :(

---

### Post by edmondt on 2007-04-23
It is easier on Fesity, just install the printer with the MFC-8420 Driver (BR-Script3) and it should work.

---

### Post by Luisjo on 2010-11-04
I can use the scaner os this printer, can you help me please!!! Thanks

---

