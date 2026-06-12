---
title: "ubuntu 8.04 camera not being detected"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-05-23
Ubuntu 8.04 not detecting my finePixa700 camera, i cant find anything about it, does anyone know why this hasn't auto detected

---

### Post by HotShotDJ on 2008-05-23
> **ibizatunes said:**
> Ubuntu 8.04 not detecting my finePixa700 camera, i cant find anything about it, does anyone know why this hasn't auto detectedThats interesting.  I know my FinePix (S6000fd) was detected without an issue.

Do you have any memory installed or are you using the built-in memory.  I've heard of others having trouble getting their cameras detected when using only built-in memory.

If that is not the issue, I'd like you to run the following command in a terminal AFTER you plug in the camera and turn it on in PC mode: ```
dmesg
```I don't need the whole thing, just the last 15 to 20 lines.

---

### Post by ibizatunes on 2008-05-23
[  307.960485] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  308.132563] usb 4-1: configuration #1 chosen from 1 choice
[  308.135562] scsi5 : SCSI emulation for USB Mass Storage devices
[  308.135771] usb-storage: device found at 2
[  308.135774] usb-storage: waiting for device to settle before scanning
[  309.875478] usb 4-1: USB disconnect, address 2
[  469.302778] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  469.472841] usb 4-1: configuration #1 chosen from 1 choice
[  469.478381] scsi6 : SCSI emulation for USB Mass Storage devices
[  469.479058] usb-storage: device found at 3
[  469.479062] usb-storage: waiting for device to settle before scanning
[  471.153826] usb 4-1: USB disconnect, address 3
[  617.122333] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  619.652979] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  619.821008] usb 4-2: configuration #1 chosen from 1 choice
[  619.826410] scsi7 : SCSI emulation for USB Mass Storage devices
[  619.827081] usb-storage: device found at 5
[  619.827084] usb-storage: waiting for device to settle before scanning
[  624.826146] usb-storage: device scan complete
[  624.833146] scsi 7:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  624.867101] sd 7:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  624.879088] sd 7:0:0:0: [sdf] Write Protect is off
[  624.879100] sd 7:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  624.879106] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  624.911071] sd 7:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  624.919546] sd 7:0:0:0: [sdf] Write Protect is off
[  624.919556] sd 7:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  624.919560] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  624.919569]  sdf: sdf1
[  624.939335] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[  624.939409] sd 7:0:0:0: Attached scsi generic sg6 type 0
[  633.894290] usb 4-2: USB disconnect, address 5
[  633.940875] scsi 7:0:0:0: rejecting I/O to dead device
[  640.769627] usb 4-2: new full speed USB device using uhci_hcd and address 6
[  649.916710] usb 4-2: new full speed USB device using uhci_hcd and address 7
[  650.083783] usb 4-2: configuration #1 chosen from 1 choice
[  650.086787] scsi8 : SCSI emulation for USB Mass Storage devices
[  650.087217] usb-storage: device found at 7
[  650.087222] usb-storage: waiting for device to settle before scanning
[  653.125984] usb 4-2: USB disconnect, address 7
[  654.138441] usb 4-2: new full speed USB device using uhci_hcd and address 8
[  654.306517] usb 4-2: configuration #1 chosen from 1 choice
[  654.318224] scsi9 : SCSI emulation for USB Mass Storage devices
[  654.318822] usb-storage: device found at 8
[  654.318827] usb-storage: waiting for device to settle before scanning
[  659.318569] usb-storage: device scan complete
[  659.325564] scsi 9:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  659.337545] sd 9:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  659.345538] sd 9:0:0:0: [sdf] Write Protect is off
[  659.345547] sd 9:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  659.345553] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  659.364523] sd 9:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  659.371517] sd 9:0:0:0: [sdf] Write Protect is off
[  659.371523] sd 9:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  659.371528] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  659.371534]  sdf: sdf1
[  659.395909] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[  659.395983] sd 9:0:0:0: Attached scsi generic sg6 type 0
[  716.849751] usb 4-2: USB disconnect, address 8
[  716.872775] scsi 9:0:0:0: rejecting I/O to dead device

---

### Post by ibizatunes on 2008-05-23
lsusb
Bus 005 Device 004: ID 055d:3021 Samsung Electro-Mechanics Co. 
Bus 005 Device 003: ID 04b8:0122 Seiko Epson Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 6993:b001 Freshtel FT-102 VoIP USB Phone
Bus 003 Device 002: ID 04a9:1091 Canon, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by HotShotDJ on 2008-05-23
> **ibizatunes said:**
> [  716.849751] usb 4-2: USB disconnect, address 8
[  716.872775] scsi 9:0:0:0: rejecting I/O to dead deviceUGH.  Thats sure not what I wanted to see. :(  Lets see if something easy corrects this... try plugging the camera into another usb port on a different hub... for example, if you are using a usb port on the front of your computer, try plugging into one of the rear ports.

---

### Post by ibizatunes on 2008-05-23
The camera has a 256 xd card and im using a direct usb cable connect to the dell pc

---

### Post by ibizatunes on 2008-05-23
0000
[  307.960485] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  308.132563] usb 4-1: configuration #1 chosen from 1 choice
[  308.135562] scsi5 : SCSI emulation for USB Mass Storage devices
[  308.135771] usb-storage: device found at 2
[  308.135774] usb-storage: waiting for device to settle before scanning
[  309.875478] usb 4-1: USB disconnect, address 2
[  469.302778] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  469.472841] usb 4-1: configuration #1 chosen from 1 choice
[  469.478381] scsi6 : SCSI emulation for USB Mass Storage devices
[  469.479058] usb-storage: device found at 3
[  469.479062] usb-storage: waiting for device to settle before scanning
[  471.153826] usb 4-1: USB disconnect, address 3
[  617.122333] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  619.652979] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  619.821008] usb 4-2: configuration #1 chosen from 1 choice
[  619.826410] scsi7 : SCSI emulation for USB Mass Storage devices
[  619.827081] usb-storage: device found at 5
[  619.827084] usb-storage: waiting for device to settle before scanning
[  624.826146] usb-storage: device scan complete
[  624.833146] scsi 7:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  624.867101] sd 7:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  624.879088] sd 7:0:0:0: [sdf] Write Protect is off
[  624.879100] sd 7:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  624.879106] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  624.911071] sd 7:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  624.919546] sd 7:0:0:0: [sdf] Write Protect is off
[  624.919556] sd 7:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  624.919560] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  624.919569]  sdf: sdf1
[  624.939335] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[  624.939409] sd 7:0:0:0: Attached scsi generic sg6 type 0
[  633.894290] usb 4-2: USB disconnect, address 5
[  633.940875] scsi 7:0:0:0: rejecting I/O to dead device
[  640.769627] usb 4-2: new full speed USB device using uhci_hcd and address 6
[  649.916710] usb 4-2: new full speed USB device using uhci_hcd and address 7
[  650.083783] usb 4-2: configuration #1 chosen from 1 choice
[  650.086787] scsi8 : SCSI emulation for USB Mass Storage devices
[  650.087217] usb-storage: device found at 7
[  650.087222] usb-storage: waiting for device to settle before scanning
[  653.125984] usb 4-2: USB disconnect, address 7
[  654.138441] usb 4-2: new full speed USB device using uhci_hcd and address 8
[  654.306517] usb 4-2: configuration #1 chosen from 1 choice
[  654.318224] scsi9 : SCSI emulation for USB Mass Storage devices
[  654.318822] usb-storage: device found at 8
[  654.318827] usb-storage: waiting for device to settle before scanning
[  659.318569] usb-storage: device scan complete
[  659.325564] scsi 9:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  659.337545] sd 9:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  659.345538] sd 9:0:0:0: [sdf] Write Protect is off
[  659.345547] sd 9:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  659.345553] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  659.364523] sd 9:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  659.371517] sd 9:0:0:0: [sdf] Write Protect is off
[  659.371523] sd 9:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  659.371528] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  659.371534]  sdf: sdf1
[  659.395909] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[  659.395983] sd 9:0:0:0: Attached scsi generic sg6 type 0
[  716.849751] usb 4-2: USB disconnect, address 8
[  716.872775] scsi 9:0:0:0: rejecting I/O to dead device
[ 2491.446980] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 2491.574910] usb 4-1: device descriptor read/64, error -71
[ 2492.534400] usb 4-1: new full speed USB device using uhci_hcd and address 10
[ 2492.706450] usb 4-1: configuration #1 chosen from 1 choice
[ 2492.717123] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2492.717445] usb-storage: device found at 10
[ 2492.717449] usb-storage: waiting for device to settle before scanning
[ 2495.664731] usb 4-1: USB disconnect, address 10
[ 2512.978348] usb 5-2: USB disconnect, address 3

---

### Post by HotShotDJ on 2008-05-23
No... that is still on bus #4.  We need to move it to another bus (this may or may not work).  Try unplugging either your USB Phone or whatever that Seiko Epson device is and plugging the camera in to the newly freed port.

---

### Post by ibizatunes on 2008-05-23
I cant add it onto another bus without going to my house (im at my g.f house atm)
[  307.960485] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  308.132563] usb 4-1: configuration #1 chosen from 1 choice
[  308.135562] scsi5 : SCSI emulation for USB Mass Storage devices
[  308.135771] usb-storage: device found at 2
[  308.135774] usb-storage: waiting for device to settle before scanning
[  309.875478] usb 4-1: USB disconnect, address 2
[  469.302778] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  469.472841] usb 4-1: configuration #1 chosen from 1 choice
[  469.478381] scsi6 : SCSI emulation for USB Mass Storage devices
[  469.479058] usb-storage: device found at 3
[  469.479062] usb-storage: waiting for device to settle before scanning
[  471.153826] usb 4-1: USB disconnect, address 3
[  617.122333] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  619.652979] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  619.821008] usb 4-2: configuration #1 chosen from 1 choice
[  619.826410] scsi7 : SCSI emulation for USB Mass Storage devices
[  619.827081] usb-storage: device found at 5
[  619.827084] usb-storage: waiting for device to settle before scanning
[  624.826146] usb-storage: device scan complete
[  624.833146] scsi 7:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  624.867101] sd 7:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  624.879088] sd 7:0:0:0: [sdf] Write Protect is off
[  624.879100] sd 7:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  624.879106] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  624.911071] sd 7:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  624.919546] sd 7:0:0:0: [sdf] Write Protect is off
[  624.919556] sd 7:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  624.919560] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  624.919569]  sdf: sdf1
[  624.939335] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[  624.939409] sd 7:0:0:0: Attached scsi generic sg6 type 0
[  633.894290] usb 4-2: USB disconnect, address 5
[  633.940875] scsi 7:0:0:0: rejecting I/O to dead device
[  640.769627] usb 4-2: new full speed USB device using uhci_hcd and address 6
[  649.916710] usb 4-2: new full speed USB device using uhci_hcd and address 7
[  650.083783] usb 4-2: configuration #1 chosen from 1 choice
[  650.086787] scsi8 : SCSI emulation for USB Mass Storage devices
[  650.087217] usb-storage: device found at 7
[  650.087222] usb-storage: waiting for device to settle before scanning
[  653.125984] usb 4-2: USB disconnect, address 7
[  654.138441] usb 4-2: new full speed USB device using uhci_hcd and address 8
[  654.306517] usb 4-2: configuration #1 chosen from 1 choice
[  654.318224] scsi9 : SCSI emulation for USB Mass Storage devices
[  654.318822] usb-storage: device found at 8
[  654.318827] usb-storage: waiting for device to settle before scanning
[  659.318569] usb-storage: device scan complete
[  659.325564] scsi 9:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  659.337545] sd 9:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  659.345538] sd 9:0:0:0: [sdf] Write Protect is off
[  659.345547] sd 9:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  659.345553] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  659.364523] sd 9:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  659.371517] sd 9:0:0:0: [sdf] Write Protect is off
[  659.371523] sd 9:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  659.371528] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  659.371534]  sdf: sdf1
[  659.395909] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[  659.395983] sd 9:0:0:0: Attached scsi generic sg6 type 0
[  716.849751] usb 4-2: USB disconnect, address 8
[  716.872775] scsi 9:0:0:0: rejecting I/O to dead device
[ 2491.446980] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 2491.574910] usb 4-1: device descriptor read/64, error -71
[ 2492.534400] usb 4-1: new full speed USB device using uhci_hcd and address 10
[ 2492.706450] usb 4-1: configuration #1 chosen from 1 choice
[ 2492.717123] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2492.717445] usb-storage: device found at 10
[ 2492.717449] usb-storage: waiting for device to settle before scanning
[ 2495.664731] usb 4-1: USB disconnect, address 10
[ 2512.978348] usb 5-2: USB disconnect, address 3
[ 3768.492059] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_irq_callback - urb status -84
[ 3768.494057] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_ctl_callback - urb status -71
[ 3768.540032] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_irq_callback - urb status -84
[ 3768.542031] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_ctl_callback - urb status -71
[ 3768.560637] usb 3-2: USB disconnect, address 3
[ 3768.562018] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_irq_callback - urb status -108
[ 3768.562025] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_irq_callback - usb_submit_urb failed -19
[ 3771.039306] usb 1-1: USB disconnect, address 4
[ 3772.527513] usb 3-1: USB disconnect, address 2
[ 3772.527858] usblp0: removed
[ 3777.483831] usb 2-2: USB disconnect, address 2
[ 3792.439768] usb 1-2: new low speed USB device using uhci_hcd and address 5
[ 3792.614824] usb 1-2: configuration #1 chosen from 1 choice
[ 3792.631008] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input7
[ 3792.672715] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-2
[ 3822.599714] usb 1-1: new low speed USB device using uhci_hcd and address 6
[ 3822.773181] usb 1-1: configuration #1 chosen from 1 choice
[ 3822.799461] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input8
[ 3822.847499] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1
[ 4043.460865] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 4043.632918] usb 3-1: configuration #1 chosen from 1 choice
[ 4043.663135] scsi11 : SCSI emulation for USB Mass Storage devices
[ 4043.664732] usb-storage: device found at 4
[ 4043.664747] usb-storage: waiting for device to settle before scanning
[ 4044.688239] usb 3-1: USB disconnect, address 4
[ 4055.634316] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 4055.816372] usb 3-1: configuration #1 chosen from 1 choice
[ 4055.821843] scsi12 : SCSI emulation for USB Mass Storage devices
[ 4055.822503] usb-storage: device found at 5
[ 4055.822507] usb-storage: waiting for device to settle before scanning
[ 4056.086107] usb 3-1: USB disconnect, address 5

---

### Post by ibizatunes on 2008-05-23
Im think of flashing my BOIS on my g.f machine, do you think this would help?
[http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R112383&formatcnt=1&libid=0&fileid=147022](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R112383&formatcnt=1&libid=0&fileid=147022)

5. Add PCI BUS resource reservations for USB 2.0 and ACPI

Could that explain why it is failing to read / write to the camera

Sadly the motherboard doenst have a separate bus for USB so i cant use anything else

---

### Post by HotShotDJ on 2008-05-23
Well, you managed to move it to bus #3 with no effect.  I've been using Google to see if anything turned up for "scsi 9:0:0:0: rejecting I/O to dead device" and several reports of this problem for various devices have turned up.  However, I've not yet found a solution.  Having looked for and ruled out "horses," we may have to wait and see if somebody else is aware of some "zebras."

---

### Post by ibizatunes on 2008-05-23
I have just tried a different camera a samsung digimax a502 and the same nothing!!
[   12.829854]   MEM window: efc00000-efcfffff
[   12.829858]   PREFETCH window: disabled.
[   12.829863] PCI: Bridge: 0000:00:1e.0
[   12.829866]   IO window: c000-cfff
[   12.829871]   MEM window: efb00000-efbfffff
[   12.829875]   PREFETCH window: disabled.
[   12.829894] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.829900] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   12.829919] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.829924] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.829936] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   12.829947] NET: Registered protocol family 2
[   12.867122] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.867422] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.867997] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   12.868286] TCP: Hash tables configured (established 131072 bind 65536)
[   12.868289] TCP reno registered
[   12.879201] checking if image is initramfs... it is
[   13.495106] Freeing initrd memory: 7704k freed
[   13.495263] Simple Boot Flag at 0x7a set to 0x1
[   13.495777] audit: initializing netlink socket (disabled)
[   13.495791] audit(1211571081.020:1): initialized
[   13.496003] highmem bounce pool size: 64 pages
[   13.498412] VFS: Disk quotas dquot_6.5.1
[   13.498501] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.498656] io scheduler noop registered
[   13.498658] io scheduler anticipatory registered
[   13.498660] io scheduler deadline registered
[   13.498672] io scheduler cfq registered (default)
[   13.498770] Boot video device is 0000:01:00.0
[   13.498778] PCI: Firmware left 0000:03:08.0 e100 interrupts enabled, disabling
[   13.498918] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.498960] assign_interrupt_mode Found MSI capability
[   13.498997] Allocate Port Service[0000:00:01.0:pcie00]
[   13.499091] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.499137] assign_interrupt_mode Found MSI capability
[   13.499174] Allocate Port Service[0000:00:1c.0:pcie00]
[   13.499217] Allocate Port Service[0000:00:1c.0:pcie02]
[   13.499539] isapnp: Scanning for PnP cards...
[   13.851325] isapnp: No Plug & Play device found
[   13.888639] Real Time Clock Driver v1.12ac
[   13.888750] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.890173] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.890254] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   13.890437] PNP: No PS/2 controller found. Probing ports directly.
[   13.892997] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.893004] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.910634] mice: PS/2 mouse device common for all mice
[   13.910786] EISA: Probing bus 0 at eisa.0
[   13.910790] EISA: Cannot allocate resource for mainboard
[   13.910797] Cannot allocate resource for EISA slot 2
[   13.910820] EISA: Detected 0 cards.
[   13.910823] cpuidle: using governor ladder
[   13.910826] cpuidle: using governor menu
[   13.910909] NET: Registered protocol family 1
[   13.910940] Using IPI No-Shortcut mode
[   13.910970] registered taskstats version 1
[   13.911074]   Magic number: 8:216:547
[   13.911180] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   13.911183] EDD information not available.
[   13.911391] Freeing unused kernel memory: 364k freed
[   15.149285] fuse init (API version 7.9)
[   15.218919] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   15.218934] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   15.390976] usbcore: registered new interface driver usbfs
[   15.391010] usbcore: registered new interface driver hub
[   15.398762] usbcore: registered new device driver usb
[   15.401765] USB Universal Host Controller Interface driver v3.0
[   15.401835] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 17
[   15.401856] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   15.401862] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   15.402118] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   15.402155] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000ff80
[   15.402361] usb usb1: configuration #1 chosen from 1 choice
[   15.402403] hub 1-0:1.0: USB hub found
[   15.402413] hub 1-0:1.0: 2 ports detected
[   15.506808] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 18
[   15.506831] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   15.506837] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   15.506874] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   15.506914] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[   15.507105] usb usb2: configuration #1 chosen from 1 choice
[   15.507148] hub 2-0:1.0: USB hub found
[   15.507159] hub 2-0:1.0: 2 ports detected
[   15.610742] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   15.610762] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   15.610768] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   15.610810] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   15.610843] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000ff40
[   15.611014] usb usb3: configuration #1 chosen from 1 choice
[   15.611054] hub 3-0:1.0: USB hub found
[   15.611063] hub 3-0:1.0: 2 ports detected
[   15.714717] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 20
[   15.714735] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   15.714742] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   15.714779] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   15.714812] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000ff20
[   15.714983] usb usb4: configuration #1 chosen from 1 choice
[   15.715022] hub 4-0:1.0: USB hub found
[   15.715032] hub 4-0:1.0: 2 ports detected
[   15.746548] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   15.770871] SCSI subsystem initialized
[   15.799102] libata version 3.00 loaded.
[   15.818674] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   15.818729] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   15.818751] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   15.818787] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
[   15.818821] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   15.818838] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   15.818882] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 17
[   15.818899] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   15.818904] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   15.818941] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   15.822846] ehci_hcd 0000:00:1d.7: debug port 1
[   15.822854] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   15.822864] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xffa80800
[   15.874474] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.874645] usb usb5: configuration #1 chosen from 1 choice
[   15.874686] hub 5-0:1.0: USB hub found
[   15.874696] hub 5-0:1.0: 8 ports detected
[   15.880282] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   15.880288] e100: Copyright(c) 1999-2006 Intel Corporation
[   15.978577] ata_piix 0000:00:1f.1: version 2.12
[   15.978601] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   15.978654] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   15.980615] scsi0 : ata_piix
[   15.981393] scsi1 : ata_piix
[   15.981472] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   15.981475] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   16.277294] usb 1-1: device not accepting address 2, error -71
[   16.301664] ata1.00: ATAPI: _NEC DVD+/-RW ND-3530A, 102B, max UDMA/33
[   16.473472] ata1.00: configured for UDMA/33
[   16.473526] ata2: port disabled. ignoring.
[   16.474627] scsi 0:0:0:0: CD-ROM            _NEC     DVD+-RW ND-3530A 102B PQ: 0 ANSI: 5
[   16.474723] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   16.629074] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
[   16.629115] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   16.629165] scsi2 : ata_piix
[   16.629349] scsi3 : ata_piix
[   16.629391] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 21
[   16.629395] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 21
[   16.806138] ata3.00: ATA-8: WDC WD3200AAKS-00YGA0, 12.01C02, max UDMA/133
[   16.806144] ata3.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   16.821734] ata3.00: configured for UDMA/133
[   17.396650] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   17.532589] usb 5-2: configuration #1 chosen from 1 choice
[   17.649676] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 12.0 PQ: 0 ANSI: 5
[   17.650110] ACPI: PCI Interrupt 0000:03:02.2[B] -> GSI 19 (level, low) -> IRQ 22
[   17.699853] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[efbea800-efbeafff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   17.704426] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   17.724584] e100: eth0: e100_probe: addr 0xefbeb000, irq 21, MAC addr 00:12:3f:95:90:48
[   17.737252] Driver 'sd' needs updating - please use bus_type methods
[   17.737376] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   17.737400] sd 2:0:0:0: [sda] Write Protect is off
[   17.737406] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.737443] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.737517] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   17.737534] sd 2:0:0:0: [sda] Write Protect is off
[   17.737537] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.737566] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.737571]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   17.744418] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   17.744423] Uniform CD-ROM driver Revision: 3.20
[   17.744496] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   17.757532]  sda5 >
[   17.757651] sd 2:0:0:0: [sda] Attached SCSI disk
[   17.765759] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   17.765797] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   17.812440] usb 5-3: new high speed USB device using ehci_hcd and address 4
[   17.947116] usb 5-3: configuration #1 chosen from 1 choice
[   17.987179] Attempting manual resume
[   17.987184] swsusp: Resume From Partition 8:5
[   17.987186] PM: Checking swsusp image.
[   17.987360] PM: Resume from disk failed.
[   18.030888] kjournald starting.  Commit interval 5 seconds
[   18.030897] EXT3-fs: mounted filesystem with ordered data mode.
[   18.608101] usbcore: registered new interface driver libusual
[   18.755017] Initializing USB Mass Storage driver...
[   18.847872] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   18.971935] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0191076c42]
[   19.021938] usb 2-2: configuration #1 chosen from 1 choice
[   19.279651] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   19.451856] usb 3-1: configuration #1 chosen from 1 choice
[   19.691416] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   19.853642] usb 3-2: configuration #1 chosen from 1 choice
[   19.865673] scsi4 : SCSI emulation for USB Mass Storage devices
[   19.865735] usb-storage: device found at 4
[   19.865739] usb-storage: waiting for device to settle before scanning
[   19.865766] usbcore: registered new interface driver usb-storage
[   19.865770] USB Mass Storage support registered.
[   20.103195] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   20.278589] usb 1-1: configuration #1 chosen from 1 choice
[   23.674153] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.710373] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.778113] Linux agpgart interface v0.102
[   23.830225] iTCO_vendor_support: vendor-support=0
[   23.862247] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   23.862778] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   23.862849] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.961931] intel_rng: Firmware space is locked read-only. If you can't or
[   23.961935] intel_rng: don't want to disable this in firmware setup, and if
[   23.961937] intel_rng: you are certain that your system has a functional
[   23.961939] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   24.355638] input: PC Speaker as /devices/platform/pcspkr/input/input1
[   24.625000] input: Power Button (FF) as /devices/virtual/input/input2
[   24.652759] ACPI: Power Button (FF) [PWRF]
[   24.652874] input: Power Button (CM) as /devices/virtual/input/input3
[   24.680741] ACPI: Power Button (CM) [VBTN]
[   24.861539] usb-storage: device scan complete
[   24.863449] scsi 4:0:0:0: Direct-Access     Samsung  CF Card       CF 1.6E PQ: 0 ANSI: 0 CCS
[   24.865315] scsi 4:0:0:1: Direct-Access     Samsung  MS Card       MS 1.6E PQ: 0 ANSI: 0 CCS
[   24.867189] scsi 4:0:0:2: Direct-Access     Samsung  SD Card   MMC/SD 1.6E PQ: 0 ANSI: 0 CCS
[   24.868937] scsi 4:0:0:3: Direct-Access     Samsung  SM/XD Card    SM 1.6E PQ: 0 ANSI: 0 CCS
[   24.870498] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   24.870567] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   24.871723] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   24.871788] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   24.872978] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   24.873041] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   24.874217] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   24.874277] sd 4:0:0:3: Attached scsi generic sg5 type 0
[   24.974715] usbcore: registered new interface driver hiddev
[   25.005000] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input4
[   25.020627] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2
[   25.038184] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input5
[   25.064643] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[   25.064669] usbcore: registered new interface driver usbhid
[   25.064675] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.277142] gameport: EMU10K1 is pci0000:03:02.1/gameport0, io 0xcc70, speed 451kHz
[   25.827449] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   25.841195] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1091
[   25.841231] usbcore: registered new interface driver usblp
[   25.994114] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[   25.994172] [fglrx] ASYNCIO init succeed!
[   25.995489] [fglrx] PAT is enabled successfully!
[   26.008036] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   26.065318] input: Yealink usb-p1k as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.3/input/input6
[   26.140128] usbcore: registered new interface driver yealink
[   26.140137] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: Yealink phone driver:yld-20051230
[   26.583348] usbcore: registered new interface driver snd-usb-audio
[   26.881339] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 18 (level, low) -> IRQ 19
[   26.885872] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 [SB0350b]
[   26.993655] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   28.557796] lp: driver loaded but no devices found
[   28.717520] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   29.276247] EXT3 FS on sda1, internal journal
[   30.413139] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.900032] No dock devices found.
[   31.977930] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   31.977938] apm: disabled - APM is not SMP safe.
[   32.191572] ppdev: user-space parallel port driver
[   32.317496] audit(1211571099.849:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5086 profile="/usr/sbin/cupsd" namespace="default"
[   33.553068] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   33.643767] Bluetooth: Core ver 2.11
[   33.645521] NET: Registered protocol family 31
[   33.645528] Bluetooth: HCI device and connection manager initialized
[   33.645534] Bluetooth: HCI socket layer initialized
[   33.694862] Bluetooth: L2CAP ver 2.9
[   33.694869] Bluetooth: L2CAP socket layer initialized
[   33.767698] Bluetooth: RFCOMM socket layer initialized
[   33.767717] Bluetooth: RFCOMM TTY layer initialized
[   33.767720] Bluetooth: RFCOMM ver 1.8
[   36.063769] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.772990] NET: Registered protocol family 17
[   38.159769] NET: Registered protocol family 10
[   38.160158] lo: Disabled Privacy Extensions
[   39.284068] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   39.284076] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[   39.284084] [fglrx] Reserve Block - 2 offset =  0X7fbf000 length = 0X40000
[   39.430421] [fglrx] interrupt source 20008000 successfully enabled
[   39.430428] [fglrx] enable ID = 0x00000004
[   39.430440] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   39.430541] [fglrx] interrupt source 10000000 successfully enabled
[   39.430546] [fglrx] enable ID = 0x00000005
[   39.430552] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   48.479942] eth0: no IPv6 routers present
[  281.689334] [fglrx] interrupt source 10000000 successfully disabled!
[  281.689340] [fglrx] enable ID = 0x00000000
[  281.689346] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000005
[  281.689366] [fglrx] interrupt source 20008000 successfully disabled!
[  281.689371] [fglrx] enable ID = 0x00000000
[  281.689375] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000004
[  286.683275] [fglrx] PCIe has already been initialized. Reinitializing ...
[  286.703052] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  286.703059] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[  286.703065] [fglrx] Reserve Block - 2 offset =  0X7fbf000 length = 0X40000
[  286.828600] [fglrx] interrupt source 20008000 successfully enabled
[  286.828609] [fglrx] enable ID = 0x00000004
[  286.829409] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  286.829755] [fglrx] interrupt source 10000000 successfully enabled
[  286.829760] [fglrx] enable ID = 0x00000005
[  286.829767] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  307.960485] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  308.132563] usb 4-1: configuration #1 chosen from 1 choice
[  308.135562] scsi5 : SCSI emulation for USB Mass Storage devices
[  308.135771] usb-storage: device found at 2
[  308.135774] usb-storage: waiting for device to settle before scanning
[  309.875478] usb 4-1: USB disconnect, address 2
[  469.302778] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  469.472841] usb 4-1: configuration #1 chosen from 1 choice
[  469.478381] scsi6 : SCSI emulation for USB Mass Storage devices
[  469.479058] usb-storage: device found at 3
[  469.479062] usb-storage: waiting for device to settle before scanning
[  471.153826] usb 4-1: USB disconnect, address 3
[  617.122333] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  619.652979] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  619.821008] usb 4-2: configuration #1 chosen from 1 choice
[  619.826410] scsi7 : SCSI emulation for USB Mass Storage devices
[  619.827081] usb-storage: device found at 5
[  619.827084] usb-storage: waiting for device to settle before scanning
[  624.826146] usb-storage: device scan complete
[  624.833146] scsi 7:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  624.867101] sd 7:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  624.879088] sd 7:0:0:0: [sdf] Write Protect is off
[  624.879100] sd 7:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  624.879106] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  624.911071] sd 7:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  624.919546] sd 7:0:0:0: [sdf] Write Protect is off
[  624.919556] sd 7:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  624.919560] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  624.919569]  sdf: sdf1
[  624.939335] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[  624.939409] sd 7:0:0:0: Attached scsi generic sg6 type 0
[  633.894290] usb 4-2: USB disconnect, address 5
[  633.940875] scsi 7:0:0:0: rejecting I/O to dead device
[  640.769627] usb 4-2: new full speed USB device using uhci_hcd and address 6
[  649.916710] usb 4-2: new full speed USB device using uhci_hcd and address 7
[  650.083783] usb 4-2: configuration #1 chosen from 1 choice
[  650.086787] scsi8 : SCSI emulation for USB Mass Storage devices
[  650.087217] usb-storage: device found at 7
[  650.087222] usb-storage: waiting for device to settle before scanning
[  653.125984] usb 4-2: USB disconnect, address 7
[  654.138441] usb 4-2: new full speed USB device using uhci_hcd and address 8
[  654.306517] usb 4-2: configuration #1 chosen from 1 choice
[  654.318224] scsi9 : SCSI emulation for USB Mass Storage devices
[  654.318822] usb-storage: device found at 8
[  654.318827] usb-storage: waiting for device to settle before scanning
[  659.318569] usb-storage: device scan complete
[  659.325564] scsi 9:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  659.337545] sd 9:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  659.345538] sd 9:0:0:0: [sdf] Write Protect is off
[  659.345547] sd 9:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  659.345553] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  659.364523] sd 9:0:0:0: [sdf] 512000 512-byte hardware sectors (262 MB)
[  659.371517] sd 9:0:0:0: [sdf] Write Protect is off
[  659.371523] sd 9:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  659.371528] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[  659.371534]  sdf: sdf1
[  659.395909] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[  659.395983] sd 9:0:0:0: Attached scsi generic sg6 type 0
[  716.849751] usb 4-2: USB disconnect, address 8
[  716.872775] scsi 9:0:0:0: rejecting I/O to dead device
[ 2491.446980] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 2491.574910] usb 4-1: device descriptor read/64, error -71
[ 2492.534400] usb 4-1: new full speed USB device using uhci_hcd and address 10
[ 2492.706450] usb 4-1: configuration #1 chosen from 1 choice
[ 2492.717123] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2492.717445] usb-storage: device found at 10
[ 2492.717449] usb-storage: waiting for device to settle before scanning
[ 2495.664731] usb 4-1: USB disconnect, address 10
[ 2512.978348] usb 5-2: USB disconnect, address 3
[ 3768.492059] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_irq_callback - urb status -84
[ 3768.494057] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_ctl_callback - urb status -71
[ 3768.540032] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_irq_callback - urb status -84
[ 3768.542031] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_ctl_callback - urb status -71
[ 3768.560637] usb 3-2: USB disconnect, address 3
[ 3768.562018] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_irq_callback - urb status -108
[ 3768.562025] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: urb_irq_callback - usb_submit_urb failed -19
[ 3771.039306] usb 1-1: USB disconnect, address 4
[ 3772.527513] usb 3-1: USB disconnect, address 2
[ 3772.527858] usblp0: removed
[ 3777.483831] usb 2-2: USB disconnect, address 2
[ 3792.439768] usb 1-2: new low speed USB device using uhci_hcd and address 5
[ 3792.614824] usb 1-2: configuration #1 chosen from 1 choice
[ 3792.631008] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input7
[ 3792.672715] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-2
[ 3822.599714] usb 1-1: new low speed USB device using uhci_hcd and address 6
[ 3822.773181] usb 1-1: configuration #1 chosen from 1 choice
[ 3822.799461] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input8
[ 3822.847499] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1
[ 4043.460865] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 4043.632918] usb 3-1: configuration #1 chosen from 1 choice
[ 4043.663135] scsi11 : SCSI emulation for USB Mass Storage devices
[ 4043.664732] usb-storage: device found at 4
[ 4043.664747] usb-storage: waiting for device to settle before scanning
[ 4044.688239] usb 3-1: USB disconnect, address 4
[ 4055.634316] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 4055.816372] usb 3-1: configuration #1 chosen from 1 choice
[ 4055.821843] scsi12 : SCSI emulation for USB Mass Storage devices
[ 4055.822503] usb-storage: device found at 5
[ 4055.822507] usb-storage: waiting for device to settle before scanning
[ 4056.086107] usb 3-1: USB disconnect, address 5
[ 4398.685944] usb 5-7: new high speed USB device using ehci_hcd and address 30
[ 4398.820733] usb 5-7: configuration #1 chosen from 1 choice
[ 4398.825896] scsi13 : SCSI emulation for USB Mass Storage devices
[ 4398.826582] usb-storage: device found at 30
[ 4398.826586] usb-storage: waiting for device to settle before scanning
[ 4403.823361] usb-storage: device scan complete
[ 4403.823975] scsi 13:0:0:0: Direct-Access     DW       PND1GSKS10103D   1.00 PQ: 0 ANSI: 2
[ 4403.825727] sd 13:0:0:0: [sdf] 2039040 512-byte hardware sectors (1044 MB)
[ 4403.826338] sd 13:0:0:0: [sdf] Write Protect is off
[ 4403.826345] sd 13:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 4403.826349] sd 13:0:0:0: [sdf] Assuming drive cache: write through
[ 4403.828957] sd 13:0:0:0: [sdf] 2039040 512-byte hardware sectors (1044 MB)
[ 4403.829583] sd 13:0:0:0: [sdf] Write Protect is off
[ 4403.829589] sd 13:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 4403.829592] sd 13:0:0:0: [sdf] Assuming drive cache: write through
[ 4403.829598]  sdf: sdf1
[ 4403.830437] sd 13:0:0:0: [sdf] Attached SCSI removable disk
[ 4403.830507] sd 13:0:0:0: Attached scsi generic sg6 type 0
[ 4425.477157] usb 5-7: USB disconnect, address 30
[ 5595.830542] usb 3-1: new full speed USB device using uhci_hcd and address 6
[ 5595.954483] usb 3-1: device descriptor read/64, error -71
[ 5596.182362] usb 3-1: device descriptor read/64, error -71
[ 5596.398243] usb 3-1: new full speed USB device using uhci_hcd and address 7
[ 5596.522178] usb 3-1: device descriptor read/64, error -71
[ 5596.750046] usb 3-1: device descriptor read/64, error -71
[ 5596.965937] usb 3-1: new full speed USB device using uhci_hcd and address 8
[ 5597.381711] usb 3-1: device not accepting address 8, error -71
[ 5597.493650] usb 3-1: new full speed USB device using uhci_hcd and address 9
[ 5597.909422] usb 3-1: device not accepting address 9, error -71

This is my full post! With the samsung camera in it!
Any ideas would be used!!

---

### Post by HotShotDJ on 2008-05-23
> **ibizatunes said:**
> [ 5597.909422] usb 3-1: device not accepting address 9, error -71Ok... THIS error I've seen before.  It suggests some kind of conflict between the USB port and some other piece of hardware... which brings us back to the changing around what ports you plug into.  In one case, we moved the user's PCI USB card to another PCI slot, which corrected the error.  If you are using a PCI card for the USB ports, you might try that.  If not, it is going to be a matter of finding a port that is using a different IRQ address.

---

