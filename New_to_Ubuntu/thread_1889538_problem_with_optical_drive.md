---
title: "problem with optical drive"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by djembeing on 2011-12-01
I hope someone can help.  My optical drive quit working on my laptop.  It will eject but nothing happens when I put a disc into it.  If I go to Places>computer and try to open it, nothing happens.  I've read a few posts about other people having similar problems but haven't found a solution. 

I tried
dmesg | grep cd
and got 
```

[    1.050751] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.050779] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.050799] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.050805] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.050850] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.050897] ehci_hcd 0000:00:1a.7: debug port 1
[    1.054785] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.054808] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704800
[    1.069021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.069316] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.069334] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.069339] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.069386] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.069431] ehci_hcd 0000:00:1d.7: debug port 1
[    1.073313] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.073334] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704c00
[    1.089045] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.089415] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.089437] uhci_hcd: USB Universal Host Controller Interface driver
[    1.089475] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.089484] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.089489] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.089540] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.089586] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    1.089853] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.089861] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.089866] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.089911] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.089955] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    1.090215] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.090224] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.090228] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.090272] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.090303] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    1.090552] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.090560] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.090565] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.090616] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.090662] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    1.090903] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.090912] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.090916] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.090962] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.090996] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    1.407364] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.424046] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.693037] usb 2-5: new high speed USB device using ehci_hcd and address 2
[ 7306.936080] usb 5-1: new low speed USB device using uhci_hcd and address 2


```And    lshw -C disk

```

*-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7563A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: WX05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: ST9160821AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AL
       serial: 5MA71HDN
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00096650
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
dave@dave-MT6728:~$ [    1.050751] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.050779] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.050799] ehci_hcd 0000:00:1a.7: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.050805] ehci_hcd 0000:00:1a.7: EHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.050850] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.050897] ehci_hcd 0000:00:1a.7: debug port 1
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.054785] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.054808] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704800
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069316] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.069334] ehci_hcd 0000:00:1d.7: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069339] ehci_hcd 0000:00:1d.7: EHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069386] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069431] ehci_hcd 0000:00:1d.7: debug port 1
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.073313] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.073334] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704c00
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089045] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089415] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.089437] uhci_hcd: USB Universal Host Controller Interface driver
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089475] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.089484] uhci_hcd 0000:00:1a.0: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089489] uhci_hcd 0000:00:1a.0: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089540] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089586] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089853] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.089861] uhci_hcd 0000:00:1a.1: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089866] uhci_hcd 0000:00:1a.1: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089911] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089955] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090215] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.090224] uhci_hcd 0000:00:1d.0: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090228] uhci_hcd 0000:00:1d.0: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090272] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090303] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090552] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.090560] uhci_hcd 0000:00:1d.1: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090565] uhci_hcd 0000:00:1d.1: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090616] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090662] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090903] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.090912] uhci_hcd 0000:00:1d.2: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090916] uhci_hcd 0000:00:1d.2: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090962] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090996] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.407364] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.424046] usb 1-1: new high speed USB device using ehci_hcd and address 2
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.693037] usb 2-5: new high speed USB device using ehci_hcd and address 2
bash: [: missing `]'
dave@dave-MT6728:~$ [ 7306.936080] usb 5-1: new low speed USB device using uhci_hcd and address 2
bash: [: missing `]'


```most of this is greek to me. although I wouldn't mind what this stuff means.
I hope someone can help.
 I am relatively new to linux so be nice.

Thanks


guess I should mention that I'm running Ubuntu 10.10 on a Gateway MT 6728 laptop. The drive worked fine up until a few weeks ago.  I would try to burn a CD and whatever app i was using (tried brasero[worked before], K3B, and Gnomebaker) would keep telling me to insert a blank disc.

---

### Post by sandyd on 2011-12-01
> **djembeing said:**
> I hope someone can help.  My optical drive quit working on my laptop.  It will eject but nothing happens when I put a disc into it.  If I go to Places>computer and try to open it, nothing happens.  I've read a few posts about other people having similar problems but haven't found a solution. 

I tried
dmesg | grep cd
and got 
```

[    1.050751] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.050779] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.050799] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.050805] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.050850] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.050897] ehci_hcd 0000:00:1a.7: debug port 1
[    1.054785] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.054808] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704800
[    1.069021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.069316] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.069334] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.069339] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.069386] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.069431] ehci_hcd 0000:00:1d.7: debug port 1
[    1.073313] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.073334] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704c00
[    1.089045] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.089415] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.089437] uhci_hcd: USB Universal Host Controller Interface driver
[    1.089475] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.089484] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.089489] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.089540] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.089586] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    1.089853] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.089861] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.089866] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.089911] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.089955] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    1.090215] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.090224] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.090228] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.090272] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.090303] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    1.090552] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.090560] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.090565] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.090616] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.090662] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    1.090903] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.090912] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.090916] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.090962] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.090996] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    1.407364] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.424046] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.693037] usb 2-5: new high speed USB device using ehci_hcd and address 2
[ 7306.936080] usb 5-1: new low speed USB device using uhci_hcd and address 2


```And    lshw -C disk

```

*-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7563A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: WX05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: ST9160821AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AL
       serial: 5MA71HDN
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00096650
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
dave@dave-MT6728:~$ [    1.050751] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.050779] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.050799] ehci_hcd 0000:00:1a.7: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.050805] ehci_hcd 0000:00:1a.7: EHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.050850] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.050897] ehci_hcd 0000:00:1a.7: debug port 1
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.054785] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.054808] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704800
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069316] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.069334] ehci_hcd 0000:00:1d.7: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069339] ehci_hcd 0000:00:1d.7: EHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069386] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.069431] ehci_hcd 0000:00:1d.7: debug port 1
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.073313] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.073334] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704c00
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089045] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089415] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.089437] uhci_hcd: USB Universal Host Controller Interface driver
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089475] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.089484] uhci_hcd 0000:00:1a.0: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089489] uhci_hcd 0000:00:1a.0: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089540] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089586] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089853] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.089861] uhci_hcd 0000:00:1a.1: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089866] uhci_hcd 0000:00:1a.1: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089911] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.089955] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090215] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.090224] uhci_hcd 0000:00:1d.0: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090228] uhci_hcd 0000:00:1d.0: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090272] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090303] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090552] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.090560] uhci_hcd 0000:00:1d.1: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090565] uhci_hcd 0000:00:1d.1: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090616] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090662] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090903] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
bash: syntax error near unexpected token `('
dave@dave-MT6728:~$ [    1.090912] uhci_hcd 0000:00:1d.2: setting latency timer to 64
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090916] uhci_hcd 0000:00:1d.2: UHCI Host Controller
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090962] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.090996] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.407364] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.424046] usb 1-1: new high speed USB device using ehci_hcd and address 2
bash: [: missing `]'
dave@dave-MT6728:~$ [    1.693037] usb 2-5: new high speed USB device using ehci_hcd and address 2
bash: [: missing `]'
dave@dave-MT6728:~$ [ 7306.936080] usb 5-1: new low speed USB device using uhci_hcd and address 2
bash: [: missing `]'


```most of this is greek to me. although I wouldn't mind what this stuff means.
I hope someone can help.
 I am relatively new to linux so be nice.

Thanks


guess I should mention that I'm running Ubuntu 10.10 on a Gateway MT 6728 laptop. The drive worked fine up until a few weeks ago.  I would try to burn a CD and whatever app i was using (tried brasero[worked before], K3B, and Gnomebaker) would keep telling me to insert a blank disc.
Have you tried using another OS to read the dvd to see if if the drive is broken?

---

### Post by djembeing on 2011-12-07
i tried with the ubuntu 10.10 I have one a jump drive, (the one I originally installed from).  same deal.

---

### Post by djembeing on 2012-01-09
I also realized that the problem started after I took my laptop apart.  Now, I know what you're thinking, but I was VERY careful. Had to repair the power jack. Had to remove the optical drive.  This probably messed something up didn't it. (put it back in)
The drive is getting power, it ejects, and when i put a disc in, the activity light for the drive lights.  Then that's it.  nothing when I click the icon in the computer folder. 
any ideas?

---

### Post by djembeing on 2012-01-16
Still struggling with this issue.  
Uninstalled all burning and ripping apps.  
installed gnomebaker from software center. 
It recognizes the drive, when i go to burn, it ejects and says, "Please insert a disk into the Optiarc DVD RW AD-7563A" I've tried a few brands, including memorex which worked before.

This is what the output window in gnomebaker said:
```

wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Optiarc '
Identification : 'DVD RW AD-7563A '
Revision       : 'WX05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000 (Reserved/Unknown)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Profile: 0xFFFF () 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 721831767 = 704913 KB
FIFO size      : 12582912 = 12288 KB
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
wodim: Cannot load media.

```
:confused:
This is what the terminal said:
```

VST_PATH not set, defaulting to /home/dave/vst:/usr/local/lib/vst:/usr/lib/vst
RemoteVSTClient: all cache files are up-to-date, not running scanner
vendor = Optiarc, model = DVD RW AD-7563A device = p&#65533;&#65533;    &#65533;&#65533;&#65533;    &#65533;&#65533;    &#1069;&#65533;    

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed
Home directory /home/dave not ours.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Home directory /home/dave not ours.
vendor = Optiarc, model = DVD RW AD-7563A device =&#65533;&#65533;    &#65533;&#65533;&#65533;    X`&#65533;    H&#65533;&#65533;    
vendor = Optiarc, model = DVD RW AD-7563A device = &#65533;&#65533;&#65533;    &#65533;&#65533;&#65533;    xby    8&#65533;&#65533;    

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed

(gnomebaker:2153): GStreamer-CRITICAL **: gst_pad_link_full: assertion `GST_PAD_IS_SINK (sinkpad)' failed
Home directory /home/dave not ours.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

```
:confused:

Really wish I could get this drive working.  
Thanks in advance.

---

### Post by djembeing on 2012-03-07
any ideas? :confused:

---

### Post by winh8r on 2012-03-07
Will the laptop boot from a Ubuntu Live CD?


One other thing which you may not have tried is insert a cd which you know to be good (it will play with no problem in another device) Then reboot the laptop with the cd still in the drive. Does this make a difference?

Also, when ejecting use the right click menu and confirm that cd will eject from menu.Rather than button on tray of cd drive.

---

### Post by djembeing on 2012-03-07
Hey, thanks.
I tried your suggestions to no avail. 
I don't have "eject" in the right click menu, but when I type eject in the terminal it pops the try out no prob.  
I tried restarting with an ubuntu live cd (nothin), and puredyne live cd (nuthin), and a Beethoven factory music cd (nuthin).  and yes, i did check the boot order in the bios, (currently, 1. usb drive[which i can boot from] 2. cdrom, 3. hard drive.)

Thanks though.

---

### Post by winh8r on 2012-03-07
Check to see if you have the following packages installed:

```
sudo apt-get install libcdio-cdda0
```

```
sudo apt-get install cdde
```

```
sudo apt-get install ubuntu-restricted-extras
```

try again with various media, pre-recorded, burnt  etc.

If no result then I am starting to suspect that maybe it is related to removing the drive whilst repairing laptop.

I don't know if replacing it and restarting would have removed/corrupted the firmware or not.

Try the above anyway and post back.

---

### Post by djembeing on 2012-03-07
Well, it seems I was missing cdde and ubuntu-restricted-extras.  Looked up those packages and from the descriptions I thought we were onto something.
However, my problem persists.  :confused:  

Thanks so much for your help though.  
I'd appreciate any other suggestions.

---

### Post by winh8r on 2012-03-08
Don't know if you tried this before but give it a go anyway:

```
sudo apt-get remove wodim --purge
```

then 

```
sudo updatedb
```

then

```
sudo apt-get install wodim
```

then

```
sudo apt-get check
```

and finally

```
sudo apt-get update
```

no guarantees, just a thought

---

### Post by djembeing on 2012-03-09
just tried it. no luck.  about to give up on it.  
If you've got anymore ideas let me know.
And thanks so much for your help so far.

---

