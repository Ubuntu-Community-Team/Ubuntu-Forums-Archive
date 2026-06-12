---
title: "Scanner problems with Acer 340U"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by Yannanael on 2012-03-26
Hello,
Some days ago I installed Ubuntu 11.10 (with Xubuntu desktop) and now I am trying out...
Printer works fine, but I've got problems if I try to scan with Simple Scan. It gives me an error saying it can't connect with the scanner.
My scanner is an Acer ScanPrisa 340U.

sane-find-scanner got me:
found USB scanner (vendor=0x04a5 [Color], product=0x2022 [ FlatbedScanner 13]) at libusb:003:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

scanimage -L then gave
No scanners were identified.

lsusb got me:
Bus 003 Device 005: ID 04a5:2022 Acer Peripherals Inc. (now BenQ Corp.) Prisa 320U/340U

I checked here: [http://www.sane-project.org/sane-backends.html#SCANNERS](http://www.sane-project.org/sane-backends.html#SCANNERS)
and got
Benq (Acer): 340U     USB id     0x04a5/0x2022     Status:Good

And now, as a newbie,  I'm stuck... Could someone tell me what to do to get my scanner scanning?

Yann

---

### Post by sandyd on 2012-03-26
> **Yannanael said:**
> Hello,
Some days ago I installed Ubuntu 11.10 (with Xubuntu desktop) and now I am trying out...
Printer works fine, but I've got problems if I try to scan with Simple Scan. It gives me an error saying it can't connect with the scanner.
My scanner is an Acer ScanPrisa 340U.

sane-find-scanner got me:
found USB scanner (vendor=0x04a5 [Color], product=0x2022 [ FlatbedScanner 13]) at libusb:003:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

scanimage -L then gave
No scanners were identified.

lsusb got me:
Bus 003 Device 005: ID 04a5:2022 Acer Peripherals Inc. (now BenQ Corp.) Prisa 320U/340U

I checked here: [http://www.sane-project.org/sane-backends.html#SCANNERS](http://www.sane-project.org/sane-backends.html#SCANNERS)
and got
Benq (Acer): 340U     USB id     0x04a5/0x2022     Status:Good

And now, as a newbie,  I'm stuck... Could someone tell me what to do to get my scanner scanning?

Yann
have you tried xsane?

---

### Post by Yannanael on 2012-03-26
Just installed XSane, plugged in the scanner and ran XSane, but I got (excuse my English):
"Couldn't find the scanner 'snapscan:libudb:003:008':
Wrong argument."
So still no scans...

Yann

---

### Post by Yannanael on 2012-03-27
Still the same problem of XSane nor SimpleScan recognising my scanner, so I looked around a bit more on the Internet and found a free trial version of VueScan.
When I start it up, it recognises my scanner. Then I close VueScan and start up XSane, and... XSane suddenly recognises the scanner, so I can scan. Till I turn off the scanner and put it on again: no recognition by XSane anymore. I first have to run VueScan again to make XSane recognise the scanner.
A very bizarre detour to get my scanner working...
I would be happy if someone could suggest a better way...

Yann

---

