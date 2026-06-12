---
title: "Ubuntu print server for MS network..."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Blutrille on 2008-06-19
I am running Ubuntu 8.04 on my network as the server for pretty much all of my services. I have two issues. Where would I add the server to my existing MS workgroup? Second, I am trying to use the server as a print server for the MS XP SP3 laptops. The printer is a HP Deskjet 5550. The printer is added on the server and work fine locally. I have attached to the server in explorer via "\\192.168.1.3" and right clicked the printer and said connect. I am told that the print driver nessary does not exist and it gives me an option to point to a alternate driver. I have been unable to find the nessary drive it is looking for. How do I allow my Ubuntu server to be the acting print server for my LAN?

Thanks ahead of time :)

---

### Post by Humph on 2008-06-19
My inclination would be to install the HP 5550 as a local printer on LPT1: on the XP machine, then change the port to point at \\192.168.1.3\printer_name.

---

### Post by Xerp on 2008-06-19
Thats handled by CUPS and Samba. Couldn't find the Ubuntu pages, but these are the Gentoo ones:

[http://gentoo-wiki.com/HOWTO_Native_Windows_Printing_with_CUPS/Samba](http://gentoo-wiki.com/HOWTO_Native_Windows_Printing_with_CUPS/Samba)

---

