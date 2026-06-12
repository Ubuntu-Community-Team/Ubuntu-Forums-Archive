---
title: "Errors were found while checking the disk drive for /."
date: 2015-09-12
forum: New to Ubuntu
---

### Post by andyl2 on 2015-09-12
I've been using Ubuntu 14.04 for some time now, this is the only OS on my pc, and everything has been great until recently when I began to get the 'Errors were found while checking the disk drive for /.' problem when booting.
I know this has come up before and I know to edit grub and change ro to rw press f10 and everything boots just fine.
But my question is - how can I make this fix permanent? I've spent hours searching for an answer and all I can come up with is to edit the file '10_lupin'. Problem is I don't have that file, only '10_linux' and being a complete noob with linux didn't really want to tinker with it in case bad things happen. Does anyone have an answer?

---

### Post by dino99 on 2015-09-12
Looks like a non genuine installation. Maybe you have tweaked a lot and installed packages found outside the ubuntu archive.
By no means your boot line should be rw (only ro for security, which is the default)
If your logs (/var/log/dmesg,...) does not help you identifying the root cause, then maybe its time to do a fresh install )
You can also first erase the .Xauthority file (ctrl+h to unhide it), it will be cleanly recreated on the next boot.

:P

---

### Post by stalkingwolf on 2015-09-12
if this is a recurring problem maybe you actually do have problems developing with the drive.  I use the hard drive regenerator on the Hirens disk to fix this.  Most recently i did this and was able to rescue all the pics and files.

---

### Post by efflandt on 2015-09-13
From a terminal window you can type **dmesg | less** and look though that for any errors related to your hard drive, or also **less /var/log/syslog**.

The Linux partition at the far end of my drive (where sectors are physically smaller closer to center of platters) began failing when my drive on my desktop PC was 3 years old and I got into Steam which was filling up that partition with games to the end of the drive. The first symptom was when I suddenly did not have permission to save files, because when Linux noticed problems, it automatically remounted the drive read-only to preserve it. Fortunately I had another Ubuntu system on SSD and from there could use e2fsck with some options to repair it and lock out bad blocks. That got me by for a while, but eventually I replaced the drive. But before I did that I shrunk Win7's partition using its own Disk Management before imaging its partitions to the new drive, so I would have more room for Linux. After that I copied over my home directory from the old drive and there were only a few corrupted game files that Steam redownloaded when verifying integrity of game cache.

Drives reserve some space to automatically transparently remap good sectors in place of bad sectors. So if you start actual seeing bad sectors when checking a drive or errors in your logs reading the drive or your system spontaneously remounts read-only, it may mean that all of the error sites are used up and the drive can only get worse. One way to check a drive is with "smartctl", for example **sudo smartctl -a /dev/sda** and look through that. Seagate and Western Digital also have diagnostic programs that can do a quick test or extended test (there is DOS version that can be booted from USB).

---

### Post by andyl2 on 2015-09-13
Thanks for the input guys. I really hope there isn't a problem with the disk, it's only a few months old!

I appreciate using the work around isn't perfect but at least it does get the machine up and running normally.

I've checked the logs and there are several errors showing...

```

[    1.397430] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.398203] ata1.00: ATA-9: WDC WD10EZEX-08M2NA0, 01.01A01, max UDMA/100
[    1.398209] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.399063] ata1.00: configured for UDMA/100
[    1.399458] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EZEX-08M 1A01 PQ: 0 ANSI: 5
[    1.400102] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.400105] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.400130] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.400134] sd 0:0:0:0: [sda] Write Protect is off
[    1.400136] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.400147] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.413775] firewire_core 0000:05:00.0: created device fw0: GUID 001e8c0000307027, S400
[    1.438009]  sda: sda1 sda2 < sda5 >
[    1.438980] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.465905] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.465911] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.466439] hub 2-1:1.0: USB hub found
[    1.466615] hub 2-1:1.0: 8 ports detected
[    1.537577] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    1.632091] usb 1-1.3: New USB device found, idVendor=058f, idProduct=6362
[    1.632097] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.632101] usb 1-1.3: Product: Mass Storage Device
[    1.632104] usb 1-1.3: Manufacturer: Generic
[    1.632107] usb 1-1.3: SerialNumber: 058F312D81B
[    1.635610] usb-storage 1-1.3:1.0: USB Mass Storage device detected
[    1.635849] scsi6 : usb-storage 1-1.3:1.0
[    1.635900] usbcore: registered new interface driver usb-storage
[    1.637572] usbcore: registered new interface driver uas
[    1.688603] random: lvm urandom read with 38 bits of entropy available
[    1.717901] ata2: SATA link down (SStatus 0 SControl 300)
[    1.733807] tsc: Refined TSC clocksource calibration: 2801.593 MHz
[    1.737801] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[    1.833378] usb 2-1.5: New USB device found, idVendor=046d, idProduct=c245
[    1.833384] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.833388] usb 2-1.5: Product: Gaming Mouse G400
[    1.833392] usb 2-1.5: Manufacturer: Logitech
[    1.837808] hidraw: raw HID events driver (C) Jiri Kosina
[    1.841846] usbcore: registered new interface driver usbhid
[    1.841847] usbhid: USB HID core driver
[    1.843354] input: Logitech Gaming Mouse G400 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/0003:046D:C245.0001/input/input3
[    1.843597] hid-generic 0003:046D:C245.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Gaming Mouse G400] on usb-0000:00:1d.0-1.5/input0
[    1.844281] hid-generic 0003:046D:C245.0002: hiddev0,hidraw1: USB HID v1.10 Device [Logitech Gaming Mouse G400] on usb-0000:00:1d.0-1.5/input1
[    2.038308] ata3: SATA link down (SStatus 0 SControl 300)
[    2.358769] ata4: SATA link down (SStatus 0 SControl 300)
[    2.636370] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.637237] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.638102] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.638951] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.639431] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    2.639682] sd 6:0:0:1: Attached scsi generic sg2 type 0
[    2.639978] sd 6:0:0:2: Attached scsi generic sg3 type 0
[    2.640148] sd 6:0:0:3: Attached scsi generic sg4 type 0
[    2.658174] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.659002] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.659740] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    2.660472] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    2.735754] Switched to clocksource tsc
[    2.851429] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.853130] ata5.00: ATAPI: Optiarc DVD RW AD-7260S, 1.00, max UDMA/100
[    2.855184] ata5.00: configured for UDMA/100
[    2.856918] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.00 PQ: 0 ANSI: 5
[    2.873191] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.873196] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.873533] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.873605] sr 4:0:0:0: Attached scsi generic sg5 type 5
[    3.191860] ata6: SATA link down (SStatus 0 SControl 300)
[    3.194456] scsi7 : pata_marvell
[    3.194843] scsi8 : pata_marvell
[    3.194943] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    3.194947] ata8: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[    3.864847] floppy0: no floppy controllers found
[    3.864860] work still pending
[    4.244926] random: nonblocking pool is initialized
[    5.227154] EXT4-fs (dm-0): warning: mounting fs with errors, running e2fsck is recommended
[    5.237869] EXT4-fs (dm-0): recovery complete
[    5.275273] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   10.854525] ata1.00: exception Emask 0x0 SAct 0x18000000 SErr 0x0 action 0x0
[   10.854532] ata1.00: irq_stat 0x40000008
[   10.854538] ata1.00: failed command: READ FPDMA QUEUED
[   10.854546] ata1.00: cmd 60/00:d8:c0:b2:c7/01:00:47:00:00/40 tag 27 ncq 131072 in
[   10.854546]          res 41/40:00:00:b3:c7/00:00:47:00:00/00 Emask 0x409 (media error) <F>
[   10.854551] ata1.00: status: { DRDY ERR }
[   10.854554] ata1.00: error: { UNC }
[   10.856131] ata1.00: configured for UDMA/100
[   10.856162] sd 0:0:0:0: [sda]  
[   10.856166] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   10.856169] sd 0:0:0:0: [sda]  
[   10.856171] Sense Key : Medium Error [current] [descriptor]
[   10.856176] Descriptor sense data with sense descriptors (in hex):
[   10.856178]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   10.856190]         47 c7 b3 00 
[   10.856196] sd 0:0:0:0: [sda]  
[   10.856199] Add. Sense: Unrecovered read error - auto reallocate failed
[   10.856202] sd 0:0:0:0: [sda] CDB: 
[   10.856204] Read(10): 28 00 47 c7 b2 c0 00 01 00 00
[   10.856215] end_request: I/O error, dev sda, sector 1204269824
[   10.856220] Buffer I/O error on device dm-0, logical block 150470752
[   10.856224] Buffer I/O error on device dm-0, logical block 150470753
[   10.856227] Buffer I/O error on device dm-0, logical block 150470754
[   10.856230] Buffer I/O error on device dm-0, logical block 150470755
[   10.856233] Buffer I/O error on device dm-0, logical block 150470756
[   10.856236] Buffer I/O error on device dm-0, logical block 150470757
[   10.856239] Buffer I/O error on device dm-0, logical block 150470758
[   10.856242] Buffer I/O error on device dm-0, logical block 150470759
[   10.856246] Buffer I/O error on device dm-0, logical block 150470760
[   10.856249] Buffer I/O error on device dm-0, logical block 150470761
[   10.856275] ata1: EH complete
[   15.044222] ata1.00: exception Emask 0x0 SAct 0x60000001 SErr 0x0 action 0x0
[   15.044228] ata1.00: irq_stat 0x40000008
[   15.044233] ata1.00: failed command: READ FPDMA QUEUED
[   15.044242] ata1.00: cmd 60/08:f0:00:b3:c7/00:00:47:00:00/40 tag 30 ncq 4096 in
[   15.044242]          res 41/40:00:00:b3:c7/00:00:47:00:00/00 Emask 0x409 (media error) <F>
[   15.044246] ata1.00: status: { DRDY ERR }
[   15.044249] ata1.00: error: { UNC }
[   15.045886] ata1.00: configured for UDMA/100
[   15.045905] sd 0:0:0:0: [sda]  
[   15.045908] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.045911] sd 0:0:0:0: [sda]  
[   15.045914] Sense Key : Medium Error [current] [descriptor]
[   15.045918] Descriptor sense data with sense descriptors (in hex):
[   15.045920]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   15.045931]         47 c7 b3 00 
[   15.045937] sd 0:0:0:0: [sda]  
[   15.045940] Add. Sense: Unrecovered read error - auto reallocate failed
[   15.045943] sd 0:0:0:0: [sda] CDB: 
[   15.045945] Read(10): 28 00 47 c7 b3 00 00 00 08 00
[   15.045955] end_request: I/O error, dev sda, sector 1204269824
[   15.045972] ata1: EH complete
[   19.810645] ata1.00: exception Emask 0x0 SAct 0x7c0407ff SErr 0x0 action 0x0
[   19.810652] ata1.00: irq_stat 0x40000008
[   19.810658] ata1.00: failed command: READ FPDMA QUEUED
[   19.810667] ata1.00: cmd 60/08:d0:00:b3:c7/00:00:47:00:00/40 tag 26 ncq 4096 in
[   19.810667]          res 41/40:00:00:b3:c7/00:00:47:00:00/00 Emask 0x409 (media error) <F>
[   19.810672] ata1.00: status: { DRDY ERR }
[   19.810675] ata1.00: error: { UNC }
[   19.812322] ata1.00: configured for UDMA/100
[   19.812349] sd 0:0:0:0: [sda]  
[   19.812352] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   19.812356] sd 0:0:0:0: [sda]  
[   19.812358] Sense Key : Medium Error [current] [descriptor]
[   19.812363] Descriptor sense data with sense descriptors (in hex):
[   19.812365]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   19.812377]         47 c7 b3 00 
[   19.812382] sd 0:0:0:0: [sda]  
[   19.812386] Add. Sense: Unrecovered read error - auto reallocate failed
[   19.812389] sd 0:0:0:0: [sda] CDB: 
[   19.812391] Read(10): 28 00 47 c7 b3 00 00 00 08 00
[   19.812401] end_request: I/O error, dev sda, sector 1204269824
[   19.812415] ata1: EH complete
[   23.996292] ata1.00: exception Emask 0x0 SAct 0x7f800017 SErr 0x0 action 0x0
[   23.996298] ata1.00: irq_stat 0x40000008
[   23.996302] ata1.00: failed command: READ FPDMA QUEUED
[   23.996311] ata1.00: cmd 60/08:10:30:b3:c7/00:00:47:00:00/40 tag 2 ncq 4096 in
[   23.996311]          res 41/40:00:30:b3:c7/00:00:47:00:00/00 Emask 0x409 (media error) <F>
[   23.996315] ata1.00: status: { DRDY ERR }
[   23.996318] ata1.00: error: { UNC }
[   23.997997] ata1.00: configured for UDMA/100
[   23.998018] sd 0:0:0:0: [sda]  
[   23.998021] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   23.998024] sd 0:0:0:0: [sda]  
[   23.998027] Sense Key : Medium Error [current] [descriptor]
[   23.998031] Descriptor sense data with sense descriptors (in hex):
[   23.998033]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   23.998045]         47 c7 b3 30 
[   23.998050] sd 0:0:0:0: [sda]  
[   23.998053] Add. Sense: Unrecovered read error - auto reallocate failed
[   23.998056] sd 0:0:0:0: [sda] CDB: 
[   23.998058] Read(10): 28 00 47 c7 b3 30 00 00 08 00
[   23.998068] end_request: I/O error, dev sda, sector 1204269872
[   23.998083] ata1: EH complete
[   28.185942] ata1.00: exception Emask 0x0 SAct 0xdfe0 SErr 0x0 action 0x0
[   28.185948] ata1.00: irq_stat 0x40000008
[   28.185952] ata1.00: failed command: READ FPDMA QUEUED
[   28.185961] ata1.00: cmd 60/08:70:38:b3:c7/00:00:47:00:00/40 tag 14 ncq 4096 in
[   28.185961]          res 41/40:00:38:b3:c7/00:00:47:00:00/00 Emask 0x409 (media error) <F>
[   28.185965] ata1.00: status: { DRDY ERR }
[   28.185968] ata1.00: error: { UNC }
[   28.187518] ata1.00: configured for UDMA/100
[   28.187538] sd 0:0:0:0: [sda]  
[   28.187540] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   28.187543] sd 0:0:0:0: [sda]  
[   28.187546] Sense Key : Medium Error [current] [descriptor]
[   28.187550] Descriptor sense data with sense descriptors (in hex):
[   28.187552]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   28.187563]         47 c7 b3 38 
[   28.187569] sd 0:0:0:0: [sda]  
[   28.187572] Add. Sense: Unrecovered read error - auto reallocate failed
[   28.187575] sd 0:0:0:0: [sda] CDB: 
[   28.187577] Read(10): 28 00 47 c7 b3 38 00 00 08 00
[   28.187588] end_request: I/O error, dev sda, sector 1204269880
[   28.187594] ata1: EH complete
[   32.375515] ata1.00: exception Emask 0x0 SAct 0x3fc0000 SErr 0x0 action 0x0
[   32.375521] ata1.00: irq_stat 0x40000008
[   32.375526] ata1.00: failed command: READ FPDMA QUEUED
[   32.375535] ata1.00: cmd 60/08:c8:48:b3:c7/00:00:47:00:00/40 tag 25 ncq 4096 in
[   32.375535]          res 41/40:00:48:b3:c7/00:00:47:00:00/00 Emask 0x409 (media error) <F>
[   32.375539] ata1.00: status: { DRDY ERR }
[   32.375542] ata1.00: error: { UNC }
[   32.377165] ata1.00: configured for UDMA/100
[   32.377186] sd 0:0:0:0: [sda]  
[   32.377190] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   32.377193] sd 0:0:0:0: [sda]  
[   32.377195] Sense Key : Medium Error [current] [descriptor]
[   32.377199] Descriptor sense data with sense descriptors (in hex):
[   32.377201]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   32.377213]         47 c7 b3 48 
[   32.377218] sd 0:0:0:0: [sda]  
[   32.377221] Add. Sense: Unrecovered read error - auto reallocate failed
[   32.377224] sd 0:0:0:0: [sda] CDB: 
[   32.377226] Read(10): 28 00 47 c7 b3 48 00 00 08 00
[   32.377236] end_request: I/O error, dev sda, sector 1204269896
[   32.377249] ata1: EH complete
[   38.183380] ata1.00: exception Emask 0x0 SAct 0x3e SErr 0x0 action 0x0
[   38.183386] ata1.00: irq_stat 0x40000008
[   38.183390] ata1.00: failed command: READ FPDMA QUEUED
[   38.183398] ata1.00: cmd 60/08:08:60:b3:c7/00:00:47:00:00/40 tag 1 ncq 4096 in
[   38.183398]          res 41/40:00:60:b3:c7/00:00:47:00:00/00 Emask 0x409 (media error) <F>
[   38.183403] ata1.00: status: { DRDY ERR }
[   38.183406] ata1.00: error: { UNC }
[   38.184934] ata1.00: configured for UDMA/100
[   38.184948] sd 0:0:0:0: [sda]  
[   38.184951] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   38.184954] sd 0:0:0:0: [sda]  
[   38.184956] Sense Key : Medium Error [current] [descriptor]
[   38.184960] Descriptor sense data with sense descriptors (in hex):
[   38.184962]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   38.184974]         47 c7 b3 60 
[   38.184980] sd 0:0:0:0: [sda]  
[   38.184983] Add. Sense: Unrecovered read error - auto reallocate failed
[   38.184986] sd 0:0:0:0: [sda] CDB: 
[   38.184987] Read(10): 28 00 47 c7 b3 60 00 00 08 00
[   38.184998] end_request: I/O error, dev sda, sector 1204269920
[   38.185015] ata1: EH complete
[   42.268544] systemd-udevd[415]: starting version 204
[   42.424910] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.436238] mei_me 0000:00:16.0: irq 53 for MSI/MSI-X
[   42.448089] ACPI Warning: SystemIO range 0x0000000000000828-0x000000000000082F conflicts with OpRegion 0x0000000000000800-0x000000000000084F (\PMRG) (20140424/utaddress-254)
[   42.448095] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   42.448098] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x000000000000054F (\GPS1) (20140424/utaddress-254)
[   42.448101] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   42.448102] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000054F (\GPS1) (20140424/utaddress-254)
[   42.448105] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000053F (\GPS0) (20140424/utaddress-254)
[   42.448107] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   42.448108] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000054F (\GPS1) (20140424/utaddress-254)
[   42.448111] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000053F (\GPS0) (20140424/utaddress-254)
[   42.448113] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   42.448114] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   42.457127] EDAC MC: Ver: 3.0.0
[   42.461097] EDAC MC0: Giving out device to module i7core_edac.c controller i7 core #0: DEV 0000:3f:03.0 (POLLED)
[   42.461134] EDAC PCI0: Giving out device to module i7core_edac controller EDAC PCI controller: DEV 0000:3f:03.0 (POLLED)
[   42.461139] EDAC i7core: Driver loaded, 1 memory controller(s) found.
[   42.467844] lp: driver loaded but no devices found
[   42.473303] ppdev: user-space parallel port driver
[   42.485563] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   42.531448] snd_hda_intel 0000:00:1b.0: irq 54 for MSI/MSI-X
[   42.531546] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   42.532034] snd_hda_intel 0000:01:00.1: irq 55 for MSI/MSI-X
[   42.539564] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input4
[   42.544846] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   42.544849] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   42.544850] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   42.544851] sound hdaudioC0D0:    mono: mono_out=0x0
[   42.544853] sound hdaudioC0D0:    dig-out=0x11/0x1e
[   42.544854] sound hdaudioC0D0:    inputs:
[   42.544856] sound hdaudioC0D0:      Front Mic=0x19
[   42.544878] sound hdaudioC0D0:      Rear Mic=0x18
[   42.544879] sound hdaudioC0D0:      Line=0x1a
[   42.557189] input: HDA Intel MID Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   42.557246] input: HDA Intel MID Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   42.557302] input: HDA Intel MID Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   42.557366] input: HDA Intel MID Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   42.557424] input: HDA Intel MID Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   42.557480] input: HDA Intel MID Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   42.596327] audit_printk_skb: 15 callbacks suppressed
[   42.596328] audit: type=1400 audit(1442156418.224:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=547 comm="apparmor_parser"
[   42.596333] audit: type=1400 audit(1442156418.224:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=547 comm="apparmor_parser"
[   42.596336] audit: type=1400 audit(1442156418.224:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=547 comm="apparmor_parser"
[   42.596343] audit: type=1400 audit(1442156418.224:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=545 comm="apparmor_parser"
[   42.596348] audit: type=1400 audit(1442156418.224:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=545 comm="apparmor_parser"
[   42.596351] audit: type=1400 audit(1442156418.224:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=545 comm="apparmor_parser"
[   42.596647] audit: type=1400 audit(1442156418.224:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=547 comm="apparmor_parser"
[   42.596651] audit: type=1400 audit(1442156418.224:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=547 comm="apparmor_parser"
[   42.596690] audit: type=1400 audit(1442156418.224:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=545 comm="apparmor_parser"
[   42.596694] audit: type=1400 audit(1442156418.224:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=545 comm="apparmor_parser"
[   43.178455] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   43.184632] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   43.518460] init: failsafe main process (741) killed by TERM signal
[   43.980819] init: cups main process (886) killed by HUP signal
[   43.980827] init: cups main process ended, respawning
[   44.032206] Bluetooth: Core ver 2.19
[   44.032220] NET: Registered protocol family 31
[   44.032221] Bluetooth: HCI device and connection manager initialized
[   44.032227] Bluetooth: HCI socket layer initialized
[   44.032228] Bluetooth: L2CAP socket layer initialized
[   44.032235] Bluetooth: SCO socket layer initialized
[   44.035105] Bluetooth: RFCOMM TTY layer initialized
[   44.035110] Bluetooth: RFCOMM socket layer initialized
[   44.035114] Bluetooth: RFCOMM ver 1.11
[   44.185495] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   44.185498] Bluetooth: BNEP filters: protocol multicast
[   44.185505] Bluetooth: BNEP socket layer initialized

```

I must admit quite a bit that is way over my head, hopefully some one with more knowledge can point me in the right direction. :)

---

### Post by SeijiSensei on 2015-09-13
The drive reports a lot of errors.  They might be fixable by running fsck, or they may be on the physical disk itself.

Telling Linux to mount the system read/write at boot isn't solving the problem.  It just fixes the symptom and could actually make things worse.

If you can successfully log in, enter a terminal and type
```
sudo touch /forcefsck
```
then reboot.  Linux will check the integrity of the file system at the next boot.  If you still see errors like this:
```
end_request: I/O error, dev sda, sector 1204269880
```
then the drive has physical errors.  It sounds like it should be within the warranty period in which case it should be replaced.

---

