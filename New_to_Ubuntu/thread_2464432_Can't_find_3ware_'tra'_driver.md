---
title: "Can't find 3ware 'tra' driver"
date: 2021-07-01
forum: New to Ubuntu
---

### Post by emiked on 2021-07-01
Searching for a 3ware raid controller driver I found this:

[http://manpages.ubuntu.com/manpages/focal/man4/twa.4freebsd.html](http://manpages.ubuntu.com/manpages/focal/man4/twa.4freebsd.html)

however, I can't find this driver anywhere.  Help.

Thanks!

---

### Post by scorp123 on 2021-07-01
> **emiked said:**
>  [http://manpages.ubuntu.com/manpages/focal/man4/twa.4freebsd.html](http://manpages.ubuntu.com/manpages/focal/man4/twa.4freebsd.html)


On my Ubuntu 20.04 system I can find these kernel modules ("drivers") that seem to be for 3ware devices:

```

/usr/lib/modules/5.4.0-77-generic/kernel/drivers/scsi/3w-sas.ko
/usr/lib/modules/5.4.0-77-generic/kernel/drivers/scsi/3w-9xxx.ko
/usr/lib/modules/5.4.0-77-generic/kernel/drivers/scsi/3w-xxxx.ko
```

Wouldn't those work as well? What happens if you try to load them, e.g.

```

sudo modprobe 3w-9xxx
sudo modprobe 3w-sas
sudo modprobe 3w-xxxx
```

Afterwards check "dmesg" if any new device gets reported:
```
sudo dmesg -T
```

---

### Post by emiked on 2021-07-04
Thanks!  An 'lsmod' actually showed that '3w-9xxx' was loaded.

Unfortunately, all commands to the card timeout.  I tried it in two pcie slots, didn't matter. Any other thoughts?

Thanks again

---

### Post by scorp123 on 2021-07-04
> **emiked said:**
> Thanks!  An 'lsmod' actually showed that '3w-9xxx' was loaded.

The output from **"sudo dmesg"** would be interesting to know. A loaded driver doesn't mean much here. The question is: Is any device being seen??

---

### Post by emiked on 2021-07-05
Dmesg:

[https://paste.ubuntu.com/p/KSXPYwB9cg/](https://paste.ubuntu.com/p/KSXPYwB9cg/)

Lspci:

[https://paste.ubuntu.com/p/XCcFkVDfqH/](https://paste.ubuntu.com/p/XCcFkVDfqH/)

---

### Post by scorp123 on 2021-07-05
> **emiked said:**
> Dmesg:

[https://paste.ubuntu.com/p/KSXPYwB9cg/](https://paste.ubuntu.com/p/KSXPYwB9cg/)

Lspci:

[https://paste.ubuntu.com/p/XCcFkVDfqH/](https://paste.ubuntu.com/p/XCcFkVDfqH/)

I took a look.

Let's talk about "lspci". Looking at this line it does seem like your card can be seen and the OS is able to talk to it?
```
04:00.0 RAID bus controller: 3ware Inc 9650SE SATA-II RAID PCIe (rev 01)
```

Looking at the "dmesg" output it seems like everything is OK at first and the controller and the attached disks get detected:
```

[    3.781300] 3ware 9000 Storage Controller device driver for Linux v2.26.02.014
...
[    4.075575] ata1: SATA max UDMA/133 abar m2048@0xdfa00000 port 0xdfa00100 irq 42
[    4.075578] ata2: SATA max UDMA/133 abar m2048@0xdfa00000 port 0xdfa00180 irq 42
[    4.075581] ata3: SATA max UDMA/133 abar m2048@0xdfa00000 port 0xdfa00200 irq 42
[    4.075584] ata4: SATA max UDMA/133 abar m2048@0xdfa00000 port 0xdfa00280 irq 42
[    4.075587] ata5: SATA max UDMA/133 abar m2048@0xdfa00000 port 0xdfa00300 irq 42
[    4.075590] ata6: SATA max UDMA/133 abar m2048@0xdfa00000 port 0xdfa00380 irq 42
...
[    4.221467] scsi host0: 3ware 9000 Storage Controller
...
[    4.221603] 3w-9xxx: scsi0: Found a 3ware 9000 Storage Controller at 0xdf920000, IRQ: 16.
...

```

... but then these things start to happen. :confused:

```

[    4.388165] ata4: SATA link down (SStatus 0 SControl 300)
[    4.388403] ata6: SATA link down (SStatus 0 SControl 300)
[    4.388569] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.388718] ata3: SATA link down (SStatus 0 SControl 300)
[    4.388902] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.389011] ata5: SATA link down (SStatus 0 SControl 300)
[    4.389144] ata1.00: ATA-8: INTEL SSDSA2BZ300G3, 6PB10362, max UDMA/133
[    4.389169] ata1.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 32)
[    4.389299] ata2.00: ATA-8: INTEL SSDSA2BZ300G3, 6PB10362, max UDMA/133
[    4.390263] ata2.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 32)
[    4.391288] ata1.00: configured for UDMA/133
[    4.392441] scsi 1:0:0:0: Direct-Access     ATA      INTEL SSDSA2BZ30 0362 PQ: 0 ANSI: 5
[    4.393493] ata2.00: configured for UDMA/133
[    4.393636] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    4.393639] ata1.00: Enabling discard_zeroes_data
[    4.393692] sd 1:0:0:0: [sda] 586072368 512-byte logical blocks: (300 GB/279 GiB)
[    4.393711] sd 1:0:0:0: [sda] Write Protect is off
[    4.393713] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.393730] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.399480] scsi 2:0:0:0: Direct-Access     ATA      INTEL SSDSA2BZ30 0362 PQ: 0 ANSI: 5
[    4.400804] ata2.00: Enabling discard_zeroes_data
[    4.400813] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    4.401911] sd 2:0:0:0: [sdb] 586072368 512-byte logical blocks: (300 GB/279 GiB)
[    4.403923] sd 2:0:0:0: [sdb] Write Protect is off
[    4.404790] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.404805] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...
[  129.329465] scsi 0:0:1:0: WARNING: (0x06:0x002C): Command (0x0) timed out, resetting card.
...
[  195.421461] 3w-9xxx: scsi0: AEN: INFO (0x04:0x000C): Initialize started:unit=0.
...
[  254.796997] scsi 0:0:3:0: WARNING: (0x06:0x002C): Command (0x12) timed out, resetting card.
[  272.356933] 3w-9xxx: scsi0: AEN: INFO (0x04:0x000C): Initialize started:unit=0.
[  282.673057] scsi 0:0:3:0: WARNING: (0x06:0x002C): Command (0x0) timed out, resetting card.
[  310.829383] scsi 0:0:3:0: Device offlined - not ready after error recovery
[  331.593557] scsi 0:0:4:0: WARNING: (0x06:0x002C): Command (0x12) timed out, resetting card.
...


```

The only idea I can come up with is that maybe that adapter card is defective??  Can you test it in another system with another distribution (e.g. Red Hat Enterprise Linux, CentOS, AlmaLinux, or Oracle Linux ... these "made for Enterprises" Linux distributions might detect the controller from the get go) or even another OS (e.g. Windows?).

If the card fails there as well then it's probably defective. Such things happen. Other than that I'm out of ideas.... :(

---

### Post by emiked on 2021-07-05
Thank you!  Hummm.  I sent of a request to 3ware (Broadcom).  As I can get into the cards bios, update the firmware, create a raid, I suspect the card is ok.

Sigh.  I'm thinking it has to do with an unknown incompatibility with the my motherboard and the card.

---

### Post by ladysoniam01 on 2021-07-07
Obtenez la meilleure formation de [coaching couple]("https://www.ladysoniam.com") en France, et au Canada. Lady Sonia est expérimentée en [couple goals]("https://www.ladysoniam.com"), [Coach personnel]("https://www.ladysoniam.com").

---

### Post by ladysoniam01 on 2021-07-07
Obtenez la meilleure formation de [coaching couple]("https://www.ladysoniam.com") en France, et au Canada. Lady Sonia est expérimentée en [couple goals]("https://www.ladysoniam.com"), [Coach personnel]("https://www.ladysoniam.com").

---

