---
title: "Printer drivers"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by timbim on 2008-07-23
Are printer drivers for printers not officially supported on linux by manufacturers avialable?  Specifically the Brother MFC-7420.

---

### Post by northern lights on 2008-07-23
Brother provides drivers as .deb [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de").

Download the one for your model and install it - a double-click should do. If not run this first```
sudo apt-get install gdebi
```

---

### Post by phidia on 2008-07-23
[That printer]("http://openprinting.org/show_printer.cgi?recnum=Brother-MFC-7420") appears to be supported. Have you tried to install it by clicking System>Admin>Printing and then clicking "New Printer"?

---

### Post by timbim on 2008-07-23
TBH I don't have the printer yet, just checking to be safe.

---

### Post by avtolle on 2008-07-23
When you get the printer, take a look at this [https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(Brother](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(Brother)) and install the correct drivers (Laser) via Synaptic.

---

### Post by LowSky on 2008-07-23
The safest Linux friendly Printers are from HP, Just my 2 cents!

---

### Post by northern lights on 2008-07-23
Actually, I personally haven't encountered a Kyocera, HP, Brother or Epson that wan't in CUPS.

But hey, if it's just hypothetical - yep there's plenty support.

---

### Post by phidia on 2008-07-23
From the Ubuntu community documents on [printers]("https://help.ubuntu.com/community/Printers") there is also a [supported printers]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters") link. Hope that's useful.

---

