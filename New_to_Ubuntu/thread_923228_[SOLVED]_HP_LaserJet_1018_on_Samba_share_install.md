---
title: "[SOLVED] HP LaserJet 1018 on Samba share install"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by MarlonDean on 2008-09-18
Hi,

I have just switched from ubuntu to kubuntu and I am wondering how to get my networked HP Laserjet 1018 installed.

In Gnome it was really simple, but I am struggling in KDE.

Here is what I did so far:

*Click KDe Button (start) -> System Settings -> Printers
*Clicked the add button Left top -> Add Printer/Class
*Clicked Next
*Selected SMB Shared Printer
*Clicked Next
*Selected Anonymous (There is no password on the windows machine)
*Clicked Next
*Clicked Scan

Now this is where I get lost. It Detects the workgroup, but it only detects one machine in that workgroup (and there is no printer installed on that one)

I already checked if I can browse the network, but the KDE print wizard doesnt detect the computer with the HP installed.

Any suggestions? Is GNOME a Simpler DE? It seems so to me - I have hade several problems with KDE so far that just worked in gnome..

Please help and thanks!

---

### Post by alexsr on 2008-09-18
"In Gnome it was really simple"

how ??? pls tell me !!!

---

### Post by MarlonDean on 2008-09-18
I'll try to remember,lets see...

System-> Administration -> Printers
Add New
Select SMB printer (if it is a windows share)
next
Browse to the computer and click on the printer
next
select the driver

and from there you cant go wrong

---

### Post by Orange_and_Green on 2008-09-18
Hi :KS

You can get to a CUPS interface via a little "trick":

open your favourite browser (Firefox, Konqueror, take your pick) and in the address bar type:
```
http://127.0.0.1:631/
```

Wee - CUPS control panel! From there you can "manage printers" etc.

This "trick" works for GNOME/KDE/anything alike.

Have fun:KS

---

### Post by MarlonDean on 2008-09-18
Brilliant! Thanks...

---

### Post by Orange_and_Green on 2008-09-18
Did it work? :) I'm so happy for you:KS

In general, if you want to install a Samba printer and searching does not find anything, you can specify a URL for the printer with this syntax:

```
smb://{username}:{password}@server_fqdn/printername
```

An example might be smb://Orange:Green@server1.orange.green.com/MySambaPrinter

Good luck:KS:KS:KS:KS:KS

---

