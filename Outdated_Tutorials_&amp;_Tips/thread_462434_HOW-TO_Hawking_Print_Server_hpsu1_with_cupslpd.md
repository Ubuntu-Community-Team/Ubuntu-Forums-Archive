---
title: "HOW-TO: Hawking Print Server hpsu1 with cups/lpd"
date: 2007-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by jgordon510 on 2007-06-02
Had to cobble this information together from a few sources.  

First, hook everything up (power adapter, ethernet, and usb cable).  The server will acquire the ip address 192.168.1.250 by default.  Type that into your browser address bar.  The default username will be blank with a password of "1234".  

Click the "Setup Wizard" link and set the print server name to whatever you want to call your printer.  Remember what you name your print server; you'll need that info later.

Go into system -> administration -> printing and click "New Printer".

Change to "Network Printer" and then select "Unix Printer (LPD)"

Under host put the ip address of your print server (192.168.1.250 by default).  In queu put "lpt1".  Click forward.

Select your printer model and driver.  Click forward.

In the "name" field, type your print server name from before.

That's it.

---

### Post by jrattner on 2007-07-13
Nope any other ideas?

---

