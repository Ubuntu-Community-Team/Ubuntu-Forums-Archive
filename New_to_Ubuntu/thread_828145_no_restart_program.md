---
title: "no restart program"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by pasargad on 2008-06-13
i want to know,does any program exist to switch between operating systems without restarting:confused:

---

### Post by Cypher on 2008-06-13
If you are running a second OS inside a Virtual machine (VitualBox, VMWare, Virutal PC) then you can easily switch. But if you are dual-booting, then you have to restart as the OS' are running independently of each other..

---

### Post by avtolle on 2008-06-13
> **pasargad said:**
> i want to know,does any program exist to switch between operating systems without restarting:confused:
AFAIK, the only way you may accomplish this is to run the other operating system(s) under a virtual machine. If you are otherwise dual booting, or running Ubuntu under a Wubi install within Windows, you must close out and restart.

---

### Post by pasargad on 2008-06-13
i install Ubuntu from windows by wubi ,is there any way exist to switch it to virtual machine

---

### Post by avtolle on 2008-06-13
You would need to delete Ubuntu (use the add-remove program feature under Windows), then install a virtual machine, and install Ubuntu from the CD or the iso (someone help here, I've never done this) as an O/S within the virtual machine.

---

### Post by Cypher on 2008-06-13
Microsoft has a free virtual machine for Windows called [Virtual PC]("http://www.microsoft.com/windows/downloads/virtualpc/default.mspx"), install that and you can then install Ubuntu within there and "boot" it up when you want and still have access to your Windows machine..

---

### Post by eriqjaffe on 2008-06-13
> **Cypher said:**
> Microsoft has a free virtual machine for Windows called [Virtual PC]("http://www.microsoft.com/windows/downloads/virtualpc/default.mspx"), install that and you can then install Ubuntu within there and "boot" it up when you want and still have access to your Windows machine..There are graphics issues installing Ubuntu inside VirtualPC.  The real-wirkd video card that Virtual PC emulates supports 24-bit video, but the virtualized version only supports 16-bit, but that screws up the hardware detection and the video comes out all garbled.

---

### Post by Cypher on 2008-06-13
I've used Fiesty under Virtual PC without any problems..I haven't tried Gutsy or Hardy to see if any issues exist..

---

