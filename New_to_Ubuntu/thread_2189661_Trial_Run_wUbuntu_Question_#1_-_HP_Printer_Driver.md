---
title: "Trial Run w/Ubuntu Question #1 - HP Printer Driver"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by terrytrumps on 2013-11-23
Greetings all!  I'm brand spanking new to Ubuntu, still have Windows 7 installed, just giving this a shot and feeling it out.  Before I wipe Windows and start over (since I don't have the Windows disk), I wanna make sure I will be funcional and operational.  So question:

Does anyone know where to find a driver for an HP7210 Officejet, or how to make the thing operational?  
As far as I got was determining that I have hplip already, that I don't know where to find an appropriate Ubuntu/HP interface, and that my printer doesn't work.

Any suggestions??  Thanks in advance!

---

### Post by manudo on 2013-11-23
Is that an USB printer? Then install CUPS and add it, it should be detected.

---

### Post by ajgreeny on 2013-11-23
Install hplip-gui for the GUI configuration interface and then open that and use the add-printer from there.

---

### Post by elliotn on 2013-11-23
HPLIP will do

---

### Post by Dennis N on 2013-11-23
Your printer (Officejet 7210) is said to be "fully supported". 

[http://hplipopensource.com/hplip-web/supported_devices/officejet.html](http://hplipopensource.com/hplip-web/supported_devices/officejet.html)

You do not need to install anything yourself, or find drivers yourself. After installing Ubuntu (or Xubuntu, Lubuntu...) open the the 'Printers' Dialog under Settings after attaching printer. The setup process is quick and easy. The right driver will be downloaded automatically and installed. Should not take more than five minutes.

---

### Post by newb85 on 2013-11-23
Welcome to Ubuntu and the forums!  For someone who is brand spanking new to Ubuntu, it is often a good idea to start with Ubuntu alongside Windows, rather than hastily wiping Windows.  You may find that there are some things you need your computer for that just aren't practical (or in some cases possible) with Linux.  With a dual-boot setup, you can choose when you turn the machine on whether to boot into Windows or Ubuntu.  That way, you can make an experienced judgement call about whether you should keep Windows.  (If you don't do a Wubi install, scrapping Windows later is always an option.)  Meanwhile, Ubuntu doesn't really take that much HDD space, compared to modern hard drives.  (I think the footprint of the latest Ubuntu is in the neighborhood of 5GB.)

Of course, this is assuming this isn't a secondary machine.  If it's a tinkering machine, and you can fall back on Windows on a different machine, then keeping Windows on this machine is probably pointless.

---

### Post by mapes12 on 2013-11-23
You will probably find that the version of hplib in your distro of Ubu is out of date. Download the latest version and follow the installation instructions from here:-

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

The setup routine will detect your printer.

Mark

---

### Post by ajgreeny on 2013-11-23
Your machine is fully supported by the version of **hplip** in all ubuntu versions still available and supported, so there is no need to bother updating to the new hplip from its own website.

I suggested installing the **hplip-gui **only because it gives you many more configuration options and control that the plain hplip driver package, and as you are a new user of ubuntu you will probably find it invaluable.
Here's a screenshot of what you will get with the hplip-gui package installed.

---

