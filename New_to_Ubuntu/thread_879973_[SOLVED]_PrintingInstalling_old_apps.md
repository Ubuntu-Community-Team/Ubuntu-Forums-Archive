---
title: "[SOLVED] Printing/Installing old apps"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by RequinB4 on 2008-08-04
Ok.  I'm trying to get my hp deskjet 3653 to work on hardy.  Apparently, the problem is the connection from cups to the printer (from a few hours of searching, i'm assuming this is the device URI's problem).  In system - administration - printing (as well as in [http://localhost:631](http://localhost:631)) Everything works fine except choosing the device - There is no option for the usb printer.  There is, however, an option for "Unknown" - an unknown usb printer.  However, I cannot select this device.

I had gotten around this problem via the following method in gutsy:
> 

After using the default "printing" program (system - admin) to tell CUPS the specifications you want for your printer and the driver (the 3650 hplip one), you then need to install the secondary "Printing" application from applications - add/remove, then run the second "Printing" in system - administration, then rightclick the deskjet_3600 and click properties. Click the Connection tab, click "Local or detected printer", "Use a detected printer", and "hp deskjet 3600"


So, I guess an alternaive to figuring out what URI I should use (much appreciated), it would also be helpful to install that program that doesn't seem to exist in hardy (why?).  Here is the screen I'm refering to:

[img]http://www.freesoftwaremagazine.com/files/www.freesoftwaremagazine.com/nodes/1265/ubuntuprinting7.jpg[/img]

---

### Post by LowSky on 2008-08-04
You printer is supported but you need an app called HPLIP, I think you can get it from Add/Remove under Applications. If not  download this app from HP [http://prdownloads.sourceforge.net/hplip/hplip-2.8.7.run](http://prdownloads.sourceforge.net/hplip/hplip-2.8.7.run)

then use these instructions to install [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)


good luck

---

### Post by RequinB4 on 2008-08-04
> **LowSky said:**
> You printer is supported but you need an app called HPLIP, I think you can get it from Add/Remove under Applications. If not  download this app from HP [http://prdownloads.sourceforge.net/hplip/hplip-2.8.7.run](http://prdownloads.sourceforge.net/hplip/hplip-2.8.7.run)

then use these instructions to install [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)


good luck

I installed HPLIP via add/remove, it says "connection error"

---

### Post by LowSky on 2008-08-04
what said connection error? actuall install or when you ran the programs and you tried connecting to the printer.

Try unpluging (not just turning it off) the printer, shutdown the computer, then plug the printer back in and reboot the computer. then run hplip

---

### Post by RequinB4 on 2008-08-04
> **LowSky said:**
> what said connection error? actuall install or when you ran the programs and you tried connecting to the printer.

Try unpluging (not just turning it off) the printer, shutdown the computer, then plug the printer back in and reboot the computer. then run hplip

Thank you much, test page printed out fine.  It never occurred to me to use hplip to set it up not just try and fix it (I thought it was a different frontend for the same backend.)

Solved.

---

