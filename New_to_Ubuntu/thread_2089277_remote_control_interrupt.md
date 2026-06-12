---
title: "remote control interrupt"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by bilboubu on 2012-11-28
how can I find out what interrupt my usb infa red remote control and my keyboard use?

 cat /proc/interrupts
           CPU0       CPU1
  0:         46          7   IO-APIC-edge      timer
  1:          1          1   IO-APIC-edge      i8042
  4:          1          1   IO-APIC-edge
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          2          2   IO-APIC-edge      i8042
 14:      25953        109   IO-APIC-edge      ata_piix
 15:       7498       6509   IO-APIC-edge      ata_piix
 16:     268446         81   IO-APIC-fasteoi   uhci_hcd:usb5, nvidia
 17:     169261     163025   IO-APIC-fasteoi   hda_intel
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:     159650     169885   IO-APIC-fasteoi   uhci_hcd:usb3, saa7130[0]
 23:     190551     326374   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 43:    1199801         77   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:    2298330    2805634   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:     403803     613212   Rescheduling interrupts
CAL:       4010       6874   Function call interrupts
TLB:       2066       2477   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC inteit rrupts
MCE:          0          0   Machine check exceptions
MCP:         13         13   Machine check polls
ERR:          0
MIS:          0

not sure which one, also 
lsusb


/bin$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2013:024f Unknown (Pinnacle?)
Bus 005 Device 002: ID 1784:0008 TopSeed Technology Corp. eHome Infrared Transceiver

---

