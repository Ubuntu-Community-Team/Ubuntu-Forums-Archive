---
title: "Network Printer Installation"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by hwatari on 2008-11-23
I have an Ethernet Lan with a PC running Ubuntu 8.04 LTS and a print server with HP LaserJet 2100.
Before I upgraded to Ubuntu 8.04 LTS from 6.1, I had no problem with the network printer but as soon as I upgraded to 8.04 LTS, I can't install the printer (LPD, IPP or AppSocket/HP JetDirect).
Does anybody have any idea about this ?
Thanks,
Hiromichi

p.s. With 6.1, the network printer installation took literally a few seconds and worked right from the start.

---

### Post by jimmy the saint on 2008-11-23
go to system>administration>printing and select add printer.  It should automatically detect the printer.  
troubleshooting:
Printer connedted to network?  double check, use the little screen thingy if it has one to check the ip adresss.
Try to ping the pritners ip.  If you cannot get through, you will not be able to add it and it may be a firewall issue.  

HPs usually work well

---

### Post by hwatari on 2008-12-02
> **jimmy the saint said:**
> go to system>administration>printing and select add printer.  It should automatically detect the printer.  
troubleshooting:
Printer connedted to network?  double check, use the little screen thingy if it has one to check the ip adresss.
Try to ping the pritners ip.  If you cannot get through, you will not be able to add it and it may be a firewall issue.  

HPs usually work well

Thank you for your reply, jimmy the saint.
Printer was not automatically detected by ubuntu so I added it manually.
I am also able to ping the print server at 192.168.2.200.
My print server is Hawking HPS1P connected directly to the router and I can print to it from my PC running Win/XP (dual boot with ubuntu) but not from ubuntu.  Do you have any other suggestions ?
Hiromichi

---

### Post by hwatari on 2008-12-05
I can't have the following url for HP LaseJet 2100 connected to Hawking HPS1P print server, CUPS complains.

socket://192.168.2.200:9100?waiteof=false

which I believe I need to prevent print server from hanging, does anybody have any idea how to do this ?
Thanks,
Hiromichi

---

### Post by collegeKid28 on 2009-02-16
> **hwatari said:**
> I can't have the following url for HP LaseJet 2100 connected to Hawking HPS1P print server, CUPS complains.

socket://192.168.2.200:9100?waiteof=false

which I believe I need to prevent print server from hanging, does anybody have any idea how to do this ?
Thanks,
Hiromichi


Did you get this working?

---

### Post by hwatari on 2009-02-16
> **collegeKid28 said:**
> Did you get this working?

No, I gave up after spending about a week on it, I have more important things to do.  Now the printer is no longer networked (sigh) it is connected
to one of my desktop and it is shared through this pc which is a real pain in you know what.  Because I have networked pc's operating in Windows and Ubuntu including the host pc so I have to set up the printer for both operating systems and set up printer sharing for both operating systems, nooooooooooo !!!!
It's a shame that I couldn't figure out such an easy task(ought to be) and couldn't get any solutions on the net, maybe that's why Windows is so popular because at the least you can make things work with it(even though the os may not be all that well put together but for most users they don't care about that.)

---

### Post by ridgeland on 2009-02-26
Hi hwatari,

I had no trouble with sharing printers on our LAN with Ubuntu 7.04.  I'm using 8.10 now and I had a hard time getting to the network printer. It's not as simple as it was. Here is how I got there:

checked first that I am in group lpadmin OK
Start Menu -> System -> Administration -> Printing
New -> Printer
Internet Printing Protocol (ipp)
Host: LAN Address for Wife's printer: 198.168.123.112
leave Queue as default of /printers/
then click on [Find Queue]
IPP Browser starts - finds Wife's printer i560 Location Gateway Laptop
states URI: ipp://Laptop.local:631/printers/i560
Warns to install something before using this printer ( was it gutenprint-cups ? ).
Checked in synaptics - looks like I have 
cups-driver-gutenprint 
so I sent a test page from gedit - printed fine.  So 1040 pdfs now.  Prints but bad color in fields ... thats a different issue.
We have our router use fixed IPs for our PCs, makes NFS easy, printing too.

---

### Post by hwatari on 2009-03-11
Hi ridgeland,
Thank you very much for your reply, I have been very busy and haven't had much time to deal with the printer server problem lately.
But when I do, I will be sure to let you know how I make out.
Thanks,
Hiromichi

------------------------------------------------------------


> **ridgeland said:**
> Hi hwatari,

I had no trouble with sharing printers on our LAN with Ubuntu 7.04.  I'm using 8.10 now and I had a hard time getting to the network printer. It's not as simple as it was. Here is how I got there:

checked first that I am in group lpadmin OK
Start Menu -> System -> Administration -> Printing
New -> Printer
Internet Printing Protocol (ipp)
Host: LAN Address for Wife's printer: 198.168.123.112
leave Queue as default of /printers/
then click on [Find Queue]
IPP Browser starts - finds Wife's printer i560 Location Gateway Laptop
states URI: ipp://Laptop.local:631/printers/i560
Warns to install something before using this printer ( was it gutenprint-cups ? ).
Checked in synaptics - looks like I have 
cups-driver-gutenprint 
so I sent a test page from gedit - printed fine.  So 1040 pdfs now.  Prints but bad color in fields ... thats a different issue.
We have our router use fixed IPs for our PCs, makes NFS easy, printing too.

---

### Post by portly on 2009-03-24
> **ridgeland said:**
> Hi hwatari,

I had no trouble with sharing printers on our LAN with Ubuntu 7.04.  I'm using 8.10 now and I had a hard time getting to the network printer. It's not as simple as it was. Here is how I got there:

checked first that I am in group lpadmin OK
Start Menu -> System -> Administration -> Printing
New -> Printer
Internet Printing Protocol (ipp)
Host: LAN Address for Wife's printer: 198.168.123.112
leave Queue as default of /printers/
then click on [Find Queue]
IPP Browser starts - finds Wife's printer i560 Location Gateway Laptop
states URI: ipp://Laptop.local:631/printers/i560
Warns to install something before using this printer ( was it gutenprint-cups ? ).
Checked in synaptics - looks like I have 
cups-driver-gutenprint 
so I sent a test page from gedit - printed fine.  So 1040 pdfs now.  Prints but bad color in fields ... thats a different issue.
We have our router use fixed IPs for our PCs, makes NFS easy, printing too.

It (ubuntu 8.10, with KDE 4 desktop) also seems to allow adding of printers like this (which to me looks like it was when I had kde 3.5.x). My problem is that the system seems to see a network printer, but OOo.org 2.4 doesn't.

Damn!

regards

Portly!

---

### Post by ridgeland on 2009-03-24
Hi Portly,
I use Gnome so I'm not sure of KDE.  Did re-booting not solve it? Does Kwrite (is that the gedit equivalent?) print to the network printer?

---

