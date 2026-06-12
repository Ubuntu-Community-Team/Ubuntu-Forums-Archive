---
title: "USB Drivers for Raid Controller"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by fish2222 on 2012-01-05
Hey guys, I have probably an easy question, but I need to ask.  I have an Intel Sr2500 Chassis server that has the intergrated RAID controller in it.  I have my drives setup, but when I get into the install process, it says that there are no drives found.  It gives me the list to choose from, but I need a megasr driver for this machine.  I download the Redhat drivers from Intel, and put them on a flash drive, but it still says there are no drivers on the flash media.  First off, does the flash drive need to formatted in an ext format instead of FAT, and will the redhat driver work with this?  It has the Intel Embedded Server RAID Technology II in it.  Thanks!

BTW - I am trying to install 11.10 server on this box.  Thanks!

---

### Post by cariboo on 2012-01-06
If the drivers are for RedHat, they more than likely have an .rpm extension, you need to convert the package to a .deb using alien, which is in the repositories. Once you have alien installed use the following command to convert the package to one that is usable:

```
alien -d packagename.rpm
```

Once the package has been converted to a .deb use the following command to install it:

```
sudo dpkg -i packagename.deb
```

---

### Post by fish2222 on 2012-01-10
Well, I followed your directions, but I am needing to install the drivers during the initial GUI install.  When I tell it to manually load drivers, it finds the megasr drivers, but says something about kernel module is missing.  It says you can try to install it anyway, but it won't work.

---

