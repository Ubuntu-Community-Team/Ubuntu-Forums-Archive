---
title: "Problem printing on network printers"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by trikkievic on 2008-05-12
Hi, I'm using Ubuntu on a dual boot system on a network which predominantly has Windows machines connected to it. Even though Ubuntu works fine for 99 % there is just one simply task I have never been able to do, namely, print a document on any of the printers connected to the network.
When I open "printing" under system-administration, I see a list of "remote printers", among which I recognize the printer(s) I want to use. However, if I try to click on any of the printers in this list, the printer configuration screen freezes. I can only move it around or force quit it.
When I try to print a document from openoffice for instance, it simply doesn't come out. Trying to print a PDF from the document viewer, the viewer freezes.
It's probably something with CUPS, or somehow Ubuntu is unable to connect to the printers properly.
Anyone can help me out?

V.

---

### Post by Golem XIV on 2008-05-12
Are these stand-alone network printers or are they connected to a Windows machine?  If they are on a Windows machine, are they being shared?  Is the File and Printer Sharing option in the Windows system(s) enabled and not blocked by a firewall?  Are there any possible access permission issues?

---

### Post by trikkievic on 2008-05-14
I believe they are stand alone printers. The one I want to use is a laser printer in a printer room. It's in the "remote printers" list of the printing menu, but CUPS says it can not connect. When I started up this morning there were still documents pending accompanied by a message "Printer ... possibly not connected" and when I cancelled the jobs it said "CUPS unnable to connect". So somehow the printers are seen (as remote printers) but CUPS has some problem actually connecting to them. I don't know how to solve this.

---

### Post by freebeer on 2008-05-14
Try restarting cupsys.  I've found that on occasion it can get stuck and a restart sometimes helps.

```

sudo /etc/init.d/cupsys restart

```

Should do it.

---

### Post by phr0ze on 2008-05-14
I had to manually add my network printer to get it to work. Try redoing the printer, if possible get the model number and check the manufacturer site for a linux print driver. Mine had a driver for Redhat which I easily converted using alien.

---

