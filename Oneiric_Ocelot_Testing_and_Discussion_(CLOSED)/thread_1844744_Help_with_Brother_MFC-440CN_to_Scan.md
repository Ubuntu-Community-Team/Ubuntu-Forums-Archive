---
title: "Help with Brother MFC-440CN to Scan"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by barrmulio on 2011-09-15
Ok - I simply cannot get my Brother MFC440CN to scan on oneiric x64 setup as a network printer.  I really need gscan2pdf to work, but gimp and xscan cannot see the printer either.

So I'm looking for any tips from folks who have gotten their network Brother printer to install correctly for scanning

Printing works mostly fine (I get 'low marker' notifications, but it prints out within a second or so).  In the end I opted for brother-xxx-bh7 ones from synaptic.  

I've tried the x32 and x64 scanner drivers from Brother's site, which worked just fine in natty, but no dice on oneiric

Per the faq on these forums and the brother site, I also edited /lib/udev/rules.d/40-libsane.rules to include 
```

# BROTHER MFC-440CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01af", ENV{libsane_matched}="yes"

```

Additional console output
```

barrmy@oneiric:~$ dpkg  -l  |  grep  Brother
ii  brother-cups-wrapper-common              1.0.0-10-0ubuntu5                       Common files for Brother cups wrapper packages
ii  brscan-skey                              0.2.1-3                                 Brother Linux scanner S-KEY tool
ii  brscan2                                  0.2.5-1                                 Brother Scanner Driver

barrmy@oneiric:~$ brsaneconfig2  -q  |  grep  SCANNER
  0 SCANNER             "MFC-440CN"         I:192.168.1.90

```

Not sure if it matters but when printing I get: 
- can't connect error (which is false because the printer is getting data and does print out just fine
- Out of a marker supply error
- Out of ink error
The drivers from the brother website have the same issue.

Thanks in advance for any tips or help

---

### Post by clivejo on 2011-09-15
Try running it as su, and let me know if it works

```
sudo gscan2pdf
```

---

### Post by barrmulio on 2011-09-15
clivejo, thanks for the help

I still get a 'no devices found' after I click on Scan Document and it attempts a scan of devices

from the terminal:
```
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/lib/perl5/Gtk2.pm line 138.
Name "PDF::API2::Version::CVersion" used only once: possible typo at /usr/bin/gscan2pdf line 433.
Use of uninitialized value $PDF::API2::Version::CVersion{"vShort"} in concatenation (.) or string at /usr/bin/gscan2pdf line 433.

```

Run with --debug, it displays
```
Running sane_get_devices
INFO - Sane->get_devices returned: $VAR1 = [];

```

---

### Post by vuy on 2011-09-16
same problem with MFC-6490CW

$ dpkg -l | grep Brother
ii  brhl2070nlpr:i386                    2.0.1-1                                    Brother HL-2070N LPR driver
ii  brscan3                              0.2.11-2                                   Brother Scanner Driver
ii  mfc6490cwcupswrapper:i386            1.1.2-2                                    Brother CUPS Inkjet Printer Definitions
ii  mfc6490cwlpr:i386                    1.1.2-2                                    Brother lpr Inkjet Printer Definitions
ii  ptouch-driver                         1.3-0ubuntu11                              CUPS/Foomatic driver for  Brother P-touch label printers


$ brsaneconfig3 -q

...
Devices on network
  0 SCANNER             "MFC-6490CW"        I:192.168.1.107

$ scanimage -h

...
scanimage: no SANE devices found

---

### Post by walt.smith1960 on 2011-09-16
I have a MFC-6490CW like vuy and scanner didn't work running either OO 64 bit or 32 bit.  The print function was working correctly.  I deleted and reinstalled and still no dice.  Then one day after running updates the scanner  was recognized.  I have no idea what changed.  I did email Brother 2 or 3 weeks ago and told them the scanner would not install in OO. This is with a USB connection.

---

