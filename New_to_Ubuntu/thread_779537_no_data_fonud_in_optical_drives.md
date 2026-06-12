---
title: "no data fonud in optical drives"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by zen_rasta on 2008-05-02
For some reason i cant burn/read and cd/dvds from my drives. when i click on my cd rom under places>computer its says unable to mount, i have two drives and non of them seem to do any thing i tried music cd , mp3 cd, ubuntu install cds, blanks , nothing happens, i have also look around and did a google search the best i could find was this command  *sudo mount /media/cdrom0/ -o unhide* i tried going straight from the the cd programs even vlc, i just keep getting an unable to mound erorr message

---

### Post by annda on 2008-05-02
are those internal or external drives? please take a look at the output of the dmesg command after you have inserted a cd. and post the relevant bottom part for us.

---

### Post by zen_rasta on 2008-05-03
I tried these two commands and this is what i got:

dmesg | tail
[   84.721982] eth0: no IPv6 routers present
[28025.106051] APIC error on CPU0: 00(40)
[30306.302072] APIC error on CPU0: 40(40)
[35145.200665] APIC error on CPU0: 40(40)
[41955.438817] APIC error on CPU0: 40(40)
[49033.200884] APIC error on CPU0: 40(40)
[88699.460908] APIC error on CPU0: 40(40)
[123205.293644] APIC error on CPU0: 40(40)
[140691.459668] APIC error on CPU0: 40(40)
[152992.288957] APIC error on CPU0: 40(40)
dwim@dwim:~$ dmesg | grep cd
[   22.061554] eth0: SiS 900 PCI Fast Ethernet at 0xa800, IRQ 16, 00:13:d4:4b:cd:a8
[   22.085378] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.085438] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   22.085658] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   22.085672] ohci_hcd 0000:00:03.0: irq 18, io mem 0xde105000
[   22.245033] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   22.245057] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   22.245071] ohci_hcd 0000:00:03.1: irq 19, io mem 0xde106000
[   22.404774] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   22.404793] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   22.404807] ohci_hcd 0000:00:03.2: irq 20, io mem 0xde107000
[   22.548432] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   22.565033] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   22.565055] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   22.565097] ehci_hcd 0000:00:03.3: irq 21, io mem 0xde109000
[   22.736109] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.576913] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   23.862273] usb 1-3: new full speed USB device using ohci_hcd and address 4



****

$ dmesg | grep -i cd
[   22.061554] eth0: SiS 900 PCI Fast Ethernet at 0xa800, IRQ 16, 00:13:d4:4b:cd:a8
[   22.085378] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.085438] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   22.085658] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   22.085672] ohci_hcd 0000:00:03.0: irq 18, io mem 0xde105000
[   22.245033] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   22.245057] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   22.245071] ohci_hcd 0000:00:03.1: irq 19, io mem 0xde106000
[   22.404774] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   22.404793] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   22.404807] ohci_hcd 0000:00:03.2: irq 20, io mem 0xde107000
[   22.548432] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   22.565033] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   22.565055] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   22.565097] ehci_hcd 0000:00:03.3: irq 21, io mem 0xde109000
[   22.736109] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.335354] ata2.01: ATAPI: ASUS    CD-S480/A5, 0.99, max UDMA/33
[   23.507372] scsi 1:0:1:0: CD-ROM            ASUS     CD-S480/A5       0.99 PQ: 0 ANSI: 5
[   23.576913] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   23.576918] Uniform CD-ROM driver Revision: 3.20
[   23.576958] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   23.862273] usb 1-3: new full speed USB device using ohci_hcd and address 4

---

