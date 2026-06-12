---
title: "[SOLVED] Epson USB Printer C90: /usr/lib/cups/backend/epson?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by simontaylor on 2008-11-07
Dear Ub-8.10-users,

My 8.10 upgrade seems to have aced my printer settings. Hard-won printer settings, I might add. 

going through admin>printing I find two possible printers, one a C90 and one Gutenprint. The latter had been the one that was working until I upgraded.

Neither now work. 

I've searched for drivers to no avail.

And going to the download panel for Gutenprint I discover that the download has something to do with Red Hat. 

In order to get 8.10 working I had to apt-get remove cman libfence3 so I wonder whether the loss of this cluster manager has somehow removed my cups/backend .... ?

Any answers or suggestions appreciated. Main thing is getting Epson C90 working with 8.10.

Thanks,

Simon

---

### Post by simontaylor on 2008-11-08
?

---

### Post by simontaylor on 2008-11-09
[http://www.linuxquestions.org/questions/ubuntu-63/pls-help-me-install-epson-c90-printer-driver-602578/](http://www.linuxquestions.org/questions/ubuntu-63/pls-help-me-install-epson-c90-printer-driver-602578/)

go to cups - as per instructions in link above - add printer - choose C68 as driver model (CUPS v1.3.x) (is listed as Gutenprint + CUPS (first C68 on list))

---

### Post by simontaylor on 2008-11-09
[http://www.linuxquestions.org/questions/ubuntu-63/pls-help-me-install-epson-c90-printer-driver-602578/](http://www.linuxquestions.org/questions/ubuntu-63/pls-help-me-install-epson-c90-printer-driver-602578/)

go to cups - as per instructions in link above - add printer - choose C68 as driver model (CUPS v1.3.x) (is listed as Gutenprint + CUPS (first C68 on list))

---

