---
title: "[SOLVED] Problem getting HP Deskjet D2400 to print."
date: 2008-06-05
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-06-05
I am having a problem getting my new D2400 printer printing.  It starts to print and after one line it quits and the power light flashes quickly and I get an error stating communications have been lost with the printer.  I am wondering if this problem could be due to the USB port I am using.  I have an old computer with USB 1.0 ports.  I was wondering if a add on card with USB 2.0 ports would help with this problem.  Any other ideas are welcome.

PS- I have already updated HPLIP, cups and foomatics to the latest versions.

Donnie

---

### Post by alienexplorers on 2008-06-05
bump

---

### Post by starcannon on 2008-06-05
Looked through the compatibility list here:
[http://hplip.sourceforge.net/models/deskjet/deskjet_d2400_series.html](http://hplip.sourceforge.net/models/deskjet/deskjet_d2400_series.html)

Looks like it should go, when in doubt go with the printer model number closest to your own, is how I got my hp c4385 running under gutsy.

I use the configurator in System-->Administration-->Printing: New Printer: choose your printer or manually add it, either way follow along the wizard.

GL hope that helps.

---

### Post by alienexplorers on 2008-06-05
Still having the same problem where printing starts and then stops and I get a connection error.

---

### Post by avtolle on 2008-06-05
Do you have another USB port available to hook the printer up to other than the one currently used? If so, try "moving" it, restart (likely not needed, but one never knows) and see if it prints.

---

### Post by alienexplorers on 2008-06-06
Changed USB 2.0 Port Cart and new cable and problem when away.  Thanks for your help.

---

