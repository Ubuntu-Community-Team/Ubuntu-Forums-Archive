---
title: "Network Printer Driver Installation HANGS (lubuntu 15.10)"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by Stef700 on 2016-01-04
I am trying to add a network printer (Epson WP-4535) in 32 bit lubuntu 15.10

The System Tools "Printers" utility finds the printer correctly identifying the ip address OK and identifies it as "LPD/LPR 'Passthru' which I believe is also correct.

It then identifies two EPSON drivers which appear to be correct according to [http://www.openprinting.org/printer/Epson/Epson-WP-4535](http://www.openprinting.org/printer/Epson/Epson-WP-4535)

However if I then try to install either of them the installation just HANGS on "Installing driver...."

Any help or ideas to resolve this much appreciated
Many Thanks Stef


PS
(This printer works fine on my other workstation Ubuntu 12.04 64bit - I installed the printer on this workstation over a year ago)

---

### Post by Stef700 on 2016-01-04
Well Kudos to myself as I *SOLVED* it. I found a fairly recent Epson .deb driver package and installed it. Then I re-ran the System Tools/Printers/Add Printers dialogue and low and behold it sailed through and now works !!!!
(I must be better at this than I thought!)

:-)

---

