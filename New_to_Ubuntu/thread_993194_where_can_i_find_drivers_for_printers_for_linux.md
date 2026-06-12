---
title: "where can i find drivers for printers for linux"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by ||Z0di4C|| on 2008-11-25
at my school i have ubuntulite and i have been trying to get a driver for a xerox phaser 8400 and at my house i run ubuntu 8.04 and im trying to get a driver for an epson printer i think that both would be a .deb file right? and if so where can i find these downloadable drivers?  Thanks

---

### Post by halitech on 2008-11-25
for the Phaser 8400 - [http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=8400&Xlang=en_US&Xcntry=USA&source=XOG](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=8400&Xlang=en_US&Xcntry=USA&source=XOG)

grab the Linux CUPS Printing Package, download it, extract it then use the add printer option to select the proper ppd file. IGNORE the other 2 options there as they will do nothing but confuse you. I'm assuming the Phaser is hooked up on a network and has an IP address?

---

### Post by damis648 on 2008-11-25
You might want to check out linuxprinting.org.

---

### Post by andrew.mckevitt on 2008-11-25
Have you tried just plugging the printers in and System - Administration - Printing.
Click 'New Printer' to see if it's already supported.

---

### Post by NewJack on 2008-11-25
> **damis648 said:**
> You might want to check out linuxprinting.org.

Here is a link to the above mentioned site:

[http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)

Great resource to check if a printer you have (or one you are looking to buy) is supported in Linux.

---

