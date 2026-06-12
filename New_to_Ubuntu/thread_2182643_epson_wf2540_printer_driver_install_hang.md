---
title: "epson wf2540 printer driver install hang"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by pulsev2 on 2013-10-21
Just upgraded to 13.10 from 13.04 and printer was working. System settings-printer install hangs in installation step after verification of manufacturer driver. Also appears Epson has just removed the Linux driver from their site as well. Suggestions?

---

### Post by MrSteve on 2013-10-22
is this of help ...

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff)

---

### Post by Maverick Meerkat on 2013-10-24
Hi there,

I was also having the driver installer hang up on mine as well.
I have been hoping to see where you got it to work.

Anyway, today I got mine to work.
My printer is a Epson Artisan 730.
I had downloaded the driver from Epson manually, but when I select "local driver" the thing would still freeze.
Luckily, my laptop ( running 12.04 ) was already set up to print, so I looked at how it was set.
I copied the Device URI from the laptop and wrote it on the PC running 13.10
On the laptop, I had been using a driver for an Artisan 710.
After putting in the URI, it prompted me for a test printout, which worked!

I hope this somehow makes sense and helps you :-)

Rick

---

### Post by NikitaUbunt on 2013-10-31
> **MrSteve said:**
> is this of help ...

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff)


Thanks. This worked for me on a HP650 laptop running Ubuntu 13.10 and the WF2540 epson wireless print/scanner.
):P

---

### Post by gogos on 2014-01-03
Ran into the same thing with an Epson Stylus NX620.

Instead installed the driver in a terminal:
```
sudo apt-get install epson-inkjet-printer-escpr
```

Then adding the printer through the System Settings as usual skipped the driver install step and worked.

---

