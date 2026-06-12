---
title: "Supported Printers"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by mcnaug on 2012-04-08
Good Day
 
I am currently running two PCs with MS XP and one Laptop with Win 7. Win 7 does not support my two printers so I am considering coming over to Ubuntu if my printers are supported.
 
I have an ADSL line with one PC conneted via Lan and the second PC and the Laptop connecting via Wireless. One printer (HP LaserJet 4L) is connected via a DIY Ethernet Print Server (old Pent2) to allow access to both PCs and the Laptop. The second printer (Lekmark X9350) is connected via wireless.
 
Both PCs can print to both printers but they are not supported in Win 7 
 
Is there a "place" where I can check which printers are supported please?
 
Gareth

---

### Post by cryptotheslow on 2012-04-08
This may help:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

How is that DIY print server making the printer available? e.g. as a shared printer in windows?


The HP shouldn't be a problem [http://www.openprinting.org/printer/HP/HP-LaserJet_4L](http://www.openprinting.org/printer/HP/HP-LaserJet_4L)

The Lexmark - openprinting doesn't mention it and the Lexmark site has no Linux drivers available for it. If you can find a PPD file on your driver CD you may be able to get it to function in some form.

Maybe boot from an Ubuntu LiveCD and try it out? (You can try without installing anything).

---

### Post by mcnaug on 2012-04-08
Hi 
 
[http://members.shaw.ca/nicholas.fong/printsrv/](http://members.shaw.ca/nicholas.fong/printsrv/)
 
I have listed the site that detailed the use of an old Pc as a print server.  I have just revisited the site again and it seems that it will only work on Windows but as can be seen it is a stand alone connected to a lan point on the ADSL Router with its own IP address.  The Web page was obviously written some time ago as it talks about Windows 2000 and XP but the author is still checking the site as I had a reply to an email that I sent.
 
As you indicate the Laserjet 4L should not be a problem if connected direct to a PC.
 
The Lexmark is obviously a differant problem.  It is a good multi function printer with USB, Lan and Wireless connections.  Whilst the cartridges are expensive I am reluctant to buy another printer just to be able to connect to either Win7 or Ubuntu.
 
I will dig out the original printer CD and check to see if there is a PPD file and take it from there.
 
Regards
 
Gareth

---

### Post by cryptotheslow on 2012-04-08
Re the Lexmark - I'd have thought that if it is connected to wireless then it has an onboard network print server. I have yet to see any brand of printer network interface not support basic LPR/LPD printing (i.e. TCP/IP printing over port 515) alongside whatever proprietary protocol they may also offer.

That at least should take care of communicating the print job to the printer. But won't help with any of the multifunction stuff.


As for the DIY print server - it appears to just offer raw IP printing, so you should be able to get that working using LPR/LPD to port 9100 (or 9101, 9102) just fine.

---

### Post by mcnaug on 2012-04-08
As you say the prntsvr is raw IP printing and depending upon the no of lpt ports can be to 9100, 9101 or 9102.
 
I did try setting up both printers with win7 but just got GIGO.
 
It seems that either OS will not give me 100% printer compatability.
 
Many thanks for your help.
 
Gareth

---

