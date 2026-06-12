---
title: "Sharing a Ubuntu printer on a Windows network"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by vancouversailor on 2008-06-17
I've set up a small (4 ubuntu workstations, 1 Windows 2003 terminal/applications server) network for a non profit society. So far everything works except I am still trying to figure out how to share an HP printer that is connected to one of the workstations, so that the user can print to it from applications they are running on the Windows Terminal Server. No problem printing locally from the workstation to the printer, and no problem accessing printers that are shared on the windows application server. So again the issue is how to share and make this printer which is physically connected to the Ubuntu workstation visible to the MS windows server.

---

### Post by avtolle on 2008-06-17
On the printer on the ubuntu workstation, did you indicate during installation of the printer that it was to be shared? Sorry, I cannot recall where that comes up during the installation, but recall saying yes to this at the time.

---

### Post by The Cog on 2008-06-17
First share the printer. Menu System->Administration->Printing, click Server Settings and then check the two boxes Share Published Printers and Allow Printing From the Internet.

Then enter a printer such as http:1.2.3.4:631/Deskjet_1280
but use your IP address and printer name of course.

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by superprash2003 on 2008-06-17
since its on a windows network you also need to edit samba [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by The Cog on 2008-06-18
> **superprash2003 said:**
> since its on a windows network you also need to edit samba [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)
No need to install samba unless you want the printer to be "browsable". The article I linked shows how to print from XP/vista to an Ubuntu printer using the CUPS server/protocol. Quick and easy.

---

