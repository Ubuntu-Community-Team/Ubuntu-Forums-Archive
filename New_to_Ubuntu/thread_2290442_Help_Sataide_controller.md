---
title: "Help Sata/ide controller"
date: 2015-08-12
forum: New to Ubuntu
---

### Post by joerack on 2015-08-12
I've installed a ide/sata pci express controller for my ide hard disk, and I'm getting a load of problems.

[  274.747662] ata9: limiting SATA link speed to 1.5 Gbps
[  274.747669] ata9: hard resetting link
[  275.471207] ata9: SATA link down (SStatus 0 SControl 310)
[  275.471244] ata9: EH complete
[  275.546995] ata9: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[  275.547008] ata9: irq_stat 0x00000040, connection status changed
[  275.547012] ata9: SError: { DevExch }



help me out please

---

### Post by dino99 on 2015-08-12
its time to read your hardware docs:
- hdd: pay attention at how to set the jumper(s)
- depending of the sata type (I II or III) card, also read its config setup, check the pci mobo slot specs
- check the bios/uefi setting about pci; check for bios update too
- check that the bios find that hdd
- sometime such card works on some mobo slot and not with an other slot (if you can choose an other pci slot)

also run:
> sudo update-pciids
sudo update-usbids

- if that pci model card is recent, then install also a recent kernel to get a better support
[http://askubuntu.com/questions/109180/mysterious-hard-disk-failure](http://askubuntu.com/questions/109180/mysterious-hard-disk-failure)

---

### Post by tgalati4 on 2015-08-12
The card could be bad.  It happens.  Was it working on a different machine?  Examine the card carefully for any missing components.  All it takes is a capacitor to be knocked off.

---

