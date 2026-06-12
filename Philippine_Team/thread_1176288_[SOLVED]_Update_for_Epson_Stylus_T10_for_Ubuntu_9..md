---
title: "[SOLVED] Update for Epson Stylus T10 for Ubuntu 9.04"
date: 2009-06-02
forum: Philippine Team
---

### Post by Script Warlock on 2009-06-02
may bago akong printer na epson stylus t10 at plug and play nga ito using the t20 galing sa databse ng printing at nang lumabas ang update na mga foos, libs, cups. yes update ko nga pero the printer stops working wew sana di ko na lang update. any driver for this printer?

sino may idea paano mapagana ang ekpstm(ink monitor) sa ubuntu....

---

### Post by loell on 2009-06-02
what ubuntu version?

---

### Post by Script Warlock on 2009-06-02
9.04

printer status monitor pala yung makita ang level ng ink

---

### Post by loell on 2009-06-02
na try mo na to?

[http://ubuntuforums.org/showthread.php?t=1096369]("http://ubuntuforums.org/showthread.php?t=1096369")

[http://linux.avasys.jp/customerservice/pips3x_ubuntu804_e.html](http://linux.avasys.jp/customerservice/pips3x_ubuntu804_e.html)


also try  **escputil** for ink monitoring available in the repo

---

### Post by Script Warlock on 2009-06-02
found it: autodetect nga ang epson stylus t10 pero ang ginamit nya na driver is sa t20 so pagkatapos magupdate dunno why it broke pero ang ginawa ko ay delete the t20 printer. tapos install ang openprinting-gutenprint_5.2.3-1lsb3.2_i386.deb from openprinting website
pagkatapos created new printer so autosearch agad si U9.04 dun nakita nya si T20 at next ng next tapos yun kita nya sa database si T20+gutenprint(recommended).

and now 100% working with escputil as printer status monitor and this is all about Ubuntu 9.04.

yung link na binigay is pagmakabalik na ako sa 8.04 later this month......ty boss

---

### Post by Script Warlock on 2009-06-07
koreksyon lang po to clear some....

t10 in ubuntu 8.04/9.04 using this [link]("http://linux.avasys.jp/customerservice/pips3x_ubuntu804_e.html") will install to printing db as t10 cups 1.3 gumagana pero konti lang ang option sa printer..

t10 in ubuntu 8.04/9.04 using the t20 driver+openprinting ay 100% working at dami option sa printing....

---

