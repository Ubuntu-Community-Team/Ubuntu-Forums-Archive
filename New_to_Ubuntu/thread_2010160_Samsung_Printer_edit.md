---
title: "Samsung Printer edit"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by expatCM on 2012-06-25
I have a Samsung ML-2850D and it works.  Well it used to.  I just changed my router and the IP range has to be reflected on the network and this is the problem ...

Does anyone know how to edit the network address of the printer or otherwise how to reset the printer to start off new?

---

### Post by expatCM on 2012-07-09
Ok ...  I have now figured this out and post in case anyone should ever need to know how ....

First set the client PC to the former IP range.

Next run sudo nmap -sP 192.168.1.0/24 (changing the IP range to the old range).  This will identify the Samsung printer, the MAC address and the IP that is used for the printer.

Use a browser to open that IP address.

There all network and printer settings are shown.  Simply edit the network address and gateway to the new IP range.

Return the client PC to the new IP range.

Done.

---

