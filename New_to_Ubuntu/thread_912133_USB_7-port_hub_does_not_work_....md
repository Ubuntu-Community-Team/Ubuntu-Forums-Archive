---
title: "USB 7-port hub does not work ..."
date: 2008-09-06
forum: New to Ubuntu
---

### Post by cwmoser on 2008-09-06
I purchased a USB 7-port hub extender and it does not work with Ubuntu Hardy.  Is there something I need to do to get this to work?

This is a powered hub.

dmesg output looks like:

[ 1933.048803] usb 5-3.3.1: device not accepting address 65, error -71
[ 1978.967345] usb 5-3.3: USB disconnect, address 61
[ 1982.045946] usb 5-6: new high speed USB device using ehci_hcd and address 66
[ 1982.175292] usb 5-6: configuration #1 chosen from 1 choice
[ 1982.175600] hub 5-6:1.0: USB hub found
[ 1982.176026] hub 5-6:1.0: 1 port detected
[ 1982.443296] usb 5-6.1: new high speed USB device using ehci_hcd and address 67


Carl

---

### Post by cwmoser on 2008-09-06
BTW, when I run the lsusb command, I get:

$ lsusb
Bus 005 Device 066: ID 067b:2515 Prolific Technology, Inc. Flash Disk Embedded Hub
Bus 005 Device 058: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 057: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 028: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 005 Device 002: ID 03f0:2917 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 001: ID 0000:0000  


The website for the manufacturer of the hub is:  [http://www.genesyslogic.com/](http://www.genesyslogic.com/)

Any help is appreciated.

Carl

---

### Post by cwmoser on 2008-09-06
sudo  modprobe  -r  ehci-hcd

---

### Post by Mr_Kurt on 2009-02-02
Thank you very much for the last command, my problem was the same and this is the key.

Regards, Kurt

---

