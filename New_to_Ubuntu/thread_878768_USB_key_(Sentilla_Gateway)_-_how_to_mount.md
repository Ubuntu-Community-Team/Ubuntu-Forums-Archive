---
title: "USB key (Sentilla Gateway) - how to mount?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by felipegaucho on 2008-08-03
I am not sure if "mount" is the correct word, but I connected teh Sentilla Gateway (USB key) and when I run the sample program, it say "Gateway not found"...

questions:

- how to check if the key is connected and recognized in the computer ?
- how to mount it, if needed ?

from my lsusb:

fgaucho@fortunario-box:~$ lsusb
Bus 006 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 006 Device 001: ID 0000:0000  
Bus 008 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

from dmesg:

[ 2355.121393] usb 6-1: FTDI USB Serial Device converter now attached to ttyUSB0
[ 2396.909403] usb 5-5: new high speed USB device using ehci_hcd and address 6
[ 2397.169107] usb 5-5: configuration #1 chosen from 1 choice
[ 2397.169320] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[ 2420.836566] ehci_hcd 0000:00:1d.7: remove, state 1
[ 2420.836576] usb usb5: USB disconnect, address 1
[ 2420.836578] usb 5-5: USB disconnect, address 6
[ 2420.841351] ehci_hcd 0000:00:1d.7: USB bus 5 deregistered
[ 2420.841388] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 2420.841395] ehci_hcd 0000:00:1a.7: remove, state 4
[ 2420.841401] usb usb4: USB disconnect, address 1
[ 2420.845493] ehci_hcd 0000:00:1a.7: USB bus 4 deregistered
[ 2420.845519] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[ 2421.123664] usb 8-1: new full speed USB device using uhci_hcd and address 2
[ 2421.397353] usb 8-1: configuration #1 chosen from 1 choice
[ 2421.400307] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)

---

### Post by red_Marvin on 2008-08-03
Not knowing what it is, but doing a google search, maybe this can help you?:
[http://weblogs.java.net/blog/felipegaucho/archive/2008/08/pervasive_compu_1.html](http://weblogs.java.net/blog/felipegaucho/archive/2008/08/pervasive_compu_1.html)

---

