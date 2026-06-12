---
title: "Pre Installation Sata Question"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by stuart264 on 2008-06-26
I am currently waiting for the components for a new pc to be delivered to run windows and rather than the dual boot system I have at the moment I am going to take my old pc and convert it to Ubuntu 8.4 AMDx64 Version but I am a bit concened about the Sata Raid Drivers and the install process.

The motherboard is a Gigabyte GA-K8VM800M with an onboard VIA VT8237 SATA RAID system that needs drivers to run I wanted to check if the drivers for this form part of the 8.4 Installation CD Rom or if I can download the driver from [http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143") and use it during the install process however I dont know how to do this, can I copy the drivers onto my USB Stick and run them from there or do I have to slipstream them into the intstallation CD the same way that Windows XP Insists on.

Stuart

---

### Post by dca on 2008-06-26
This isn't gonna' help you but when I installed RHEL it prompted during install for the drivers...
 
According to this:
[http://www.viaarena.com/default.aspx?PageID=2&Type=3](http://www.viaarena.com/default.aspx?PageID=2&Type=3)
 
...it lists Ubuntu as one of the options so I would assume it's similar.

---

### Post by stuart264 on 2008-06-26
When it prompted did it give the option to look for the drivers so I can load them off a USB Stick?

---

### Post by dca on 2008-06-26
I want to say we used a 'nostorage' or some other kind of kernel command to invoke driver installation...  Can't remember, however:
 
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143)
 
If you click on the links for 'click here to download' for 7.10 x686/64 it includes an installation PDF that may help...

---

### Post by stuart264 on 2008-06-26
I dont know how to do that, it would make life so much easier if I could install drivers from my flash drive

---

