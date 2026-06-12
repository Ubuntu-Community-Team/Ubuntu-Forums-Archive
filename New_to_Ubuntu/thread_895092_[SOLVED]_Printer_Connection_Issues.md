---
title: "[SOLVED] Printer Connection Issues"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by ElTesorillo on 2008-08-19
Hi, I am trying to connect to a printer on a wireless network but I cannot connect to the printer and I don't know how to set it up. Any help would be great. THanks

---

### Post by halitech on 2008-08-19
Is the printer connected directly to the network with an IP address or is it connected to another machine? Also, what type of printer is it?

---

### Post by LowSky on 2008-08-19
See if CUPS can find it, try this link
[http://localhost:631/](http://localhost:631/)

---

### Post by ElTesorillo on 2008-08-19
it is directly connected to a wireless network... CUPS confuses me and I dont know how to work it.

---

### Post by halitech on 2008-08-19
do you know the IP address of the printer? also, what type of printer is it?

---

### Post by ElTesorillo on 2008-08-19
The printer is a Canon MX300 and the IP address is 10.0.1.4

---

### Post by halitech on 2008-08-19
Doesn't look like 7.10 has support for that printer so will need to find drivers for it first. Once you have the drivers, follow the steps below.

go to System - Administration - Printing

click New Printer, select AppSocket/HPJetDirect and enter the IP address (10.0.1.4) and leave the port on 9100. Click Next

Select Provide PPD file and browse to where the file is located and click next. From there on it should be a matter of clicking next on the remaining screens

edit: actually it looks like you should be able to use the Canon PIXMA MP150 - CUPS+Gutenprint v5.0.1 driver that is already installed instead of providing the PPD file.

---

### Post by ElTesorillo on 2008-08-20
I did everything that you laid out but it says the the printer is not connected. I really am stumped, I used that driver from CUPS and it did not work. Is there a way around it?

---

### Post by ramjet_1953 on 2008-08-21
Here is a link to the Open Printing database for your printer:

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MX300](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MX300)

What your issue appears to be is that you don't have the driver loaded, so the printer won't work.

What I have always found useful when adding a wireless printer is to physically install the printer first, by plugging it directly into the PC, installing it, so that the correct drivers are loaded.

Now you are ready to try installing it onto your wireless network.

Good luck!

Regards,
Roger :cool:

---

### Post by halitech on 2008-08-21
> **ElTesorillo said:**
> I did everything that you laid out but it says the the printer is not connected. I really am stumped, I used that driver from CUPS and it did not work. Is there a way around it?

can you ping the printer when it is connected to the network?

---

### Post by ElTesorillo on 2008-08-22
When I connected my printer with the USB cable, it worked fine but it still does not work wirelessly, how do you ping the computer? Sry I have never done that before.

---

### Post by halitech on 2008-08-22
open a terminal (Applications - Accessories - Terminal)
then type in ```
ping 10.0.1.4
``` then press Enter

if you get replies, unplug or turn off the printer and ping it again. if you still get a response, you are pinging the wrong IP address

---

