---
title: "new install usb mouse troubles"
date: 2015-05-16
forum: New to Ubuntu
---

### Post by daktaklakpak5576 on 2015-05-16
so I have installed this Ubuntu 12.04.5 LTS but not much luck with it so far.. no networking and no mouse.

Mouse is just a regular old logitech corded usb optical mouse. Mouse works fine in other OS. I have no idea what this ubuntu is trying to do with it though, mouse light goes out when starting ubuntu then driver just keeps hammering the usb bus? Have rebooted several times trying to fix this, mouse did work one time, now it just spews kernel messages to the console.

```
nyx yak # cat /mnt/tmp/var/log/kern.log | grep "May 16 09" | grep -E '(hu|us)b'May 16 09:01:29 unyx kernel: [    0.353670] usbcore: registered new interface driver usbfs
May 16 09:01:29 unyx kernel: [    0.353677] usbcore: registered new interface driver hub
May 16 09:01:29 unyx kernel: [    0.353700] usbcore: registered new device driver usb
May 16 09:01:29 unyx kernel: [    1.019932] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
May 16 09:01:29 unyx kernel: [    1.019934] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.019935] usb usb1: Product: EHCI Host Controller
May 16 09:01:29 unyx kernel: [    1.019936] usb usb1: Manufacturer: Linux 3.13.0-32-generic ehci_hcd
May 16 09:01:29 unyx kernel: [    1.019938] usb usb1: SerialNumber: 0000:00:12.2
May 16 09:01:29 unyx kernel: [    1.020035] hub 1-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.020041] hub 1-0:1.0: 5 ports detected
May 16 09:01:29 unyx kernel: [    1.031928] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
May 16 09:01:29 unyx kernel: [    1.031931] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.031932] usb usb2: Product: EHCI Host Controller
May 16 09:01:29 unyx kernel: [    1.031935] usb usb2: Manufacturer: Linux 3.13.0-32-generic ehci_hcd
May 16 09:01:29 unyx kernel: [    1.031936] usb usb2: SerialNumber: 0000:00:13.2
May 16 09:01:29 unyx kernel: [    1.032043] hub 2-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.032050] hub 2-0:1.0: 5 ports detected
May 16 09:01:29 unyx kernel: [    1.043919] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
May 16 09:01:29 unyx kernel: [    1.043920] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.043922] usb usb3: Product: EHCI Host Controller
May 16 09:01:29 unyx kernel: [    1.043923] usb usb3: Manufacturer: Linux 3.13.0-32-generic ehci_hcd
May 16 09:01:29 unyx kernel: [    1.043924] usb usb3: SerialNumber: 0000:00:16.2
May 16 09:01:29 unyx kernel: [    1.044038] hub 3-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.044043] hub 3-0:1.0: 4 ports detected
May 16 09:01:29 unyx kernel: [    1.103940] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
May 16 09:01:29 unyx kernel: [    1.103942] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.103944] usb usb4: Product: OHCI PCI host controller
May 16 09:01:29 unyx kernel: [    1.103945] usb usb4: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
May 16 09:01:29 unyx kernel: [    1.103946] usb usb4: SerialNumber: 0000:00:12.0
May 16 09:01:29 unyx kernel: [    1.104063] hub 4-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.104070] hub 4-0:1.0: 5 ports detected
May 16 09:01:29 unyx kernel: [    1.164027] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
May 16 09:01:29 unyx kernel: [    1.164029] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.164031] usb usb5: Product: OHCI PCI host controller
May 16 09:01:29 unyx kernel: [    1.164032] usb usb5: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
May 16 09:01:29 unyx kernel: [    1.164034] usb usb5: SerialNumber: 0000:00:13.0
May 16 09:01:29 unyx kernel: [    1.164152] hub 5-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.164159] hub 5-0:1.0: 5 ports detected
May 16 09:01:29 unyx kernel: [    1.224158] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
May 16 09:01:29 unyx kernel: [    1.224161] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.224163] usb usb6: Product: OHCI PCI host controller
May 16 09:01:29 unyx kernel: [    1.224164] usb usb6: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
May 16 09:01:29 unyx kernel: [    1.224165] usb usb6: SerialNumber: 0000:00:14.5
May 16 09:01:29 unyx kernel: [    1.224267] hub 6-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.224275] hub 6-0:1.0: 2 ports detected
May 16 09:01:29 unyx kernel: [    1.284107] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
May 16 09:01:29 unyx kernel: [    1.284110] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.284112] usb usb7: Product: OHCI PCI host controller
May 16 09:01:29 unyx kernel: [    1.284113] usb usb7: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
May 16 09:01:29 unyx kernel: [    1.284114] usb usb7: SerialNumber: 0000:00:16.0
May 16 09:01:29 unyx kernel: [    1.284285] hub 7-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.284293] hub 7-0:1.0: 4 ports detected
May 16 09:01:29 unyx kernel: [    1.284596] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
May 16 09:01:29 unyx kernel: [    1.284598] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.284599] usb usb8: Product: xHCI Host Controller
May 16 09:01:29 unyx kernel: [    1.284601] usb usb8: Manufacturer: Linux 3.13.0-32-generic xhci_hcd
May 16 09:01:29 unyx kernel: [    1.284602] usb usb8: SerialNumber: 0000:02:00.0
May 16 09:01:29 unyx kernel: [    1.284676] hub 8-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.284682] hub 8-0:1.0: 1 port detected
May 16 09:01:29 unyx kernel: [    1.284769] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
May 16 09:01:29 unyx kernel: [    1.284771] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 16 09:01:29 unyx kernel: [    1.284772] usb usb9: Product: xHCI Host Controller
May 16 09:01:29 unyx kernel: [    1.284774] usb usb9: Manufacturer: Linux 3.13.0-32-generic xhci_hcd
May 16 09:01:29 unyx kernel: [    1.284775] usb usb9: SerialNumber: 0000:02:00.0
May 16 09:01:29 unyx kernel: [    1.284853] hub 9-0:1.0: USB hub found
May 16 09:01:29 unyx kernel: [    1.284869] hub 9-0:1.0: 4 ports detected
May 16 09:01:29 unyx kernel: [    1.388191] usb 1-4: new high-speed USB device number 3 using ehci-pci
May 16 09:01:29 unyx kernel: [    1.500358] usb 1-4: device descriptor read/64, error -71
May 16 09:01:29 unyx kernel: [    1.716472] usb 1-4: device descriptor read/64, error -71
May 16 09:01:29 unyx kernel: [    1.932619] usb 1-4: new high-speed USB device number 4 using ehci-pci
May 16 09:01:29 unyx kernel: [    2.044682] usb 1-4: device descriptor read/64, error -71
May 16 09:01:29 unyx kernel: [    2.260850] usb 1-4: device descriptor read/64, error -71
May 16 09:01:29 unyx kernel: [    2.476970] usb 1-4: new high-speed USB device number 5 using ehci-pci
May 16 09:01:29 unyx kernel: [    2.521503] usb 1-4: device descriptor read/8, error -71
May 16 09:01:29 unyx kernel: [    2.665828] usb 1-4: device descriptor read/8, error -71
May 16 09:01:29 unyx kernel: [    2.881299] usb 1-4: new high-speed USB device number 6 using ehci-pci
May 16 09:01:29 unyx kernel: [    2.926027] usb 1-4: device descriptor read/8, error -71
May 16 09:01:29 unyx kernel: [    3.069730] usb 1-4: device descriptor read/8, error -71
May 16 09:01:29 unyx kernel: [    3.173427] hub 1-0:1.0: unable to enumerate USB device on port 4
May 16 09:01:30 unyx kernel: [    3.965885] usb 5-3: new full-speed USB device number 2 using ohci-pci
May 16 09:01:30 unyx kernel: [    4.133956] usb 5-3: device descriptor read/64, error -32
May 16 09:01:30 unyx kernel: [    4.382044] usb 5-3: device descriptor read/64, error -32
May 16 09:01:30 unyx kernel: [    4.626316] usb 5-3: new full-speed USB device number 3 using ohci-pci
May 16 09:01:30 unyx kernel: [    4.766359] usb 5-3: device descriptor read/64, error -32
May 16 09:01:31 unyx kernel: [    5.014592] usb 5-3: device descriptor read/64, error -32
May 16 09:01:31 unyx kernel: [    5.254707] usb 5-3: new full-speed USB device number 4 using ohci-pci
May 16 09:01:31 unyx kernel: [    5.662874] usb 5-3: device not accepting address 4, error -32
May 16 09:01:32 unyx kernel: [    5.806984] usb 5-3: new full-speed USB device number 5 using ohci-pci
May 16 09:01:32 unyx kernel: [    6.219322] usb 5-3: device not accepting address 5, error -32
May 16 09:01:32 unyx kernel: [    6.219423] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:01:32 unyx kernel: [    6.355357] usb 4-3: new low-speed USB device number 2 using ohci-pci
May 16 09:01:32 unyx kernel: [    6.499430] usb 4-3: device descriptor read/64, error -32
May 16 09:01:32 unyx kernel: [    6.743687] usb 4-3: device descriptor read/64, error -32
May 16 09:01:33 unyx kernel: [    6.983753] usb 4-3: new low-speed USB device number 3 using ohci-pci
May 16 09:01:33 unyx kernel: [    7.127990] usb 4-3: device descriptor read/64, error -32
May 16 09:01:33 unyx kernel: [    7.372087] usb 4-3: device descriptor read/64, error -32
May 16 09:01:33 unyx kernel: [    7.612241] usb 4-3: new low-speed USB device number 4 using ohci-pci
May 16 09:01:34 unyx kernel: [    8.020488] usb 4-3: device not accepting address 4, error -32
May 16 09:01:34 unyx kernel: [    8.156598] usb 4-3: new low-speed USB device number 5 using ohci-pci
May 16 09:01:34 unyx kernel: [    8.564821] usb 4-3: device not accepting address 5, error -32
May 16 09:01:34 unyx kernel: [    8.564834] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:01:35 unyx kernel: [    8.829035] usb 4-4: new full-speed USB device number 6 using ohci-pci
May 16 09:01:35 unyx kernel: [    8.969192] usb 4-4: device descriptor read/64, error -71
May 16 09:01:35 unyx kernel: [    9.213279] usb 4-4: device descriptor read/64, error -71
May 16 09:01:35 unyx kernel: [    9.453437] usb 4-4: new full-speed USB device number 7 using ohci-pci
May 16 09:01:35 unyx kernel: [    9.593527] usb 4-4: device descriptor read/64, error -71
May 16 09:01:36 unyx kernel: [    9.837686] usb 4-4: device descriptor read/64, error -71
May 16 09:01:36 unyx kernel: [   10.077844] usb 4-4: new full-speed USB device number 8 using ohci-pci
May 16 09:01:36 unyx kernel: [   10.102920] usb 4-4: device descriptor read/8, error -62
May 16 09:01:36 unyx kernel: [   10.227049] usb 4-4: device descriptor read/8, error -62
May 16 09:01:36 unyx kernel: [   10.466101] usb 4-4: new full-speed USB device number 9 using ohci-pci
May 16 09:01:36 unyx kernel: [   10.491222] usb 4-4: device descriptor read/8, error -62
May 16 09:01:36 unyx kernel: [   10.615318] usb 4-4: device descriptor read/8, error -62
May 16 09:01:36 unyx kernel: [   10.718265] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:01:37 unyx kernel: [   10.830355] usb 8-1: new high-speed USB device number 2 using xhci_hcd
May 16 09:01:37 unyx kernel: [   10.848145] usb 8-1: New USB device found, idVendor=2109, idProduct=3431
May 16 09:01:37 unyx kernel: [   10.848148] usb 8-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
May 16 09:01:37 unyx kernel: [   10.848150] usb 8-1: Product: USB2.0 Hub
May 16 09:01:37 unyx kernel: [   10.848681] hub 8-1:1.0: USB hub found
May 16 09:01:37 unyx kernel: [   10.849002] hub 8-1:1.0: 4 ports detected
May 16 09:01:37 unyx kernel: [   11.722918] usb 5-3: new full-speed USB device number 6 using ohci-pci
May 16 09:01:38 unyx kernel: [   11.863068] usb 5-3: device descriptor read/64, error -32
May 16 09:01:38 unyx kernel: [   12.107188] usb 5-3: device descriptor read/64, error -32
May 16 09:01:38 unyx kernel: [   12.347327] usb 5-3: new full-speed USB device number 7 using ohci-pci
May 16 09:01:38 unyx kernel: [   12.487434] usb 5-3: device descriptor read/64, error -32
May 16 09:01:38 unyx kernel: [   12.731588] usb 5-3: device descriptor read/64, error -32
May 16 09:01:39 unyx kernel: [   12.971747] usb 5-3: new full-speed USB device number 8 using ohci-pci
May 16 09:01:39 unyx kernel: [   13.380004] usb 5-3: device not accepting address 8, error -32
May 16 09:01:39 unyx kernel: [   13.516060] usb 5-3: new full-speed USB device number 9 using ohci-pci
May 16 09:01:40 unyx kernel: [   13.924409] usb 5-3: device not accepting address 9, error -32
May 16 09:01:40 unyx kernel: [   13.924527] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:01:40 unyx kernel: [   14.136509] usb 5-3: new full-speed USB device number 10 using ohci-pci
May 16 09:01:40 unyx kernel: [   14.276602] usb 5-3: device descriptor read/64, error -32
May 16 09:01:40 unyx kernel: [   14.520758] usb 5-3: device descriptor read/64, error -32
May 16 09:01:40 unyx kernel: [   14.760915] usb 5-3: new full-speed USB device number 11 using ohci-pci
May 16 09:01:41 unyx kernel: [   14.901055] usb 5-3: device descriptor read/64, error -32
May 16 09:01:41 unyx kernel: [   15.145171] usb 5-3: device descriptor read/64, error -32
May 16 09:01:41 unyx kernel: [   15.385324] usb 5-3: new full-speed USB device number 12 using ohci-pci
May 16 09:01:41 unyx kernel: [   15.793581] usb 5-3: device not accepting address 12, error -32
May 16 09:01:42 unyx kernel: [   15.929685] usb 5-3: new full-speed USB device number 13 using ohci-pci
May 16 09:01:42 unyx kernel: [   16.337934] usb 5-3: device not accepting address 13, error -32
May 16 09:01:42 unyx kernel: [   16.338026] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:01:42 unyx kernel: [   16.474043] usb 4-3: new low-speed USB device number 10 using ohci-pci
May 16 09:01:42 unyx kernel: [   16.614089] usb 4-3: device descriptor read/64, error -32
May 16 09:01:43 unyx kernel: [   16.858286] usb 4-3: device descriptor read/64, error -32
May 16 09:01:43 unyx kernel: [   17.098428] usb 4-3: new low-speed USB device number 11 using ohci-pci
May 16 09:01:43 unyx kernel: [   17.238534] usb 4-3: device descriptor read/64, error -32
May 16 09:01:43 unyx kernel: [   17.482693] usb 4-3: device descriptor read/64, error -32
May 16 09:01:43 unyx kernel: [   17.722851] usb 4-3: new low-speed USB device number 12 using ohci-pci
May 16 09:01:44 unyx kernel: [   18.131105] usb 4-3: device not accepting address 12, error -32
May 16 09:01:44 unyx kernel: [   18.267268] usb 4-3: new low-speed USB device number 13 using ohci-pci
May 16 09:01:44 unyx kernel: [   18.675461] usb 4-3: device not accepting address 13, error -32
May 16 09:01:44 unyx kernel: [   18.675551] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:01:45 unyx kernel: [   18.811567] usb 4-4: new full-speed USB device number 14 using ohci-pci
May 16 09:01:45 unyx kernel: [   18.951660] usb 4-4: device descriptor read/64, error -71
May 16 09:01:45 unyx kernel: [   19.195812] usb 4-4: device descriptor read/64, error -71
May 16 09:01:45 unyx kernel: [   19.435971] usb 4-4: new full-speed USB device number 15 using ohci-pci
May 16 09:01:45 unyx kernel: [   19.576061] usb 4-4: device descriptor read/64, error -71
May 16 09:01:46 unyx kernel: [   19.820221] usb 4-4: device descriptor read/64, error -71
May 16 09:01:46 unyx kernel: [   20.060378] usb 4-4: new full-speed USB device number 16 using ohci-pci
May 16 09:01:46 unyx kernel: [   20.085497] usb 4-4: device descriptor read/8, error -62
May 16 09:01:46 unyx kernel: [   20.209578] usb 4-4: device descriptor read/8, error -62
May 16 09:01:46 unyx kernel: [   20.448632] usb 4-4: new full-speed USB device number 17 using ohci-pci
May 16 09:01:46 unyx kernel: [   20.473750] usb 4-4: device descriptor read/8, error -62
May 16 09:01:46 unyx kernel: [   20.597831] usb 4-4: device descriptor read/8, error -62
May 16 09:01:46 unyx kernel: [   20.700825] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:01:47 unyx kernel: [   20.836891] usb 5-3: new full-speed USB device number 14 using ohci-pci
May 16 09:01:47 unyx kernel: [   20.977040] usb 5-3: device descriptor read/64, error -32
May 16 09:01:47 unyx kernel: [   21.221136] usb 5-3: device descriptor read/64, error -32
May 16 09:01:47 unyx kernel: [   21.461294] usb 5-3: new full-speed USB device number 15 using ohci-pci
May 16 09:01:47 unyx kernel: [   21.601384] usb 5-3: device descriptor read/64, error -32
May 16 09:01:48 unyx kernel: [   21.845550] usb 5-3: device descriptor read/64, error -32
May 16 09:01:48 unyx kernel: [   22.085707] usb 5-3: new full-speed USB device number 16 using ohci-pci
May 16 09:01:48 unyx kernel: [   22.493954] usb 5-3: device not accepting address 16, error -32
May 16 09:01:48 unyx kernel: [   22.630063] usb 5-3: new full-speed USB device number 17 using ohci-pci
May 16 09:01:49 unyx kernel: [   23.038310] usb 5-3: device not accepting address 17, error -32
May 16 09:01:49 unyx kernel: [   23.038403] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:01:49 unyx kernel: [   23.238459] usb 4-3: new low-speed USB device number 18 using ohci-pci
May 16 09:01:49 unyx kernel: [   23.378550] usb 4-3: device descriptor read/64, error -32
May 16 09:01:49 unyx kernel: [   23.622705] usb 4-3: device descriptor read/64, error -32
May 16 09:01:50 unyx kernel: [   23.862870] usb 4-3: new low-speed USB device number 19 using ohci-pci
May 16 09:01:50 unyx kernel: [   24.002959] usb 4-3: device descriptor read/64, error -32
May 16 09:01:50 unyx kernel: [   24.247112] usb 4-3: device descriptor read/64, error -32
May 16 09:01:50 unyx kernel: [   24.487273] usb 4-3: new low-speed USB device number 20 using ohci-pci
May 16 09:01:51 unyx kernel: [   24.895576] usb 4-3: device not accepting address 20, error -32
May 16 09:01:51 unyx kernel: [   25.031632] usb 4-3: new low-speed USB device number 21 using ohci-pci
May 16 09:01:51 unyx kernel: [   25.439878] usb 4-3: device not accepting address 21, error -32
May 16 09:01:51 unyx kernel: [   25.439985] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:01:51 unyx kernel: [   25.575986] usb 4-4: new full-speed USB device number 22 using ohci-pci
May 16 09:01:51 unyx kernel: [   25.716078] usb 4-4: device descriptor read/64, error -71
May 16 09:01:52 unyx kernel: [   25.960294] usb 4-4: device descriptor read/64, error -71
May 16 09:01:52 unyx kernel: [   26.200395] usb 4-4: new full-speed USB device number 23 using ohci-pci
May 16 09:01:52 unyx kernel: [   26.340488] usb 4-4: device descriptor read/64, error -71
May 16 09:01:52 unyx kernel: [   26.584639] usb 4-4: device descriptor read/64, error -71
May 16 09:01:53 unyx kernel: [   26.824796] usb 4-4: new full-speed USB device number 24 using ohci-pci
May 16 09:01:53 unyx kernel: [   26.849975] usb 4-4: device descriptor read/8, error -62
May 16 09:01:53 unyx kernel: [   26.974055] usb 4-4: device descriptor read/8, error -62
May 16 09:01:53 unyx kernel: [   27.213050] usb 4-4: new full-speed USB device number 25 using ohci-pci
May 16 09:01:53 unyx kernel: [   27.238228] usb 4-4: device descriptor read/8, error -62
May 16 09:01:53 unyx kernel: [   27.362310] usb 4-4: device descriptor read/8, error -62
May 16 09:01:53 unyx kernel: [   27.465243] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:01:53 unyx kernel: [   27.677351] usb 4-3: new low-speed USB device number 26 using ohci-pci
May 16 09:01:54 unyx kernel: [   27.817445] usb 4-3: device descriptor read/64, error -32
May 16 09:01:54 unyx kernel: [   28.061604] usb 4-3: device descriptor read/64, error -32
May 16 09:01:54 unyx kernel: [   28.301761] usb 4-3: new low-speed USB device number 27 using ohci-pci
May 16 09:01:54 unyx kernel: [   28.441855] usb 4-3: device descriptor read/64, error -32
May 16 09:01:54 unyx kernel: [   28.686011] usb 4-3: device descriptor read/64, error -32
May 16 09:01:55 unyx kernel: [   28.926169] usb 4-3: new low-speed USB device number 28 using ohci-pci
May 16 09:01:55 unyx kernel: [   29.334422] usb 4-3: device not accepting address 28, error -32
May 16 09:01:55 unyx kernel: [   29.470531] usb 4-3: new low-speed USB device number 29 using ohci-pci
May 16 09:01:56 unyx kernel: [   29.878775] usb 4-3: device not accepting address 29, error -32
May 16 09:01:56 unyx kernel: [   29.878881] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:01:56 unyx kernel: [   30.014881] usb 4-4: new full-speed USB device number 30 using ohci-pci
May 16 09:01:56 unyx kernel: [   30.154972] usb 4-4: device descriptor read/64, error -71
May 16 09:01:56 unyx kernel: [   30.399131] usb 4-4: device descriptor read/64, error -71
May 16 09:01:56 unyx kernel: [   30.639288] usb 4-4: new full-speed USB device number 31 using ohci-pci
May 16 09:01:56 unyx kernel: [   30.779385] usb 4-4: device descriptor read/64, error -71
May 16 09:01:57 unyx kernel: [   31.023538] usb 4-4: device descriptor read/64, error -71
May 16 09:01:57 unyx kernel: [   31.263696] usb 4-4: new full-speed USB device number 32 using ohci-pci
May 16 09:01:57 unyx kernel: [   31.288817] usb 4-4: device descriptor read/8, error -62
May 16 09:01:57 unyx kernel: [   31.412897] usb 4-4: device descriptor read/8, error -62
May 16 09:01:57 unyx kernel: [   31.651906] usb 4-4: new full-speed USB device number 33 using ohci-pci
May 16 09:01:57 unyx kernel: [   31.677041] usb 4-4: device descriptor read/8, error -62
May 16 09:01:57 unyx kernel: [   31.801151] usb 4-4: device descriptor read/8, error -62
May 16 09:01:58 unyx kernel: [   31.904182] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:01:58 unyx kernel: [   32.040210] usb 5-3: new full-speed USB device number 18 using ohci-pci
May 16 09:01:58 unyx kernel: [   32.180295] usb 5-3: device descriptor read/64, error -32
May 16 09:01:58 unyx kernel: [   32.424454] usb 5-3: device descriptor read/64, error -32
May 16 09:01:58 unyx kernel: [   32.664611] usb 5-3: new full-speed USB device number 19 using ohci-pci
May 16 09:01:58 unyx kernel: [   32.804712] usb 5-3: device descriptor read/64, error -32
May 16 09:01:59 unyx kernel: [   33.048862] usb 5-3: device descriptor read/64, error -32
May 16 09:01:59 unyx kernel: [   33.289020] usb 5-3: new full-speed USB device number 20 using ohci-pci
May 16 09:01:59 unyx kernel: [   33.697273] usb 5-3: device not accepting address 20, error -32
May 16 09:02:00 unyx kernel: [   33.833383] usb 5-3: new full-speed USB device number 21 using ohci-pci
May 16 09:02:00 unyx kernel: [   34.241628] usb 5-3: device not accepting address 21, error -32
May 16 09:02:00 unyx kernel: [   34.242474] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:00 unyx kernel: [   34.441779] usb 4-3: new low-speed USB device number 34 using ohci-pci
May 16 09:02:00 unyx kernel: [   34.581863] usb 4-3: device descriptor read/64, error -32
May 16 09:02:01 unyx kernel: [   34.826023] usb 4-3: device descriptor read/64, error -32
May 16 09:02:01 unyx kernel: [   35.066186] usb 4-3: new low-speed USB device number 35 using ohci-pci
May 16 09:02:01 unyx kernel: [   35.206271] usb 4-3: device descriptor read/64, error -32
May 16 09:02:01 unyx kernel: [   35.450430] usb 4-3: device descriptor read/64, error -32
May 16 09:02:01 unyx kernel: [   35.690588] usb 4-3: new low-speed USB device number 36 using ohci-pci
May 16 09:02:02 unyx kernel: [   36.098841] usb 4-3: device not accepting address 36, error -32
May 16 09:02:02 unyx kernel: [   36.234950] usb 4-3: new low-speed USB device number 37 using ohci-pci
May 16 09:02:02 unyx kernel: [   36.643197] usb 4-3: device not accepting address 37, error -32
May 16 09:02:02 unyx kernel: [   36.644096] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:02 unyx kernel: [   36.779305] usb 4-4: new full-speed USB device number 38 using ohci-pci
May 16 09:02:03 unyx kernel: [   36.919449] usb 4-4: device descriptor read/64, error -71
May 16 09:02:03 unyx kernel: [   37.163549] usb 4-4: device descriptor read/64, error -71
May 16 09:02:03 unyx kernel: [   37.403707] usb 4-4: new full-speed USB device number 39 using ohci-pci
May 16 09:02:03 unyx kernel: [   37.543798] usb 4-4: device descriptor read/64, error -71
May 16 09:02:03 unyx kernel: [   37.787957] usb 4-4: device descriptor read/64, error -71
May 16 09:02:04 unyx kernel: [   38.028115] usb 4-4: new full-speed USB device number 40 using ohci-pci
May 16 09:02:04 unyx kernel: [   38.053175] usb 4-4: device descriptor read/8, error -62
May 16 09:02:04 unyx kernel: [   38.177257] usb 4-4: device descriptor read/8, error -62
May 16 09:02:04 unyx kernel: [   38.416373] usb 4-4: new full-speed USB device number 41 using ohci-pci
May 16 09:02:04 unyx kernel: [   38.441429] usb 4-4: device descriptor read/8, error -62
May 16 09:02:04 unyx kernel: [   38.565509] usb 4-4: device descriptor read/8, error -62
May 16 09:02:04 unyx kernel: [   38.668546] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:05 unyx kernel: [   38.880678] usb 4-3: new low-speed USB device number 42 using ohci-pci
May 16 09:02:05 unyx kernel: [   39.020767] usb 4-3: device descriptor read/64, error -32
May 16 09:02:05 unyx kernel: [   39.264921] usb 4-3: device descriptor read/64, error -32
May 16 09:02:05 unyx kernel: [   39.505079] usb 4-3: new low-speed USB device number 43 using ohci-pci
May 16 09:02:05 unyx kernel: [   39.645170] usb 4-3: device descriptor read/64, error -32
May 16 09:02:06 unyx kernel: [   39.889329] usb 4-3: device descriptor read/64, error -32
May 16 09:02:06 unyx kernel: [   40.129487] usb 4-3: new low-speed USB device number 44 using ohci-pci
May 16 09:02:06 unyx kernel: [   40.537741] usb 4-3: device not accepting address 44, error -32
May 16 09:02:06 unyx kernel: [   40.673849] usb 4-3: new low-speed USB device number 45 using ohci-pci
May 16 09:02:07 unyx kernel: [   41.082149] usb 4-3: device not accepting address 45, error -32
May 16 09:02:07 unyx kernel: [   41.083088] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:07 unyx kernel: [   41.218205] usb 4-4: new full-speed USB device number 46 using ohci-pci
May 16 09:02:07 unyx kernel: [   41.358289] usb 4-4: device descriptor read/64, error -71
May 16 09:02:07 unyx kernel: [   41.602476] usb 4-4: device descriptor read/64, error -71
May 16 09:02:08 unyx kernel: [   41.842608] usb 4-4: new full-speed USB device number 47 using ohci-pci
May 16 09:02:08 unyx kernel: [   41.982758] usb 4-4: device descriptor read/64, error -71
May 16 09:02:08 unyx kernel: [   42.226857] usb 4-4: device descriptor read/64, error -71
May 16 09:02:08 unyx kernel: [   42.467014] usb 4-4: new full-speed USB device number 48 using ohci-pci
May 16 09:02:08 unyx kernel: [   42.492132] usb 4-4: device descriptor read/8, error -62
May 16 09:02:08 unyx kernel: [   42.616211] usb 4-4: device descriptor read/8, error -62
May 16 09:02:09 unyx kernel: [   42.855268] usb 4-4: new full-speed USB device number 49 using ohci-pci
May 16 09:02:09 unyx kernel: [   42.880384] usb 4-4: device descriptor read/8, error -62
May 16 09:02:09 unyx kernel: [   43.004466] usb 4-4: device descriptor read/8, error -62
May 16 09:02:09 unyx kernel: [   43.107463] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:09 unyx kernel: [   43.243528] usb 5-3: new full-speed USB device number 22 using ohci-pci
May 16 09:02:09 unyx kernel: [   43.383617] usb 5-3: device descriptor read/64, error -32
May 16 09:02:09 unyx kernel: [   43.627771] usb 5-3: device descriptor read/64, error -32
May 16 09:02:10 unyx kernel: [   43.867929] usb 5-3: new full-speed USB device number 23 using ohci-pci
May 16 09:02:10 unyx kernel: [   44.008037] usb 5-3: device descriptor read/64, error -32
May 16 09:02:10 unyx kernel: [   44.252179] usb 5-3: device descriptor read/64, error -32
May 16 09:02:10 unyx kernel: [   44.492337] usb 5-3: new full-speed USB device number 24 using ohci-pci
May 16 09:02:11 unyx kernel: [   44.900640] usb 5-3: device not accepting address 24, error -32
May 16 09:02:11 unyx kernel: [   45.036698] usb 5-3: new full-speed USB device number 25 using ohci-pci
May 16 09:02:11 unyx kernel: [   45.444945] usb 5-3: device not accepting address 25, error -32
May 16 09:02:11 unyx kernel: [   45.445815] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:11 unyx kernel: [   45.645096] usb 4-3: new low-speed USB device number 50 using ohci-pci
May 16 09:02:11 unyx kernel: [   45.785186] usb 4-3: device descriptor read/64, error -32
May 16 09:02:12 unyx kernel: [   46.029347] usb 4-3: device descriptor read/64, error -32
May 16 09:02:12 unyx kernel: [   46.269498] usb 4-3: new low-speed USB device number 51 using ohci-pci
May 16 09:02:12 unyx kernel: [   46.409588] usb 4-3: device descriptor read/64, error -32
May 16 09:02:12 unyx kernel: [   46.653748] usb 4-3: device descriptor read/64, error -32
May 16 09:02:13 unyx kernel: [   46.893966] usb 4-3: new low-speed USB device number 52 using ohci-pci
May 16 09:02:13 unyx kernel: [   47.302159] usb 4-3: device not accepting address 52, error -32
May 16 09:02:13 unyx kernel: [   47.438267] usb 4-3: new low-speed USB device number 53 using ohci-pci
May 16 09:02:14 unyx kernel: [   47.846513] usb 4-3: device not accepting address 53, error -32
May 16 09:02:14 unyx kernel: [   47.847368] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:14 unyx kernel: [   47.982678] usb 4-4: new full-speed USB device number 54 using ohci-pci
May 16 09:02:14 unyx kernel: [   48.122708] usb 4-4: device descriptor read/64, error -71
May 16 09:02:14 unyx kernel: [   48.366867] usb 4-4: device descriptor read/64, error -71
May 16 09:02:14 unyx kernel: [   48.607024] usb 4-4: new full-speed USB device number 55 using ohci-pci
May 16 09:02:14 unyx kernel: [   48.747115] usb 4-4: device descriptor read/64, error -71
May 16 09:02:15 unyx kernel: [   48.991275] usb 4-4: device descriptor read/64, error -71
May 16 09:02:15 unyx kernel: [   49.231433] usb 4-4: new full-speed USB device number 56 using ohci-pci
May 16 09:02:15 unyx kernel: [   49.256557] usb 4-4: device descriptor read/8, error -62
May 16 09:02:15 unyx kernel: [   49.380638] usb 4-4: device descriptor read/8, error -62
May 16 09:02:15 unyx kernel: [   49.619686] usb 4-4: new full-speed USB device number 57 using ohci-pci
May 16 09:02:15 unyx kernel: [   49.644812] usb 4-4: device descriptor read/8, error -62
May 16 09:02:15 unyx kernel: [   49.768892] usb 4-4: device descriptor read/8, error -62
May 16 09:02:16 unyx kernel: [   49.871870] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:16 unyx kernel: [   50.083994] usb 4-3: new low-speed USB device number 58 using ohci-pci
May 16 09:02:16 unyx kernel: [   50.224104] usb 4-3: device descriptor read/64, error -32
May 16 09:02:16 unyx kernel: [   50.468240] usb 4-3: device descriptor read/64, error -32
May 16 09:02:16 unyx kernel: [   50.708398] usb 4-3: new low-speed USB device number 59 using ohci-pci
May 16 09:02:17 unyx kernel: [   50.848488] usb 4-3: device descriptor read/64, error -32
May 16 09:02:17 unyx kernel: [   51.092648] usb 4-3: device descriptor read/64, error -32
May 16 09:02:17 unyx kernel: [   51.332806] usb 4-3: new low-speed USB device number 60 using ohci-pci
May 16 09:02:17 unyx kernel: [   51.741059] usb 4-3: device not accepting address 60, error -32
May 16 09:02:18 unyx kernel: [   51.877166] usb 4-3: new low-speed USB device number 61 using ohci-pci
May 16 09:02:18 unyx kernel: [   52.285415] usb 4-3: device not accepting address 61, error -32
May 16 09:02:18 unyx kernel: [   52.286234] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:18 unyx kernel: [   52.421522] usb 4-4: new full-speed USB device number 62 using ohci-pci
May 16 09:02:18 unyx kernel: [   52.561612] usb 4-4: device descriptor read/64, error -71
May 16 09:02:18 unyx kernel: [   52.805767] usb 4-4: device descriptor read/64, error -71
May 16 09:02:19 unyx kernel: [   53.045924] usb 4-4: new full-speed USB device number 63 using ohci-pci
May 16 09:02:19 unyx kernel: [   53.186015] usb 4-4: device descriptor read/64, error -71
May 16 09:02:19 unyx kernel: [   53.430174] usb 4-4: device descriptor read/64, error -71
May 16 09:02:19 unyx kernel: [   53.670332] usb 4-4: new full-speed USB device number 64 using ohci-pci
May 16 09:02:19 unyx kernel: [   53.695515] usb 4-4: device descriptor read/8, error -62
May 16 09:02:19 unyx kernel: [   53.818597] usb 4-4: device descriptor read/8, error -62
May 16 09:02:20 unyx kernel: [   54.058586] usb 4-4: new full-speed USB device number 65 using ohci-pci
May 16 09:02:20 unyx kernel: [   54.083769] usb 4-4: device descriptor read/8, error -62
May 16 09:02:20 unyx kernel: [   54.206852] usb 4-4: device descriptor read/8, error -62
May 16 09:02:20 unyx kernel: [   54.310787] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:20 unyx kernel: [   54.446845] usb 5-3: new full-speed USB device number 26 using ohci-pci
May 16 09:02:20 unyx kernel: [   54.586936] usb 5-3: device descriptor read/64, error -32
May 16 09:02:20 unyx kernel: [   54.831089] usb 5-3: device descriptor read/64, error -32
May 16 09:02:21 unyx kernel: [   55.071250] usb 5-3: new full-speed USB device number 27 using ohci-pci
May 16 09:02:21 unyx kernel: [   55.211343] usb 5-3: device descriptor read/64, error -32
May 16 09:02:21 unyx kernel: [   55.455497] usb 5-3: device descriptor read/64, error -32
May 16 09:02:21 unyx kernel: [   55.695652] usb 5-3: new full-speed USB device number 28 using ohci-pci
May 16 09:02:22 unyx kernel: [   56.103909] usb 5-3: device not accepting address 28, error -32
May 16 09:02:22 unyx kernel: [   56.240015] usb 5-3: new full-speed USB device number 29 using ohci-pci
May 16 09:02:22 unyx kernel: [   56.648228] usb 5-3: device not accepting address 29, error -32
May 16 09:02:22 unyx kernel: [   56.648802] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:23 unyx kernel: [   56.848414] usb 4-3: new low-speed USB device number 66 using ohci-pci
May 16 09:02:23 unyx kernel: [   56.988564] usb 4-3: device descriptor read/64, error -32
May 16 09:02:23 unyx kernel: [   57.232658] usb 4-3: device descriptor read/64, error -32
May 16 09:02:23 unyx kernel: [   57.472842] usb 4-3: new low-speed USB device number 67 using ohci-pci
May 16 09:02:23 unyx kernel: [   57.612912] usb 4-3: device descriptor read/64, error -32
May 16 09:02:24 unyx kernel: [   57.857066] usb 4-3: device descriptor read/64, error -32
May 16 09:02:24 unyx kernel: [   58.097224] usb 4-3: new low-speed USB device number 68 using ohci-pci
May 16 09:02:24 unyx kernel: [   58.505477] usb 4-3: device not accepting address 68, error -32
May 16 09:02:24 unyx kernel: [   58.641585] usb 4-3: new low-speed USB device number 69 using ohci-pci
May 16 09:02:25 unyx kernel: [   59.049882] usb 4-3: device not accepting address 69, error -32
May 16 09:02:25 unyx kernel: [   59.050518] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:25 unyx kernel: [   59.185940] usb 4-4: new full-speed USB device number 70 using ohci-pci
May 16 09:02:25 unyx kernel: [   59.326026] usb 4-4: device descriptor read/64, error -71
May 16 09:02:25 unyx kernel: [   59.570185] usb 4-4: device descriptor read/64, error -71
May 16 09:02:25 unyx kernel: [   59.810342] usb 4-4: new full-speed USB device number 71 using ohci-pci
May 16 09:02:26 unyx kernel: [   59.950497] usb 4-4: device descriptor read/64, error -71
May 16 09:02:26 unyx kernel: [   60.194593] usb 4-4: device descriptor read/64, error -71
May 16 09:02:26 unyx kernel: [   60.434750] usb 4-4: new full-speed USB device number 72 using ohci-pci
May 16 09:02:26 unyx kernel: [   60.459927] usb 4-4: device descriptor read/8, error -62
May 16 09:02:26 unyx kernel: [   60.584007] usb 4-4: device descriptor read/8, error -62
May 16 09:02:26 unyx kernel: [   60.823004] usb 4-4: new full-speed USB device number 73 using ohci-pci
May 16 09:02:27 unyx kernel: [   60.848180] usb 4-4: device descriptor read/8, error -62
May 16 09:02:27 unyx kernel: [   60.972278] usb 4-4: device descriptor read/8, error -62
May 16 09:02:27 unyx kernel: [   61.075203] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:27 unyx kernel: [   61.287313] usb 4-3: new low-speed USB device number 74 using ohci-pci
May 16 09:02:27 unyx kernel: [   61.427403] usb 4-3: device descriptor read/64, error -32
May 16 09:02:27 unyx kernel: [   61.671557] usb 4-3: device descriptor read/64, error -32
May 16 09:02:28 unyx kernel: [   61.911775] usb 4-3: new low-speed USB device number 75 using ohci-pci
May 16 09:02:28 unyx kernel: [   62.051806] usb 4-3: device descriptor read/64, error -32
May 16 09:02:28 unyx kernel: [   62.296038] usb 4-3: device descriptor read/64, error -32
May 16 09:02:28 unyx kernel: [   62.536129] usb 4-3: new low-speed USB device number 76 using ohci-pci
May 16 09:02:29 unyx kernel: [   62.944428] usb 4-3: device not accepting address 76, error -32
May 16 09:02:29 unyx kernel: [   63.080485] usb 4-3: new low-speed USB device number 77 using ohci-pci
May 16 09:02:29 unyx kernel: [   63.488732] usb 4-3: device not accepting address 77, error -32
May 16 09:02:29 unyx kernel: [   63.489392] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:29 unyx kernel: [   63.624851] usb 4-4: new full-speed USB device number 78 using ohci-pci
May 16 09:02:29 unyx kernel: [   63.764925] usb 4-4: device descriptor read/64, error -71
May 16 09:02:30 unyx kernel: [   64.009147] usb 4-4: device descriptor read/64, error -71
May 16 09:02:30 unyx kernel: [   64.249247] usb 4-4: new full-speed USB device number 79 using ohci-pci
May 16 09:02:30 unyx kernel: [   64.389333] usb 4-4: device descriptor read/64, error -71
May 16 09:02:30 unyx kernel: [   64.633493] usb 4-4: device descriptor read/64, error -71
May 16 09:02:31 unyx kernel: [   64.873650] usb 4-4: new full-speed USB device number 80 using ohci-pci
May 16 09:02:31 unyx kernel: [   64.898795] usb 4-4: device descriptor read/8, error -62
May 16 09:02:31 unyx kernel: [   65.022851] usb 4-4: device descriptor read/8, error -62
May 16 09:02:31 unyx kernel: [   65.261967] usb 4-4: new full-speed USB device number 81 using ohci-pci
May 16 09:02:31 unyx kernel: [   65.287023] usb 4-4: device descriptor read/8, error -62
May 16 09:02:31 unyx kernel: [   65.411104] usb 4-4: device descriptor read/8, error -62
May 16 09:02:31 unyx kernel: [   65.514134] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:33 unyx kernel: [   67.311304] usb 5-3: new full-speed USB device number 30 using ohci-pci
May 16 09:02:33 unyx kernel: [   67.451394] usb 5-3: device descriptor read/64, error -32
May 16 09:02:33 unyx kernel: [   67.695553] usb 5-3: device descriptor read/64, error -32
May 16 09:02:34 unyx kernel: [   67.935711] usb 5-3: new full-speed USB device number 31 using ohci-pci
May 16 09:02:34 unyx kernel: [   68.075801] usb 5-3: device descriptor read/64, error -32
May 16 09:02:34 unyx kernel: [   68.319961] usb 5-3: device descriptor read/64, error -32
May 16 09:02:34 unyx kernel: [   68.560138] usb 5-3: new full-speed USB device number 32 using ohci-pci
May 16 09:02:35 unyx kernel: [   68.968309] usb 5-3: device not accepting address 32, error -32
May 16 09:02:35 unyx kernel: [   69.104477] usb 5-3: new full-speed USB device number 33 using ohci-pci
May 16 09:02:35 unyx kernel: [   69.512718] usb 5-3: device not accepting address 33, error -32
May 16 09:02:35 unyx kernel: [   69.514225] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:35 unyx kernel: [   69.724880] usb 5-3: new full-speed USB device number 34 using ohci-pci
May 16 09:02:36 unyx kernel: [   69.864971] usb 5-3: device descriptor read/64, error -32
May 16 09:02:36 unyx kernel: [   70.109130] usb 5-3: device descriptor read/64, error -32
May 16 09:02:36 unyx kernel: [   70.349287] usb 5-3: new full-speed USB device number 35 using ohci-pci
May 16 09:02:36 unyx kernel: [   70.489377] usb 5-3: device descriptor read/64, error -32
May 16 09:02:36 unyx kernel: [   70.733540] usb 5-3: device descriptor read/64, error -32
May 16 09:02:37 unyx kernel: [   70.973697] usb 5-3: new full-speed USB device number 36 using ohci-pci
May 16 09:02:37 unyx kernel: [   71.381938] usb 5-3: device not accepting address 36, error -32
May 16 09:02:37 unyx kernel: [   71.518050] usb 5-3: new full-speed USB device number 37 using ohci-pci
May 16 09:02:38 unyx kernel: [   71.926296] usb 5-3: device not accepting address 37, error -32
May 16 09:02:38 unyx kernel: [   71.927791] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:38 unyx kernel: [   72.126448] usb 4-3: new low-speed USB device number 82 using ohci-pci
May 16 09:02:38 unyx kernel: [   72.266539] usb 4-3: device descriptor read/64, error -32
May 16 09:02:38 unyx kernel: [   72.510699] usb 4-3: device descriptor read/64, error -32
May 16 09:02:38 unyx kernel: [   72.750856] usb 4-3: new low-speed USB device number 83 using ohci-pci
May 16 09:02:39 unyx kernel: [   72.890947] usb 4-3: device descriptor read/64, error -32
May 16 09:02:39 unyx kernel: [   73.135130] usb 4-3: device descriptor read/64, error -32
May 16 09:02:39 unyx kernel: [   73.375264] usb 4-3: new low-speed USB device number 84 using ohci-pci
May 16 09:02:39 unyx kernel: [   73.783508] usb 4-3: device not accepting address 84, error -32
May 16 09:02:40 unyx kernel: [   73.919621] usb 4-3: new low-speed USB device number 85 using ohci-pci
May 16 09:02:40 unyx kernel: [   74.327863] usb 4-3: device not accepting address 85, error -32
May 16 09:02:40 unyx kernel: [   74.329371] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:40 unyx kernel: [   74.463977] usb 4-4: new full-speed USB device number 86 using ohci-pci
May 16 09:02:40 unyx kernel: [   74.604066] usb 4-4: device descriptor read/64, error -71
May 16 09:02:41 unyx kernel: [   74.848225] usb 4-4: device descriptor read/64, error -71
May 16 09:02:41 unyx kernel: [   75.088383] usb 4-4: new full-speed USB device number 87 using ohci-pci
May 16 09:02:41 unyx kernel: [   75.228473] usb 4-4: device descriptor read/64, error -71
May 16 09:02:41 unyx kernel: [   75.472632] usb 4-4: device descriptor read/64, error -71
May 16 09:02:41 unyx kernel: [   75.712791] usb 4-4: new full-speed USB device number 88 using ohci-pci
May 16 09:02:41 unyx kernel: [   75.737909] usb 4-4: device descriptor read/8, error -62
May 16 09:02:42 unyx kernel: [   75.861991] usb 4-4: device descriptor read/8, error -62
May 16 09:02:42 unyx kernel: [   76.101046] usb 4-4: new full-speed USB device number 89 using ohci-pci
May 16 09:02:42 unyx kernel: [   76.126163] usb 4-4: device descriptor read/8, error -62
May 16 09:02:42 unyx kernel: [   76.250243] usb 4-4: device descriptor read/8, error -62
May 16 09:02:42 unyx kernel: [   76.353215] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:42 unyx kernel: [   76.565348] usb 4-3: new low-speed USB device number 90 using ohci-pci
May 16 09:02:42 unyx kernel: [   76.705444] usb 4-3: device descriptor read/64, error -32
May 16 09:02:43 unyx kernel: [   76.949598] usb 4-3: device descriptor read/64, error -32
May 16 09:02:43 unyx kernel: [   77.189756] usb 4-3: new low-speed USB device number 91 using ohci-pci
May 16 09:02:43 unyx kernel: [   77.329846] usb 4-3: device descriptor read/64, error -32
May 16 09:02:43 unyx kernel: [   77.574005] usb 4-3: device descriptor read/64, error -32
May 16 09:02:43 unyx kernel: [   77.814164] usb 4-3: new low-speed USB device number 92 using ohci-pci
May 16 09:02:44 unyx kernel: [   78.222407] usb 4-3: device not accepting address 92, error -32
May 16 09:02:44 unyx kernel: [   78.358521] usb 4-3: new low-speed USB device number 93 using ohci-pci
May 16 09:02:44 unyx kernel: [   78.766763] usb 4-3: device not accepting address 93, error -32
May 16 09:02:44 unyx kernel: [   78.768269] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:45 unyx kernel: [   78.902877] usb 4-4: new full-speed USB device number 94 using ohci-pci
May 16 09:02:45 unyx kernel: [   79.042965] usb 4-4: device descriptor read/64, error -71
May 16 09:02:45 unyx kernel: [   79.287134] usb 4-4: device descriptor read/64, error -71
May 16 09:02:45 unyx kernel: [   79.527281] usb 4-4: new full-speed USB device number 95 using ohci-pci
May 16 09:02:45 unyx kernel: [   79.667375] usb 4-4: device descriptor read/64, error -71
May 16 09:02:46 unyx kernel: [   79.911532] usb 4-4: device descriptor read/64, error -71
May 16 09:02:46 unyx kernel: [   80.151691] usb 4-4: new full-speed USB device number 96 using ohci-pci
May 16 09:02:46 unyx kernel: [   80.176802] usb 4-4: device descriptor read/8, error -62
May 16 09:02:46 unyx kernel: [   80.300882] usb 4-4: device descriptor read/8, error -62
May 16 09:02:46 unyx kernel: [   80.539946] usb 4-4: new full-speed USB device number 97 using ohci-pci
May 16 09:02:46 unyx kernel: [   80.565054] usb 4-4: device descriptor read/8, error -62
May 16 09:02:46 unyx kernel: [   80.689136] usb 4-4: device descriptor read/8, error -62
May 16 09:02:46 unyx kernel: [   80.792113] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:47 unyx kernel: [   81.584625] usb 5-3: new full-speed USB device number 38 using ohci-pci
May 16 09:02:47 unyx kernel: [   81.724717] usb 5-3: device descriptor read/64, error -32
May 16 09:02:48 unyx kernel: [   81.968902] usb 5-3: device descriptor read/64, error -32
May 16 09:02:48 unyx kernel: [   82.209035] usb 5-3: new full-speed USB device number 39 using ohci-pci
May 16 09:02:48 unyx kernel: [   82.349124] usb 5-3: device descriptor read/64, error -32
May 16 09:02:48 unyx kernel: [   82.593284] usb 5-3: device descriptor read/64, error -32
May 16 09:02:48 unyx kernel: [   82.833442] usb 5-3: new full-speed USB device number 40 using ohci-pci
May 16 09:02:49 unyx kernel: [   83.241699] usb 5-3: device not accepting address 40, error -32
May 16 09:02:49 unyx kernel: [   83.377803] usb 5-3: new full-speed USB device number 41 using ohci-pci
May 16 09:02:49 unyx kernel: [   83.786042] usb 5-3: device not accepting address 41, error -32
May 16 09:02:49 unyx kernel: [   83.787535] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:50 unyx kernel: [   83.998203] usb 5-3: new full-speed USB device number 42 using ohci-pci
May 16 09:02:50 unyx kernel: [   84.138294] usb 5-3: device descriptor read/64, error -32
May 16 09:02:50 unyx kernel: [   84.382456] usb 5-3: device descriptor read/64, error -32
May 16 09:02:50 unyx kernel: [   84.622610] usb 5-3: new full-speed USB device number 43 using ohci-pci
May 16 09:02:50 unyx kernel: [   84.762701] usb 5-3: device descriptor read/64, error -32
May 16 09:02:51 unyx kernel: [   85.006861] usb 5-3: device descriptor read/64, error -32
May 16 09:02:51 unyx kernel: [   85.247018] usb 5-3: new full-speed USB device number 44 using ohci-pci
May 16 09:02:51 unyx kernel: [   85.655262] usb 5-3: device not accepting address 44, error -32
May 16 09:02:51 unyx kernel: [   85.791375] usb 5-3: new full-speed USB device number 45 using ohci-pci
May 16 09:02:52 unyx kernel: [   86.199618] usb 5-3: device not accepting address 45, error -32
May 16 09:02:52 unyx kernel: [   86.201128] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:52 unyx kernel: [   86.399774] usb 4-3: new low-speed USB device number 98 using ohci-pci
May 16 09:02:52 unyx kernel: [   86.539862] usb 4-3: device descriptor read/64, error -32
May 16 09:02:52 unyx kernel: [   86.784021] usb 4-3: device descriptor read/64, error -32
May 16 09:02:53 unyx kernel: [   87.024179] usb 4-3: new low-speed USB device number 99 using ohci-pci
May 16 09:02:53 unyx kernel: [   87.164270] usb 4-3: device descriptor read/64, error -32
May 16 09:02:53 unyx kernel: [   87.408430] usb 4-3: device descriptor read/64, error -32
May 16 09:02:53 unyx kernel: [   87.648587] usb 4-3: new low-speed USB device number 100 using ohci-pci
May 16 09:02:54 unyx kernel: [   88.056791] usb 4-3: device not accepting address 100, error -32
May 16 09:02:54 unyx kernel: [   88.192949] usb 4-3: new low-speed USB device number 101 using ohci-pci
May 16 09:02:54 unyx kernel: [   88.601188] usb 4-3: device not accepting address 101, error -32
May 16 09:02:54 unyx kernel: [   88.602698] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:54 unyx kernel: [   88.737299] usb 4-4: new full-speed USB device number 102 using ohci-pci
May 16 09:02:55 unyx kernel: [   88.877389] usb 4-4: device descriptor read/64, error -71
May 16 09:02:55 unyx kernel: [   89.121549] usb 4-4: device descriptor read/64, error -71
May 16 09:02:55 unyx kernel: [   89.361706] usb 4-4: new full-speed USB device number 103 using ohci-pci
May 16 09:02:55 unyx kernel: [   89.501796] usb 4-4: device descriptor read/64, error -71
May 16 09:02:55 unyx kernel: [   89.745956] usb 4-4: device descriptor read/64, error -71
May 16 09:02:56 unyx kernel: [   89.986115] usb 4-4: new full-speed USB device number 104 using ohci-pci
May 16 09:02:56 unyx kernel: [   90.011229] usb 4-4: device descriptor read/8, error -62
May 16 09:02:56 unyx kernel: [   90.135309] usb 4-4: device descriptor read/8, error -62
May 16 09:02:56 unyx kernel: [   90.374373] usb 4-4: new full-speed USB device number 105 using ohci-pci
May 16 09:02:56 unyx kernel: [   90.399481] usb 4-4: device descriptor read/8, error -62
May 16 09:02:56 unyx kernel: [   90.523563] usb 4-4: device descriptor read/8, error -62
May 16 09:02:56 unyx kernel: [   90.626537] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:02:56 unyx kernel: [   90.838671] usb 4-3: new low-speed USB device number 106 using ohci-pci
May 16 09:02:57 unyx kernel: [   90.978765] usb 4-3: device descriptor read/64, error -32
May 16 09:02:57 unyx kernel: [   91.222921] usb 4-3: device descriptor read/64, error -32
May 16 09:02:57 unyx kernel: [   91.463080] usb 4-3: new low-speed USB device number 107 using ohci-pci
May 16 09:02:57 unyx kernel: [   91.603169] usb 4-3: device descriptor read/64, error -32
May 16 09:02:57 unyx kernel: [   91.847329] usb 4-3: device descriptor read/64, error -32
May 16 09:02:58 unyx kernel: [   92.087487] usb 4-3: new low-speed USB device number 108 using ohci-pci
May 16 09:02:58 unyx kernel: [   92.495731] usb 4-3: device not accepting address 108, error -32
May 16 09:02:58 unyx kernel: [   92.631844] usb 4-3: new low-speed USB device number 109 using ohci-pci
May 16 09:02:59 unyx kernel: [   93.040087] usb 4-3: device not accepting address 109, error -32
May 16 09:02:59 unyx kernel: [   93.041622] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:02:59 unyx kernel: [   93.176200] usb 4-4: new full-speed USB device number 110 using ohci-pci
May 16 09:02:59 unyx kernel: [   93.316292] usb 4-4: device descriptor read/64, error -71
May 16 09:02:59 unyx kernel: [   93.560448] usb 4-4: device descriptor read/64, error -71
May 16 09:02:59 unyx kernel: [   93.800606] usb 4-4: new full-speed USB device number 111 using ohci-pci
May 16 09:03:00 unyx kernel: [   93.940683] usb 4-4: device descriptor read/64, error -71
May 16 09:03:00 unyx kernel: [   94.184856] usb 4-4: device descriptor read/64, error -71
May 16 09:03:00 unyx kernel: [   94.425014] usb 4-4: new full-speed USB device number 112 using ohci-pci
May 16 09:03:00 unyx kernel: [   94.450124] usb 4-4: device descriptor read/8, error -62
May 16 09:03:00 unyx kernel: [   94.574205] usb 4-4: device descriptor read/8, error -62
May 16 09:03:00 unyx kernel: [   94.813267] usb 4-4: new full-speed USB device number 113 using ohci-pci
May 16 09:03:00 unyx kernel: [   94.838379] usb 4-4: device descriptor read/8, error -62
May 16 09:03:01 unyx kernel: [   94.962459] usb 4-4: device descriptor read/8, error -62
May 16 09:03:01 unyx kernel: [   95.065437] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:03:01 unyx kernel: [   95.829931] usb 5-3: new full-speed USB device number 46 using ohci-pci
May 16 09:03:02 unyx kernel: [   95.970022] usb 5-3: device descriptor read/64, error -32
May 16 09:03:02 unyx kernel: [   96.214182] usb 5-3: device descriptor read/64, error -32
May 16 09:03:02 unyx kernel: [   96.454339] usb 5-3: new full-speed USB device number 47 using ohci-pci
May 16 09:03:02 unyx kernel: [   96.594429] usb 5-3: device descriptor read/64, error -32
May 16 09:03:02 unyx kernel: [   96.838589] usb 5-3: device descriptor read/64, error -32
May 16 09:03:03 unyx kernel: [   97.078747] usb 5-3: new full-speed USB device number 48 using ohci-pci
May 16 09:03:03 unyx kernel: [   97.486990] usb 5-3: device not accepting address 48, error -32
May 16 09:03:03 unyx kernel: [   97.623105] usb 5-3: new full-speed USB device number 49 using ohci-pci
May 16 09:03:04 unyx kernel: [   98.031348] usb 5-3: device not accepting address 49, error -32
May 16 09:03:04 unyx kernel: [   98.032864] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:04 unyx kernel: [   98.243508] usb 5-3: new full-speed USB device number 50 using ohci-pci
May 16 09:03:04 unyx kernel: [   98.383611] usb 5-3: device descriptor read/64, error -32
May 16 09:03:04 unyx kernel: [   98.627758] usb 5-3: device descriptor read/64, error -32
May 16 09:03:05 unyx kernel: [   98.867916] usb 5-3: new full-speed USB device number 51 using ohci-pci
May 16 09:03:05 unyx kernel: [   99.008007] usb 5-3: device descriptor read/64, error -32
May 16 09:03:05 unyx kernel: [   99.252166] usb 5-3: device descriptor read/64, error -32
May 16 09:03:05 unyx kernel: [   99.492324] usb 5-3: new full-speed USB device number 52 using ohci-pci
May 16 09:03:06 unyx kernel: [   99.900566] usb 5-3: device not accepting address 52, error -32
May 16 09:03:06 unyx kernel: [  100.036679] usb 5-3: new full-speed USB device number 53 using ohci-pci
May 16 09:03:06 unyx kernel: [  100.444923] usb 5-3: device not accepting address 53, error -32
May 16 09:03:06 unyx kernel: [  100.446431] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:06 unyx kernel: [  100.581034] usb 4-3: new low-speed USB device number 114 using ohci-pci
May 16 09:03:06 unyx kernel: [  100.721128] usb 4-3: device descriptor read/64, error -32
May 16 09:03:07 unyx kernel: [  100.965285] usb 4-3: device descriptor read/64, error -32
May 16 09:03:07 unyx kernel: [  101.205443] usb 4-3: new low-speed USB device number 115 using ohci-pci
May 16 09:03:07 unyx kernel: [  101.345532] usb 4-3: device descriptor read/64, error -32
May 16 09:03:07 unyx kernel: [  101.589693] usb 4-3: device descriptor read/64, error -32
May 16 09:03:07 unyx kernel: [  101.829851] usb 4-3: new low-speed USB device number 116 using ohci-pci
May 16 09:03:08 unyx kernel: [  102.238094] usb 4-3: device not accepting address 116, error -32
May 16 09:03:08 unyx kernel: [  102.374205] usb 4-3: new low-speed USB device number 117 using ohci-pci
May 16 09:03:08 unyx kernel: [  102.782450] usb 4-3: device not accepting address 117, error -32
May 16 09:03:08 unyx kernel: [  102.783954] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:09 unyx kernel: [  102.918563] usb 4-4: new full-speed USB device number 118 using ohci-pci
May 16 09:03:09 unyx kernel: [  103.058652] usb 4-4: device descriptor read/64, error -71
May 16 09:03:09 unyx kernel: [  103.302811] usb 4-4: device descriptor read/64, error -71
May 16 09:03:09 unyx kernel: [  103.542970] usb 4-4: new full-speed USB device number 119 using ohci-pci
May 16 09:03:09 unyx kernel: [  103.683060] usb 4-4: device descriptor read/64, error -71
May 16 09:03:10 unyx kernel: [  103.927219] usb 4-4: device descriptor read/64, error -71
May 16 09:03:10 unyx kernel: [  104.167377] usb 4-4: new full-speed USB device number 120 using ohci-pci
May 16 09:03:10 unyx kernel: [  104.192488] usb 4-4: device descriptor read/8, error -62
May 16 09:03:10 unyx kernel: [  104.316567] usb 4-4: device descriptor read/8, error -62
May 16 09:03:10 unyx kernel: [  104.555631] usb 4-4: new full-speed USB device number 121 using ohci-pci
May 16 09:03:10 unyx kernel: [  104.580741] usb 4-4: device descriptor read/8, error -62
May 16 09:03:10 unyx kernel: [  104.704821] usb 4-4: device descriptor read/8, error -62
May 16 09:03:10 unyx kernel: [  104.807814] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:03:11 unyx kernel: [  104.943887] usb 5-3: new full-speed USB device number 54 using ohci-pci
May 16 09:03:11 unyx kernel: [  105.083975] usb 5-3: device descriptor read/64, error -32
May 16 09:03:11 unyx kernel: [  105.328135] usb 5-3: device descriptor read/64, error -32
May 16 09:03:11 unyx kernel: [  105.568227] usb 5-3: new full-speed USB device number 55 using ohci-pci
May 16 09:03:11 unyx kernel: [  105.708383] usb 5-3: device descriptor read/64, error -32
May 16 09:03:12 unyx kernel: [  105.952542] usb 5-3: device descriptor read/64, error -32
May 16 09:03:12 unyx kernel: [  106.192700] usb 5-3: new full-speed USB device number 56 using ohci-pci
May 16 09:03:12 unyx kernel: [  106.600944] usb 5-3: device not accepting address 56, error -32
May 16 09:03:12 unyx kernel: [  106.737057] usb 5-3: new full-speed USB device number 57 using ohci-pci
May 16 09:03:13 unyx kernel: [  107.145300] usb 5-3: device not accepting address 57, error -32
May 16 09:03:13 unyx kernel: [  107.146805] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:13 unyx kernel: [  107.345454] usb 4-3: new low-speed USB device number 122 using ohci-pci
May 16 09:03:13 unyx kernel: [  107.485544] usb 4-3: device descriptor read/64, error -32
May 16 09:03:13 unyx kernel: [  107.729704] usb 4-3: device descriptor read/64, error -32
May 16 09:03:14 unyx kernel: [  107.969861] usb 4-3: new low-speed USB device number 123 using ohci-pci
May 16 09:03:14 unyx kernel: [  108.109952] usb 4-3: device descriptor read/64, error -32
May 16 09:03:14 unyx kernel: [  108.354111] usb 4-3: device descriptor read/64, error -32
May 16 09:03:14 unyx kernel: [  108.594269] usb 4-3: new low-speed USB device number 124 using ohci-pci
May 16 09:03:15 unyx kernel: [  109.002514] usb 4-3: device not accepting address 124, error -32
May 16 09:03:15 unyx kernel: [  109.138627] usb 4-3: new low-speed USB device number 125 using ohci-pci
May 16 09:03:15 unyx kernel: [  109.546867] usb 4-3: device not accepting address 125, error -32
May 16 09:03:15 unyx kernel: [  109.548402] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:15 unyx kernel: [  109.682979] usb 4-4: new full-speed USB device number 126 using ohci-pci
May 16 09:03:15 unyx kernel: [  109.823071] usb 4-4: device descriptor read/64, error -71
May 16 09:03:16 unyx kernel: [  110.067231] usb 4-4: device descriptor read/64, error -71
May 16 09:03:16 unyx kernel: [  110.307388] usb 4-4: new full-speed USB device number 127 using ohci-pci
May 16 09:03:16 unyx kernel: [  110.447478] usb 4-4: device descriptor read/64, error -71
May 16 09:03:16 unyx kernel: [  110.691638] usb 4-4: device descriptor read/64, error -71
May 16 09:03:17 unyx kernel: [  110.931795] usb 4-4: new full-speed USB device number 2 using ohci-pci
May 16 09:03:17 unyx kernel: [  110.956909] usb 4-4: device descriptor read/8, error -62
May 16 09:03:17 unyx kernel: [  111.080990] usb 4-4: device descriptor read/8, error -62
May 16 09:03:17 unyx kernel: [  111.320051] usb 4-4: new full-speed USB device number 3 using ohci-pci
May 16 09:03:17 unyx kernel: [  111.345164] usb 4-4: device descriptor read/8, error -62
May 16 09:03:17 unyx kernel: [  111.469243] usb 4-4: device descriptor read/8, error -62
May 16 09:03:17 unyx kernel: [  111.572220] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:03:17 unyx kernel: [  111.784352] usb 4-3: new low-speed USB device number 4 using ohci-pci
May 16 09:03:18 unyx kernel: [  111.924444] usb 4-3: device descriptor read/64, error -32
May 16 09:03:18 unyx kernel: [  112.168603] usb 4-3: device descriptor read/64, error -32
May 16 09:03:18 unyx kernel: [  112.408760] usb 4-3: new low-speed USB device number 5 using ohci-pci
May 16 09:03:18 unyx kernel: [  112.548851] usb 4-3: device descriptor read/64, error -32
May 16 09:03:18 unyx kernel: [  112.793010] usb 4-3: device descriptor read/64, error -32
May 16 09:03:19 unyx kernel: [  113.033192] usb 4-3: new low-speed USB device number 6 using ohci-pci
May 16 09:03:19 unyx kernel: [  113.441412] usb 4-3: device not accepting address 6, error -32
May 16 09:03:19 unyx kernel: [  113.577525] usb 4-3: new low-speed USB device number 7 using ohci-pci
May 16 09:03:20 unyx kernel: [  113.985769] usb 4-3: device not accepting address 7, error -32
May 16 09:03:20 unyx kernel: [  113.987296] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:20 unyx kernel: [  114.121879] usb 4-4: new full-speed USB device number 8 using ohci-pci
May 16 09:03:20 unyx kernel: [  114.261970] usb 4-4: device descriptor read/64, error -71
May 16 09:03:20 unyx kernel: [  114.506129] usb 4-4: device descriptor read/64, error -71
May 16 09:03:20 unyx kernel: [  114.746286] usb 4-4: new full-speed USB device number 9 using ohci-pci
May 16 09:03:21 unyx kernel: [  114.886378] usb 4-4: device descriptor read/64, error -71
May 16 09:03:21 unyx kernel: [  115.130543] usb 4-4: device descriptor read/64, error -71
May 16 09:03:21 unyx kernel: [  115.370696] usb 4-4: new full-speed USB device number 10 using ohci-pci
May 16 09:03:21 unyx kernel: [  115.395809] usb 4-4: device descriptor read/8, error -62
May 16 09:03:21 unyx kernel: [  115.519887] usb 4-4: device descriptor read/8, error -62
May 16 09:03:21 unyx kernel: [  115.758949] usb 4-4: new full-speed USB device number 11 using ohci-pci
May 16 09:03:21 unyx kernel: [  115.784062] usb 4-4: device descriptor read/8, error -62
May 16 09:03:22 unyx kernel: [  115.908141] usb 4-4: device descriptor read/8, error -62
May 16 09:03:22 unyx kernel: [  116.011120] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:03:22 unyx kernel: [  116.799629] usb 5-3: new full-speed USB device number 58 using ohci-pci
May 16 09:03:23 unyx kernel: [  116.939720] usb 5-3: device descriptor read/64, error -32
May 16 09:03:23 unyx kernel: [  117.183884] usb 5-3: device descriptor read/64, error -32
May 16 09:03:23 unyx kernel: [  117.424037] usb 5-3: new full-speed USB device number 59 using ohci-pci
May 16 09:03:23 unyx kernel: [  117.564127] usb 5-3: device descriptor read/64, error -32
May 16 09:03:23 unyx kernel: [  117.808286] usb 5-3: device descriptor read/64, error -32
May 16 09:03:24 unyx kernel: [  118.048445] usb 5-3: new full-speed USB device number 60 using ohci-pci
May 16 09:03:24 unyx kernel: [  118.456689] usb 5-3: device not accepting address 60, error -32
May 16 09:03:24 unyx kernel: [  118.592799] usb 5-3: new full-speed USB device number 61 using ohci-pci
May 16 09:03:25 unyx kernel: [  119.001045] usb 5-3: device not accepting address 61, error -32
May 16 09:03:25 unyx kernel: [  119.002556] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:25 unyx kernel: [  119.213205] usb 5-3: new full-speed USB device number 62 using ohci-pci
May 16 09:03:25 unyx kernel: [  119.353296] usb 5-3: device descriptor read/64, error -32
May 16 09:03:25 unyx kernel: [  119.597455] usb 5-3: device descriptor read/64, error -32
May 16 09:03:25 unyx kernel: [  119.837613] usb 5-3: new full-speed USB device number 63 using ohci-pci
May 16 09:03:26 unyx kernel: [  119.977703] usb 5-3: device descriptor read/64, error -32
May 16 09:03:26 unyx kernel: [  120.221887] usb 5-3: device descriptor read/64, error -32
May 16 09:03:26 unyx kernel: [  120.462020] usb 5-3: new full-speed USB device number 64 using ohci-pci
May 16 09:03:26 unyx kernel: [  120.870264] usb 5-3: device not accepting address 64, error -32
May 16 09:03:27 unyx kernel: [  121.006378] usb 5-3: new full-speed USB device number 65 using ohci-pci
May 16 09:03:27 unyx kernel: [  121.414620] usb 5-3: device not accepting address 65, error -32
May 16 09:03:27 unyx kernel: [  121.416129] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:27 unyx kernel: [  121.614720] usb 4-3: new low-speed USB device number 12 using ohci-pci
May 16 09:03:27 unyx kernel: [  121.754864] usb 4-3: device descriptor read/64, error -32
May 16 09:03:28 unyx kernel: [  121.999022] usb 4-3: device descriptor read/64, error -32
May 16 09:03:28 unyx kernel: [  122.239182] usb 4-3: new low-speed USB device number 13 using ohci-pci
May 16 09:03:28 unyx kernel: [  122.379272] usb 4-3: device descriptor read/64, error -32
May 16 09:03:28 unyx kernel: [  122.623431] usb 4-3: device descriptor read/64, error -32
May 16 09:03:28 unyx kernel: [  122.863589] usb 4-3: new low-speed USB device number 14 using ohci-pci
May 16 09:03:29 unyx kernel: [  123.271833] usb 4-3: device not accepting address 14, error -32
May 16 09:03:29 unyx kernel: [  123.407947] usb 4-3: new low-speed USB device number 15 using ohci-pci
May 16 09:03:29 unyx kernel: [  123.816213] usb 4-3: device not accepting address 15, error -32
May 16 09:03:29 unyx kernel: [  123.817720] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:30 unyx kernel: [  123.952302] usb 4-4: new full-speed USB device number 16 using ohci-pci
May 16 09:03:30 unyx kernel: [  124.092391] usb 4-4: device descriptor read/64, error -71
May 16 09:03:30 unyx kernel: [  124.336556] usb 4-4: device descriptor read/64, error -71
May 16 09:03:30 unyx kernel: [  124.576718] usb 4-4: new full-speed USB device number 17 using ohci-pci
May 16 09:03:30 unyx kernel: [  124.716799] usb 4-4: device descriptor read/64, error -71
May 16 09:03:31 unyx kernel: [  124.960959] usb 4-4: device descriptor read/64, error -71
May 16 09:03:31 unyx kernel: [  125.201118] usb 4-4: new full-speed USB device number 18 using ohci-pci
May 16 09:03:31 unyx kernel: [  125.226227] usb 4-4: device descriptor read/8, error -62
May 16 09:03:31 unyx kernel: [  125.350309] usb 4-4: device descriptor read/8, error -62
May 16 09:03:31 unyx kernel: [  125.589369] usb 4-4: new full-speed USB device number 19 using ohci-pci
May 16 09:03:31 unyx kernel: [  125.614480] usb 4-4: device descriptor read/8, error -62
May 16 09:03:31 unyx kernel: [  125.738562] usb 4-4: device descriptor read/8, error -62
May 16 09:03:31 unyx kernel: [  125.841539] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:03:32 unyx kernel: [  126.053674] usb 4-3: new low-speed USB device number 20 using ohci-pci
May 16 09:03:32 unyx kernel: [  126.193763] usb 4-3: device descriptor read/64, error -32
May 16 09:03:32 unyx kernel: [  126.437923] usb 4-3: device descriptor read/64, error -32
May 16 09:03:32 unyx kernel: [  126.678085] usb 4-3: new low-speed USB device number 21 using ohci-pci
May 16 09:03:32 unyx kernel: [  126.818174] usb 4-3: device descriptor read/64, error -32
May 16 09:03:33 unyx kernel: [  127.062332] usb 4-3: device descriptor read/64, error -32
May 16 09:03:33 unyx kernel: [  127.302491] usb 4-3: new low-speed USB device number 22 using ohci-pci
May 16 09:03:33 unyx kernel: [  127.710733] usb 4-3: device not accepting address 22, error -32
May 16 09:03:33 unyx kernel: [  127.846845] usb 4-3: new low-speed USB device number 23 using ohci-pci
May 16 09:03:34 unyx kernel: [  128.255089] usb 4-3: device not accepting address 23, error -32
May 16 09:03:34 unyx kernel: [  128.256596] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:34 unyx kernel: [  128.391228] usb 4-4: new full-speed USB device number 24 using ohci-pci
May 16 09:03:34 unyx kernel: [  128.531291] usb 4-4: device descriptor read/64, error -71
May 16 09:03:34 unyx kernel: [  128.775451] usb 4-4: device descriptor read/64, error -71
May 16 09:03:35 unyx kernel: [  129.015608] usb 4-4: new full-speed USB device number 25 using ohci-pci
May 16 09:03:35 unyx kernel: [  129.155699] usb 4-4: device descriptor read/64, error -71
May 16 09:03:35 unyx kernel: [  129.399859] usb 4-4: device descriptor read/64, error -71
May 16 09:03:35 unyx kernel: [  129.640016] usb 4-4: new full-speed USB device number 26 using ohci-pci
May 16 09:03:35 unyx kernel: [  129.665132] usb 4-4: device descriptor read/8, error -62
May 16 09:03:35 unyx kernel: [  129.789214] usb 4-4: device descriptor read/8, error -62
May 16 09:03:36 unyx kernel: [  130.028265] usb 4-4: new full-speed USB device number 27 using ohci-pci
May 16 09:03:36 unyx kernel: [  130.053385] usb 4-4: device descriptor read/8, error -62
May 16 09:03:36 unyx kernel: [  130.177466] usb 4-4: device descriptor read/8, error -62
May 16 09:03:36 unyx kernel: [  130.280440] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:03:37 unyx kernel: [  131.068949] usb 5-3: new full-speed USB device number 66 using ohci-pci
May 16 09:03:37 unyx kernel: [  131.209040] usb 5-3: device descriptor read/64, error -32
May 16 09:03:37 unyx kernel: [  131.453200] usb 5-3: device descriptor read/64, error -32
May 16 09:03:37 unyx kernel: [  131.693357] usb 5-3: new full-speed USB device number 67 using ohci-pci
May 16 09:03:37 unyx kernel: [  131.833447] usb 5-3: device descriptor read/64, error -32
May 16 09:03:38 unyx kernel: [  132.077607] usb 5-3: device descriptor read/64, error -32
May 16 09:03:38 unyx kernel: [  132.317764] usb 5-3: new full-speed USB device number 68 using ohci-pci
May 16 09:03:38 unyx kernel: [  132.726008] usb 5-3: device not accepting address 68, error -32
May 16 09:03:38 unyx kernel: [  132.862122] usb 5-3: new full-speed USB device number 69 using ohci-pci
May 16 09:03:39 unyx kernel: [  133.270363] usb 5-3: device not accepting address 69, error -32
May 16 09:03:39 unyx kernel: [  133.271879] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:39 unyx kernel: [  133.482526] usb 5-3: new full-speed USB device number 70 using ohci-pci
May 16 09:03:39 unyx kernel: [  133.622617] usb 5-3: device descriptor read/64, error -32
May 16 09:03:39 unyx kernel: [  133.866779] usb 5-3: device descriptor read/64, error -32
May 16 09:03:40 unyx kernel: [  134.106933] usb 5-3: new full-speed USB device number 71 using ohci-pci
May 16 09:03:40 unyx kernel: [  134.247025] usb 5-3: device descriptor read/64, error -32
May 16 09:03:40 unyx kernel: [  134.491185] usb 5-3: device descriptor read/64, error -32
May 16 09:03:40 unyx kernel: [  134.731342] usb 5-3: new full-speed USB device number 72 using ohci-pci
May 16 09:03:41 unyx kernel: [  135.139584] usb 5-3: device not accepting address 72, error -32
May 16 09:03:41 unyx kernel: [  135.275699] usb 5-3: new full-speed USB device number 73 using ohci-pci
May 16 09:03:41 unyx kernel: [  135.683942] usb 5-3: device not accepting address 73, error -32
May 16 09:03:41 unyx kernel: [  135.685448] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:41 unyx kernel: [  135.884116] usb 4-3: new low-speed USB device number 28 using ohci-pci
May 16 09:03:42 unyx kernel: [  136.024185] usb 4-3: device descriptor read/64, error -32
May 16 09:03:42 unyx kernel: [  136.268344] usb 4-3: device descriptor read/64, error -32
May 16 09:03:42 unyx kernel: [  136.508506] usb 4-3: new low-speed USB device number 29 using ohci-pci
May 16 09:03:42 unyx kernel: [  136.648593] usb 4-3: device descriptor read/64, error -32
May 16 09:03:43 unyx kernel: [  136.892753] usb 4-3: device descriptor read/64, error -32
May 16 09:03:43 unyx kernel: [  137.132912] usb 4-3: new low-speed USB device number 30 using ohci-pci
May 16 09:03:43 unyx kernel: [  137.541154] usb 4-3: device not accepting address 30, error -32
May 16 09:03:43 unyx kernel: [  137.677268] usb 4-3: new low-speed USB device number 31 using ohci-pci
May 16 09:03:44 unyx kernel: [  138.085511] usb 4-3: device not accepting address 31, error -32
May 16 09:03:44 unyx kernel: [  138.087017] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:44 unyx kernel: [  138.221623] usb 4-4: new full-speed USB device number 32 using ohci-pci
May 16 09:03:44 unyx kernel: [  138.361712] usb 4-4: device descriptor read/64, error -71
May 16 09:03:44 unyx kernel: [  138.605870] usb 4-4: device descriptor read/64, error -71
May 16 09:03:44 unyx kernel: [  138.846029] usb 4-4: new full-speed USB device number 33 using ohci-pci
May 16 09:03:45 unyx kernel: [  138.986120] usb 4-4: device descriptor read/64, error -71
May 16 09:03:45 unyx kernel: [  139.230280] usb 4-4: device descriptor read/64, error -71
May 16 09:03:45 unyx kernel: [  139.470438] usb 4-4: new full-speed USB device number 34 using ohci-pci
May 16 09:03:45 unyx kernel: [  139.495549] usb 4-4: device descriptor read/8, error -62
May 16 09:03:45 unyx kernel: [  139.619630] usb 4-4: device descriptor read/8, error -62
May 16 09:03:45 unyx kernel: [  139.858691] usb 4-4: new full-speed USB device number 35 using ohci-pci
May 16 09:03:45 unyx kernel: [  139.883802] usb 4-4: device descriptor read/8, error -62
May 16 09:03:46 unyx kernel: [  140.007883] usb 4-4: device descriptor read/8, error -62
May 16 09:03:46 unyx kernel: [  140.110861] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:03:46 unyx kernel: [  140.322994] usb 4-3: new low-speed USB device number 36 using ohci-pci
May 16 09:03:46 unyx kernel: [  140.463085] usb 4-3: device descriptor read/64, error -32
May 16 09:03:46 unyx kernel: [  140.707244] usb 4-3: device descriptor read/64, error -32
May 16 09:03:47 unyx kernel: [  140.947405] usb 4-3: new low-speed USB device number 37 using ohci-pci
May 16 09:03:47 unyx kernel: [  141.087493] usb 4-3: device descriptor read/64, error -32
May 16 09:03:47 unyx kernel: [  141.331652] usb 4-3: device descriptor read/64, error -32
May 16 09:03:47 unyx kernel: [  141.571809] usb 4-3: new low-speed USB device number 38 using ohci-pci
May 16 09:03:48 unyx kernel: [  141.980053] usb 4-3: device not accepting address 38, error -32
May 16 09:03:48 unyx kernel: [  142.116164] usb 4-3: new low-speed USB device number 39 using ohci-pci
May 16 09:03:48 unyx kernel: [  142.524409] usb 4-3: device not accepting address 39, error -32
May 16 09:03:48 unyx kernel: [  142.525915] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:48 unyx kernel: [  142.660523] usb 4-4: new full-speed USB device number 40 using ohci-pci
May 16 09:03:48 unyx kernel: [  142.800611] usb 4-4: device descriptor read/64, error -71
May 16 09:03:49 unyx kernel: [  143.044772] usb 4-4: device descriptor read/64, error -71
May 16 09:03:49 unyx kernel: [  143.284928] usb 4-4: new full-speed USB device number 41 using ohci-pci
May 16 09:03:49 unyx kernel: [  143.425020] usb 4-4: device descriptor read/64, error -71
May 16 09:03:49 unyx kernel: [  143.669179] usb 4-4: device descriptor read/64, error -71
May 16 09:03:50 unyx kernel: [  143.909336] usb 4-4: new full-speed USB device number 42 using ohci-pci
May 16 09:03:50 unyx kernel: [  143.934448] usb 4-4: device descriptor read/8, error -62
May 16 09:03:50 unyx kernel: [  144.058529] usb 4-4: device descriptor read/8, error -62
May 16 09:03:50 unyx kernel: [  144.297594] usb 4-4: new full-speed USB device number 43 using ohci-pci
May 16 09:03:50 unyx kernel: [  144.322701] usb 4-4: device descriptor read/8, error -62
May 16 09:03:50 unyx kernel: [  144.446783] usb 4-4: device descriptor read/8, error -62
May 16 09:03:50 unyx kernel: [  144.549777] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:03:51 unyx kernel: [  145.342273] usb 5-3: new full-speed USB device number 74 using ohci-pci
May 16 09:03:51 unyx kernel: [  145.482363] usb 5-3: device descriptor read/64, error -32
May 16 09:03:51 unyx kernel: [  145.726522] usb 5-3: device descriptor read/64, error -32
May 16 09:03:52 unyx kernel: [  145.966681] usb 5-3: new full-speed USB device number 75 using ohci-pci
May 16 09:03:52 unyx kernel: [  146.106771] usb 5-3: device descriptor read/64, error -32
May 16 09:03:52 unyx kernel: [  146.350933] usb 5-3: device descriptor read/64, error -32
May 16 09:03:52 unyx kernel: [  146.591088] usb 5-3: new full-speed USB device number 76 using ohci-pci
May 16 09:03:53 unyx kernel: [  146.999333] usb 5-3: device not accepting address 76, error -32
May 16 09:03:53 unyx kernel: [  147.135446] usb 5-3: new full-speed USB device number 77 using ohci-pci
May 16 09:03:53 unyx kernel: [  147.543687] usb 5-3: device not accepting address 77, error -32
May 16 09:03:53 unyx kernel: [  147.545179] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:53 unyx kernel: [  147.755849] usb 5-3: new full-speed USB device number 78 using ohci-pci
May 16 09:03:54 unyx kernel: [  147.895939] usb 5-3: device descriptor read/64, error -32
May 16 09:03:54 unyx kernel: [  148.140098] usb 5-3: device descriptor read/64, error -32
May 16 09:03:54 unyx kernel: [  148.380257] usb 5-3: new full-speed USB device number 79 using ohci-pci
May 16 09:03:54 unyx kernel: [  148.520347] usb 5-3: device descriptor read/64, error -32
May 16 09:03:54 unyx kernel: [  148.764508] usb 5-3: device descriptor read/64, error -32
May 16 09:03:55 unyx kernel: [  149.004665] usb 5-3: new full-speed USB device number 80 using ohci-pci
May 16 09:03:55 unyx kernel: [  149.412910] usb 5-3: device not accepting address 80, error -32
May 16 09:03:55 unyx kernel: [  149.549021] usb 5-3: new full-speed USB device number 81 using ohci-pci
May 16 09:03:56 unyx kernel: [  149.957222] usb 5-3: device not accepting address 81, error -32
May 16 09:03:56 unyx kernel: [  149.958747] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:56 unyx kernel: [  150.157420] usb 4-3: new low-speed USB device number 44 using ohci-pci
May 16 09:03:56 unyx kernel: [  150.297508] usb 4-3: device descriptor read/64, error -32
May 16 09:03:56 unyx kernel: [  150.541667] usb 4-3: device descriptor read/64, error -32
May 16 09:03:56 unyx kernel: [  150.781827] usb 4-3: new low-speed USB device number 45 using ohci-pci
May 16 09:03:57 unyx kernel: [  150.921916] usb 4-3: device descriptor read/64, error -32
May 16 09:03:57 unyx kernel: [  151.166077] usb 4-3: device descriptor read/64, error -32
May 16 09:03:57 unyx kernel: [  151.406234] usb 4-3: new low-speed USB device number 46 using ohci-pci
May 16 09:03:57 unyx kernel: [  151.814478] usb 4-3: device not accepting address 46, error -32
May 16 09:03:58 unyx kernel: [  151.950591] usb 4-3: new low-speed USB device number 47 using ohci-pci
May 16 09:03:58 unyx kernel: [  152.358834] usb 4-3: device not accepting address 47, error -32
May 16 09:03:58 unyx kernel: [  152.360342] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:03:58 unyx kernel: [  152.494946] usb 4-4: new full-speed USB device number 48 using ohci-pci
May 16 09:03:58 unyx kernel: [  152.635035] usb 4-4: device descriptor read/64, error -71
May 16 09:03:58 unyx kernel: [  152.879196] usb 4-4: device descriptor read/64, error -71
May 16 09:03:59 unyx kernel: [  153.119353] usb 4-4: new full-speed USB device number 49 using ohci-pci
May 16 09:03:59 unyx kernel: [  153.259443] usb 4-4: device descriptor read/64, error -71
May 16 09:03:59 unyx kernel: [  153.503603] usb 4-4: device descriptor read/64, error -71
May 16 09:03:59 unyx kernel: [  153.743760] usb 4-4: new full-speed USB device number 50 using ohci-pci
May 16 09:03:59 unyx kernel: [  153.768872] usb 4-4: device descriptor read/8, error -62
May 16 09:03:59 unyx kernel: [  153.892954] usb 4-4: device descriptor read/8, error -62
May 16 09:04:00 unyx kernel: [  154.132016] usb 4-4: new full-speed USB device number 51 using ohci-pci
May 16 09:04:00 unyx kernel: [  154.157125] usb 4-4: device descriptor read/8, error -62
May 16 09:04:00 unyx kernel: [  154.281207] usb 4-4: device descriptor read/8, error -62
May 16 09:04:00 unyx kernel: [  154.384183] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:00 unyx kernel: [  154.596316] usb 4-3: new low-speed USB device number 52 using ohci-pci
May 16 09:04:00 unyx kernel: [  154.736407] usb 4-3: device descriptor read/64, error -32
May 16 09:04:01 unyx kernel: [  154.980567] usb 4-3: device descriptor read/64, error -32
May 16 09:04:01 unyx kernel: [  155.220727] usb 4-3: new low-speed USB device number 53 using ohci-pci
May 16 09:04:01 unyx kernel: [  155.360816] usb 4-3: device descriptor read/64, error -32
May 16 09:04:01 unyx kernel: [  155.604977] usb 4-3: device descriptor read/64, error -32
May 16 09:04:01 unyx kernel: [  155.845133] usb 4-3: new low-speed USB device number 54 using ohci-pci
May 16 09:04:02 unyx kernel: [  156.253376] usb 4-3: device not accepting address 54, error -32
May 16 09:04:02 unyx kernel: [  156.389488] usb 4-3: new low-speed USB device number 55 using ohci-pci
May 16 09:04:02 unyx kernel: [  156.797733] usb 4-3: device not accepting address 55, error -32
May 16 09:04:02 unyx kernel: [  156.799268] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:03 unyx kernel: [  156.933849] usb 4-4: new full-speed USB device number 56 using ohci-pci
May 16 09:04:03 unyx kernel: [  157.073935] usb 4-4: device descriptor read/64, error -71
May 16 09:04:03 unyx kernel: [  157.318093] usb 4-4: device descriptor read/64, error -71
May 16 09:04:03 unyx kernel: [  157.558256] usb 4-4: new full-speed USB device number 57 using ohci-pci
May 16 09:04:03 unyx kernel: [  157.698343] usb 4-4: device descriptor read/64, error -71
May 16 09:04:04 unyx kernel: [  157.942503] usb 4-4: device descriptor read/64, error -71
May 16 09:04:04 unyx kernel: [  158.182660] usb 4-4: new full-speed USB device number 58 using ohci-pci
May 16 09:04:04 unyx kernel: [  158.207792] usb 4-4: device descriptor read/8, error -62
May 16 09:04:04 unyx kernel: [  158.331872] usb 4-4: device descriptor read/8, error -62
May 16 09:04:04 unyx kernel: [  158.570921] usb 4-4: new full-speed USB device number 59 using ohci-pci
May 16 09:04:04 unyx kernel: [  158.596045] usb 4-4: device descriptor read/8, error -62
May 16 09:04:04 unyx kernel: [  158.720126] usb 4-4: device descriptor read/8, error -62
May 16 09:04:04 unyx kernel: [  158.823084] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:05 unyx kernel: [  159.615596] usb 5-3: new full-speed USB device number 82 using ohci-pci
May 16 09:04:05 unyx kernel: [  159.755686] usb 5-3: device descriptor read/64, error -32
May 16 09:04:06 unyx kernel: [  159.999847] usb 5-3: device descriptor read/64, error -32
May 16 09:04:06 unyx kernel: [  160.240005] usb 5-3: new full-speed USB device number 83 using ohci-pci
May 16 09:04:06 unyx kernel: [  160.380094] usb 5-3: device descriptor read/64, error -32
May 16 09:04:06 unyx kernel: [  160.624254] usb 5-3: device descriptor read/64, error -32
May 16 09:04:06 unyx kernel: [  160.864411] usb 5-3: new full-speed USB device number 84 using ohci-pci
May 16 09:04:07 unyx kernel: [  161.272656] usb 5-3: device not accepting address 84, error -32
May 16 09:04:07 unyx kernel: [  161.408769] usb 5-3: new full-speed USB device number 85 using ohci-pci
May 16 09:04:07 unyx kernel: [  161.817010] usb 5-3: device not accepting address 85, error -32
May 16 09:04:07 unyx kernel: [  161.818531] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:08 unyx kernel: [  162.029173] usb 5-3: new full-speed USB device number 86 using ohci-pci
May 16 09:04:08 unyx kernel: [  162.169264] usb 5-3: device descriptor read/64, error -32
May 16 09:04:08 unyx kernel: [  162.413422] usb 5-3: device descriptor read/64, error -32
May 16 09:04:08 unyx kernel: [  162.653580] usb 5-3: new full-speed USB device number 87 using ohci-pci
May 16 09:04:08 unyx kernel: [  162.793671] usb 5-3: device descriptor read/64, error -32
May 16 09:04:09 unyx kernel: [  163.037832] usb 5-3: device descriptor read/64, error -32
May 16 09:04:09 unyx kernel: [  163.277989] usb 5-3: new full-speed USB device number 88 using ohci-pci
May 16 09:04:09 unyx kernel: [  163.686232] usb 5-3: device not accepting address 88, error -32
May 16 09:04:09 unyx kernel: [  163.822343] usb 5-3: new full-speed USB device number 89 using ohci-pci
May 16 09:04:10 unyx kernel: [  164.230588] usb 5-3: device not accepting address 89, error -32
May 16 09:04:10 unyx kernel: [  164.232098] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:10 unyx kernel: [  164.430741] usb 4-3: new low-speed USB device number 60 using ohci-pci
May 16 09:04:10 unyx kernel: [  164.570832] usb 4-3: device descriptor read/64, error -32
May 16 09:04:10 unyx kernel: [  164.814990] usb 4-3: device descriptor read/64, error -32
May 16 09:04:11 unyx kernel: [  165.055149] usb 4-3: new low-speed USB device number 61 using ohci-pci
May 16 09:04:11 unyx kernel: [  165.195239] usb 4-3: device descriptor read/64, error -32
May 16 09:04:11 unyx kernel: [  165.439399] usb 4-3: device descriptor read/64, error -32
May 16 09:04:11 unyx kernel: [  165.679557] usb 4-3: new low-speed USB device number 62 using ohci-pci
May 16 09:04:12 unyx kernel: [  166.087801] usb 4-3: device not accepting address 62, error -32
May 16 09:04:12 unyx kernel: [  166.223912] usb 4-3: new low-speed USB device number 63 using ohci-pci
May 16 09:04:12 unyx kernel: [  166.632156] usb 4-3: device not accepting address 63, error -32
May 16 09:04:12 unyx kernel: [  166.633667] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:12 unyx kernel: [  166.768268] usb 4-4: new full-speed USB device number 64 using ohci-pci
May 16 09:04:13 unyx kernel: [  166.908358] usb 4-4: device descriptor read/64, error -71
May 16 09:04:13 unyx kernel: [  167.152519] usb 4-4: device descriptor read/64, error -71
May 16 09:04:13 unyx kernel: [  167.392676] usb 4-4: new full-speed USB device number 65 using ohci-pci
May 16 09:04:13 unyx kernel: [  167.532766] usb 4-4: device descriptor read/64, error -71
May 16 09:04:13 unyx kernel: [  167.776951] usb 4-4: device descriptor read/64, error -71
May 16 09:04:14 unyx kernel: [  168.017083] usb 4-4: new full-speed USB device number 66 using ohci-pci
May 16 09:04:14 unyx kernel: [  168.042217] usb 4-4: device descriptor read/8, error -62
May 16 09:04:14 unyx kernel: [  168.166301] usb 4-4: device descriptor read/8, error -62
May 16 09:04:14 unyx kernel: [  168.405338] usb 4-4: new full-speed USB device number 67 using ohci-pci
May 16 09:04:14 unyx kernel: [  168.430451] usb 4-4: device descriptor read/8, error -62
May 16 09:04:14 unyx kernel: [  168.554531] usb 4-4: device descriptor read/8, error -62
May 16 09:04:14 unyx kernel: [  168.657508] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:14 unyx kernel: [  168.869641] usb 4-3: new low-speed USB device number 68 using ohci-pci
May 16 09:04:15 unyx kernel: [  169.009731] usb 4-3: device descriptor read/64, error -32
May 16 09:04:15 unyx kernel: [  169.253895] usb 4-3: device descriptor read/64, error -32
May 16 09:04:15 unyx kernel: [  169.494048] usb 4-3: new low-speed USB device number 69 using ohci-pci
May 16 09:04:15 unyx kernel: [  169.634139] usb 4-3: device descriptor read/64, error -32
May 16 09:04:15 unyx kernel: [  169.878317] usb 4-3: device descriptor read/64, error -32
May 16 09:04:16 unyx kernel: [  170.118457] usb 4-3: new low-speed USB device number 70 using ohci-pci
May 16 09:04:16 unyx kernel: [  170.526686] usb 4-3: device not accepting address 70, error -32
May 16 09:04:16 unyx kernel: [  170.662811] usb 4-3: new low-speed USB device number 71 using ohci-pci
May 16 09:04:17 unyx kernel: [  171.071056] usb 4-3: device not accepting address 71, error -32
May 16 09:04:17 unyx kernel: [  171.072566] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:17 unyx kernel: [  171.207169] usb 4-4: new full-speed USB device number 72 using ohci-pci
May 16 09:04:17 unyx kernel: [  171.347259] usb 4-4: device descriptor read/64, error -71
May 16 09:04:17 unyx kernel: [  171.591417] usb 4-4: device descriptor read/64, error -71
May 16 09:04:17 unyx kernel: [  171.831575] usb 4-4: new full-speed USB device number 73 using ohci-pci
May 16 09:04:18 unyx kernel: [  171.971666] usb 4-4: device descriptor read/64, error -71
May 16 09:04:18 unyx kernel: [  172.215834] usb 4-4: device descriptor read/64, error -71
May 16 09:04:18 unyx kernel: [  172.455983] usb 4-4: new full-speed USB device number 74 using ohci-pci
May 16 09:04:18 unyx kernel: [  172.481094] usb 4-4: device descriptor read/8, error -62
May 16 09:04:18 unyx kernel: [  172.605177] usb 4-4: device descriptor read/8, error -62
May 16 09:04:18 unyx kernel: [  172.844237] usb 4-4: new full-speed USB device number 75 using ohci-pci
May 16 09:04:18 unyx kernel: [  172.869348] usb 4-4: device descriptor read/8, error -62
May 16 09:04:19 unyx kernel: [  172.993430] usb 4-4: device descriptor read/8, error -62
May 16 09:04:19 unyx kernel: [  173.096406] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:19 unyx kernel: [  173.872908] usb 5-3: new full-speed USB device number 90 using ohci-pci
May 16 09:04:20 unyx kernel: [  174.012999] usb 5-3: device descriptor read/64, error -32
May 16 09:04:20 unyx kernel: [  174.257160] usb 5-3: device descriptor read/64, error -32
May 16 09:04:20 unyx kernel: [  174.497317] usb 5-3: new full-speed USB device number 91 using ohci-pci
May 16 09:04:20 unyx kernel: [  174.637407] usb 5-3: device descriptor read/64, error -32
May 16 09:04:20 unyx kernel: [  174.881567] usb 5-3: device descriptor read/64, error -32
May 16 09:04:21 unyx kernel: [  175.121725] usb 5-3: new full-speed USB device number 92 using ohci-pci
May 16 09:04:21 unyx kernel: [  175.529968] usb 5-3: device not accepting address 92, error -32
May 16 09:04:21 unyx kernel: [  175.666082] usb 5-3: new full-speed USB device number 93 using ohci-pci
May 16 09:04:22 unyx kernel: [  176.074325] usb 5-3: device not accepting address 93, error -32
May 16 09:04:22 unyx kernel: [  176.075818] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:22 unyx kernel: [  176.286484] usb 5-3: new full-speed USB device number 94 using ohci-pci
May 16 09:04:22 unyx kernel: [  176.426576] usb 5-3: device descriptor read/64, error -32
May 16 09:04:22 unyx kernel: [  176.670735] usb 5-3: device descriptor read/64, error -32
May 16 09:04:22 unyx kernel: [  176.910893] usb 5-3: new full-speed USB device number 95 using ohci-pci
May 16 09:04:23 unyx kernel: [  177.050984] usb 5-3: device descriptor read/64, error -32
May 16 09:04:23 unyx kernel: [  177.295144] usb 5-3: device descriptor read/64, error -32
May 16 09:04:23 unyx kernel: [  177.535307] usb 5-3: new full-speed USB device number 96 using ohci-pci
May 16 09:04:24 unyx kernel: [  177.943544] usb 5-3: device not accepting address 96, error -32
May 16 09:04:24 unyx kernel: [  178.079658] usb 5-3: new full-speed USB device number 97 using ohci-pci
May 16 09:04:24 unyx kernel: [  178.487900] usb 5-3: device not accepting address 97, error -32
May 16 09:04:24 unyx kernel: [  178.489433] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:24 unyx kernel: [  178.688053] usb 4-3: new low-speed USB device number 76 using ohci-pci
May 16 09:04:24 unyx kernel: [  178.828145] usb 4-3: device descriptor read/64, error -32
May 16 09:04:25 unyx kernel: [  179.072326] usb 4-3: device descriptor read/64, error -32
May 16 09:04:25 unyx kernel: [  179.312462] usb 4-3: new low-speed USB device number 77 using ohci-pci
May 16 09:04:25 unyx kernel: [  179.452553] usb 4-3: device descriptor read/64, error -32
May 16 09:04:25 unyx kernel: [  179.696711] usb 4-3: device descriptor read/64, error -32
May 16 09:04:26 unyx kernel: [  179.936869] usb 4-3: new low-speed USB device number 78 using ohci-pci
May 16 09:04:26 unyx kernel: [  180.345116] usb 4-3: device not accepting address 78, error -32
May 16 09:04:26 unyx kernel: [  180.481225] usb 4-3: new low-speed USB device number 79 using ohci-pci
May 16 09:04:26 unyx kernel: [  180.889469] usb 4-3: device not accepting address 79, error -32
May 16 09:04:26 unyx kernel: [  180.890979] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:27 unyx kernel: [  181.025582] usb 4-4: new full-speed USB device number 80 using ohci-pci
May 16 09:04:27 unyx kernel: [  181.165674] usb 4-4: device descriptor read/64, error -71
May 16 09:04:27 unyx kernel: [  181.409831] usb 4-4: device descriptor read/64, error -71
May 16 09:04:27 unyx kernel: [  181.649989] usb 4-4: new full-speed USB device number 81 using ohci-pci
May 16 09:04:27 unyx kernel: [  181.790079] usb 4-4: device descriptor read/64, error -71
May 16 09:04:28 unyx kernel: [  182.034239] usb 4-4: device descriptor read/64, error -71
May 16 09:04:28 unyx kernel: [  182.274397] usb 4-4: new full-speed USB device number 82 using ohci-pci
May 16 09:04:28 unyx kernel: [  182.299509] usb 4-4: device descriptor read/8, error -62
May 16 09:04:28 unyx kernel: [  182.423590] usb 4-4: device descriptor read/8, error -62
May 16 09:04:28 unyx kernel: [  182.662595] usb 4-4: new full-speed USB device number 83 using ohci-pci
May 16 09:04:28 unyx kernel: [  182.687763] usb 4-4: device descriptor read/8, error -62
May 16 09:04:28 unyx kernel: [  182.811843] usb 4-4: device descriptor read/8, error -62
May 16 09:04:28 unyx kernel: [  182.914831] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:29 unyx kernel: [  183.126954] usb 4-3: new low-speed USB device number 84 using ohci-pci
May 16 09:04:29 unyx kernel: [  183.267045] usb 4-3: device descriptor read/64, error -32
May 16 09:04:29 unyx kernel: [  183.511204] usb 4-3: device descriptor read/64, error -32
May 16 09:04:29 unyx kernel: [  183.751361] usb 4-3: new low-speed USB device number 85 using ohci-pci
May 16 09:04:29 unyx kernel: [  183.891451] usb 4-3: device descriptor read/64, error -32
May 16 09:04:30 unyx kernel: [  184.135612] usb 4-3: device descriptor read/64, error -32
May 16 09:04:30 unyx kernel: [  184.375775] usb 4-3: new low-speed USB device number 86 using ohci-pci
May 16 09:04:30 unyx kernel: [  184.784013] usb 4-3: device not accepting address 86, error -32
May 16 09:04:31 unyx kernel: [  184.920139] usb 4-3: new low-speed USB device number 87 using ohci-pci
May 16 09:04:31 unyx kernel: [  185.328368] usb 4-3: device not accepting address 87, error -32
May 16 09:04:31 unyx kernel: [  185.329874] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:31 unyx kernel: [  185.464482] usb 4-4: new full-speed USB device number 88 using ohci-pci
May 16 09:04:31 unyx kernel: [  185.604570] usb 4-4: device descriptor read/64, error -71
May 16 09:04:31 unyx kernel: [  185.848731] usb 4-4: device descriptor read/64, error -71
May 16 09:04:32 unyx kernel: [  186.088888] usb 4-4: new full-speed USB device number 89 using ohci-pci
May 16 09:04:32 unyx kernel: [  186.228981] usb 4-4: device descriptor read/64, error -71
May 16 09:04:32 unyx kernel: [  186.473138] usb 4-4: device descriptor read/64, error -71
May 16 09:04:32 unyx kernel: [  186.713296] usb 4-4: new full-speed USB device number 90 using ohci-pci
May 16 09:04:32 unyx kernel: [  186.738408] usb 4-4: device descriptor read/8, error -62
May 16 09:04:32 unyx kernel: [  186.862488] usb 4-4: device descriptor read/8, error -62
May 16 09:04:33 unyx kernel: [  187.101551] usb 4-4: new full-speed USB device number 91 using ohci-pci
May 16 09:04:33 unyx kernel: [  187.126661] usb 4-4: device descriptor read/8, error -62
May 16 09:04:33 unyx kernel: [  187.250742] usb 4-4: device descriptor read/8, error -62
May 16 09:04:33 unyx kernel: [  187.353720] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:34 unyx kernel: [  188.150235] usb 5-3: new full-speed USB device number 98 using ohci-pci
May 16 09:04:34 unyx kernel: [  188.290325] usb 5-3: device descriptor read/64, error -32
May 16 09:04:34 unyx kernel: [  188.534485] usb 5-3: device descriptor read/64, error -32
May 16 09:04:34 unyx kernel: [  188.774643] usb 5-3: new full-speed USB device number 99 using ohci-pci
May 16 09:04:34 unyx kernel: [  188.914733] usb 5-3: device descriptor read/64, error -32
May 16 09:04:35 unyx kernel: [  189.158893] usb 5-3: device descriptor read/64, error -32
May 16 09:04:35 unyx kernel: [  189.399050] usb 5-3: new full-speed USB device number 100 using ohci-pci
May 16 09:04:35 unyx kernel: [  189.807294] usb 5-3: device not accepting address 100, error -32
May 16 09:04:36 unyx kernel: [  189.943407] usb 5-3: new full-speed USB device number 101 using ohci-pci
May 16 09:04:36 unyx kernel: [  190.351650] usb 5-3: device not accepting address 101, error -32
May 16 09:04:36 unyx kernel: [  190.353168] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:36 unyx kernel: [  190.563811] usb 5-3: new full-speed USB device number 102 using ohci-pci
May 16 09:04:36 unyx kernel: [  190.703902] usb 5-3: device descriptor read/64, error -32
May 16 09:04:37 unyx kernel: [  190.948061] usb 5-3: device descriptor read/64, error -32
May 16 09:04:37 unyx kernel: [  191.188220] usb 5-3: new full-speed USB device number 103 using ohci-pci
May 16 09:04:37 unyx kernel: [  191.328310] usb 5-3: device descriptor read/64, error -32
May 16 09:04:37 unyx kernel: [  191.572469] usb 5-3: device descriptor read/64, error -32
May 16 09:04:37 unyx kernel: [  191.812627] usb 5-3: new full-speed USB device number 104 using ohci-pci
May 16 09:04:38 unyx kernel: [  192.220871] usb 5-3: device not accepting address 104, error -32
May 16 09:04:38 unyx kernel: [  192.356984] usb 5-3: new full-speed USB device number 105 using ohci-pci
May 16 09:04:38 unyx kernel: [  192.765226] usb 5-3: device not accepting address 105, error -32
May 16 09:04:38 unyx kernel: [  192.766733] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:39 unyx kernel: [  192.965380] usb 4-3: new low-speed USB device number 92 using ohci-pci
May 16 09:04:39 unyx kernel: [  193.105470] usb 4-3: device descriptor read/64, error -32
May 16 09:04:39 unyx kernel: [  193.349630] usb 4-3: device descriptor read/64, error -32
May 16 09:04:39 unyx kernel: [  193.589787] usb 4-3: new low-speed USB device number 93 using ohci-pci
May 16 09:04:39 unyx kernel: [  193.729878] usb 4-3: device descriptor read/64, error -32
May 16 09:04:40 unyx kernel: [  193.974037] usb 4-3: device descriptor read/64, error -32
May 16 09:04:40 unyx kernel: [  194.214196] usb 4-3: new low-speed USB device number 94 using ohci-pci
May 16 09:04:40 unyx kernel: [  194.622440] usb 4-3: device not accepting address 94, error -32
May 16 09:04:40 unyx kernel: [  194.758558] usb 4-3: new low-speed USB device number 95 using ohci-pci
May 16 09:04:41 unyx kernel: [  195.166794] usb 4-3: device not accepting address 95, error -32
May 16 09:04:41 unyx kernel: [  195.168397] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:41 unyx kernel: [  195.302909] usb 4-4: new full-speed USB device number 96 using ohci-pci
May 16 09:04:41 unyx kernel: [  195.442998] usb 4-4: device descriptor read/64, error -71
May 16 09:04:41 unyx kernel: [  195.687157] usb 4-4: device descriptor read/64, error -71
May 16 09:04:42 unyx kernel: [  195.927316] usb 4-4: new full-speed USB device number 97 using ohci-pci
May 16 09:04:42 unyx kernel: [  196.067406] usb 4-4: device descriptor read/64, error -71
May 16 09:04:42 unyx kernel: [  196.311566] usb 4-4: device descriptor read/64, error -71
May 16 09:04:42 unyx kernel: [  196.551726] usb 4-4: new full-speed USB device number 98 using ohci-pci
May 16 09:04:42 unyx kernel: [  196.576837] usb 4-4: device descriptor read/8, error -62
May 16 09:04:42 unyx kernel: [  196.700917] usb 4-4: device descriptor read/8, error -62
May 16 09:04:43 unyx kernel: [  196.939976] usb 4-4: new full-speed USB device number 99 using ohci-pci
May 16 09:04:43 unyx kernel: [  196.965088] usb 4-4: device descriptor read/8, error -62
May 16 09:04:43 unyx kernel: [  197.089170] usb 4-4: device descriptor read/8, error -62
May 16 09:04:43 unyx kernel: [  197.192110] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:43 unyx kernel: [  197.404281] usb 4-3: new low-speed USB device number 100 using ohci-pci
May 16 09:04:43 unyx kernel: [  197.544372] usb 4-3: device descriptor read/64, error -32
May 16 09:04:43 unyx kernel: [  197.788529] usb 4-3: device descriptor read/64, error -32
May 16 09:04:44 unyx kernel: [  198.028688] usb 4-3: new low-speed USB device number 101 using ohci-pci
May 16 09:04:44 unyx kernel: [  198.168779] usb 4-3: device descriptor read/64, error -32
May 16 09:04:44 unyx kernel: [  198.412937] usb 4-3: device descriptor read/64, error -32
May 16 09:04:44 unyx kernel: [  198.653095] usb 4-3: new low-speed USB device number 102 using ohci-pci
May 16 09:04:45 unyx kernel: [  199.061341] usb 4-3: device not accepting address 102, error -32
May 16 09:04:45 unyx kernel: [  199.197450] usb 4-3: new low-speed USB device number 103 using ohci-pci
May 16 09:04:45 unyx kernel: [  199.605694] usb 4-3: device not accepting address 103, error -32
May 16 09:04:45 unyx kernel: [  199.607294] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:45 unyx kernel: [  199.741807] usb 4-4: new full-speed USB device number 104 using ohci-pci
May 16 09:04:45 unyx kernel: [  199.881897] usb 4-4: device descriptor read/64, error -71
May 16 09:04:46 unyx kernel: [  200.126077] usb 4-4: device descriptor read/64, error -71
May 16 09:04:46 unyx kernel: [  200.366213] usb 4-4: new full-speed USB device number 105 using ohci-pci
May 16 09:04:46 unyx kernel: [  200.506305] usb 4-4: device descriptor read/64, error -71
May 16 09:04:46 unyx kernel: [  200.750464] usb 4-4: device descriptor read/64, error -71
May 16 09:04:47 unyx kernel: [  200.990622] usb 4-4: new full-speed USB device number 106 using ohci-pci
May 16 09:04:47 unyx kernel: [  201.015733] usb 4-4: device descriptor read/8, error -62
May 16 09:04:47 unyx kernel: [  201.139815] usb 4-4: device descriptor read/8, error -62
May 16 09:04:47 unyx kernel: [  201.378877] usb 4-4: new full-speed USB device number 107 using ohci-pci
May 16 09:04:47 unyx kernel: [  201.403986] usb 4-4: device descriptor read/8, error -62
May 16 09:04:47 unyx kernel: [  201.528068] usb 4-4: device descriptor read/8, error -62
May 16 09:04:47 unyx kernel: [  201.631045] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:48 unyx kernel: [  202.419556] usb 5-3: new full-speed USB device number 106 using ohci-pci
May 16 09:04:48 unyx kernel: [  202.559591] usb 5-3: device descriptor read/64, error -32
May 16 09:04:48 unyx kernel: [  202.803805] usb 5-3: device descriptor read/64, error -32
May 16 09:04:49 unyx kernel: [  203.043973] usb 5-3: new full-speed USB device number 107 using ohci-pci
May 16 09:04:49 unyx kernel: [  203.184055] usb 5-3: device descriptor read/64, error -32
May 16 09:04:49 unyx kernel: [  203.428214] usb 5-3: device descriptor read/64, error -32
May 16 09:04:49 unyx kernel: [  203.668371] usb 5-3: new full-speed USB device number 108 using ohci-pci
May 16 09:04:50 unyx kernel: [  204.076616] usb 5-3: device not accepting address 108, error -32
May 16 09:04:50 unyx kernel: [  204.212728] usb 5-3: new full-speed USB device number 109 using ohci-pci
May 16 09:04:50 unyx kernel: [  204.620971] usb 5-3: device not accepting address 109, error -32
May 16 09:04:50 unyx kernel: [  204.621059] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:50 unyx kernel: [  204.833132] usb 5-3: new full-speed USB device number 110 using ohci-pci
May 16 09:04:51 unyx kernel: [  204.973222] usb 5-3: device descriptor read/64, error -32
May 16 09:04:51 unyx kernel: [  205.217383] usb 5-3: device descriptor read/64, error -32
May 16 09:04:51 unyx kernel: [  205.457540] usb 5-3: new full-speed USB device number 111 using ohci-pci
May 16 09:04:51 unyx kernel: [  205.597630] usb 5-3: device descriptor read/64, error -32
May 16 09:04:51 unyx kernel: [  205.841790] usb 5-3: device descriptor read/64, error -32
May 16 09:04:52 unyx kernel: [  206.081948] usb 5-3: new full-speed USB device number 112 using ohci-pci
May 16 09:04:52 unyx kernel: [  206.490191] usb 5-3: device not accepting address 112, error -32
May 16 09:04:52 unyx kernel: [  206.626303] usb 5-3: new full-speed USB device number 113 using ohci-pci
May 16 09:04:53 unyx kernel: [  207.034548] usb 5-3: device not accepting address 113, error -32
May 16 09:04:53 unyx kernel: [  207.034638] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:53 unyx kernel: [  207.234701] usb 4-3: new low-speed USB device number 108 using ohci-pci
May 16 09:04:53 unyx kernel: [  207.374791] usb 4-3: device descriptor read/64, error -32
May 16 09:04:53 unyx kernel: [  207.618964] usb 4-3: device descriptor read/64, error -32
May 16 09:04:53 unyx kernel: [  207.859108] usb 4-3: new low-speed USB device number 109 using ohci-pci
May 16 09:04:54 unyx kernel: [  207.999198] usb 4-3: device descriptor read/64, error -32
May 16 09:04:54 unyx kernel: [  208.243359] usb 4-3: device descriptor read/64, error -32
May 16 09:04:54 unyx kernel: [  208.483517] usb 4-3: new low-speed USB device number 110 using ohci-pci
May 16 09:04:54 unyx kernel: [  208.891761] usb 4-3: device not accepting address 110, error -32
May 16 09:04:55 unyx kernel: [  209.027872] usb 4-3: new low-speed USB device number 111 using ohci-pci
May 16 09:04:55 unyx kernel: [  209.436117] usb 4-3: device not accepting address 111, error -32
May 16 09:04:55 unyx kernel: [  209.436203] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:04:55 unyx kernel: [  209.572227] usb 4-4: new full-speed USB device number 112 using ohci-pci
May 16 09:04:55 unyx kernel: [  209.712318] usb 4-4: device descriptor read/64, error -71
May 16 09:04:56 unyx kernel: [  209.956478] usb 4-4: device descriptor read/64, error -71
May 16 09:04:56 unyx kernel: [  210.196635] usb 4-4: new full-speed USB device number 113 using ohci-pci
May 16 09:04:56 unyx kernel: [  210.336725] usb 4-4: device descriptor read/64, error -71
May 16 09:04:56 unyx kernel: [  210.580884] usb 4-4: device descriptor read/64, error -71
May 16 09:04:56 unyx kernel: [  210.821043] usb 4-4: new full-speed USB device number 114 using ohci-pci
May 16 09:04:56 unyx kernel: [  210.846154] usb 4-4: device descriptor read/8, error -62
May 16 09:04:57 unyx kernel: [  210.970238] usb 4-4: device descriptor read/8, error -62
May 16 09:04:57 unyx kernel: [  211.209298] usb 4-4: new full-speed USB device number 115 using ohci-pci
May 16 09:04:57 unyx kernel: [  211.234409] usb 4-4: device descriptor read/8, error -62
May 16 09:04:57 unyx kernel: [  211.358489] usb 4-4: device descriptor read/8, error -62
May 16 09:04:57 unyx kernel: [  211.461468] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:04:57 unyx kernel: [  211.673600] usb 4-3: new low-speed USB device number 116 using ohci-pci
May 16 09:04:57 unyx kernel: [  211.813690] usb 4-3: device descriptor read/64, error -32
May 16 09:04:58 unyx kernel: [  212.057848] usb 4-3: device descriptor read/64, error -32
May 16 09:04:58 unyx kernel: [  212.298009] usb 4-3: new low-speed USB device number 117 using ohci-pci
May 16 09:04:58 unyx kernel: [  212.438098] usb 4-3: device descriptor read/64, error -32
May 16 09:04:58 unyx kernel: [  212.682260] usb 4-3: device descriptor read/64, error -32
May 16 09:04:58 unyx kernel: [  212.922415] usb 4-3: new low-speed USB device number 118 using ohci-pci
May 16 09:04:59 unyx kernel: [  213.330659] usb 4-3: device not accepting address 118, error -32
May 16 09:04:59 unyx kernel: [  213.466776] usb 4-3: new low-speed USB device number 119 using ohci-pci
May 16 09:04:59 unyx kernel: [  213.875015] usb 4-3: device not accepting address 119, error -32
May 16 09:04:59 unyx kernel: [  213.875101] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:05:00 unyx kernel: [  214.011126] usb 4-4: new full-speed USB device number 120 using ohci-pci
May 16 09:05:00 unyx kernel: [  214.151217] usb 4-4: device descriptor read/64, error -71
May 16 09:05:00 unyx kernel: [  214.395382] usb 4-4: device descriptor read/64, error -71
May 16 09:05:00 unyx kernel: [  214.635534] usb 4-4: new full-speed USB device number 121 using ohci-pci
May 16 09:05:00 unyx kernel: [  214.775626] usb 4-4: device descriptor read/64, error -71
May 16 09:05:01 unyx kernel: [  215.019785] usb 4-4: device descriptor read/64, error -71
May 16 09:05:01 unyx kernel: [  215.259943] usb 4-4: new full-speed USB device number 122 using ohci-pci
May 16 09:05:01 unyx kernel: [  215.285053] usb 4-4: device descriptor read/8, error -62
May 16 09:05:01 unyx kernel: [  215.409133] usb 4-4: device descriptor read/8, error -62
May 16 09:05:01 unyx kernel: [  215.648196] usb 4-4: new full-speed USB device number 123 using ohci-pci
May 16 09:05:01 unyx kernel: [  215.673307] usb 4-4: device descriptor read/8, error -62
May 16 09:05:01 unyx kernel: [  215.797387] usb 4-4: device descriptor read/8, error -62
May 16 09:05:01 unyx kernel: [  215.900366] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:05:02 unyx kernel: [  216.688875] usb 5-3: new full-speed USB device number 114 using ohci-pci
May 16 09:05:02 unyx kernel: [  216.828967] usb 5-3: device descriptor read/64, error -32
May 16 09:05:03 unyx kernel: [  217.073127] usb 5-3: device descriptor read/64, error -32
May 16 09:05:03 unyx kernel: [  217.313285] usb 5-3: new full-speed USB device number 115 using ohci-pci
May 16 09:05:03 unyx kernel: [  217.453374] usb 5-3: device descriptor read/64, error -32
May 16 09:05:03 unyx kernel: [  217.697534] usb 5-3: device descriptor read/64, error -32
May 16 09:05:03 unyx kernel: [  217.937692] usb 5-3: new full-speed USB device number 116 using ohci-pci
May 16 09:05:04 unyx kernel: [  218.345935] usb 5-3: device not accepting address 116, error -32
May 16 09:05:04 unyx kernel: [  218.482050] usb 5-3: new full-speed USB device number 117 using ohci-pci
May 16 09:05:04 unyx kernel: [  218.890291] usb 5-3: device not accepting address 117, error -32
May 16 09:05:04 unyx kernel: [  218.890381] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:05:05 unyx kernel: [  219.102452] usb 5-3: new full-speed USB device number 118 using ohci-pci
May 16 09:05:05 unyx kernel: [  219.242543] usb 5-3: device descriptor read/64, error -32
May 16 09:05:05 unyx kernel: [  219.486703] usb 5-3: device descriptor read/64, error -32
May 16 09:05:05 unyx kernel: [  219.726861] usb 5-3: new full-speed USB device number 119 using ohci-pci
May 16 09:05:05 unyx kernel: [  219.866951] usb 5-3: device descriptor read/64, error -32
May 16 09:05:06 unyx kernel: [  220.111111] usb 5-3: device descriptor read/64, error -32
May 16 09:05:06 unyx kernel: [  220.351277] usb 5-3: new full-speed USB device number 120 using ohci-pci
May 16 09:05:06 unyx kernel: [  220.759511] usb 5-3: device not accepting address 120, error -32
May 16 09:05:06 unyx kernel: [  220.895625] usb 5-3: new full-speed USB device number 121 using ohci-pci
May 16 09:05:07 unyx kernel: [  221.303868] usb 5-3: device not accepting address 121, error -32
May 16 09:05:07 unyx kernel: [  221.303983] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:05:07 unyx kernel: [  221.504021] usb 4-3: new low-speed USB device number 124 using ohci-pci
May 16 09:05:07 unyx kernel: [  221.644113] usb 4-3: device descriptor read/64, error -32
May 16 09:05:07 unyx kernel: [  221.888271] usb 4-3: device descriptor read/64, error -32
May 16 09:05:08 unyx kernel: [  222.128429] usb 4-3: new low-speed USB device number 125 using ohci-pci
May 16 09:05:08 unyx kernel: [  222.268519] usb 4-3: device descriptor read/64, error -32
May 16 09:05:08 unyx kernel: [  222.512680] usb 4-3: device descriptor read/64, error -32
May 16 09:05:08 unyx kernel: [  222.752837] usb 4-3: new low-speed USB device number 126 using ohci-pci
May 16 09:05:09 unyx kernel: [  223.161082] usb 4-3: device not accepting address 126, error -32
May 16 09:05:09 unyx kernel: [  223.297194] usb 4-3: new low-speed USB device number 127 using ohci-pci
May 16 09:05:09 unyx kernel: [  223.705437] usb 4-3: device not accepting address 127, error -32
May 16 09:05:09 unyx kernel: [  223.705524] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:05:09 unyx kernel: [  223.841549] usb 4-4: new full-speed USB device number 2 using ohci-pci
May 16 09:05:10 unyx kernel: [  223.981638] usb 4-4: device descriptor read/64, error -71
May 16 09:05:10 unyx kernel: [  224.225798] usb 4-4: device descriptor read/64, error -71
May 16 09:05:10 unyx kernel: [  224.465956] usb 4-4: new full-speed USB device number 3 using ohci-pci
May 16 09:05:10 unyx kernel: [  224.606047] usb 4-4: device descriptor read/64, error -71
May 16 09:05:10 unyx kernel: [  224.850206] usb 4-4: device descriptor read/64, error -71
May 16 09:05:11 unyx kernel: [  225.090368] usb 4-4: new full-speed USB device number 4 using ohci-pci
May 16 09:05:11 unyx kernel: [  225.115475] usb 4-4: device descriptor read/8, error -62
May 16 09:05:11 unyx kernel: [  225.239555] usb 4-4: device descriptor read/8, error -62
May 16 09:05:11 unyx kernel: [  225.478617] usb 4-4: new full-speed USB device number 5 using ohci-pci
May 16 09:05:11 unyx kernel: [  225.503730] usb 4-4: device descriptor read/8, error -62
May 16 09:05:11 unyx kernel: [  225.627809] usb 4-4: device descriptor read/8, error -62
May 16 09:05:11 unyx kernel: [  225.730788] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:05:11 unyx kernel: [  225.942920] usb 4-3: new low-speed USB device number 6 using ohci-pci
May 16 09:05:12 unyx kernel: [  226.083015] usb 4-3: device descriptor read/64, error -32
May 16 09:05:12 unyx kernel: [  226.327170] usb 4-3: device descriptor read/64, error -32
May 16 09:05:12 unyx kernel: [  226.567330] usb 4-3: new low-speed USB device number 7 using ohci-pci
May 16 09:05:12 unyx kernel: [  226.707418] usb 4-3: device descriptor read/64, error -32
May 16 09:05:13 unyx kernel: [  226.951578] usb 4-3: device descriptor read/64, error -32
May 16 09:05:13 unyx kernel: [  227.191736] usb 4-3: new low-speed USB device number 8 using ohci-pci
May 16 09:05:13 unyx kernel: [  227.599979] usb 4-3: device not accepting address 8, error -32
May 16 09:05:13 unyx kernel: [  227.736092] usb 4-3: new low-speed USB device number 9 using ohci-pci
May 16 09:05:14 unyx kernel: [  228.144336] usb 4-3: device not accepting address 9, error -32
May 16 09:05:14 unyx kernel: [  228.145838] hub 4-0:1.0: unable to enumerate USB device on port 3
May 16 09:05:14 unyx kernel: [  228.280449] usb 4-4: new full-speed USB device number 10 using ohci-pci
May 16 09:05:14 unyx kernel: [  228.420538] usb 4-4: device descriptor read/64, error -71
May 16 09:05:14 unyx kernel: [  228.664697] usb 4-4: device descriptor read/64, error -71
May 16 09:05:14 unyx kernel: [  228.904855] usb 4-4: new full-speed USB device number 11 using ohci-pci
May 16 09:05:15 unyx kernel: [  229.044947] usb 4-4: device descriptor read/64, error -71
May 16 09:05:15 unyx kernel: [  229.289106] usb 4-4: device descriptor read/64, error -71
May 16 09:05:15 unyx kernel: [  229.529263] usb 4-4: new full-speed USB device number 12 using ohci-pci
May 16 09:05:15 unyx kernel: [  229.554375] usb 4-4: device descriptor read/8, error -62
May 16 09:05:15 unyx kernel: [  229.678455] usb 4-4: device descriptor read/8, error -62
May 16 09:05:15 unyx kernel: [  229.917516] usb 4-4: new full-speed USB device number 13 using ohci-pci
May 16 09:05:15 unyx kernel: [  229.942627] usb 4-4: device descriptor read/8, error -62
May 16 09:05:16 unyx kernel: [  230.066709] usb 4-4: device descriptor read/8, error -62
May 16 09:05:16 unyx kernel: [  230.169687] hub 4-0:1.0: unable to enumerate USB device on port 4
May 16 09:05:17 unyx kernel: [  230.958197] usb 5-3: new full-speed USB device number 122 using ohci-pci
May 16 09:05:17 unyx kernel: [  231.098288] usb 5-3: device descriptor read/64, error -32
May 16 09:05:17 unyx kernel: [  231.342461] usb 5-3: device descriptor read/64, error -32
May 16 09:05:17 unyx kernel: [  231.582604] usb 5-3: new full-speed USB device number 123 using ohci-pci
May 16 09:05:17 unyx kernel: [  231.722696] usb 5-3: device descriptor read/64, error -32
May 16 09:05:18 unyx kernel: [  231.966854] usb 5-3: device descriptor read/64, error -32
May 16 09:05:18 unyx kernel: [  232.207017] usb 5-3: new full-speed USB device number 124 using ohci-pci
May 16 09:05:18 unyx kernel: [  232.615257] usb 5-3: device not accepting address 124, error -32
May 16 09:05:18 unyx kernel: [  232.751370] usb 5-3: new full-speed USB device number 125 using ohci-pci
May 16 09:05:19 unyx kernel: [  233.159613] usb 5-3: device not accepting address 125, error -32
May 16 09:05:19 unyx kernel: [  233.161211] hub 5-0:1.0: unable to enumerate USB device on port 3
May 16 09:05:19 unyx kernel: [  233.371773] usb 5-3: new full-speed USB device number 126 using ohci-pci
May 16 09:05:19 unyx kernel: [  233.511864] usb 5-3: device descriptor read/64, error -32
May 16 09:05:19 unyx kernel: [  233.756024] usb 5-3: device descriptor read/64, error -32
May 16 09:05:20 unyx kernel: [  233.996181] usb 5-3: new full-speed USB device number 127 using ohci-pci
May 16 09:05:20 unyx kernel: [  234.136272] usb 5-3: device descriptor read/64, error -32
May 16 09:05:20 unyx kernel: [  234.380432] usb 5-3: device descriptor read/64, error -32
May 16 09:05:20 unyx kernel: [  234.620589] usb 5-3: new full-speed USB device number 2 using ohci-pci
May 16 09:05:21 unyx kernel: [  235.028833] usb 5-3: device not accepting address 2, error -32
May 16 09:05:21 unyx kernel: [  235.164947] usb 5-3: new full-speed USB device number 3 using
```

---

### Post by dino99 on 2015-05-16
as your keyboard works, open a terminal to run:
> sudo update-usbids
sudo update-pciids

if the problem persist, then boot with an other kernel

---

### Post by daktaklakpak5576 on 2015-05-16
so I updated the ids, which due to no network and unreadable console in ubuntu, went like this:

```
nyx yak # mount /dev/sdc3 /mnt/tmp/nyx yak # mount /dev/sdc1 /mnt/tmp/boot
nyx yak # mount -o bind /dev /mnt/tmp/dev
nyx yak # mount -t proc proc /mnt/tmp/proc
nyx yak # mount -o bind /sys /mnt/tmp/sys
nyx yak # chroot /mnt/tmp /bin/bash
groups: cannot find name for group ID 11
root@nyx:/# su fog
fog@nyx:/$ sudo update-usbids
sudo: unable to resolve host nyx
[sudo] password for fog: 
--2015-05-16 12:27:34--  http://www.linux-usb.org/usb.ids
Resolving www.linux-usb.org (www.linux-usb.org)... failed: Name or service not known.
wget: unable to resolve host address `www.linux-usb.org'
update-usbids: download failed
fog@nyx:/$ cat /etc/resolv.conf 
fog@nyx:/$ file /etc/resolf.conf
/etc/resolf.conf: ERROR: cannot open `/etc/resolf.conf' (No such file or directory)
fog@nyx:/$ file /etc/resolv.conf
/etc/resolv.conf: symbolic link to `../run/resolvconf/resolv.conf'
fog@nyx:/$ rm /etc/resolv.conf
rm: cannot remove `/etc/resolv.conf': Permission denied
fog@nyx:/$ sudo rm /etc/resolv.conf
sudo: unable to resolve host nyx
[sudo] password for fog: 
fog@nyx:/$ exit
exit
root@nyx:/# exit
exit
nyx yak # cp /etc/resolv.conf /mnt/tmp/etc/
nyx yak # chroot /mnt/tmp /bin/bash
groups: cannot find name for group ID 11
root@nyx:/# su fog
fog@nyx:/$ sudo update-usbids
[sudo] password for fog: 
--2015-05-16 12:30:06--  http://www.linux-usb.org/usb.ids
Resolving www.linux-usb.org (www.linux-usb.org)... 216.34.181.97
Connecting to www.linux-usb.org (www.linux-usb.org)|216.34.181.97|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 547006 (534K) [text/plain]
Saving to: `/var/lib/usbutils/usb.ids.new'


100%[======================================>] 547,006     63.2K/s   in 8.3s    


2015-05-16 12:30:16 (64.4 KB/s) - `/var/lib/usbutils/usb.ids.new' saved [547006/547006]


Done.
fog@nyx:/$ sudo update-pciids
[sudo] password for fog: 
Downloaded daily snapshot dated 2015-05-13 03:15:02



```


from within ubuntu
```
nyx yak # mount /dev/sdc3 /mnt/tmpnyx yak # cat /mnt/tmp/home/fog/lsusb.txt 
Bus 004 Device 004: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 005 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
nyx yak # cat /mnt/tmp/home/fog/lspci.txt 
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A)
00:0b.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (NB-SB link)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XT [Radeon HD 7790/8770 / R9 260 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 0002
02:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 12)
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4850]
04:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV770 HDMI Audio [Radeon HD 4850/4870]
05:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)



```

so I guess I'll look into changing the kernel. This may sound weird but I really have no idea how to do that for ubuntu, I've always just compiled kernels from source. 

On second thought, after looking at the Kernel/Upgrade  and Kernel/Compile wiki pages, I may just fdisk this ancient LTS version, don't care if Steam is supported on it or not it's like beating a dead horse.

Thanks for the assistance.

---

### Post by mörgæs on 2015-05-17
How does it work in a live boot of 15.04?

---

### Post by daktaklakpak5576 on 2015-05-17
> **mörgæs said:**
> How does it work in a live boot of 15.04?

just tried 14.04.2 Trusty Tahr with pretty much the same results except the mouse did work on the live dvd during the installation. The other issue, networking, is loading the driver r8169 just I believe not doing dhcp/route or something after it segfaults and reloads? 


```
May 17 05:35:45 unyx kernel: [    0.000000] Initializing cgroup subsys cpusetMay 17 05:35:45 unyx kernel: [    0.000000] Initializing cgroup subsys cpu
May 17 05:35:45 unyx kernel: [    0.000000] Initializing cgroup subsys cpuacct
May 17 05:35:45 unyx kernel: [    0.000000] Linux version 3.16.0-30-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 (Ubuntu 3.16.0-30.40~14.04.1-generic 3.16.7-ckt3)
May 17 05:35:45 unyx kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.16.0-30-generic root=UUID=dc541c6f-6555-44f0-aec3-ac78802a78ec ro quiet splash vt.handoff=7
May 17 05:35:45 unyx kernel: [    0.000000] KERNEL supported cpus:
May 17 05:35:45 unyx kernel: [    0.000000]   Intel GenuineIntel
May 17 05:35:45 unyx kernel: [    0.000000]   AMD AuthenticAMD
May 17 05:35:45 unyx kernel: [    0.000000]   Centaur CentaurHauls
May 17 05:35:45 unyx kernel: [    0.000000] e820: BIOS-provided physical RAM map:
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009e860fff] usable
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x000000009e861000-0x000000009ea38fff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x000000009ea39000-0x000000009ea42fff] ACPI data
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x000000009ea43000-0x000000009ee32fff] ACPI NVS
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x000000009ee33000-0x000000009f159fff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x000000009f15a000-0x000000009f15afff] usable
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x000000009f15b000-0x000000009f360fff] ACPI NVS
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x000000009f361000-0x000000009f7fffff] usable
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
May 17 05:35:45 unyx kernel: [    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000045effffff] usable
May 17 05:35:45 unyx kernel: [    0.000000] NX (Execute Disable) protection: active
May 17 05:35:45 unyx kernel: [    0.000000] SMBIOS 2.7 present.
May 17 05:35:45 unyx kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. To be filled by O.E.M./990FXA-UD3, BIOS F2 07/15/2013
May 17 05:35:45 unyx kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
May 17 05:35:45 unyx kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
May 17 05:35:45 unyx kernel: [    0.000000] AGP: No AGP bridge found
May 17 05:35:45 unyx kernel: [    0.000000] e820: last_pfn = 0x45f000 max_arch_pfn = 0x400000000
May 17 05:35:45 unyx kernel: [    0.000000] MTRR default type: uncachable
May 17 05:35:45 unyx kernel: [    0.000000] MTRR fixed ranges enabled:
May 17 05:35:45 unyx kernel: [    0.000000]   00000-9FFFF write-back
May 17 05:35:45 unyx kernel: [    0.000000]   A0000-BFFFF write-through
May 17 05:35:45 unyx kernel: [    0.000000]   C0000-CFFFF write-protect
May 17 05:35:45 unyx kernel: [    0.000000]   D0000-EBFFF uncachable
May 17 05:35:45 unyx kernel: [    0.000000]   EC000-FFFFF write-protect
May 17 05:35:45 unyx kernel: [    0.000000] MTRR variable ranges enabled:
May 17 05:35:45 unyx kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
May 17 05:35:45 unyx kernel: [    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
May 17 05:35:45 unyx kernel: [    0.000000]   2 base 00009F800000 mask FFFFFF800000 uncachable
May 17 05:35:45 unyx kernel: [    0.000000]   3 disabled
May 17 05:35:45 unyx kernel: [    0.000000]   4 disabled
May 17 05:35:45 unyx kernel: [    0.000000]   5 disabled
May 17 05:35:45 unyx kernel: [    0.000000]   6 disabled
May 17 05:35:45 unyx kernel: [    0.000000]   7 disabled
May 17 05:35:45 unyx kernel: [    0.000000] TOM2: 000000045f000000 aka 17904M
May 17 05:35:45 unyx kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May 17 05:35:45 unyx kernel: [    0.000000] original variable MTRRs
May 17 05:35:45 unyx kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
May 17 05:35:45 unyx kernel: [    0.000000] reg 1, base: 2GB, range: 512MB, type WB
May 17 05:35:45 unyx kernel: [    0.000000] reg 2, base: 2552MB, range: 8MB, type UC
May 17 05:35:45 unyx kernel: [    0.000000] total RAM covered: 2552M
May 17 05:35:45 unyx kernel: [    0.000000] Found optimal setting for mtrr clean up
May 17 05:35:45 unyx kernel: [    0.000000]  gran_size: 64K     chunk_size: 16M num_reg: 3      lose cover RAM: 0G
May 17 05:35:45 unyx kernel: [    0.000000] New variable MTRRs
May 17 05:35:45 unyx kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
May 17 05:35:45 unyx kernel: [    0.000000] reg 1, base: 2GB, range: 512MB, type WB
May 17 05:35:45 unyx kernel: [    0.000000] reg 2, base: 2552MB, range: 8MB, type UC
May 17 05:35:45 unyx kernel: [    0.000000] e820: update [mem 0x9f800000-0xffffffff] usable ==> reserved
May 17 05:35:45 unyx kernel: [    0.000000] e820: last_pfn = 0x9f800 max_arch_pfn = 0x400000000
May 17 05:35:45 unyx kernel: [    0.000000] found SMP MP-table at [mem 0x000fd880-0x000fd88f] mapped at [ffff8800000fd880]
May 17 05:35:45 unyx kernel: [    0.000000] Scanning 1 areas for low memory corruption
May 17 05:35:45 unyx kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
May 17 05:35:45 unyx kernel: [    0.000000] Using GB pages for direct mapping
May 17 05:35:45 unyx kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
May 17 05:35:45 unyx kernel: [    0.000000] BRK [0x01fbe000, 0x01fbefff] PGTABLE
May 17 05:35:45 unyx kernel: [    0.000000] BRK [0x01fbf000, 0x01fbffff] PGTABLE
May 17 05:35:45 unyx kernel: [    0.000000] BRK [0x01fc0000, 0x01fc0fff] PGTABLE
May 17 05:35:45 unyx kernel: [    0.000000] init_memory_mapping: [mem 0x45ee00000-0x45effffff]
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x45ee00000-0x45effffff] page 2M
May 17 05:35:45 unyx kernel: [    0.000000] BRK [0x01fc1000, 0x01fc1fff] PGTABLE
May 17 05:35:45 unyx kernel: [    0.000000] init_memory_mapping: [mem 0x45c000000-0x45edfffff]
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x45c000000-0x45edfffff] page 2M
May 17 05:35:45 unyx kernel: [    0.000000] init_memory_mapping: [mem 0x400000000-0x45bffffff]
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x400000000-0x43fffffff] page 1G
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x440000000-0x45bffffff] page 2M
May 17 05:35:45 unyx kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x9e860fff]
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x80000000-0x9e7fffff] page 2M
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x9e800000-0x9e860fff] page 4k
May 17 05:35:45 unyx kernel: [    0.000000] init_memory_mapping: [mem 0x9f15a000-0x9f15afff]
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x9f15a000-0x9f15afff] page 4k
May 17 05:35:45 unyx kernel: [    0.000000] BRK [0x01fc2000, 0x01fc2fff] PGTABLE
May 17 05:35:45 unyx kernel: [    0.000000] init_memory_mapping: [mem 0x9f361000-0x9f7fffff]
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x9f361000-0x9f3fffff] page 4k
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x9f400000-0x9f7fffff] page 2M
May 17 05:35:45 unyx kernel: [    0.000000] BRK [0x01fc3000, 0x01fc3fff] PGTABLE
May 17 05:35:45 unyx kernel: [    0.000000] init_memory_mapping: [mem 0x100001000-0x3ffffffff]
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x100001000-0x1001fffff] page 4k
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x100200000-0x13fffffff] page 2M
May 17 05:35:45 unyx kernel: [    0.000000]  [mem 0x140000000-0x3ffffffff] page 1G
May 17 05:35:45 unyx kernel: [    0.000000] RAMDISK: [mem 0x35adc000-0x36d65fff]
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: Early table checksum verification disabled
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: RSDP 0x00000000000F0490 000024 (v02 ALASKA)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: XSDT 0x000000009EA3B068 000054 (v01 ALASKA A M I    01072009 AMI  00010013)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: FACP 0x000000009EA40D18 0000F4 (v04 ALASKA A M I    01072009 AMI  00010013)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20140424/tbfadt-649)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: DSDT 0x000000009EA3B150 005BC1 (v02 ALASKA A M I    00000000 INTL 20051117)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: FACS 0x000000009EE2DF80 000040
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: APIC 0x000000009EA40E10 00009E (v03 ALASKA A M I    01072009 AMI  00010013)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: FPDT 0x000000009EA40EB0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: MCFG 0x000000009EA40EF8 00003C (v01 ALASKA A M I    01072009 MSFT 00010013)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: HPET 0x000000009EA40F38 000038 (v01 ALASKA A M I    01072009 AMI  00000005)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: SSDT 0x000000009EA40F70 001714 (v01 AMD    POWERNOW 00000001 AMD  00000001)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 17 05:35:45 unyx kernel: [    0.000000] No NUMA configuration found
May 17 05:35:45 unyx kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000045effffff]
May 17 05:35:45 unyx kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x45effffff]
May 17 05:35:45 unyx kernel: [    0.000000]   NODE_DATA [mem 0x45eff7000-0x45effbfff]
May 17 05:35:45 unyx kernel: [    0.000000]  [ffffea0000000000-ffffea00117fffff] PMD -> [ffff88044e600000-ffff88045e5fffff] on node 0
May 17 05:35:45 unyx kernel: [    0.000000] Zone ranges:
May 17 05:35:45 unyx kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
May 17 05:35:45 unyx kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
May 17 05:35:45 unyx kernel: [    0.000000]   Normal   [mem 0x100000000-0x45effffff]
May 17 05:35:45 unyx kernel: [    0.000000] Movable zone start for each node
May 17 05:35:45 unyx kernel: [    0.000000] Early memory node ranges
May 17 05:35:45 unyx kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
May 17 05:35:45 unyx kernel: [    0.000000]   node   0: [mem 0x00100000-0x9e860fff]
May 17 05:35:45 unyx kernel: [    0.000000]   node   0: [mem 0x9f15a000-0x9f15afff]
May 17 05:35:45 unyx kernel: [    0.000000]   node   0: [mem 0x9f361000-0x9f7fffff]
May 17 05:35:45 unyx kernel: [    0.000000]   node   0: [mem 0x100001000-0x45effffff]
May 17 05:35:45 unyx kernel: [    0.000000] On node 0 totalpages: 4185245
May 17 05:35:45 unyx kernel: [    0.000000]   DMA zone: 64 pages used for memmap
May 17 05:35:45 unyx kernel: [    0.000000]   DMA zone: 21 pages reserved
May 17 05:35:45 unyx kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
May 17 05:35:45 unyx kernel: [    0.000000]   DMA32 zone: 10101 pages used for memmap
May 17 05:35:45 unyx kernel: [    0.000000]   DMA32 zone: 646401 pages, LIFO batch:31
May 17 05:35:45 unyx kernel: [    0.000000]   Normal zone: 55232 pages used for memmap
May 17 05:35:45 unyx kernel: [    0.000000]   Normal zone: 3534847 pages, LIFO batch:31
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x16] enabled)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x17] enabled)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec00000] gsi_base[0])
May 17 05:35:45 unyx kernel: [    0.000000] IOAPIC[0]: apic_id 9, version 33, address 0xfec00000, GSI 0-23
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec20000] gsi_base[24])
May 17 05:35:45 unyx kernel: [    0.000000] IOAPIC[1]: apic_id 10, version 33, address 0xfec20000, GSI 24-55
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: IRQ0 used by override.
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: IRQ2 used by override.
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: IRQ9 used by override.
May 17 05:35:45 unyx kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 17 05:35:45 unyx kernel: [    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
May 17 05:35:45 unyx kernel: [    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
May 17 05:35:45 unyx kernel: [    0.000000] nr_irqs_gsi: 72
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e861000-0x9ea38fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9ea39000-0x9ea42fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9ea43000-0x9ee32fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9ee33000-0x9f159fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f15b000-0x9f360fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xf7ffffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfec1ffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec20000-0xfec20fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec21000-0xfecfffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed60fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed61000-0xfed70fff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed71000-0xfed7ffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeefffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffffffff]
May 17 05:35:45 unyx kernel: [    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
May 17 05:35:45 unyx kernel: [    0.000000] e820: [mem 0x9f800000-0xf7ffffff] available for PCI devices
May 17 05:35:45 unyx kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May 17 05:35:45 unyx kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
May 17 05:35:45 unyx kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88045ec00000 s82304 r8192 d24192 u262144
May 17 05:35:45 unyx kernel: [    0.000000] pcpu-alloc: s82304 r8192 d24192 u262144 alloc=1*2097152
May 17 05:35:45 unyx kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
May 17 05:35:45 unyx kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4119827
May 17 05:35:45 unyx kernel: [    0.000000] Policy zone: Normal
May 17 05:35:45 unyx kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-30-generic root=UUID=dc541c6f-6555-44f0-aec3-ac78802a78ec ro quiet splash vt.handoff=7
May 17 05:35:45 unyx kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May 17 05:35:45 unyx kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
May 17 05:35:45 unyx kernel: [    0.000000] AGP: Checking aperture...
May 17 05:35:45 unyx kernel: [    0.000000] AGP: No AGP bridge found
May 17 05:35:45 unyx kernel: [    0.000000] AGP: Node 0: aperture [bus addr 0xf8000000-0xfbffffff] (64MB)
May 17 05:35:45 unyx kernel: [    0.000000] Memory: 16376384K/16740980K available (7615K kernel code, 1131K rwdata, 3596K rodata, 1356K init, 1300K bss, 364596K reserved)
May 17 05:35:45 unyx kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
May 17 05:35:45 unyx kernel: [    0.000000] Hierarchical RCU implementation.
May 17 05:35:45 unyx kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
May 17 05:35:45 unyx kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
May 17 05:35:45 unyx kernel: [    0.000000]     Offload RCU callbacks from all CPUs
May 17 05:35:45 unyx kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-7.
May 17 05:35:45 unyx kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
May 17 05:35:45 unyx kernel: [    0.000000] NR_IRQS:16640 nr_irqs:1288 16
May 17 05:35:45 unyx kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
May 17 05:35:45 unyx kernel: [    0.000000] vt handoff: transparent VT on vt#7
May 17 05:35:45 unyx kernel: [    0.000000] Console: colour dummy device 80x25
May 17 05:35:45 unyx kernel: [    0.000000] console [tty0] enabled
May 17 05:35:45 unyx kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
May 17 05:35:45 unyx kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May 17 05:35:45 unyx kernel: [    0.000000] hpet clockevent registered
May 17 05:35:45 unyx kernel: [    0.000000] tsc: Fast TSC calibration using PIT
May 17 05:35:45 unyx kernel: [    0.000000] tsc: Detected 4018.342 MHz processor
May 17 05:35:45 unyx kernel: [    0.000022] Calibrating delay loop (skipped), value calculated using timer frequency.. 8036.68 BogoMIPS (lpj=16073368)
May 17 05:35:45 unyx kernel: [    0.000024] pid_max: default: 32768 minimum: 301
May 17 05:35:45 unyx kernel: [    0.000031] ACPI: Core revision 20140424
May 17 05:35:45 unyx kernel: [    0.002620] ACPI: All ACPI Tables successfully acquired
May 17 05:35:45 unyx kernel: [    0.004529] Security Framework initialized
May 17 05:35:45 unyx kernel: [    0.004548] AppArmor: AppArmor initialized
May 17 05:35:45 unyx kernel: [    0.004549] Yama: becoming mindful.
May 17 05:35:45 unyx kernel: [    0.005523] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
May 17 05:35:45 unyx kernel: [    0.008965] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
May 17 05:35:45 unyx kernel: [    0.010525] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
May 17 05:35:45 unyx kernel: [    0.010542] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
May 17 05:35:45 unyx kernel: [    0.010797] Initializing cgroup subsys memory
May 17 05:35:45 unyx kernel: [    0.010816] Initializing cgroup subsys devices
May 17 05:35:45 unyx kernel: [    0.010821] Initializing cgroup subsys freezer
May 17 05:35:45 unyx kernel: [    0.010824] Initializing cgroup subsys net_cls
May 17 05:35:45 unyx kernel: [    0.010827] Initializing cgroup subsys blkio
May 17 05:35:45 unyx kernel: [    0.010830] Initializing cgroup subsys perf_event
May 17 05:35:45 unyx kernel: [    0.010832] Initializing cgroup subsys net_prio
May 17 05:35:45 unyx kernel: [    0.010837] Initializing cgroup subsys hugetlb
May 17 05:35:45 unyx kernel: [    0.010854] tseg: 009f800000
May 17 05:35:45 unyx kernel: [    0.010856] CPU: Physical Processor ID: 0
May 17 05:35:45 unyx kernel: [    0.010857] CPU: Processor Core ID: 0
May 17 05:35:45 unyx kernel: [    0.010858] mce: CPU supports 7 MCE banks
May 17 05:35:45 unyx kernel: [    0.010864] LVT offset 1 assigned for vector 0xf9
May 17 05:35:45 unyx kernel: [    0.010869] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
May 17 05:35:45 unyx kernel: [    0.010869] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512, 1GB 0
May 17 05:35:45 unyx kernel: [    0.010869] tlb_flushall_shift: 6
May 17 05:35:45 unyx kernel: [    0.010948] Freeing SMP alternatives memory: 32K (ffffffff81e6f000 - ffffffff81e77000)
May 17 05:35:45 unyx kernel: [    0.011621] ftrace: allocating 29209 entries in 115 pages
May 17 05:35:45 unyx kernel: [    0.019836] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May 17 05:35:45 unyx kernel: [    0.059548] smpboot: CPU0: AMD FX(tm)-8350 Eight-Core Processor (fam: 15, model: 02, stepping: 00)
May 17 05:35:45 unyx kernel: [    0.164218] Performance Events: Fam15h core perfctr, AMD PMU driver.
May 17 05:35:45 unyx kernel: [    0.164223] ... version:                0
May 17 05:35:45 unyx kernel: [    0.164224] ... bit width:              48
May 17 05:35:45 unyx kernel: [    0.164224] ... generic registers:      6
May 17 05:35:45 unyx kernel: [    0.164225] ... value mask:             0000ffffffffffff
May 17 05:35:45 unyx kernel: [    0.164226] ... max period:             00007fffffffffff
May 17 05:35:45 unyx kernel: [    0.164227] ... fixed-purpose events:   0
May 17 05:35:45 unyx kernel: [    0.164228] ... event mask:             000000000000003f
May 17 05:35:45 unyx kernel: [    0.165737] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
May 17 05:35:45 unyx kernel: [    0.165801] x86: Booting SMP configuration:
May 17 05:35:45 unyx kernel: [    0.165803] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
May 17 05:35:45 unyx kernel: [    0.257873] x86: Booted up 1 node, 8 CPUs
May 17 05:35:45 unyx kernel: [    0.257876] smpboot: Total of 8 processors activated (64293.47 BogoMIPS)
May 17 05:35:45 unyx kernel: [    0.267047] devtmpfs: initialized
May 17 05:35:45 unyx kernel: [    0.271344] evm: security.selinux
May 17 05:35:45 unyx kernel: [    0.271346] evm: security.SMACK64
May 17 05:35:45 unyx kernel: [    0.271347] evm: security.SMACK64EXEC
May 17 05:35:45 unyx kernel: [    0.271348] evm: security.SMACK64TRANSMUTE
May 17 05:35:45 unyx kernel: [    0.271348] evm: security.SMACK64MMAP
May 17 05:35:45 unyx kernel: [    0.271349] evm: security.ima
May 17 05:35:45 unyx kernel: [    0.271350] evm: security.capability
May 17 05:35:45 unyx kernel: [    0.271419] PM: Registering ACPI NVS region [mem 0x9ea43000-0x9ee32fff] (4128768 bytes)
May 17 05:35:45 unyx kernel: [    0.271479] PM: Registering ACPI NVS region [mem 0x9f15b000-0x9f360fff] (2121728 bytes)
May 17 05:35:45 unyx kernel: [    0.272296] pinctrl core: initialized pinctrl subsystem
May 17 05:35:45 unyx kernel: [    0.272362] regulator-dummy: no parameters
May 17 05:35:45 unyx kernel: [    0.272387] RTC time:  9:35:42, date: 05/17/15
May 17 05:35:45 unyx kernel: [    0.272433] NET: Registered protocol family 16
May 17 05:35:45 unyx kernel: [    0.272578] cpuidle: using governor ladder
May 17 05:35:45 unyx kernel: [    0.272580] cpuidle: using governor menu
May 17 05:35:45 unyx kernel: [    0.272653] ACPI: bus type PCI registered
May 17 05:35:45 unyx kernel: [    0.272655] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
May 17 05:35:45 unyx kernel: [    0.272721] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
May 17 05:35:45 unyx kernel: [    0.272723] PCI: not using MMCONFIG
May 17 05:35:45 unyx kernel: [    0.272724] PCI: Using configuration type 1 for base access
May 17 05:35:45 unyx kernel: [    0.272725] PCI: Using configuration type 1 for extended access
May 17 05:35:45 unyx kernel: [    0.276785] ACPI: Added _OSI(Module Device)
May 17 05:35:45 unyx kernel: [    0.276787] ACPI: Added _OSI(Processor Device)
May 17 05:35:45 unyx kernel: [    0.276788] ACPI: Added _OSI(3.0 _SCP Extensions)
May 17 05:35:45 unyx kernel: [    0.276790] ACPI: Added _OSI(Processor Aggregator Device)
May 17 05:35:45 unyx kernel: [    0.278922] ACPI: Executed 3 blocks of module-level executable AML code
May 17 05:35:45 unyx kernel: [    0.284738] ACPI: Interpreter enabled
May 17 05:35:45 unyx kernel: [    0.284743] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
May 17 05:35:45 unyx kernel: [    0.284746] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
May 17 05:35:45 unyx kernel: [    0.284760] ACPI: (supports S0 S3 S4 S5)
May 17 05:35:45 unyx kernel: [    0.284761] ACPI: Using IOAPIC for interrupt routing
May 17 05:35:45 unyx kernel: [    0.284887] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
May 17 05:35:45 unyx kernel: [    0.284925] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
May 17 05:35:45 unyx kernel: [    0.285211] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
May 17 05:35:45 unyx kernel: [    0.323107] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
May 17 05:35:45 unyx kernel: [    0.323112] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
May 17 05:35:45 unyx kernel: [    0.323116] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
May 17 05:35:45 unyx kernel: [    0.323553] PCI host bridge to bus 0000:00
May 17 05:35:45 unyx kernel: [    0.323556] pci_bus 0000:00: root bus resource [bus 00-ff]
May 17 05:35:45 unyx kernel: [    0.323558] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
May 17 05:35:45 unyx kernel: [    0.323559] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
May 17 05:35:45 unyx kernel: [    0.323561] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
May 17 05:35:45 unyx kernel: [    0.323562] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
May 17 05:35:45 unyx kernel: [    0.323563] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
May 17 05:35:45 unyx kernel: [    0.323565] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
May 17 05:35:45 unyx kernel: [    0.323566] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xffffffff]
May 17 05:35:45 unyx kernel: [    0.323576] pci 0000:00:00.0: [1002:5a14] type 00 class 0x060000
May 17 05:35:45 unyx kernel: [    0.323697] pci 0000:00:02.0: [1002:5a16] type 01 class 0x060400
May 17 05:35:45 unyx kernel: [    0.323730] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
May 17 05:35:45 unyx kernel: [    0.323778] pci 0000:00:02.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.323818] pci 0000:00:09.0: [1002:5a1c] type 01 class 0x060400
May 17 05:35:45 unyx kernel: [    0.323850] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
May 17 05:35:45 unyx kernel: [    0.323897] pci 0000:00:09.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.323932] pci 0000:00:0a.0: [1002:5a1d] type 01 class 0x060400
May 17 05:35:45 unyx kernel: [    0.323963] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
May 17 05:35:45 unyx kernel: [    0.324011] pci 0000:00:0a.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.324045] pci 0000:00:0b.0: [1002:5a1f] type 01 class 0x060400
May 17 05:35:45 unyx kernel: [    0.324077] pci 0000:00:0b.0: PME# supported from D0 D3hot D3cold
May 17 05:35:45 unyx kernel: [    0.324124] pci 0000:00:0b.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.324166] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
May 17 05:35:45 unyx kernel: [    0.324181] pci 0000:00:11.0: reg 0x10: [io  0xf040-0xf047]
May 17 05:35:45 unyx kernel: [    0.324188] pci 0000:00:11.0: reg 0x14: [io  0xf030-0xf033]
May 17 05:35:45 unyx kernel: [    0.324195] pci 0000:00:11.0: reg 0x18: [io  0xf020-0xf027]
May 17 05:35:45 unyx kernel: [    0.324202] pci 0000:00:11.0: reg 0x1c: [io  0xf010-0xf013]
May 17 05:35:45 unyx kernel: [    0.324210] pci 0000:00:11.0: reg 0x20: [io  0xf000-0xf00f]
May 17 05:35:45 unyx kernel: [    0.324217] pci 0000:00:11.0: reg 0x24: [mem 0xfeb0b000-0xfeb0b3ff]
May 17 05:35:45 unyx kernel: [    0.324325] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
May 17 05:35:45 unyx kernel: [    0.324335] pci 0000:00:12.0: reg 0x10: [mem 0xfeb0a000-0xfeb0afff]
May 17 05:35:45 unyx kernel: [    0.324418] pci 0000:00:12.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.324458] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
May 17 05:35:45 unyx kernel: [    0.324474] pci 0000:00:12.2: reg 0x10: [mem 0xfeb09000-0xfeb090ff]
May 17 05:35:45 unyx kernel: [    0.324536] pci 0000:00:12.2: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.324537] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
May 17 05:35:45 unyx kernel: [    0.324585] pci 0000:00:12.2: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.324623] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
May 17 05:35:45 unyx kernel: [    0.324633] pci 0000:00:13.0: reg 0x10: [mem 0xfeb08000-0xfeb08fff]
May 17 05:35:45 unyx kernel: [    0.324716] pci 0000:00:13.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.324755] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
May 17 05:35:45 unyx kernel: [    0.324769] pci 0000:00:13.2: reg 0x10: [mem 0xfeb07000-0xfeb070ff]
May 17 05:35:45 unyx kernel: [    0.324830] pci 0000:00:13.2: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.324831] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
May 17 05:35:45 unyx kernel: [    0.324880] pci 0000:00:13.2: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.324921] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
May 17 05:35:45 unyx kernel: [    0.325040] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
May 17 05:35:45 unyx kernel: [    0.325056] pci 0000:00:14.2: reg 0x10: [mem 0xfeb00000-0xfeb03fff 64bit]
May 17 05:35:45 unyx kernel: [    0.325105] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
May 17 05:35:45 unyx kernel: [    0.325152] pci 0000:00:14.2: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.325186] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
May 17 05:35:45 unyx kernel: [    0.325305] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
May 17 05:35:45 unyx kernel: [    0.325372] pci 0000:00:14.4: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.325409] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
May 17 05:35:45 unyx kernel: [    0.325419] pci 0000:00:14.5: reg 0x10: [mem 0xfeb06000-0xfeb06fff]
May 17 05:35:45 unyx kernel: [    0.325503] pci 0000:00:14.5: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.325543] pci 0000:00:15.0: [1002:43a0] type 01 class 0x060400
May 17 05:35:45 unyx kernel: [    0.325600] pci 0000:00:15.0: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.325651] pci 0000:00:15.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.325692] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
May 17 05:35:45 unyx kernel: [    0.325702] pci 0000:00:16.0: reg 0x10: [mem 0xfeb05000-0xfeb05fff]
May 17 05:35:45 unyx kernel: [    0.325786] pci 0000:00:16.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.325825] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
May 17 05:35:45 unyx kernel: [    0.325839] pci 0000:00:16.2: reg 0x10: [mem 0xfeb04000-0xfeb040ff]
May 17 05:35:45 unyx kernel: [    0.325901] pci 0000:00:16.2: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.325902] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
May 17 05:35:45 unyx kernel: [    0.325951] pci 0000:00:16.2: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.325990] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
May 17 05:35:45 unyx kernel: [    0.326067] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
May 17 05:35:45 unyx kernel: [    0.326140] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
May 17 05:35:45 unyx kernel: [    0.326214] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
May 17 05:35:45 unyx kernel: [    0.326291] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
May 17 05:35:45 unyx kernel: [    0.326364] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
May 17 05:35:45 unyx kernel: [    0.326486] pci 0000:01:00.0: [1002:665c] type 00 class 0x030000
May 17 05:35:45 unyx kernel: [    0.326500] pci 0000:01:00.0: reg 0x10: [mem 0xa0000000-0xafffffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.326510] pci 0000:01:00.0: reg 0x18: [mem 0xb0000000-0xb07fffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.326517] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
May 17 05:35:45 unyx kernel: [    0.326524] pci 0000:01:00.0: reg 0x24: [mem 0xfea00000-0xfea3ffff]
May 17 05:35:45 unyx kernel: [    0.326531] pci 0000:01:00.0: reg 0x30: [mem 0xfea40000-0xfea5ffff pref]
May 17 05:35:45 unyx kernel: [    0.326581] pci 0000:01:00.0: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.326582] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
May 17 05:35:45 unyx kernel: [    0.326644] pci 0000:01:00.1: [1002:0002] type 00 class 0x040300
May 17 05:35:45 unyx kernel: [    0.326663] pci 0000:01:00.1: reg 0x10: [mem 0xfea60000-0xfea63fff 64bit]
May 17 05:35:45 unyx kernel: [    0.326731] pci 0000:01:00.1: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.332359] pci 0000:00:02.0: PCI bridge to [bus 01]
May 17 05:35:45 unyx kernel: [    0.332363] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
May 17 05:35:45 unyx kernel: [    0.332365] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
May 17 05:35:45 unyx kernel: [    0.332368] pci 0000:00:02.0:   bridge window [mem 0xa0000000-0xb07fffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.332413] pci 0000:02:00.0: [1106:3483] type 00 class 0x0c0330
May 17 05:35:45 unyx kernel: [    0.332425] pci 0000:02:00.0: reg 0x10: [mem 0xfe900000-0xfe900fff 64bit]
May 17 05:35:45 unyx kernel: [    0.332478] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May 17 05:35:45 unyx kernel: [    0.340357] pci 0000:00:09.0: PCI bridge to [bus 02]
May 17 05:35:45 unyx kernel: [    0.340361] pci 0000:00:09.0:   bridge window [mem 0xfe900000-0xfe9fffff]
May 17 05:35:45 unyx kernel: [    0.340409] pci 0000:03:00.0: [1b4b:9172] type 00 class 0x010601
May 17 05:35:45 unyx kernel: [    0.340419] pci 0000:03:00.0: reg 0x10: [io  0xd040-0xd047]
May 17 05:35:45 unyx kernel: [    0.340425] pci 0000:03:00.0: reg 0x14: [io  0xd030-0xd033]
May 17 05:35:45 unyx kernel: [    0.340432] pci 0000:03:00.0: reg 0x18: [io  0xd020-0xd027]
May 17 05:35:45 unyx kernel: [    0.340438] pci 0000:03:00.0: reg 0x1c: [io  0xd010-0xd013]
May 17 05:35:45 unyx kernel: [    0.340444] pci 0000:03:00.0: reg 0x20: [io  0xd000-0xd00f]
May 17 05:35:45 unyx kernel: [    0.340450] pci 0000:03:00.0: reg 0x24: [mem 0xfe810000-0xfe8101ff]
May 17 05:35:45 unyx kernel: [    0.340457] pci 0000:03:00.0: reg 0x30: [mem 0xfe800000-0xfe80ffff pref]
May 17 05:35:45 unyx kernel: [    0.340486] pci 0000:03:00.0: PME# supported from D3hot
May 17 05:35:45 unyx kernel: [    0.348363] pci 0000:00:0a.0: PCI bridge to [bus 03]
May 17 05:35:45 unyx kernel: [    0.348366] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
May 17 05:35:45 unyx kernel: [    0.348368] pci 0000:00:0a.0:   bridge window [mem 0xfe800000-0xfe8fffff]
May 17 05:35:45 unyx kernel: [    0.348417] pci 0000:04:00.0: [1002:9442] type 00 class 0x030000
May 17 05:35:45 unyx kernel: [    0.348431] pci 0000:04:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.348440] pci 0000:04:00.0: reg 0x18: [mem 0xfe720000-0xfe72ffff 64bit]
May 17 05:35:45 unyx kernel: [    0.348446] pci 0000:04:00.0: reg 0x20: [io  0xc000-0xc0ff]
May 17 05:35:45 unyx kernel: [    0.348455] pci 0000:04:00.0: reg 0x30: [mem 0xfe700000-0xfe71ffff pref]
May 17 05:35:45 unyx kernel: [    0.348491] pci 0000:04:00.0: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.348538] pci 0000:04:00.1: [1002:aa30] type 00 class 0x040300
May 17 05:35:45 unyx kernel: [    0.348553] pci 0000:04:00.1: reg 0x10: [mem 0xfe730000-0xfe733fff 64bit]
May 17 05:35:45 unyx kernel: [    0.348618] pci 0000:04:00.1: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.356369] pci 0000:00:0b.0: PCI bridge to [bus 04]
May 17 05:35:45 unyx kernel: [    0.356372] pci 0000:00:0b.0:   bridge window [io  0xc000-0xcfff]
May 17 05:35:45 unyx kernel: [    0.356375] pci 0000:00:0b.0:   bridge window [mem 0xfe700000-0xfe7fffff]
May 17 05:35:45 unyx kernel: [    0.356378] pci 0000:00:0b.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.356431] pci 0000:05:0e.0: [1106:3044] type 00 class 0x0c0010
May 17 05:35:45 unyx kernel: [    0.356450] pci 0000:05:0e.0: reg 0x10: [mem 0xfe600000-0xfe6007ff]
May 17 05:35:45 unyx kernel: [    0.356460] pci 0000:05:0e.0: reg 0x14: [io  0xb000-0xb07f]
May 17 05:35:45 unyx kernel: [    0.356561] pci 0000:05:0e.0: supports D2
May 17 05:35:45 unyx kernel: [    0.356563] pci 0000:05:0e.0: PME# supported from D2 D3hot D3cold
May 17 05:35:45 unyx kernel: [    0.356625] pci 0000:00:14.4: PCI bridge to [bus 05] (subtractive decode)
May 17 05:35:45 unyx kernel: [    0.356629] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
May 17 05:35:45 unyx kernel: [    0.356632] pci 0000:00:14.4:   bridge window [mem 0xfe600000-0xfe6fffff]
May 17 05:35:45 unyx kernel: [    0.356635] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
May 17 05:35:45 unyx kernel: [    0.356636] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
May 17 05:35:45 unyx kernel: [    0.356638] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
May 17 05:35:45 unyx kernel: [    0.356639] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May 17 05:35:45 unyx kernel: [    0.356640] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May 17 05:35:45 unyx kernel: [    0.356642] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
May 17 05:35:45 unyx kernel: [    0.356643] pci 0000:00:14.4:   bridge window [mem 0xa0000000-0xffffffff] (subtractive decode)
May 17 05:35:45 unyx kernel: [    0.356714] pci 0000:06:00.0: [10ec:8168] type 00 class 0x020000
May 17 05:35:45 unyx kernel: [    0.356732] pci 0000:06:00.0: reg 0x10: [io  0xa000-0xa0ff]
May 17 05:35:45 unyx kernel: [    0.356757] pci 0000:06:00.0: reg 0x18: [mem 0xfe500000-0xfe500fff 64bit]
May 17 05:35:45 unyx kernel: [    0.356773] pci 0000:06:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.356856] pci 0000:06:00.0: supports D1 D2
May 17 05:35:45 unyx kernel: [    0.356857] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May 17 05:35:45 unyx kernel: [    0.356887] pci 0000:06:00.0: System wakeup disabled by ACPI
May 17 05:35:45 unyx kernel: [    0.364378] pci 0000:00:15.0: PCI bridge to [bus 06]
May 17 05:35:45 unyx kernel: [    0.364383] pci 0000:00:15.0:   bridge window [io  0xa000-0xafff]
May 17 05:35:45 unyx kernel: [    0.364386] pci 0000:00:15.0:   bridge window [mem 0xfe500000-0xfe5fffff]
May 17 05:35:45 unyx kernel: [    0.364390] pci 0000:00:15.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.364414] pci_bus 0000:00: on NUMA node 0
May 17 05:35:45 unyx kernel: [    0.364831] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
May 17 05:35:45 unyx kernel: [    0.364895] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
May 17 05:35:45 unyx kernel: [    0.364960] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
May 17 05:35:45 unyx kernel: [    0.365023] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
May 17 05:35:45 unyx kernel: [    0.365098] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 10 11 14 15) *0
May 17 05:35:45 unyx kernel: [    0.365139] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 10 11 14 15) *0
May 17 05:35:45 unyx kernel: [    0.365180] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 11 14 15) *0
May 17 05:35:45 unyx kernel: [    0.365220] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 10 11 14 15) *0
May 17 05:35:45 unyx kernel: [    0.365398] vgaarb: setting as boot device: PCI:0000:01:00.0
May 17 05:35:45 unyx kernel: [    0.365399] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
May 17 05:35:45 unyx kernel: [    0.365403] vgaarb: device added: PCI:0000:04:00.0,decodes=io+mem,owns=none,locks=none
May 17 05:35:45 unyx kernel: [    0.365404] vgaarb: loaded
May 17 05:35:45 unyx kernel: [    0.365405] vgaarb: bridge control possible 0000:04:00.0
May 17 05:35:45 unyx kernel: [    0.365406] vgaarb: bridge control possible 0000:01:00.0
May 17 05:35:45 unyx kernel: [    0.365632] SCSI subsystem initialized
May 17 05:35:45 unyx kernel: [    0.365681] libata version 3.00 loaded.
May 17 05:35:45 unyx kernel: [    0.365703] ACPI: bus type USB registered
May 17 05:35:45 unyx kernel: [    0.365721] usbcore: registered new interface driver usbfs
May 17 05:35:45 unyx kernel: [    0.365731] usbcore: registered new interface driver hub
May 17 05:35:45 unyx kernel: [    0.365752] usbcore: registered new device driver usb
May 17 05:35:45 unyx kernel: [    0.365893] PCI: Using ACPI for IRQ routing
May 17 05:35:45 unyx kernel: [    0.372173] PCI: pci_cache_line_size set to 64 bytes
May 17 05:35:45 unyx kernel: [    0.372230] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
May 17 05:35:45 unyx kernel: [    0.372232] e820: reserve RAM buffer [mem 0x9e861000-0x9fffffff]
May 17 05:35:45 unyx kernel: [    0.372233] e820: reserve RAM buffer [mem 0x9f15b000-0x9fffffff]
May 17 05:35:45 unyx kernel: [    0.372234] e820: reserve RAM buffer [mem 0x9f800000-0x9fffffff]
May 17 05:35:45 unyx kernel: [    0.372235] e820: reserve RAM buffer [mem 0x45f000000-0x45fffffff]
May 17 05:35:45 unyx kernel: [    0.372331] NetLabel: Initializing
May 17 05:35:45 unyx kernel: [    0.372332] NetLabel:  domain hash size = 128
May 17 05:35:45 unyx kernel: [    0.372333] NetLabel:  protocols = UNLABELED CIPSOv4
May 17 05:35:45 unyx kernel: [    0.372344] NetLabel:  unlabeled traffic allowed by default
May 17 05:35:45 unyx kernel: [    0.372403] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
May 17 05:35:45 unyx kernel: [    0.372406] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
May 17 05:35:45 unyx kernel: [    0.374479] Switched to clocksource hpet
May 17 05:35:45 unyx kernel: [    0.380964] AppArmor: AppArmor Filesystem Enabled
May 17 05:35:45 unyx kernel: [    0.380987] pnp: PnP ACPI init
May 17 05:35:45 unyx kernel: [    0.380998] ACPI: bus type PNP registered
May 17 05:35:45 unyx kernel: [    0.381087] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
May 17 05:35:45 unyx kernel: [    0.381090] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
May 17 05:35:45 unyx kernel: [    0.381361] system 00:01: [io  0x040b] has been reserved
May 17 05:35:45 unyx kernel: [    0.381363] system 00:01: [io  0x04d6] has been reserved
May 17 05:35:45 unyx kernel: [    0.381364] system 00:01: [io  0x0c00-0x0c01] has been reserved
May 17 05:35:45 unyx kernel: [    0.381366] system 00:01: [io  0x0c14] has been reserved
May 17 05:35:45 unyx kernel: [    0.381368] system 00:01: [io  0x0c50-0x0c51] has been reserved
May 17 05:35:45 unyx kernel: [    0.381371] system 00:01: [io  0x0c52] has been reserved
May 17 05:35:45 unyx kernel: [    0.381372] system 00:01: [io  0x0c6c] has been reserved
May 17 05:35:45 unyx kernel: [    0.381374] system 00:01: [io  0x0c6f] has been reserved
May 17 05:35:45 unyx kernel: [    0.381375] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
May 17 05:35:45 unyx kernel: [    0.381377] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
May 17 05:35:45 unyx kernel: [    0.381378] system 00:01: [io  0x0cd4-0x0cd5] has been reserved
May 17 05:35:45 unyx kernel: [    0.381380] system 00:01: [io  0x0cd6-0x0cd7] has been reserved
May 17 05:35:45 unyx kernel: [    0.381382] system 00:01: [io  0x0cd8-0x0cdf] has been reserved
May 17 05:35:45 unyx kernel: [    0.381383] system 00:01: [io  0x0800-0x089f] could not be reserved
May 17 05:35:45 unyx kernel: [    0.381385] system 00:01: [io  0x0b20-0x0b3f] has been reserved
May 17 05:35:45 unyx kernel: [    0.381386] system 00:01: [io  0x0900-0x090f] has been reserved
May 17 05:35:45 unyx kernel: [    0.381388] system 00:01: [io  0x0910-0x091f] has been reserved
May 17 05:35:45 unyx kernel: [    0.381390] system 00:01: [io  0xfe00-0xfefe] has been reserved
May 17 05:35:45 unyx kernel: [    0.381392] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
May 17 05:35:45 unyx kernel: [    0.381394] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
May 17 05:35:45 unyx kernel: [    0.381396] system 00:01: [mem 0xfed80000-0xfed8ffff] has been reserved
May 17 05:35:45 unyx kernel: [    0.381398] system 00:01: [mem 0xfed61000-0xfed70fff] has been reserved
May 17 05:35:45 unyx kernel: [    0.381399] system 00:01: [mem 0xfec10000-0xfec10fff] has been reserved
May 17 05:35:45 unyx kernel: [    0.381401] system 00:01: [mem 0xfed00000-0xfed00fff] could not be reserved
May 17 05:35:45 unyx kernel: [    0.381403] system 00:01: [mem 0xffc00000-0xffffffff] has been reserved
May 17 05:35:45 unyx kernel: [    0.381405] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
May 17 05:35:45 unyx kernel: [    0.381554] system 00:02: [io  0x0220-0x0227] has been reserved
May 17 05:35:45 unyx kernel: [    0.381555] system 00:02: [io  0x0228-0x0237] has been reserved
May 17 05:35:45 unyx kernel: [    0.381557] system 00:02: [io  0x0a20-0x0a2f] has been reserved
May 17 05:35:45 unyx kernel: [    0.381559] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
May 17 05:35:45 unyx kernel: [    0.381606] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
May 17 05:35:45 unyx kernel: [    0.381841] pnp 00:04: [dma 0 disabled]
May 17 05:35:45 unyx kernel: [    0.381885] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
May 17 05:35:45 unyx kernel: [    0.381913] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
May 17 05:35:45 unyx kernel: [    0.381973] system 00:06: [io  0x04d0-0x04d1] has been reserved
May 17 05:35:45 unyx kernel: [    0.381975] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
May 17 05:35:45 unyx kernel: [    0.382014] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
May 17 05:35:45 unyx kernel: [    0.382172] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
May 17 05:35:45 unyx kernel: [    0.382289] system 00:09: [mem 0xfec20000-0xfec200ff] could not be reserved
May 17 05:35:45 unyx kernel: [    0.382291] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
May 17 05:35:45 unyx kernel: [    0.382394] pnp: PnP ACPI: found 10 devices
May 17 05:35:45 unyx kernel: [    0.382395] ACPI: bus type PNP unregistered
May 17 05:35:45 unyx kernel: [    0.388941] pci 0000:00:02.0: PCI bridge to [bus 01]
May 17 05:35:45 unyx kernel: [    0.388943] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
May 17 05:35:45 unyx kernel: [    0.388946] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
May 17 05:35:45 unyx kernel: [    0.388949] pci 0000:00:02.0:   bridge window [mem 0xa0000000-0xb07fffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.388952] pci 0000:00:09.0: PCI bridge to [bus 02]
May 17 05:35:45 unyx kernel: [    0.388954] pci 0000:00:09.0:   bridge window [mem 0xfe900000-0xfe9fffff]
May 17 05:35:45 unyx kernel: [    0.388957] pci 0000:00:0a.0: PCI bridge to [bus 03]
May 17 05:35:45 unyx kernel: [    0.388959] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
May 17 05:35:45 unyx kernel: [    0.388962] pci 0000:00:0a.0:   bridge window [mem 0xfe800000-0xfe8fffff]
May 17 05:35:45 unyx kernel: [    0.388965] pci 0000:00:0b.0: PCI bridge to [bus 04]
May 17 05:35:45 unyx kernel: [    0.388967] pci 0000:00:0b.0:   bridge window [io  0xc000-0xcfff]
May 17 05:35:45 unyx kernel: [    0.388969] pci 0000:00:0b.0:   bridge window [mem 0xfe700000-0xfe7fffff]
May 17 05:35:45 unyx kernel: [    0.388971] pci 0000:00:0b.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.388974] pci 0000:00:14.4: PCI bridge to [bus 05]
May 17 05:35:45 unyx kernel: [    0.388976] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
May 17 05:35:45 unyx kernel: [    0.388980] pci 0000:00:14.4:   bridge window [mem 0xfe600000-0xfe6fffff]
May 17 05:35:45 unyx kernel: [    0.388986] pci 0000:00:15.0: PCI bridge to [bus 06]
May 17 05:35:45 unyx kernel: [    0.388988] pci 0000:00:15.0:   bridge window [io  0xa000-0xafff]
May 17 05:35:45 unyx kernel: [    0.388991] pci 0000:00:15.0:   bridge window [mem 0xfe500000-0xfe5fffff]
May 17 05:35:45 unyx kernel: [    0.388993] pci 0000:00:15.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.388998] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
May 17 05:35:45 unyx kernel: [    0.388999] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
May 17 05:35:45 unyx kernel: [    0.389001] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
May 17 05:35:45 unyx kernel: [    0.389002] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
May 17 05:35:45 unyx kernel: [    0.389003] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
May 17 05:35:45 unyx kernel: [    0.389005] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
May 17 05:35:45 unyx kernel: [    0.389006] pci_bus 0000:00: resource 10 [mem 0xa0000000-0xffffffff]
May 17 05:35:45 unyx kernel: [    0.389008] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
May 17 05:35:45 unyx kernel: [    0.389009] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
May 17 05:35:45 unyx kernel: [    0.389010] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xb07fffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.389012] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
May 17 05:35:45 unyx kernel: [    0.389013] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
May 17 05:35:45 unyx kernel: [    0.389015] pci_bus 0000:03: resource 1 [mem 0xfe800000-0xfe8fffff]
May 17 05:35:45 unyx kernel: [    0.389016] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
May 17 05:35:45 unyx kernel: [    0.389017] pci_bus 0000:04: resource 1 [mem 0xfe700000-0xfe7fffff]
May 17 05:35:45 unyx kernel: [    0.389019] pci_bus 0000:04: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.389020] pci_bus 0000:05: resource 0 [io  0xb000-0xbfff]
May 17 05:35:45 unyx kernel: [    0.389021] pci_bus 0000:05: resource 1 [mem 0xfe600000-0xfe6fffff]
May 17 05:35:45 unyx kernel: [    0.389023] pci_bus 0000:05: resource 4 [io  0x0000-0x03af]
May 17 05:35:45 unyx kernel: [    0.389024] pci_bus 0000:05: resource 5 [io  0x03e0-0x0cf7]
May 17 05:35:45 unyx kernel: [    0.389025] pci_bus 0000:05: resource 6 [io  0x03b0-0x03df]
May 17 05:35:45 unyx kernel: [    0.389027] pci_bus 0000:05: resource 7 [io  0x0d00-0xffff]
May 17 05:35:45 unyx kernel: [    0.389028] pci_bus 0000:05: resource 8 [mem 0x000a0000-0x000bffff]
May 17 05:35:45 unyx kernel: [    0.389029] pci_bus 0000:05: resource 9 [mem 0x000c0000-0x000dffff]
May 17 05:35:45 unyx kernel: [    0.389031] pci_bus 0000:05: resource 10 [mem 0xa0000000-0xffffffff]
May 17 05:35:45 unyx kernel: [    0.389032] pci_bus 0000:06: resource 0 [io  0xa000-0xafff]
May 17 05:35:45 unyx kernel: [    0.389033] pci_bus 0000:06: resource 1 [mem 0xfe500000-0xfe5fffff]
May 17 05:35:45 unyx kernel: [    0.389035] pci_bus 0000:06: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
May 17 05:35:45 unyx kernel: [    0.389056] NET: Registered protocol family 2
May 17 05:35:45 unyx kernel: [    0.389276] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 17 05:35:45 unyx kernel: [    0.389538] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May 17 05:35:45 unyx kernel: [    0.389716] TCP: Hash tables configured (established 131072 bind 65536)
May 17 05:35:45 unyx kernel: [    0.389741] TCP: reno registered
May 17 05:35:45 unyx kernel: [    0.389760] UDP hash table entries: 8192 (order: 6, 262144 bytes)
May 17 05:35:45 unyx kernel: [    0.389822] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
May 17 05:35:45 unyx kernel: [    0.389910] NET: Registered protocol family 1
May 17 05:35:45 unyx kernel: [    0.714918] pci 0000:01:00.0: Video device with shadowed ROM
May 17 05:35:45 unyx kernel: [    0.715039] PCI: CLS 64 bytes, default 64
May 17 05:35:45 unyx kernel: [    0.715101] Trying to unpack rootfs image as initramfs...
May 17 05:35:45 unyx kernel: [    0.947603] Freeing initrd memory: 18984K (ffff880035adc000 - ffff880036d66000)
May 17 05:35:45 unyx kernel: [    0.947954] PCI-DMA: Disabling AGP.
May 17 05:35:45 unyx kernel: [    0.948023] PCI-DMA: aperture base @ f8000000 size 65536 KB
May 17 05:35:45 unyx kernel: [    0.948024] init_memory_mapping: [mem 0xf8000000-0xfbffffff]
May 17 05:35:45 unyx kernel: [    0.948026]  [mem 0xf8000000-0xfbffffff] page 2M
May 17 05:35:45 unyx kernel: [    0.948034] PCI-DMA: using GART IOMMU.
May 17 05:35:45 unyx kernel: [    0.948036] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
May 17 05:35:45 unyx kernel: [    0.951962] perf: AMD NB counters detected
May 17 05:35:45 unyx kernel: [    0.952024] microcode: CPU0: patch_level=0x06000822
May 17 05:35:45 unyx kernel: [    0.952030] microcode: CPU1: patch_level=0x06000822
May 17 05:35:45 unyx kernel: [    0.952039] microcode: CPU2: patch_level=0x06000822
May 17 05:35:45 unyx kernel: [    0.952047] microcode: CPU3: patch_level=0x06000822
May 17 05:35:45 unyx kernel: [    0.952055] microcode: CPU4: patch_level=0x06000822
May 17 05:35:45 unyx kernel: [    0.952063] microcode: CPU5: patch_level=0x06000822
May 17 05:35:45 unyx kernel: [    0.952071] microcode: CPU6: patch_level=0x06000822
May 17 05:35:45 unyx kernel: [    0.952079] microcode: CPU7: patch_level=0x06000822
May 17 05:35:45 unyx kernel: [    0.952128] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
May 17 05:35:45 unyx kernel: [    0.952132] LVT offset 0 assigned for vector 0x400
May 17 05:35:45 unyx kernel: [    0.952148] perf: AMD IBS detected (0x000000ff)
May 17 05:35:45 unyx kernel: [    0.952166] Scanning for low memory corruption every 60 seconds
May 17 05:35:45 unyx kernel: [    0.952502] futex hash table entries: 2048 (order: 5, 131072 bytes)
May 17 05:35:45 unyx kernel: [    0.952525] Initialise system trusted keyring
May 17 05:35:45 unyx kernel: [    0.952543] audit: initializing netlink subsys (disabled)
May 17 05:35:45 unyx kernel: [    0.952557] audit: type=2000 audit(1431855342.844:1): initialized
May 17 05:35:45 unyx kernel: [    0.952856] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May 17 05:35:45 unyx kernel: [    0.954443] zpool: loaded
May 17 05:35:45 unyx kernel: [    0.954445] zbud: loaded
May 17 05:35:45 unyx kernel: [    0.954586] VFS: Disk quotas dquot_6.5.2
May 17 05:35:45 unyx kernel: [    0.954618] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May 17 05:35:45 unyx kernel: [    0.955107] fuse init (API version 7.23)
May 17 05:35:45 unyx kernel: [    0.955217] msgmni has been set to 32151
May 17 05:35:45 unyx kernel: [    0.955272] Key type big_key registered
May 17 05:35:45 unyx kernel: [    0.955649] Key type asymmetric registered
May 17 05:35:45 unyx kernel: [    0.955652] Asymmetric key parser 'x509' registered
May 17 05:35:45 unyx kernel: [    0.955684] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
May 17 05:35:45 unyx kernel: [    0.955736] io scheduler noop registered
May 17 05:35:45 unyx kernel: [    0.955738] io scheduler deadline registered (default)
May 17 05:35:45 unyx kernel: [    0.955784] io scheduler cfq registered
May 17 05:35:45 unyx kernel: [    0.956239] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 17 05:35:45 unyx kernel: [    0.956254] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 17 05:35:45 unyx kernel: [    0.956299] vesafb: mode is 1920x1200x32, linelength=7680, pages=0
May 17 05:35:45 unyx kernel: [    0.956300] vesafb: scrolling: redraw
May 17 05:35:45 unyx kernel: [    0.956302] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
May 17 05:35:45 unyx kernel: [    0.956321] vesafb: framebuffer at 0xa0000000, mapped to 0xffffc90011b80000, using 9024k, total 9024k
May 17 05:35:45 unyx kernel: [    0.956416] Console: switching to colour frame buffer device 240x75
May 17 05:35:45 unyx kernel: [    0.956443] fb0: VESA VGA frame buffer device
May 17 05:35:45 unyx kernel: [    0.956525] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
May 17 05:35:45 unyx kernel: [    0.956528] ACPI: Power Button [PWRB]
May 17 05:35:45 unyx kernel: [    0.956564] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May 17 05:35:45 unyx kernel: [    0.956566] ACPI: Power Button [PWRF]
May 17 05:35:45 unyx kernel: [    0.956603] ACPI: acpi_idle registered with cpuidle
May 17 05:35:45 unyx kernel: [    0.957336] GHES: HEST is not enabled!
May 17 05:35:45 unyx kernel: [    0.957427] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May 17 05:35:45 unyx kernel: [    0.977823] 00:04: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
May 17 05:35:45 unyx kernel: [    0.979478] Linux agpgart interface v0.103
May 17 05:35:45 unyx kernel: [    0.980793] brd: module loaded
May 17 05:35:45 unyx kernel: [    0.981420] loop: module loaded
May 17 05:35:45 unyx kernel: [    0.981619] libphy: Fixed MDIO Bus: probed
May 17 05:35:45 unyx kernel: [    0.981622] tun: Universal TUN/TAP device driver, 1.6
May 17 05:35:45 unyx kernel: [    0.981623] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May 17 05:35:45 unyx kernel: [    0.981667] PPP generic driver version 2.4.2
May 17 05:35:45 unyx kernel: [    0.981709] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May 17 05:35:45 unyx kernel: [    0.981713] ehci-pci: EHCI PCI platform driver
May 17 05:35:45 unyx kernel: [    0.981790] QUIRK: Enable AMD PLL fix
May 17 05:35:45 unyx kernel: [    0.981805] ehci-pci 0000:00:12.2: EHCI Host Controller
May 17 05:35:45 unyx kernel: [    0.981810] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
May 17 05:35:45 unyx kernel: [    0.981813] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
May 17 05:35:45 unyx kernel: [    0.981822] ehci-pci 0000:00:12.2: debug port 1
May 17 05:35:45 unyx kernel: [    0.981852] ehci-pci 0000:00:12.2: irq 17, io mem 0xfeb09000
May 17 05:35:45 unyx kernel: [    0.990927] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
May 17 05:35:45 unyx kernel: [    0.990966] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
May 17 05:35:45 unyx kernel: [    0.990967] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    0.990969] usb usb1: Product: EHCI Host Controller
May 17 05:35:45 unyx kernel: [    0.990970] usb usb1: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
May 17 05:35:45 unyx kernel: [    0.990971] usb usb1: SerialNumber: 0000:00:12.2
May 17 05:35:45 unyx kernel: [    0.991132] hub 1-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    0.991138] hub 1-0:1.0: 5 ports detected
May 17 05:35:45 unyx kernel: [    0.991335] ehci-pci 0000:00:13.2: EHCI Host Controller
May 17 05:35:45 unyx kernel: [    0.991339] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
May 17 05:35:45 unyx kernel: [    0.991342] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
May 17 05:35:45 unyx kernel: [    0.991349] ehci-pci 0000:00:13.2: debug port 1
May 17 05:35:45 unyx kernel: [    0.991370] ehci-pci 0000:00:13.2: irq 17, io mem 0xfeb07000
May 17 05:35:45 unyx kernel: [    1.002937] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
May 17 05:35:45 unyx kernel: [    1.002982] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
May 17 05:35:45 unyx kernel: [    1.002984] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    1.002985] usb usb2: Product: EHCI Host Controller
May 17 05:35:45 unyx kernel: [    1.002986] usb usb2: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
May 17 05:35:45 unyx kernel: [    1.002987] usb usb2: SerialNumber: 0000:00:13.2
May 17 05:35:45 unyx kernel: [    1.003152] hub 2-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    1.003156] hub 2-0:1.0: 5 ports detected
May 17 05:35:45 unyx kernel: [    1.003345] ehci-pci 0000:00:16.2: EHCI Host Controller
May 17 05:35:45 unyx kernel: [    1.003349] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
May 17 05:35:45 unyx kernel: [    1.003351] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
May 17 05:35:45 unyx kernel: [    1.003359] ehci-pci 0000:00:16.2: debug port 1
May 17 05:35:45 unyx kernel: [    1.003381] ehci-pci 0000:00:16.2: irq 17, io mem 0xfeb04000
May 17 05:35:45 unyx kernel: [    1.014982] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
May 17 05:35:45 unyx kernel: [    1.015017] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
May 17 05:35:45 unyx kernel: [    1.015019] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    1.015021] usb usb3: Product: EHCI Host Controller
May 17 05:35:45 unyx kernel: [    1.015022] usb usb3: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
May 17 05:35:45 unyx kernel: [    1.015023] usb usb3: SerialNumber: 0000:00:16.2
May 17 05:35:45 unyx kernel: [    1.015231] hub 3-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    1.015236] hub 3-0:1.0: 4 ports detected
May 17 05:35:45 unyx kernel: [    1.015346] ehci-platform: EHCI generic platform driver
May 17 05:35:45 unyx kernel: [    1.015355] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May 17 05:35:45 unyx kernel: [    1.015358] ohci-pci: OHCI PCI platform driver
May 17 05:35:45 unyx kernel: [    1.015439] ohci-pci 0000:00:12.0: OHCI PCI host controller
May 17 05:35:45 unyx kernel: [    1.015443] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
May 17 05:35:45 unyx kernel: [    1.015462] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb0a000
May 17 05:35:45 unyx kernel: [    1.075039] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
May 17 05:35:45 unyx kernel: [    1.075041] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    1.075043] usb usb4: Product: OHCI PCI host controller
May 17 05:35:45 unyx kernel: [    1.075044] usb usb4: Manufacturer: Linux 3.16.0-30-generic ohci_hcd
May 17 05:35:45 unyx kernel: [    1.075046] usb usb4: SerialNumber: 0000:00:12.0
May 17 05:35:45 unyx kernel: [    1.075277] hub 4-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    1.075285] hub 4-0:1.0: 5 ports detected
May 17 05:35:45 unyx kernel: [    1.075469] ohci-pci 0000:00:13.0: OHCI PCI host controller
May 17 05:35:45 unyx kernel: [    1.075473] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
May 17 05:35:45 unyx kernel: [    1.075491] ohci-pci 0000:00:13.0: irq 18, io mem 0xfeb08000
May 17 05:35:45 unyx kernel: [    1.135092] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
May 17 05:35:45 unyx kernel: [    1.135094] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    1.135096] usb usb5: Product: OHCI PCI host controller
May 17 05:35:45 unyx kernel: [    1.135097] usb usb5: Manufacturer: Linux 3.16.0-30-generic ohci_hcd
May 17 05:35:45 unyx kernel: [    1.135098] usb usb5: SerialNumber: 0000:00:13.0
May 17 05:35:45 unyx kernel: [    1.135287] hub 5-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    1.135294] hub 5-0:1.0: 5 ports detected
May 17 05:35:45 unyx kernel: [    1.135482] ohci-pci 0000:00:14.5: OHCI PCI host controller
May 17 05:35:45 unyx kernel: [    1.135486] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
May 17 05:35:45 unyx kernel: [    1.135501] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb06000
May 17 05:35:45 unyx kernel: [    1.195156] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
May 17 05:35:45 unyx kernel: [    1.195158] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    1.195160] usb usb6: Product: OHCI PCI host controller
May 17 05:35:45 unyx kernel: [    1.195162] usb usb6: Manufacturer: Linux 3.16.0-30-generic ohci_hcd
May 17 05:35:45 unyx kernel: [    1.195163] usb usb6: SerialNumber: 0000:00:14.5
May 17 05:35:45 unyx kernel: [    1.195328] hub 6-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    1.195335] hub 6-0:1.0: 2 ports detected
May 17 05:35:45 unyx kernel: [    1.195490] ohci-pci 0000:00:16.0: OHCI PCI host controller
May 17 05:35:45 unyx kernel: [    1.195494] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
May 17 05:35:45 unyx kernel: [    1.195509] ohci-pci 0000:00:16.0: irq 18, io mem 0xfeb05000
May 17 05:35:45 unyx kernel: [    1.255167] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
May 17 05:35:45 unyx kernel: [    1.255169] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    1.255171] usb usb7: Product: OHCI PCI host controller
May 17 05:35:45 unyx kernel: [    1.255173] usb usb7: Manufacturer: Linux 3.16.0-30-generic ohci_hcd
May 17 05:35:45 unyx kernel: [    1.255174] usb usb7: SerialNumber: 0000:00:16.0
May 17 05:35:45 unyx kernel: [    1.255364] hub 7-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    1.255373] hub 7-0:1.0: 4 ports detected
May 17 05:35:45 unyx kernel: [    1.255480] ohci-platform: OHCI generic platform driver
May 17 05:35:45 unyx kernel: [    1.255489] uhci_hcd: USB Universal Host Controller Interface driver
May 17 05:35:45 unyx kernel: [    1.255554] xhci_hcd 0000:02:00.0: xHCI Host Controller
May 17 05:35:45 unyx kernel: [    1.255558] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
May 17 05:35:45 unyx kernel: [    1.255644] xhci_hcd 0000:02:00.0: irq 72 for MSI/MSI-X
May 17 05:35:45 unyx kernel: [    1.255689] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
May 17 05:35:45 unyx kernel: [    1.255690] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    1.255691] usb usb8: Product: xHCI Host Controller
May 17 05:35:45 unyx kernel: [    1.255693] usb usb8: Manufacturer: Linux 3.16.0-30-generic xhci_hcd
May 17 05:35:45 unyx kernel: [    1.255694] usb usb8: SerialNumber: 0000:02:00.0
May 17 05:35:45 unyx kernel: [    1.255818] hub 8-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    1.255823] hub 8-0:1.0: 1 port detected
May 17 05:35:45 unyx kernel: [    1.255884] xhci_hcd 0000:02:00.0: xHCI Host Controller
May 17 05:35:45 unyx kernel: [    1.255886] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
May 17 05:35:45 unyx kernel: [    1.255918] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
May 17 05:35:45 unyx kernel: [    1.255919] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 17 05:35:45 unyx kernel: [    1.255920] usb usb9: Product: xHCI Host Controller
May 17 05:35:45 unyx kernel: [    1.255922] usb usb9: Manufacturer: Linux 3.16.0-30-generic xhci_hcd
May 17 05:35:45 unyx kernel: [    1.255923] usb usb9: SerialNumber: 0000:02:00.0
May 17 05:35:45 unyx kernel: [    1.256014] hub 9-0:1.0: USB hub found
May 17 05:35:45 unyx kernel: [    1.256020] hub 9-0:1.0: 4 ports detected
May 17 05:35:45 unyx kernel: [    1.256160] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May 17 05:35:45 unyx kernel: [    1.256162] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May 17 05:35:45 unyx kernel: [    1.257258] serio: i8042 KBD port at 0x60,0x64 irq 1
May 17 05:35:45 unyx kernel: [    1.257454] mousedev: PS/2 mouse device common for all mice
May 17 05:35:45 unyx kernel: [    1.257598] rtc_cmos 00:05: RTC can wake from S4
May 17 05:35:45 unyx kernel: [    1.257691] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
May 17 05:35:45 unyx kernel: [    1.257709] rtc_cmos 00:05: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 17 05:35:45 unyx kernel: [    1.257771] device-mapper: uevent: version 1.0.3
May 17 05:35:45 unyx kernel: [    1.257840] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
May 17 05:35:45 unyx kernel: [    1.257852] ledtrig-cpu: registered to indicate activity on CPUs
May 17 05:35:45 unyx kernel: [    1.257930] TCP: cubic registered
May 17 05:35:45 unyx kernel: [    1.258036] NET: Registered protocol family 10
May 17 05:35:45 unyx kernel: [    1.258273] NET: Registered protocol family 17
May 17 05:35:45 unyx kernel: [    1.258283] Key type dns_resolver registered
May 17 05:35:45 unyx kernel: [    1.258938] Loading compiled-in X.509 certificates
May 17 05:35:45 unyx kernel: [    1.259689] Loaded X.509 cert 'Magrathea: Glacier signing key: 7be2a7200f17f00ca011f70e5a874c37e3e0f6be'
May 17 05:35:45 unyx kernel: [    1.259704] registered taskstats version 1
May 17 05:35:45 unyx kernel: [    1.261614] Key type trusted registered
May 17 05:35:45 unyx kernel: [    1.263139] Key type encrypted registered
May 17 05:35:45 unyx kernel: [    1.264956] AppArmor: AppArmor sha1 policy hashing enabled
May 17 05:35:45 unyx kernel: [    1.264960] ima: No TPM chip found, activating TPM-bypass!
May 17 05:35:45 unyx kernel: [    1.264979] evm: HMAC attrs: 0x1
May 17 05:35:45 unyx kernel: [    1.265325]   Magic number: 15:253:576
May 17 05:35:45 unyx kernel: [    1.265435] rtc_cmos 00:05: setting system clock to 2015-05-17 09:35:43 UTC (1431855343)
May 17 05:35:45 unyx kernel: [    1.265628] acpi-cpufreq: overriding BIOS provided _PSD data
May 17 05:35:45 unyx kernel: [    1.265943] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 17 05:35:45 unyx kernel: [    1.265944] EDD information not available.
May 17 05:35:45 unyx kernel: [    1.266015] PM: Hibernation image not present or could not be loaded.
May 17 05:35:45 unyx kernel: [    1.266965] Freeing unused kernel memory: 1356K (ffffffff81d1c000 - ffffffff81e6f000)
May 17 05:35:45 unyx kernel: [    1.266967] Write protecting the kernel read-only data: 12288k
May 17 05:35:45 unyx kernel: [    1.268865] Freeing unused kernel memory: 564K (ffff880001773000 - ffff880001800000)
May 17 05:35:45 unyx kernel: [    1.270454] Freeing unused kernel memory: 500K (ffff880001b83000 - ffff880001c00000)
May 17 05:35:45 unyx kernel: [    1.278463] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
May 17 05:35:45 unyx kernel: [    1.299919] ahci 0000:00:11.0: version 3.0
May 17 05:35:45 unyx kernel: [    1.300093] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
May 17 05:35:45 unyx kernel: [    1.300096] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
May 17 05:35:45 unyx kernel: [    1.301532] scsi0 : ahci
May 17 05:35:45 unyx kernel: [    1.301663] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May 17 05:35:45 unyx kernel: [    1.301674] r8169 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
May 17 05:35:45 unyx kernel: [    1.301724] scsi1 : ahci
May 17 05:35:45 unyx kernel: [    1.301896] scsi2 : ahci
May 17 05:35:45 unyx kernel: [    1.301904] r8169 0000:06:00.0: irq 73 for MSI/MSI-X
May 17 05:35:45 unyx kernel: [    1.302036] scsi3 : ahci
May 17 05:35:45 unyx kernel: [    1.302097] r8169 0000:06:00.0 eth0: RTL8168evl/8111evl at 0xffffc9001246a000, fc:aa:14:77:fe:54, XID 0c900800 IRQ 73
May 17 05:35:45 unyx kernel: [    1.302100] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
May 17 05:35:45 unyx kernel: [    1.302206] scsi4 : ahci
May 17 05:35:45 unyx kernel: [    1.302344] scsi5 : ahci
May 17 05:35:45 unyx kernel: [    1.302442] ata1: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b100 irq 19
May 17 05:35:45 unyx kernel: [    1.302445] ata2: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b180 irq 19
May 17 05:35:45 unyx kernel: [    1.302447] ata3: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b200 irq 19
May 17 05:35:45 unyx kernel: [    1.302450] ata4: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b280 irq 19
May 17 05:35:45 unyx kernel: [    1.302452] ata5: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b300 irq 19
May 17 05:35:45 unyx kernel: [    1.302454] ata6: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b380 irq 19
May 17 05:35:45 unyx kernel: [    1.302594] ahci 0000:03:00.0: irq 74 for MSI/MSI-X
May 17 05:35:45 unyx kernel: [    1.302646] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
May 17 05:35:45 unyx kernel: [    1.302649] ahci 0000:03:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
May 17 05:35:45 unyx kernel: [    1.303123] scsi6 : ahci
May 17 05:35:45 unyx kernel: [    1.303285] scsi7 : ahci
May 17 05:35:45 unyx kernel: [    1.303358] ata7: SATA max UDMA/133 abar m512@0xfe810000 port 0xfe810100 irq 74
May 17 05:35:45 unyx kernel: [    1.303360] ata8: SATA max UDMA/133 abar m512@0xfe810000 port 0xfe810180 irq 74
May 17 05:35:45 unyx kernel: [    1.359306] usb 1-4: new high-speed USB device number 3 using ehci-pci
May 17 05:35:45 unyx kernel: [    1.363260] firewire_ohci 0000:05:0e.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
May 17 05:35:45 unyx kernel: [    1.471378] usb 1-4: device descriptor read/64, error -71
May 17 05:35:45 unyx kernel: [    1.623418] ata7: SATA link down (SStatus 0 SControl 300)
May 17 05:35:45 unyx kernel: [    1.623448] ata3: SATA link down (SStatus 0 SControl 300)
May 17 05:35:45 unyx kernel: [    1.623457] ata8: SATA link down (SStatus 0 SControl 300)
May 17 05:35:45 unyx kernel: [    1.623492] ata1: SATA link down (SStatus 0 SControl 300)
May 17 05:35:45 unyx kernel: [    1.687518] usb 1-4: device descriptor read/64, error -71
May 17 05:35:45 unyx kernel: [    1.791515] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 17 05:35:45 unyx kernel: [    1.795512] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
May 17 05:35:45 unyx kernel: [    1.795542] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 17 05:35:45 unyx kernel: [    1.795570] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
May 17 05:35:45 unyx kernel: [    1.795727] ata5.00: ATAPI: ASUS    DRW-2014L1T, 1.02, max UDMA/66
May 17 05:35:45 unyx kernel: [    1.795799] ata2.00: ATA-8: PLEXTOR PX-64M3, 1.01, max UDMA/133
May 17 05:35:45 unyx kernel: [    1.795805] ata2.00: 125045424 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
May 17 05:35:45 unyx kernel: [    1.795826] ata6.00: ATA-8: PLEXTOR PX-64M3, 1.00, max UDMA/133
May 17 05:35:45 unyx kernel: [    1.795828] ata6.00: 125045424 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
May 17 05:35:45 unyx kernel: [    1.796059] ata2.00: configured for UDMA/133
May 17 05:35:45 unyx kernel: [    1.796083] ata5.00: configured for UDMA/66
May 17 05:35:45 unyx kernel: [    1.796088] ata6.00: configured for UDMA/133
May 17 05:35:45 unyx kernel: [    1.796174] scsi 1:0:0:0: Direct-Access     ATA      PLEXTOR PX-64M3  1.01 PQ: 0 ANSI: 5
May 17 05:35:45 unyx kernel: [    1.796426] sd 1:0:0:0: [sda] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
May 17 05:35:45 unyx kernel: [    1.796452] sd 1:0:0:0: Attached scsi generic sg0 type 0
May 17 05:35:45 unyx kernel: [    1.796544] sd 1:0:0:0: [sda] Write Protect is off
May 17 05:35:45 unyx kernel: [    1.796547] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 17 05:35:45 unyx kernel: [    1.796588] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 17 05:35:45 unyx kernel: [    1.797128]  sda: sda1 sda2 sda3
May 17 05:35:45 unyx kernel: [    1.797495] sd 1:0:0:0: [sda] Attached SCSI disk
May 17 05:35:45 unyx kernel: [    1.797960] ata4.00: ATA-7: SAMSUNG HD103UJ, 1AA01118, max UDMA7
May 17 05:35:45 unyx kernel: [    1.797962] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
May 17 05:35:45 unyx kernel: [    1.804456] ata4.00: configured for UDMA/133
May 17 05:35:45 unyx kernel: [    1.804544] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1118 PQ: 0 ANSI: 5
May 17 05:35:45 unyx kernel: [    1.804782] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
May 17 05:35:45 unyx kernel: [    1.804817] sd 3:0:0:0: Attached scsi generic sg1 type 0
May 17 05:35:45 unyx kernel: [    1.804874] sd 3:0:0:0: [sdb] Write Protect is off
May 17 05:35:45 unyx kernel: [    1.804876] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May 17 05:35:45 unyx kernel: [    1.804920] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 17 05:35:45 unyx kernel: [    1.805264] scsi 4:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.02 PQ: 0 ANSI: 5
May 17 05:35:45 unyx kernel: [    1.808118]  sdb: sdb1
May 17 05:35:45 unyx kernel: [    1.808419] sd 3:0:0:0: [sdb] Attached SCSI disk
May 17 05:35:45 unyx kernel: [    1.825704] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May 17 05:35:45 unyx kernel: [    1.825711] cdrom: Uniform CD-ROM driver Revision: 3.20
May 17 05:35:45 unyx kernel: [    1.826043] sr 4:0:0:0: Attached scsi CD-ROM sr0
May 17 05:35:45 unyx kernel: [    1.826144] sr 4:0:0:0: Attached scsi generic sg2 type 5
May 17 05:35:45 unyx kernel: [    1.826367] scsi 5:0:0:0: Direct-Access     ATA      PLEXTOR PX-64M3  1.00 PQ: 0 ANSI: 5
May 17 05:35:45 unyx kernel: [    1.826887] sd 5:0:0:0: [sdc] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
May 17 05:35:45 unyx kernel: [    1.826977] sd 5:0:0:0: [sdc] Write Protect is off
May 17 05:35:45 unyx kernel: [    1.826980] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May 17 05:35:45 unyx kernel: [    1.827002] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 17 05:35:45 unyx kernel: [    1.827003] sd 5:0:0:0: Attached scsi generic sg3 type 0
May 17 05:35:45 unyx kernel: [    1.828637]  sdc: sdc1 sdc2 sdc3
May 17 05:35:45 unyx kernel: [    1.829143] sd 5:0:0:0: [sdc] Attached SCSI disk
May 17 05:35:45 unyx kernel: [    1.856895] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
May 17 05:35:45 unyx kernel: [    1.863655] firewire_core 0000:05:0e.0: created device fw0: GUID 0035d474ec1d8c00, S400
May 17 05:35:45 unyx kernel: [    1.903715] usb 1-4: new high-speed USB device number 4 using ehci-pci
May 17 05:35:45 unyx kernel: [    1.951618] tsc: Refined TSC clocksource calibration: 4018.308 MHz
May 17 05:35:45 unyx kernel: [    2.015733] usb 1-4: device descriptor read/64, error -71
May 17 05:35:45 unyx kernel: [    2.276301] usb 1-4: device descriptor read/all, error -71
May 17 05:35:45 unyx kernel: [    2.391978] usb 1-4: new high-speed USB device number 5 using ehci-pci
May 17 05:35:45 unyx kernel: [    2.412800] usb 1-4: device descriptor read/all, error 0
May 17 05:35:45 unyx kernel: [    2.528066] usb 1-4: new high-speed USB device number 6 using ehci-pci
May 17 05:35:45 unyx kernel: [    2.572455] usb 1-4: device descriptor read/8, error -71
May 17 05:35:45 unyx kernel: [    2.716655] usb 1-4: device descriptor read/8, error -71
May 17 05:35:45 unyx kernel: [    2.820262] usb usb1-port4: unable to enumerate USB device
May 17 05:35:45 unyx kernel: [    2.952587] Switched to clocksource tsc
May 17 05:35:45 unyx kernel: [    3.158407] random: init urandom read with 79 bits of entropy available
May 17 05:35:45 unyx kernel: [    3.248716] Adding 4194300k swap on /dev/sda2.  Priority:-1 extents:1 across:4194300k SSFS
May 17 05:35:45 unyx kernel: [    3.250999] Adding 3999740k swap on /dev/sdc2.  Priority:-2 extents:1 across:3999740k SSFS
May 17 05:35:45 unyx kernel: [    3.297815] EXT4-fs (sdc3): re-mounted. Opts: errors=remount-ro
May 17 05:35:45 unyx kernel: [    3.324197] lp: driver loaded but no devices found
May 17 05:35:45 unyx kernel: [    3.329613] ppdev: user-space parallel port driver
May 17 05:35:45 unyx kernel: [    3.344624] EXT4-fs (sdc1): mounting ext2 file system using the ext4 subsystem
May 17 05:35:45 unyx kernel: [    3.345172] EXT4-fs (sdc1): mounted filesystem without journal. Opts: (null)
May 17 05:35:45 unyx kernel: [    3.357635] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 17 05:35:45 unyx kernel: [    3.358575] wmi: Mapper loaded
May 17 05:35:45 unyx kernel: [    3.378037] random: nonblocking pool is initialized
May 17 05:35:45 unyx kernel: [    3.391630] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
May 17 05:35:45 unyx kernel: [    3.391689] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
May 17 05:35:45 unyx kernel: [    3.393821] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
May 17 05:35:45 unyx kernel: [    3.393881] sp5100_tco: PCI Revision ID: 0x42
May 17 05:35:45 unyx kernel: [    3.393911] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
May 17 05:35:45 unyx kernel: [    3.393921] sp5100_tco: Last reboot was not triggered by watchdog.
May 17 05:35:45 unyx kernel: [    3.393983] sp5100_tco: initialized (0xffffc90012468b00). heartbeat=60 sec (nowayout=0)
May 17 05:35:45 unyx kernel: [    3.394373] [drm] Initialized drm 1.1.0 20060810
May 17 05:35:45 unyx kernel: [    3.397982] MCE: In-kernel MCE decoding enabled.
May 17 05:35:45 unyx kernel: [    3.402612] EDAC MC: Ver: 3.0.0
May 17 05:35:45 unyx kernel: [    3.405405] AMD64 EDAC driver v3.4.0
May 17 05:35:45 unyx kernel: [    3.405437] EDAC amd64: DRAM ECC disabled.
May 17 05:35:45 unyx kernel: [    3.405444] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May 17 05:35:45 unyx kernel: [    3.405444]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May 17 05:35:45 unyx kernel: [    3.405444]  (Note that use of the override may cause unknown side effects.)
May 17 05:35:45 unyx kernel: [    3.425322] AVX version of gcm_enc/dec engaged.
May 17 05:35:45 unyx kernel: [    3.428379] [drm] radeon kernel modesetting enabled.
May 17 05:35:45 unyx kernel: [    3.428456] checking generic (a0000000 8d0000) vs hw (a0000000 10000000)
May 17 05:35:45 unyx kernel: [    3.428457] fb: switching to radeondrmfb from VESA VGA
May 17 05:35:45 unyx kernel: [    3.428661] Console: switching to colour dummy device 80x25
May 17 05:35:45 unyx kernel: [    3.429026] [drm] initializing kernel modesetting (BONAIRE 0x1002:0x665C 0x1462:0x2930).
May 17 05:35:45 unyx kernel: [    3.429039] [drm] register mmio base: 0xFEA00000
May 17 05:35:45 unyx kernel: [    3.429040] [drm] register mmio size: 262144
May 17 05:35:45 unyx kernel: [    3.429045] [drm] doorbell mmio base: 0xB0000000
May 17 05:35:45 unyx kernel: [    3.429046] [drm] doorbell mmio size: 8388608
May 17 05:35:45 unyx kernel: [    3.429098] ATOM BIOS: 113
May 17 05:35:45 unyx kernel: [    3.429164] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
May 17 05:35:45 unyx kernel: [    3.429166] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
May 17 05:35:45 unyx kernel: [    3.429168] [drm] Detected VRAM RAM=1024M, BAR=256M
May 17 05:35:45 unyx kernel: [    3.429169] [drm] RAM width 128bits DDR
May 17 05:35:45 unyx kernel: [    3.429221] [TTM] Zone  kernel: Available graphics memory: 8231886 kiB
May 17 05:35:45 unyx kernel: [    3.429222] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
May 17 05:35:45 unyx kernel: [    3.429223] [TTM] Initializing pool allocator
May 17 05:35:45 unyx kernel: [    3.429229] [TTM] Initializing DMA pool allocator
May 17 05:35:45 unyx kernel: [    3.429253] [drm] radeon: 1024M of VRAM memory ready
May 17 05:35:45 unyx kernel: [    3.429255] [drm] radeon: 1024M of GTT memory ready.
May 17 05:35:45 unyx kernel: [    3.429274] [drm] Loading BONAIRE Microcode
May 17 05:35:45 unyx kernel: [    3.447674] [drm] radeon/BONAIRE_mc2.bin: 31792 bytes
May 17 05:35:45 unyx kernel: [    3.448823] [drm] Internal thermal controller with fan control
May 17 05:35:45 unyx kernel: [    3.448870] [drm] probing gen 2 caps for device 1002:5a16 = 31cd02/0
May 17 05:35:45 unyx kernel: [    3.456008] [drm] radeon: dpm initialized
May 17 05:35:45 unyx kernel: [    3.468382] kvm: Nested Virtualization enabled
May 17 05:35:45 unyx kernel: [    3.468388] kvm: Nested Paging enabled
May 17 05:35:45 unyx kernel: [    3.481657] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
May 17 05:35:45 unyx kernel: [    3.481691] [drm] GART: num cpu pages 262144, num gpu pages 262144
May 17 05:35:45 unyx kernel: [    3.483041] [drm] probing gen 2 caps for device 1002:5a16 = 31cd02/0
May 17 05:35:45 unyx kernel: [    3.483046] [drm] PCIE gen 2 link speeds already enabled
May 17 05:35:45 unyx kernel: [    3.497048] Bluetooth: Core ver 2.19
May 17 05:35:45 unyx kernel: [    3.497065] NET: Registered protocol family 31
May 17 05:35:45 unyx kernel: [    3.497067] Bluetooth: HCI device and connection manager initialized
May 17 05:35:45 unyx kernel: [    3.497073] Bluetooth: HCI socket layer initialized
May 17 05:35:45 unyx kernel: [    3.497076] Bluetooth: L2CAP socket layer initialized
May 17 05:35:45 unyx kernel: [    3.497084] Bluetooth: SCO socket layer initialized
May 17 05:35:45 unyx kernel: [    3.499134] [drm] PCIE GART of 1024M enabled (table at 0x000000000078B000).
May 17 05:35:45 unyx kernel: [    3.499249] radeon 0000:01:00.0: WB enabled
May 17 05:35:45 unyx kernel: [    3.499262] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880445177c00
May 17 05:35:45 unyx kernel: [    3.499264] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff880445177c04
May 17 05:35:45 unyx kernel: [    3.499267] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff880445177c08
May 17 05:35:45 unyx kernel: [    3.499269] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880445177c0c
May 17 05:35:45 unyx kernel: [    3.499271] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff880445177c10
May 17 05:35:45 unyx kernel: [    3.499709] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90011eb6c98
May 17 05:35:45 unyx kernel: [    3.499788] radeon 0000:01:00.0: fence driver on ring 6 use gpu addr 0x0000000040000c18 and cpu addr 0xffff880445177c18
May 17 05:35:45 unyx kernel: [    3.499790] radeon 0000:01:00.0: fence driver on ring 7 use gpu addr 0x0000000040000c1c and cpu addr 0xffff880445177c1c
May 17 05:35:45 unyx kernel: [    3.499793] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
May 17 05:35:45 unyx kernel: [    3.499794] [drm] Driver supports precise vblank timestamp query.
May 17 05:35:45 unyx kernel: [    3.499814] radeon 0000:01:00.0: irq 75 for MSI/MSI-X
May 17 05:35:45 unyx kernel: [    3.499839] radeon 0000:01:00.0: radeon: using MSI.
May 17 05:35:45 unyx kernel: [    3.499865] [drm] radeon: irq initialized.
May 17 05:35:45 unyx kernel: [    3.502040] [drm] ring test on 0 succeeded in 3 usecs
May 17 05:35:45 unyx kernel: [    3.502113] [drm] ring test on 1 succeeded in 2 usecs
May 17 05:35:45 unyx kernel: [    3.502128] [drm] ring test on 2 succeeded in 2 usecs
May 17 05:35:45 unyx kernel: [    3.502219] [drm] ring test on 3 succeeded in 4 usecs
May 17 05:35:45 unyx kernel: [    3.502230] [drm] ring test on 4 succeeded in 4 usecs
May 17 05:35:45 unyx kernel: [    3.505551] Bluetooth: RFCOMM TTY layer initialized
May 17 05:35:45 unyx kernel: [    3.505559] Bluetooth: RFCOMM socket layer initialized
May 17 05:35:45 unyx kernel: [    3.505563] Bluetooth: RFCOMM ver 1.11
May 17 05:35:45 unyx kernel: [    3.512018] audit: type=1400 audit(1431855345.740:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=678 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.512024] audit: type=1400 audit(1431855345.740:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=678 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.512029] audit: type=1400 audit(1431855345.740:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=678 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.512331] audit: type=1400 audit(1431855345.740:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=678 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.512336] audit: type=1400 audit(1431855345.740:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=678 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.512496] audit: type=1400 audit(1431855345.740:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=678 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.516341] audit: type=1400 audit(1431855345.744:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=656 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.516348] audit: type=1400 audit(1431855345.744:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=656 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.516686] audit: type=1400 audit(1431855345.748:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=656 comm="apparmor_parser"
May 17 05:35:45 unyx kernel: [    3.516816] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 17 05:35:45 unyx kernel: [    3.516823] Bluetooth: BNEP filters: protocol multicast
May 17 05:35:45 unyx kernel: [    3.516849] Bluetooth: BNEP socket layer initialized
May 17 05:35:45 unyx kernel: [    3.522010] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
May 17 05:35:45 unyx kernel: [    3.522014] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
May 17 05:35:45 unyx kernel: [    3.522016] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
May 17 05:35:45 unyx kernel: [    3.522018] sound hdaudioC0D0:    mono: mono_out=0x0
May 17 05:35:45 unyx kernel: [    3.522020] sound hdaudioC0D0:    dig-out=0x11/0x1e
May 17 05:35:45 unyx kernel: [    3.522021] sound hdaudioC0D0:    inputs:
May 17 05:35:45 unyx kernel: [    3.522023] sound hdaudioC0D0:      Front Mic=0x19
May 17 05:35:45 unyx kernel: [    3.522026] sound hdaudioC0D0:      Rear Mic=0x18
May 17 05:35:45 unyx kernel: [    3.522027] sound hdaudioC0D0:      Line=0x1a
May 17 05:35:45 unyx kernel: [    3.536238] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input3
May 17 05:35:45 unyx kernel: [    3.537105] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
May 17 05:35:45 unyx kernel: [    3.537184] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
May 17 05:35:45 unyx kernel: [    3.537263] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
May 17 05:35:45 unyx kernel: [    3.537344] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
May 17 05:35:45 unyx kernel: [    3.537431] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
May 17 05:35:45 unyx kernel: [    3.537523] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
May 17 05:35:45 unyx kernel: [    3.537600] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
May 17 05:35:45 unyx kernel: [    3.557908] [drm] ring test on 5 succeeded in 2 usecs
May 17 05:35:45 unyx kernel: [    3.577790] [drm] UVD initialized successfully.
May 17 05:35:45 unyx kernel: [    3.612698] usb 5-3: new full-speed USB device number 2 using ohci-pci
May 17 05:35:45 unyx kernel: [    3.687099] [drm] ring test on 6 succeeded in 19 usecs
May 17 05:35:45 unyx kernel: [    3.687112] [drm] ring test on 7 succeeded in 3 usecs
May 17 05:35:45 unyx kernel: [    3.687113] [drm] VCE initialized successfully.
May 17 05:35:45 unyx kernel: [    3.687390] [drm] ib test on ring 0 succeeded in 0 usecs
May 17 05:35:45 unyx kernel: [    3.687557] [drm] ib test on ring 1 succeeded in 0 usecs
May 17 05:35:45 unyx kernel: [    3.687737] [drm] ib test on ring 2 succeeded in 0 usecs
May 17 05:35:45 unyx kernel: [    3.687901] [drm] ib test on ring 3 succeeded in 0 usecs
May 17 05:35:45 unyx kernel: [    3.688086] [drm] ib test on ring 4 succeeded in 0 usecs
May 17 05:35:45 unyx kernel: [    3.708830] [drm] ib test on ring 5 succeeded
May 17 05:35:45 unyx kernel: [    3.729643] [drm] ib test on ring 6 succeeded
May 17 05:35:45 unyx kernel: [    3.730454] [drm] ib test on ring 7 succeeded
May 17 05:35:45 unyx kernel: [    3.731083] [drm] Radeon Display Connectors
May 17 05:35:45 unyx kernel: [    3.731084] [drm] Connector 0:
May 17 05:35:45 unyx kernel: [    3.731085] [drm]   DP-1
May 17 05:35:45 unyx kernel: [    3.731086] [drm]   HPD2
May 17 05:35:45 unyx kernel: [    3.731087] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
May 17 05:35:45 unyx kernel: [    3.731088] [drm]   Encoders:
May 17 05:35:45 unyx kernel: [    3.731089] [drm]     DFP1: INTERNAL_UNIPHY2
May 17 05:35:45 unyx kernel: [    3.731090] [drm] Connector 1:
May 17 05:35:45 unyx kernel: [    3.731091] [drm]   HDMI-A-1
May 17 05:35:45 unyx kernel: [    3.731091] [drm]   HPD3
May 17 05:35:45 unyx kernel: [    3.731092] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
May 17 05:35:45 unyx kernel: [    3.731093] [drm]   Encoders:
May 17 05:35:45 unyx kernel: [    3.731094] [drm]     DFP2: INTERNAL_UNIPHY2
May 17 05:35:45 unyx kernel: [    3.731094] [drm] Connector 2:
May 17 05:35:45 unyx kernel: [    3.731095] [drm]   DVI-D-1
May 17 05:35:45 unyx kernel: [    3.731096] [drm]   HPD1
May 17 05:35:45 unyx kernel: [    3.731097] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
May 17 05:35:45 unyx kernel: [    3.731098] [drm]   Encoders:
May 17 05:35:45 unyx kernel: [    3.731098] [drm]     DFP3: INTERNAL_UNIPHY1
May 17 05:35:45 unyx kernel: [    3.731099] [drm] Connector 3:
May 17 05:35:45 unyx kernel: [    3.731100] [drm]   DVI-I-1
May 17 05:35:45 unyx kernel: [    3.731100] [drm]   HPD6
May 17 05:35:45 unyx kernel: [    3.731102] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
May 17 05:35:45 unyx kernel: [    3.731102] [drm]   Encoders:
May 17 05:35:45 unyx kernel: [    3.731103] [drm]     DFP4: INTERNAL_UNIPHY
May 17 05:35:45 unyx kernel: [    3.731104] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
May 17 05:35:45 unyx kernel: [    3.752767] usb 5-3: device descriptor read/64, error -32
May 17 05:35:46 unyx kernel: [    3.819047] [drm] fb mappable at 0xA098E000
May 17 05:35:46 unyx kernel: [    3.819049] [drm] vram apper at 0xA0000000
May 17 05:35:46 unyx kernel: [    3.819050] [drm] size 9216000
May 17 05:35:46 unyx kernel: [    3.819051] [drm] fb depth is 24
May 17 05:35:46 unyx kernel: [    3.819052] [drm]    pitch is 7680
May 17 05:35:46 unyx kernel: [    3.819138] fbcon: radeondrmfb (fb0) is primary device
May 17 05:35:46 unyx kernel: [    3.819211] Console: switching to colour frame buffer device 200x75
May 17 05:35:46 unyx kernel: [    3.819236] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
May 17 05:35:46 unyx kernel: [    3.819237] radeon 0000:01:00.0: registered panic notifier
May 17 05:35:46 unyx kernel: [    3.858897] r8169 0000:06:00.0 eth0: link down
May 17 05:35:46 unyx kernel: [    3.858929] r8169 0000:06:00.0 eth0: link down
May 17 05:35:46 unyx kernel: [    3.858960] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
May 17 05:35:46 unyx kernel: [    3.873645] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 0
May 17 05:35:46 unyx kernel: [    3.873716] radeon 0000:04:00.0: enabling device (0000 -> 0003)
May 17 05:35:46 unyx kernel: [    3.873766] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
May 17 05:35:46 unyx kernel: [    3.873866] snd_hda_intel 0000:01:00.1: irq 76 for MSI/MSI-X
May 17 05:35:46 unyx kernel: [    3.873955] [drm] initializing kernel modesetting (RV770 0x1002:0x9442 0x174B:0x3000).
May 17 05:35:46 unyx kernel: [    3.873968] [drm] register mmio base: 0xFE720000
May 17 05:35:46 unyx kernel: [    3.873969] [drm] register mmio size: 65536
May 17 05:35:46 unyx kernel: [    3.948785] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input11
May 17 05:35:46 unyx kernel: [    3.948912] input: HD-Audio Generic HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input12
May 17 05:35:46 unyx kernel: [    3.949001] input: HD-Audio Generic HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
May 17 05:35:46 unyx kernel: [    3.949105] input: HD-Audio Generic HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
May 17 05:35:46 unyx kernel: [    3.949188] input: HD-Audio Generic HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
May 17 05:35:46 unyx kernel: [    3.949282] input: HD-Audio Generic HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
May 17 05:35:46 unyx kernel: [    3.991163] ATOM BIOS: Wekiva
May 17 05:35:46 unyx kernel: [    3.991176] [drm] GPU not posted. posting now...
May 17 05:35:46 unyx kernel: [    4.071220] radeon 0000:04:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
May 17 05:35:46 unyx kernel: [    4.071222] radeon 0000:04:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
May 17 05:35:46 unyx kernel: [    4.071224] [drm] Detected VRAM RAM=512M, BAR=256M
May 17 05:35:46 unyx kernel: [    4.071225] [drm] RAM width 256bits DDR
May 17 05:35:46 unyx kernel: [    4.071236] [drm] radeon: 512M of VRAM memory ready
May 17 05:35:46 unyx kernel: [    4.071238] [drm] radeon: 1024M of GTT memory ready.
May 17 05:35:46 unyx kernel: [    4.071252] [drm] Loading RV770 Microcode
May 17 05:35:46 unyx kernel: [    4.072029] [drm] Internal thermal controller with fan control
May 17 05:35:46 unyx kernel: [    4.072095] [drm] radeon: power management initialized
May 17 05:35:46 unyx kernel: [    4.072099] [drm] GART: num cpu pages 262144, num gpu pages 262144
May 17 05:35:46 unyx kernel: [    4.073156] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
May 17 05:35:46 unyx kernel: [    4.076296] [drm] PCIE GART of 1024M enabled (table at 0x0000000000040000).
May 17 05:35:46 unyx kernel: [    4.076318] radeon 0000:04:00.0: WB enabled
May 17 05:35:46 unyx kernel: [    4.076321] radeon 0000:04:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880444cb0c00
May 17 05:35:46 unyx kernel: [    4.076322] radeon 0000:04:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880444cb0c0c
May 17 05:35:46 unyx kernel: [    4.076324] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
May 17 05:35:46 unyx kernel: [    4.076325] [drm] Driver supports precise vblank timestamp query.
May 17 05:35:46 unyx kernel: [    4.076326] radeon 0000:04:00.0: radeon: MSI limited to 32-bit
May 17 05:35:46 unyx kernel: [    4.076340] radeon 0000:04:00.0: irq 77 for MSI/MSI-X
May 17 05:35:46 unyx kernel: [    4.076348] radeon 0000:04:00.0: radeon: using MSI.
May 17 05:35:46 unyx kernel: [    4.076366] [drm] radeon: irq initialized.
May 17 05:35:46 unyx kernel: [    4.122303] [drm] ring test on 0 succeeded in 1 usecs
May 17 05:35:46 unyx kernel: [    4.122308] [drm] ring test on 3 succeeded in 2 usecs
May 17 05:35:46 unyx kernel: [    4.122403] [drm] ib test on ring 0 succeeded in 0 usecs
May 17 05:35:46 unyx kernel: [    4.122414] [drm] ib test on ring 3 succeeded in 0 usecs
May 17 05:35:46 unyx kernel: [    4.122789] [drm] Radeon Display Connectors
May 17 05:35:46 unyx kernel: [    4.122790] [drm] Connector 0:
May 17 05:35:46 unyx kernel: [    4.122791] [drm]   VGA-1
May 17 05:35:46 unyx kernel: [    4.122792] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
May 17 05:35:46 unyx kernel: [    4.122793] [drm]   Encoders:
May 17 05:35:46 unyx kernel: [    4.122794] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
May 17 05:35:46 unyx kernel: [    4.122795] [drm] Connector 1:
May 17 05:35:46 unyx kernel: [    4.122795] [drm]   HDMI-A-2
May 17 05:35:46 unyx kernel: [    4.122796] [drm]   HPD3
May 17 05:35:46 unyx kernel: [    4.122797] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
May 17 05:35:46 unyx kernel: [    4.122798] [drm]   Encoders:
May 17 05:35:46 unyx kernel: [    4.122799] [drm]     DFP1: INTERNAL_UNIPHY
May 17 05:35:46 unyx kernel: [    4.122800] [drm] Connector 2:
May 17 05:35:46 unyx kernel: [    4.122800] [drm]   DVI-I-2
May 17 05:35:46 unyx kernel: [    4.122801] [drm]   HPD2
May 17 05:35:46 unyx kernel: [    4.122802] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
May 17 05:35:46 unyx kernel: [    4.122803] [drm]   Encoders:
May 17 05:35:46 unyx kernel: [    4.122803] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
May 17 05:35:46 unyx kernel: [    4.122804] [drm]     DFP2: INTERNAL_KLDSCP_LVTMA
May 17 05:35:46 unyx kernel: [    4.206801] [drm] fb mappable at 0xC0241000
May 17 05:35:46 unyx kernel: [    4.206803] [drm] vram apper at 0xC0000000
May 17 05:35:46 unyx kernel: [    4.206804] [drm] size 8294400
May 17 05:35:46 unyx kernel: [    4.206805] [drm] fb depth is 24
May 17 05:35:46 unyx kernel: [    4.206805] [drm]    pitch is 7680
May 17 05:35:46 unyx kernel: [    4.206935] radeon 0000:04:00.0: fb1: radeondrmfb frame buffer device
May 17 05:35:46 unyx kernel: [    4.206939] [drm] Initialized radeon 2.39.0 20080528 for 0000:04:00.0 on minor 1
May 17 05:35:46 unyx kernel: [    4.207121] snd_hda_intel 0000:04:00.1: Handle VGA-switcheroo audio client
May 17 05:35:46 unyx kernel: [    4.207319] snd_hda_intel 0000:04:00.1: irq 78 for MSI/MSI-X
May 17 05:35:46 unyx kernel: [    4.221018] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0b.0/0000:04:00.1/sound/card2/input17
May 17 05:35:46 unyx kernel: [    4.405127] usb 5-3: device not accepting address 2, error -32
May 17 05:35:46 unyx kernel: [    4.541329] usb 5-3: new full-speed USB device number 3 using ohci-pci
May 17 05:35:46 unyx kernel: [    4.681370] usb 5-3: device descriptor read/64, error -32
May 17 05:35:47 unyx kernel: [    4.933539] usb 5-3: device descriptor read/64, error -32
May 17 05:35:47 unyx kernel: [    5.173634] usb 5-3: new full-speed USB device number 4 using ohci-pci
May 17 05:35:47 unyx kernel: [    5.206846] usb 5-3: device descriptor read/all, error -32
May 17 05:35:47 unyx kernel: [    5.345848] usb 5-3: new full-speed USB device number 5 using ohci-pci
May 17 05:35:47 unyx kernel: [    5.394701] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none:owns=none
May 17 05:35:47 unyx kernel: [    5.394705] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
May 17 05:35:47 unyx kernel: [    5.754075] usb 5-3: device not accepting address 5, error -32
May 17 05:35:47 unyx kernel: [    5.754132] usb usb5-port3: unable to enumerate USB device
May 17 05:35:48 unyx kernel: [    5.890246] usb 4-3: new low-speed USB device number 2 using ohci-pci
May 17 05:35:48 unyx kernel: [    5.946414] r8169 0000:06:00.0 eth0: link up
May 17 05:35:48 unyx kernel: [    5.946420] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 17 05:35:48 unyx kernel: [    5.960797] audit_printk_skb: 153 callbacks suppressed
May 17 05:35:48 unyx kernel: [    5.960800] audit: type=1400 audit(1431855348.188:62): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1248 comm="nm-dhcp-client." lport=29946 family="inet" sock_type="dgram" protocol=17
May 17 05:35:48 unyx kernel: [    5.960806] audit: type=1400 audit(1431855348.188:63): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1248 comm="nm-dhcp-client." lport=4429 family="inet6" sock_type="dgram" protocol=17
May 17 05:35:48 unyx kernel: [    6.030319] usb 4-3: device descriptor read/64, error -32
May 17 05:35:48 unyx kernel: [    6.278417] usb 4-3: device descriptor read/64, error -32
May 17 05:35:48 unyx kernel: [    6.530610] usb 4-3: new low-speed USB device number 3 using ohci-pci
May 17 05:35:48 unyx kernel: [    6.670717] usb 4-3: device descriptor read/64, error -32
May 17 05:35:49 unyx kernel: [    6.914857] usb 4-3: device descriptor read/64, error -32
May 17 05:35:49 unyx kernel: [    7.154926] usb 4-3: new low-speed USB device number 4 using ohci-pci
May 17 05:35:49 unyx kernel: [    7.563264] usb 4-3: device not accepting address 4, error -32
May 17 05:35:49 unyx kernel: [    7.699329] usb 4-3: new low-speed USB device number 5 using ohci-pci
May 17 05:35:50 unyx kernel: [    8.107660] usb 4-3: device not accepting address 5, error -32
May 17 05:35:50 unyx kernel: [    8.107694] usb usb4-port3: unable to enumerate USB device
May 17 05:35:50 unyx kernel: [    8.371811] usb 4-4: new full-speed USB device number 6 using ohci-pci
May 17 05:35:50 unyx kernel: [    8.511885] usb 4-4: device descriptor read/64, error -71
May 17 05:35:50 unyx kernel: [    8.756056] usb 4-4: device descriptor read/64, error -71
May 17 05:35:51 unyx kernel: [    8.996259] usb 4-4: new full-speed USB device number 7 using ohci-pci
May 17 05:35:51 unyx kernel: [    9.136303] usb 4-4: device descriptor read/64, error -71
May 17 05:35:51 unyx kernel: [    9.380457] usb 4-4: device descriptor read/64, error -71
May 17 05:35:51 unyx kernel: [    9.620611] usb 4-4: new full-speed USB device number 8 using ohci-pci
May 17 05:35:51 unyx kernel: [    9.645745] usb 4-4: device descriptor read/8, error -62
May 17 05:35:52 unyx kernel: [    9.769826] usb 4-4: device descriptor read/8, error -62
May 17 05:35:52 unyx kernel: [   10.008920] usb 4-4: new full-speed USB device number 9 using ohci-pci
May 17 05:35:52 unyx kernel: [   10.033997] usb 4-4: device descriptor read/8, error -62
May 17 05:35:52 unyx kernel: [   10.158080] usb 4-4: device descriptor read/8, error -62
May 17 05:35:52 unyx kernel: [   10.261042] usb usb4-port4: unable to enumerate USB device
May 17 05:35:52 unyx kernel: [   10.373104] usb 8-1: new high-speed USB device number 2 using xhci_hcd
May 17 05:35:52 unyx kernel: [   10.503163] usb 8-1: New USB device found, idVendor=2109, idProduct=3431
May 17 05:35:52 unyx kernel: [   10.503165] usb 8-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
May 17 05:35:52 unyx kernel: [   10.503167] usb 8-1: Product: USB2.0 Hub
May 17 05:35:52 unyx kernel: [   10.503718] hub 8-1:1.0: USB hub found
May 17 05:35:52 unyx kernel: [   10.504010] hub 8-1:1.0: 4 ports detected
May 17 05:35:53 unyx kernel: [   10.937536] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:53 unyx kernel: [   10.954906] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:53 unyx kernel: [   11.237651] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:53 unyx kernel: [   11.537912] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:54 unyx kernel: [   11.838090] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:54 unyx kernel: [   12.138249] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:54 unyx kernel: [   12.438427] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:54 unyx kernel: [   12.738644] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:55 unyx kernel: [   13.038904] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:35:55 unyx kernel: [   13.339050] sound hdaudioC2D0: HDMI ATI/AMD: no speaker allocation for ELD
May 17 05:36:15 unyx kernel: [   33.613539] audit: type=1400 audit(1431855375.824:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2656 comm="apparmor_parser"
May 17 05:36:15 unyx kernel: [   33.613560] audit: type=1400 audit(1431855375.824:65): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2656 comm="apparmor_parser"
May 17 05:36:15 unyx kernel: [   33.613866] audit: type=1400 audit(1431855375.824:66): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2656 comm="apparmor_parser"
May 17 05:36:36 unyx kernel: [   54.149910] audit: type=1400 audit(1431855396.348:67): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2734 comm="nm-dhcp-client." lport=24584 family="inet" sock_type="dgram" protocol=17
May 17 05:36:36 unyx kernel: [   54.149918] audit: type=1400 audit(1431855396.348:68): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2734 comm="nm-dhcp-client." lport=38364 family="inet6" sock_type="dgram" protocol=17
May 17 05:36:48 unyx kernel: [   65.889294] ------------[ cut here ]------------
May 17 05:36:48 unyx kernel: [   65.889329] WARNING: CPU: 7 PID: 0 at /build/buildd/linux-lts-utopic-3.16.0/net/sched/sch_generic.c:264 dev_watchdog+0x276/0x280()
May 17 05:36:48 unyx kernel: [   65.889334] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
May 17 05:36:48 unyx kernel: [   65.889337] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic bnep mxm_wmi snd_hda_intel rfcomm snd_hda_controller bluetooth 6lowpan_iphc snd_hda_codec snd_hwdep snd_pcm kvm_amd snd_seq_midi snd_seq_midi_event kvm snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel snd_seq_device radeon aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_timer serio_raw edac_core fam15h_power ttm edac_mce_amd k10temp drm_kms_helper sp5100_tco i2c_piix4 drm snd i2c_algo_bit soundcore tpm_infineon wmi shpchp mac_hid parport_pc ppdev lp parport firewire_ohci r8169 firewire_core ahci mii crc_itu_t libahci
May 17 05:36:48 unyx kernel: [   65.889421] CPU: 7 PID: 0 Comm: swapper/7 Not tainted 3.16.0-30-generic #40~14.04.1-Ubuntu
May 17 05:36:48 unyx kernel: [   65.889425] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./990FXA-UD3, BIOS F2 07/15/2013
May 17 05:36:48 unyx kernel: [   65.889432]  0000000000000009 ffff88045edc3d98 ffffffff81762590 ffff88045edc3de0
May 17 05:36:48 unyx kernel: [   65.889444]  ffff88045edc3dd0 ffffffff8106dd2d 0000000000000000 ffff880443e48000
May 17 05:36:48 unyx kernel: [   65.889454]  ffff880444907680 0000000000000001 0000000000000007 ffff88045edc3e30
May 17 05:36:48 unyx kernel: [   65.889461] Call Trace:
May 17 05:36:48 unyx kernel: [   65.889468]  <IRQ>  [<ffffffff81762590>] dump_stack+0x45/0x56
May 17 05:36:48 unyx kernel: [   65.889497]  [<ffffffff8106dd2d>] warn_slowpath_common+0x7d/0xa0
May 17 05:36:48 unyx kernel: [   65.889511]  [<ffffffff8106dd9c>] warn_slowpath_fmt+0x4c/0x50
May 17 05:36:48 unyx kernel: [   65.889530]  [<ffffffff816831e6>] dev_watchdog+0x276/0x280
May 17 05:36:48 unyx kernel: [   65.889535]  [<ffffffff81682f70>] ? dev_graft_qdisc+0x80/0x80
May 17 05:36:48 unyx kernel: [   65.889539]  [<ffffffff8107a426>] call_timer_fn+0x36/0x100
May 17 05:36:48 unyx kernel: [   65.889548]  [<ffffffff81682f70>] ? dev_graft_qdisc+0x80/0x80
May 17 05:36:48 unyx kernel: [   65.889551]  [<ffffffff8107bbdf>] run_timer_softirq+0x20f/0x310
May 17 05:36:48 unyx kernel: [   65.889554]  [<ffffffff81073055>] __do_softirq+0xf5/0x2e0
May 17 05:36:48 unyx kernel: [   65.889557]  [<ffffffff81073515>] irq_exit+0x105/0x110
May 17 05:36:48 unyx kernel: [   65.889567]  [<ffffffff8176dba5>] smp_apic_timer_interrupt+0x45/0x60
May 17 05:36:48 unyx kernel: [   65.889570]  [<ffffffff8176bc7d>] apic_timer_interrupt+0x6d/0x80
May 17 05:36:48 unyx kernel: [   65.889570]  <EOI>  [<ffffffff815fb89f>] ? cpuidle_enter_state+0x4f/0xc0
May 17 05:36:48 unyx kernel: [   65.889575]  [<ffffffff815fb898>] ? cpuidle_enter_state+0x48/0xc0
May 17 05:36:48 unyx kernel: [   65.889585]  [<ffffffff815fb9c7>] cpuidle_enter+0x17/0x20
May 17 05:36:48 unyx kernel: [   65.889588]  [<ffffffff810b528d>] cpu_startup_entry+0x31d/0x450
May 17 05:36:48 unyx kernel: [   65.889591]  [<ffffffff810e027d>] ? tick_check_new_device+0xdd/0xf0
May 17 05:36:48 unyx kernel: [   65.889593]  [<ffffffff8104526d>] start_secondary+0x21d/0x2e0
May 17 05:36:48 unyx kernel: [   65.889603] ---[ end trace 14bd9216410f9ac4 ]---
May 17 05:36:48 unyx kernel: [   65.895733] r8169 0000:06:00.0 eth0: link up
May 17 05:37:24 unyx kernel: [  102.189344] audit: type=1400 audit(1431855444.356:69): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2766 comm="nm-dhcp-client." lport=14296 family="inet" sock_type="dgram" protocol=17
May 17 05:37:24 unyx kernel: [  102.189355] audit: type=1400 audit(1431855444.356:70): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2766 comm="nm-dhcp-client." lport=20131 family="inet6" sock_type="dgram" protocol=17
May 17 05:38:12 unyx kernel: [  150.220528] audit: type=1400 audit(1431855492.356:71): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2777 comm="nm-dhcp-client." lport=26048 family="inet" sock_type="dgram" protocol=17
May 17 05:38:12 unyx kernel: [  150.220551] audit: type=1400 audit(1431855492.356:72): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2777 comm="nm-dhcp-client." lport=22448 family="inet6" sock_type="dgram" protocol=17
May 17 05:38:24 unyx kernel: [  161.958436] r8169 0000:06:00.0 eth0: link up
May 17 05:43:57 unyx kernel: [  495.501136] audit: type=1400 audit(1431855837.408:73): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3103 comm="nm-dhcp-client." lport=28569 family="inet" sock_type="dgram" protocol=17
May 17 05:43:57 unyx kernel: [  495.501145] audit: type=1400 audit(1431855837.408:74): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3103 comm="nm-dhcp-client." lport=35074 family="inet6" sock_type="dgram" protocol=17
May 17 05:44:12 unyx kernel: [  510.185623] r8169 0000:06:00.0 eth0: link up
May 17 05:44:45 unyx kernel: [  543.477026] audit: type=1400 audit(1431855885.356:75): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3106 comm="nm-dhcp-client." lport=53483 family="inet" sock_type="dgram" protocol=17
May 17 05:44:45 unyx kernel: [  543.477046] audit: type=1400 audit(1431855885.356:76): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3106 comm="nm-dhcp-client." lport=39963 family="inet6" sock_type="dgram" protocol=17
May 17 05:45:33 unyx kernel: [  591.508716] audit: type=1400 audit(1431855933.356:77): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3124 comm="nm-dhcp-client." lport=23457 family="inet" sock_type="dgram" protocol=17
May 17 05:45:33 unyx kernel: [  591.508736] audit: type=1400 audit(1431855933.356:78): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3124 comm="nm-dhcp-client." lport=4791 family="inet6" sock_type="dgram" protocol=17
May 17 05:45:42 unyx kernel: [  600.244375] r8169 0000:06:00.0 eth0: link up
May 17 05:46:21 unyx kernel: [  639.540705] audit: type=1400 audit(1431855981.356:79): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3142 comm="nm-dhcp-client." lport=40717 family="inet" sock_type="dgram" protocol=17
May 17 05:46:21 unyx kernel: [  639.540724] audit: type=1400 audit(1431855981.356:80): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3142 comm="nm-dhcp-client." lport=37078 family="inet6" sock_type="dgram" protocol=17
May 17 05:46:36 unyx kernel: [  654.279661] r8169 0000:06:00.0 eth0: link up
May 17 05:46:54 unyx kernel: [  673.172275] audit: type=1400 audit(1431856014.964:81): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=3193 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  673.238975] audit: type=1400 audit(1431856015.032:82): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/tcpdump" pid=3196 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  673.348487] audit: type=1400 audit(1431856015.140:83): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=3188 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  673.362003] audit: type=1400 audit(1431856015.156:84): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=3188 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  673.445377] audit: type=1400 audit(1431856015.236:85): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3194 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  673.445710] audit: type=1400 audit(1431856015.240:86): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3194 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  674.033751] audit: type=1400 audit(1431856015.824:87): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=3192 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  674.034231] audit: type=1400 audit(1431856015.828:88): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=3192 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  674.042391] audit: type=1400 audit(1431856015.836:89): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="pxgsettings" pid=3192 comm="apparmor_parser"
May 17 05:46:55 unyx kernel: [  674.042663] audit: type=1400 audit(1431856015.836:90): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=3192 comm="apparmor_parser"



```

Guess I may as well try 15.04 while I'm at it, see if it goes belly up too. 

As an aside, installing these ubuntus is kinda scary as in who knows what it's going to try to fdisk or run mkswap on. I did the "something else" option and it still had to run mkswap on all my swap partitions there was no way to stop it?

---

### Post by buzzingrobot on 2015-05-17
> **daktaklakpak5576 said:**
> 

...installing these ubuntus is kinda scary as in who knows what it's going to try to fdisk or run mkswap on. I did the "something else" option and it still had to run mkswap on all my swap partitions there was no way to stop it?

I've never installed with anything other than manual aka "Something Else". Partitions won't be removed unless you remove them.  They won't be formatted unless you choose to. Running mkswap on the swap partition seems a normal requirement.

---

### Post by daktaklakpak5576 on 2015-05-17
> **buzzingrobot said:**
> I've never installed with anything other than manual aka "Something Else". Partitions won't be removed unless you remove them.  They won't be formatted unless you choose to. Running mkswap on the swap partition seems a normal requirement.

Yes mkswap would be required except these partitions were already initialized as swap. Why should ubuntu have to mess with my /dev/sda? Ubuntu is not installing on that drive it should leave it alone when it is partitioning and making filesystems. If it wants to recognize it as an available swap partition and use it later on, fine no problem then. Other way around I can also use the swap from the ubuntu drive /dev/sdc in my other OS no problem, no mkswap required

```
nyx yak # swapon -s
Filename                Type        Size    Used    Priority
/dev/sda2                                  partition    4194300    0    -1
nyx yak # swapon /dev/sdc2
nyx yak # swapon -s
Filename                Type        Size    Used    Priority
/dev/sda2                                  partition    4194300    0    -1
/dev/sdc2                                  partition    3999740    0    -2

```

or I could put it in /etc/fstab and make it permanent. 

The rest of what you said about not removing/formatting unless chosen is completely true, still doesn't mean I like doing it repeatedly especially with only a keyboard and no mouse. Especially since partitioning and making filesystems is lumped together into one operation, would be easy enough to make a mistake and take out a partition. 

And then this last time installing 15.04 there was this warning about the installer being booted as UEFI but another OS being booted in BIOS mode, if you continue you may have trouble booting your other OS, [go back][continue]. What does that even mean? If [go back] was selected then proceed with the installation which exactly did it do? BIOS or EFI? It's totally unclear. 

Nevermind that I have installed three versions of ubuntu now and still don't have a functioning mouse, I should be allowed to be critical of the install process at this point :)

---

### Post by dino99 on 2015-05-17
Looks like that r8169 have had some issues already:
[http://ubuntuforums.org/showthread.php?t=1667263](http://ubuntuforums.org/showthread.php?t=1667263)
[http://ubuntuforums.org/showthread.php?t=1766962](http://ubuntuforums.org/showthread.php?t=1766962) (maybe a solution done)
[http://askubuntu.com/questions/505748/ubuntu-14-04-wired-connection-not-detecting](http://askubuntu.com/questions/505748/ubuntu-14-04-wired-connection-not-detecting)

looks like that driver is a bad one (very old wiki)  [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek)

***** maybe you can find more info on the realtek site/forum ********

---

### Post by daktaklakpak5576 on 2015-05-17
> **mörgæs said:**
> How does it work in a live boot of 15.04?

So mouse still doesn't work in 15.04, neither the live dvd or installed. So is it kernel related and I am stuck having to make a custom kernel?

I found the kernel config under /boot guess I will look that over and see if I can figure anything out.

---

### Post by daktaklakpak5576 on 2015-05-17
> **dino99 said:**
> Looks like that r8169 have had some issues already:
[http://ubuntuforums.org/showthread.php?t=1667263](http://ubuntuforums.org/showthread.php?t=1667263)
[http://ubuntuforums.org/showthread.php?t=1766962](http://ubuntuforums.org/showthread.php?t=1766962) (maybe a solution done)
[http://askubuntu.com/questions/505748/ubuntu-14-04-wired-connection-not-detecting](http://askubuntu.com/questions/505748/ubuntu-14-04-wired-connection-not-detecting)

looks like that driver is a bad one (very old wiki)  [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek)

***** maybe you can find more info on the realtek site/forum ********


Thank you for this. This reminded me, trying to remember if I had issues with this in the past.. might have. Thought it was fixed a long time ago but maybe not. I know for a fact that the darn thing works when compiled into a 4.0.2 kernel and at least a few versions before that. Maybe it was just trouble as a module, I'll look into it.

---

### Post by dino99 on 2015-05-17
note that when searching the ubuntu archive, there are a few special related realtek package, like that one you could try: r8168-dkms
but if it also fails, then a custom kernel built might be the solution, till you get a linux fix ( after sending a report on launchpad (with ubuntu-bug linux) explaining the issue and the tests made)

r8168-dkms details
> This driver should only be used for devices not yet supported by the in-kernel driver r8169. Please see the README.Debian for instructions how
to report bugs against r8169 that made it necessary to use r8168-dkms.

Installation of the r8168-dkms package will disable the in-kernel r8169 module. To re-enable r8169, the r8168-dkms package must be purged.

nictools-pci is an other package to diagnose problems with an ethernet card

---

### Post by daktaklakpak5576 on 2015-05-17
> **dino99 said:**
> note that when searching the ubuntu archive, there are a few special related realtek package, like that one you could try: r8168-dkms
but if it also fails, then a custom kernel built might be the solution, till you get a linux fix ( after sending a report on launchpad (with ubuntu-bug linux) explaining the issue and the tests made)

r8168-dkms details


nictools-pci is an other package to diagnose problems with an ethernet card


When I had booted into ubuntu 15.04 I don't know it looks like the driver loaded okay not doing the reconnecting like the older versions but still no ipv4 address and no route.

```
fog@nyx:~$ cat /var/log/kern.log | grep r8169
May 17 07:18:32 unyx kernel: [    1.286030] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May 17 07:18:32 unyx kernel: [    1.286040] r8169 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
May 17 07:18:32 unyx kernel: [    1.286582] r8169 0000:06:00.0 eth0: RTL8168evl/8111evl at 0xffffc90011b9a000, fc:aa:14:77:fe:54, XID 0c900800 IRQ 29
May 17 07:18:32 unyx kernel: [    1.286585] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
May 17 07:18:32 unyx kernel: [    9.514565] r8169 0000:06:00.0 eth0: link down
May 17 07:18:32 unyx kernel: [    9.514584] r8169 0000:06:00.0 eth0: link down
May 17 07:18:34 unyx kernel: [   11.708105] r8169 0000:06:00.0 eth0: link up
May 17 10:17:43 unyx kernel: [    1.286511] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May 17 10:17:43 unyx kernel: [    1.286519] r8169 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
May 17 10:17:43 unyx kernel: [    1.287306] r8169 0000:06:00.0 eth0: RTL8168evl/8111evl at 0xffffc90011b9c000, fc:aa:14:77:fe:54, XID 0c900800 IRQ 29
May 17 10:17:43 unyx kernel: [    1.287308] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
May 17 10:17:43 unyx kernel: [   10.114905] r8169 0000:06:00.0 eth0: link down
May 17 10:17:43 unyx kernel: [   10.114921] r8169 0000:06:00.0 eth0: link down
May 17 10:17:45 unyx kernel: [   12.190372] r8169 0000:06:00.0 eth0: link up

```

```
fog@nyx:~$ cat ifconfig.txt 
eth0      Link encap:Ethernet  HWaddr fc:aa:14:77:fe:54
          inet6 addr: fe80::feaa:14ff:fe77:fe54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:135274 (135.2 KB)  TX bytes:135274 (135.2 KB)



```

I Installed nictools-pci wonder what the rtl8139-diag would do since it was written for the old fast ethernet card and r8169 is gigabit.. but think I will try some other things first. I just really don't understand what ubuntu is doing with networkmanager. It should be set up for dhcp, something with /sbin/dhclient? And the network should restart with 'sudo service networking restart' but the config files.. who knows? I've always just used dhcpcd before, it just seems simpler to me. I guess if all else fails may try putting in static addresses with ifconfig.

still the usb is hosed so unless there's a driver fix for that I'm back to building a kernel.. should be interesting. Thanks for the info about the r8168-dkms had no idea about that will give it a test if I can do something with the usb.

---

### Post by daktaklakpak5576 on 2015-05-17
So I did apt-get source linux-image-3.19.0-15-generic and mucked around in there for awhile. Found no way to build just one arch without creating a custom flavour.. what a mess that is I'm not going near that again anytime soon if ever.

Found linux-source and installed that and compiled a kernel and installed the debs. Sadly after all the reboots and chroot work it fixed nothing. Tried the r8168-dkms driver, nothing. Tried dhcpcd and it got nothing but a link local address.

Finally for kicks I plugged the mouse into all kinds of different usb ports then it worked.. sort of.. if one likes a strobing mouse cursor. I don't care if it's a usb3, usb2, or usb1.1 port they are backward compatible it should just work.

I just wanted to play Dota2, but I have no idea how those nuts at Valve could think ubuntu could handle playing any games when it can't even do usb or networking. I'm tossing all 3 ubuntu dvds in the trash and trying another distribution, don't care what Valve recommends for Steam anymore.

Thanks for trying to help guys and gals, but I'm done with ubuntu. So long and thanks for all the fish.

---

### Post by Vladlenin5000 on 2015-05-18
You may care about what Valve recommends regarding Graphics drivers. BTW, your graphics card really requires them. Have you tried it already? It's as simple as going to System Settings > Software & Updates, find the rightmost tab, additional drivers, wait a moment and select&apply the recommended fglrx.

---

### Post by daktaklakpak5576 on 2015-05-18
> **Vladlenin5000 said:**
> You may care about what Valve recommends regarding Graphics drivers. BTW, your graphics card really requires them. Have you tried it already? It's as simple as going to System Settings > Software & Updates, find the rightmost tab, additional drivers, wait a moment and select&apply the recommended fglrx.

Yes thank you I'm aware, just never really got that far. I was a bit frustrated and harsh on ubuntu. I'm of the opinion that the usb issues are definitely a bug. The r8169 has its firmware issues that ubuntu doesn't seem to handle very well. It didn't work with a Mint live dvd either. Debian kindly asked for the firmware during the install.

Steam has issues of its own. I had it running quite nicely with the radeon/gallium3d drivers and was happily playing Dota2 until either I updated things and mucked it up, or Valve did a patch and mucked it up, or the Mesa3d guys added a feature, who knows. I've fought it for weeks now and it still crashes. It crashes the entire xserver, or locks it up, lose all your work have to hit the reset button kind of stuff. I think that's enough to **** anybody off; X should NEVER be doing that. 

I can't really even try fglrx on my current distribution without it messing things up, as it's all configured for the open source driver, so I'm looking at other options. Maybe I find one, maybe I don't.

---

### Post by dino99 on 2015-05-18
note1: if you have a bios setting for IOMMU, then try it
note2: boot or switch to upstart (install upstart-sysv) or simply test on 'advanced' grub booting choice

---

