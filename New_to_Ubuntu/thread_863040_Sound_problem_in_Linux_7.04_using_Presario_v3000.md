---
title: "Sound problem in Linux 7.04 using Presario v3000"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by kambeng02 on 2008-07-18
hye to all,
 
last time i used 7.04 ubuntu and realize my wireless and my sound didnt work, i tried everyting but it still give the same result. after that, i upgrade to ubuntu 7.10 and my wireless are now working. but my sound still cant work. 
can anyone help me? this is my information

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


i have installed alsa but it still give the same result.

---

### Post by prshah on 2008-07-18
> **kambeng02 said:**
> 
upgrade to ubuntu 7.10 and my wireless are now working. but my sound still cant work. 


I suspect an IRQ conflict between sound/wireless. To confirm, give the following command```
dmesg | grep -i irq
``` and post the output here.

---

### Post by kambeng02 on 2008-07-18
This is the output, pleasse help me and thanks for reply :)

> [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[   20.433562] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   21.026709] ENABLING IO-APIC IRQs
[   21.339686] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   21.339795] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   21.339901] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   21.340008] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   21.340122] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   21.340231] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   21.340337] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   21.340444] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   21.343618] PCI: Using ACPI for IRQ routing
[   21.343621] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.403555] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   21.403589] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
[   21.403620] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   22.576991] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.578659] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.579577] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.579583] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   22.579586] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   22.579588] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   22.579591] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.776000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.776000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    3.880000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[    3.880000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[    3.984000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 20
[    3.984000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860
[    4.088000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 21
[    4.088000] uhci_hcd 0000:00:1d.3: irq 21, io base 0x00001880
[    4.192000] ACPI: PCI Interrupt 0000:08:09.0[A] -> GSI 16 (level, low) -> IRQ 21
[    4.256000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d4101000-d41017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.260000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> <6>ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ 22
[    4.260000] GSI 23 (level, low) -> IRQ 19
[    4.260000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd4544000
[    4.288000] e100: eth0: e100_probe: addr 0xd4100000, irq 22, MAC addr 00:16:D3:1A:88:0B
[    4.488000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
[    4.488000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.488000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    5.076000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 20 (level, low) -> IRQ 22
[    6.080000] ata3: SATA max UDMA/133 cmd 0xf886c500 ctl 0x00000000 bmdma 0x00000000 irq 22
[    6.080000] ata4: SATA max UDMA/133 cmd 0xf886c580 ctl 0x00000000 bmdma 0x00000000 irq 22
[    6.080000] ata5: SATA max UDMA/133 cmd 0xf886c600 ctl 0x00000000 bmdma 0x00000000 irq 22
[    6.080000] ata6: SATA max UDMA/133 cmd 0xf886c680 ctl 0x00000000 bmdma 0x00000000 irq 22
[   18.588000] ACPI: PCI Interrupt 0000:08:09.1[B] -> GSI 18 (level, low) -> IRQ 17
[   18.588000] mmc0: SDHCI at 0xd4101800 irq 17 DMA
[   19.348000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   20.904000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[   20.908000] ndiswrapper: using IRQ 18
[   26.180000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 21


---

