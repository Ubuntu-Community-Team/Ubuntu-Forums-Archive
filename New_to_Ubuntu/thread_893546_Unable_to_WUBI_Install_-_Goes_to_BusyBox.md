---
title: "Unable to WUBI Install - Goes to BusyBox"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Darksci on 2008-08-18
I'm trying to install Ubuntu 8.04 WUBI to test it out on Vista.
It installs correctly and I get a Windows boot screen, so I select Ubuntu.

It goes to the Graphical Splash Screen so I can see the loading bar move.

However after that it then goes straight to a commandline interface and straight to "BusyBox".

It gives me the error:
Driver 'sd' needs updating - please use bus_type methods
Attached SCSI removable disk
Attached scsi generic sg0 type 0


I'm pretty sure it means it detects my usb external Optical disk, but not my actual Hard Drive.

The hard drive i'm using is: 1.8" Samsung SpinPoint N2 HS06THB
Believe it is a ZIF type interface. The pc i'm using is a Kohjinsha SC3.

Any ideas as to why it might not detect the HDD?

---

### Post by Darksci on 2008-08-18
[img]http://c.imagehost.org/0262/15082008190.jpg[/img]

Guess an image might help ^^;

---

### Post by thebigbluecan on 2008-08-23
It's a bug... I posted it myself. 
[https://bugs.launchpad.net/ubuntu/+bug/217616](https://bugs.launchpad.net/ubuntu/+bug/217616)
My system works now that I switched to 64bit
By the looks of it ([http://ark.intel.com/cpu.aspx?groupID=35466](http://ark.intel.com/cpu.aspx?groupID=35466))
Your proccessor doesnt support 64bit :(

---

