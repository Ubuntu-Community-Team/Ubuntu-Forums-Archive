---
title: "Sony Ericsson W580i refuses to connect to Ibex through USB"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Zachs Kappler on 2008-11-15
After upgrading to Ubuntu 8.10 my Sony Ericsson phone while it's in file transfer mode. Unlike the other thread I saw about this model, mine will not show up at all. performing the dmesg | tail -30 command got me this: 

[78784.237668] sd 2:0:0:0: [sdb] Write Protect is off
[78784.237684] sd 2:0:0:0: [sdb] Mode Sense: 00 46 94 00
[78784.237692] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[78784.237704]  sdb:<3>ldm_parse_privhead(): Cannot find PRIVHEAD structure. LDM database is corrupt. Aborting.
[78784.397697] ldm_validate_privheads(): Cannot find PRIVHEAD 1.
[78784.397711] 
[82721.176800] usb 1-3.1: new full speed USB device using ehci_hcd and address 14
[82721.329988] usb 1-3.1: configuration #3 chosen from 1 choice
[82722.416258] cdc_acm 1-3.1:3.1: ttyACM0: USB ACM device
[82722.421594] cdc_acm 1-3.1:3.3: ttyACM1: USB ACM device
[82722.423126] cdc_wdm 1-3.1:3.7: cdc-wdm0: USB WDM device
[82722.424157] usbcore: registered new interface driver cdc_wdm
[82722.424465] usbcore: registered new interface driver cdc_acm
[82722.425855] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[82722.476334] usb0: register 'cdc_ether' at usb-0000:00:1d.7-3.1, CDC Ethernet Device, 02:80:37:0a:03:00
[82722.477070] usbcore: registered new interface driver cdc_ether
[82732.494135] usb 1-3.1: USB disconnect, address 14
[82732.510566] ehci_hcd 0000:00:1d.7: dma_pool_free buffer-2048, f3e51400/33e51400 (bad dma)
[82732.511630] usb0: unregister 'cdc_ether' usb-0000:00:1d.7-3.1, CDC Ethernet Device
[82734.484447] usb 1-3.1: new full speed USB device using ehci_hcd and address 15
[82749.556362] usb 1-3.1: device descriptor read/64, error -110
[82764.732384] usb 1-3.1: device descriptor read/64, error -110
[82764.908396] usb 1-3.1: new full speed USB device using ehci_hcd and address 16
[82779.981570] usb 1-3.1: device descriptor read/64, error -110
[82795.156421] usb 1-3.1: device descriptor read/64, error -110
[82795.336155] usb 1-3.1: new full speed USB device using ehci_hcd and address 17
[82805.744125] usb 1-3.1: device not accepting address 17, error -110
[82805.816369] usb 1-3.1: new full speed USB device using ehci_hcd and address 18
[82816.224055] usb 1-3.1: device not accepting address 18, error -110
[82816.226361] hub 1-3:1.0: unable to enumerate USB device on port 1

I have several usb devices fed through a hub at the moment, but it will not work when it's the only usb device connected. 

Interestingly, Ibex recognizes the modem function while in phone mode.

---

### Post by Zachs Kappler on 2008-11-15
after disconnecting the whole hub and running dmesg | tail -30 i get:

[78784.237668] sd 2:0:0:0: [sdb] Write Protect is off
[78784.237684] sd 2:0:0:0: [sdb] Mode Sense: 00 46 94 00
[78784.237692] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[78784.237704]  sdb:<3>ldm_parse_privhead(): Cannot find PRIVHEAD structure. LDM database is corrupt. Aborting.
[78784.397697] ldm_validate_privheads(): Cannot find PRIVHEAD 1.
[78784.397711] 
[82721.176800] usb 1-3.1: new full speed USB device using ehci_hcd and address 14
[82721.329988] usb 1-3.1: configuration #3 chosen from 1 choice
[82722.416258] cdc_acm 1-3.1:3.1: ttyACM0: USB ACM device
[82722.421594] cdc_acm 1-3.1:3.3: ttyACM1: USB ACM device
[82722.423126] cdc_wdm 1-3.1:3.7: cdc-wdm0: USB WDM device
[82722.424157] usbcore: registered new interface driver cdc_wdm
[82722.424465] usbcore: registered new interface driver cdc_acm
[82722.425855] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[82722.476334] usb0: register 'cdc_ether' at usb-0000:00:1d.7-3.1, CDC Ethernet Device, 02:80:37:0a:03:00
[82722.477070] usbcore: registered new interface driver cdc_ether
[82732.494135] usb 1-3.1: USB disconnect, address 14
[82732.510566] ehci_hcd 0000:00:1d.7: dma_pool_free buffer-2048, f3e51400/33e51400 (bad dma)
[82732.511630] usb0: unregister 'cdc_ether' usb-0000:00:1d.7-3.1, CDC Ethernet Device
[82734.484447] usb 1-3.1: new full speed USB device using ehci_hcd and address 15
[82749.556362] usb 1-3.1: device descriptor read/64, error -110
[82764.732384] usb 1-3.1: device descriptor read/64, error -110
[82764.908396] usb 1-3.1: new full speed USB device using ehci_hcd and address 16
[82779.981570] usb 1-3.1: device descriptor read/64, error -110
[82795.156421] usb 1-3.1: device descriptor read/64, error -110
[82795.336155] usb 1-3.1: new full speed USB device using ehci_hcd and address 17
[82805.744125] usb 1-3.1: device not accepting address 17, error -110
[82805.816369] usb 1-3.1: new full speed USB device using ehci_hcd and address 18
[82816.224055] usb 1-3.1: device not accepting address 18, error -110
[82816.226361] hub 1-3:1.0: unable to enumerate USB device on port 1
daniel@WingFortress:~$ dmesg | tail -30
[83592.884750] attempt to access beyond end of device
[83592.884753] sdb: rw=0, want=1867767, limit=1867653
[83592.884756] attempt to access beyond end of device
[83592.884759] sdb: rw=0, want=1867768, limit=1867653
[83592.884763] attempt to access beyond end of device
[83592.884766] sdb: rw=0, want=1867769, limit=1867653
[83592.884769] attempt to access beyond end of device
[83592.884773] sdb: rw=0, want=1867770, limit=1867653
[83592.884776] attempt to access beyond end of device
[83592.884779] sdb: rw=0, want=1867771, limit=1867653
[83592.884788] attempt to access beyond end of device
[83592.884792] sdb: rw=0, want=1867772, limit=1867653
[83592.884795] attempt to access beyond end of device
[83592.884798] sdb: rw=0, want=1867773, limit=1867653
[83592.884802] attempt to access beyond end of device
[83592.884805] sdb: rw=0, want=1867774, limit=1867653
[83592.884809] attempt to access beyond end of device
[83592.884812] sdb: rw=0, want=1867775, limit=1867653
[83592.884815] attempt to access beyond end of device
[83592.884818] sdb: rw=0, want=1867776, limit=1867653
[83592.884827] attempt to access beyond end of device
[83592.884830] sdb: rw=0, want=1867772, limit=1867653
[83592.884833] attempt to access beyond end of device
[83592.884837] sdb: rw=0, want=1867773, limit=1867653
[83592.884840] attempt to access beyond end of device
[83592.884843] sdb: rw=0, want=1867774, limit=1867653
[83592.884847] attempt to access beyond end of device
[83592.884850] sdb: rw=0, want=1867775, limit=1867653
[83592.884853] attempt to access beyond end of device
[83592.884856] sdb: rw=0, want=1867776, limit=1867653

it brought up the icon for the memory card inside it but i would like to be able to use my external keyboard while working with it.

---

### Post by Zachs Kappler on 2009-02-10
Ok, I have solved this now. It was the hub I have; it was making my phone read incorrectly. The hub is one of these: [http://www.buzzillions.com/dz_448799_gigaware_usb_7_port_desktop_hub_reviews]("http://www.buzzillions.com/dz_448799_gigaware_usb_7_port_desktop_hub_reviews")

I also learned this thing messes with TI calculators like my TI-84+!

---

