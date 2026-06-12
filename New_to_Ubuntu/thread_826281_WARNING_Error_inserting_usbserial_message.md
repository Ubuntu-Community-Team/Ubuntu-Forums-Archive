---
title: "WARNING: Error inserting usbserial message"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by worlestone on 2008-06-11
I'm trying to connect my Garmin Quest GPS to Mapsource under WINE and running Hardy.  I have done this successfully a few weeks ago.  Now have the message:

~$ modprobe garmin_gps
WARNING: Error inserting usbserial (/lib/modules/2.6.24-18-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted
FATAL: Error inserting garmin_gps (/lib/modules/2.6.24-18-generic/kernel/drivers/usb/serial/garmin_gps.ko): Operation not permitted
 
Any pointers appreciated

Thanks

---

### Post by gr4nf on 2008-06-11
try:
```

sudo modprobe garmin_gps

```

---

### Post by tinny on 2008-06-11
Has there been a kernel update lately???????

---

### Post by worlestone on 2008-06-12
Ahh - yes, thank you.  Fixed.

Thank goodness for the Forum :)

Adrian

---

