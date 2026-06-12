---
title: "Server Install is driving me nuts"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by mlwsutton on 2012-08-01
Hi guys,

I have a 2001 windows machine & I thought it might be interesting to turn it into a web server.  However, it doesn't seeem to be working.  The CD/DVD player is bust so I am trying to install via a USB key.  I have downloaded pendrivelux usb installer & the iso files for Ubuntu server 11.04 & 10.04. I then set the boot order to USB first but the machine just hangs for ages, gives up & boots windows from the hard drive.  

Anybody had a similar problem? Able to offer any advice

Thanks

---

### Post by krustenBrot on 2012-08-01
Try another clean Stick / another USB port? ... my first and only guess - sorry :)

---

### Post by LinuxBill on 2012-08-01
> **mlwsutton said:**
> Hi guys,

I have a 2001 windows machine & I thought it might be interesting to turn it into a web server.  However, it doesn't seeem to be working.  The CD/DVD player is bust so I am trying to install via a USB key.  I have downloaded pendrivelux usb installer & the iso files for Ubuntu server 11.04 & 10.04. I then set the boot order to USB first but the machine just hangs for ages, gives up & boots windows from the hard drive.  

Anybody had a similar problem? Able to offer any advice

Thanks

What I would do is from in the BIOS disable the boot order so it doesn't try to boot from anything else other than the USB. See what it says once it tries to boo from the USB. It may come up with an error about no bootable media. If this is the case I would attempt to put Ubuntu on the USB again or try another stick. 

Bill

---

### Post by mastablasta on 2012-08-01
try unetbootin for "burning" the image to usb.
or linuxliveusb

---

### Post by mlwsutton on 2012-08-14
Thanks for the replies.  

I have tried different USB ports, different versions of the server (10 & 12.04), a USB CD drive & different USB installers.   I am still getting a no bootable device error every time.  Next step is try a different USB key.  That or throw the thing out of the window.....

---

### Post by Cheesemill on 2012-08-14
Does your machine actually support booting from USB?

---

### Post by mr-woof on 2012-08-14
If your machine can't boot from usb, you can try the plop bootloader:

[http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)

It will allow you to boot from usb after its loaded

---

### Post by mlwsutton on 2012-08-20
Brilliant!  Plop did the trick.  I guess my machine couldn't boot from USB, which is confusing as the BIOS gave an option for USB.  Thanks for your help

---

