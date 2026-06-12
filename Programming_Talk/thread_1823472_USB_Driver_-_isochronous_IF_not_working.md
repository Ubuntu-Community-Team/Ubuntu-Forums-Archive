---
title: "USB Driver - isochronous IF not working"
date: 2011-08-12
forum: Programming Talk
---

### Post by Rack1600 on 2011-08-12
Hello,
I am working on a driver for a Bluetooth chip, which uses several interfaces - Interrupt (Bluetooth HCI message), Bulk (Bluetooth ACL Data), and Isochronous (Bluetooth SCO data).

Laptop is a Dell Vostro 1520
Ubuntu 2.6.31-23-generic

The Interrupt and Bulk interfaces seem to be working fine, but I cannot get anything to happen on the Isochronous interface when a SCO is started.

I have checked on a windows machine that the SCO data is coming up over USB in the Isoc IF, but now I am just a bit stumped as to what could be going wrong on the Isoc IF.

I have been looking at [http://lxr.linux.no/linux+v3.0.1/drivers/bluetooth/btusb.c](http://lxr.linux.no/linux+v3.0.1/drivers/bluetooth/btusb.c) for inspiration, but I cannot seem to get it to work. :(

Basically I have sprinkled some printk's around the TxIsoc and RxIsoc calls, but cannot really see what is going wrong.

I can get any debug, but I dont have a USB analyser or anything.  
Is there anyone out there who knows USB Isoc IF, can give me some pointers on config params to check, etc?  Any debug info wanted I can provide

TIA!
Rack

---

