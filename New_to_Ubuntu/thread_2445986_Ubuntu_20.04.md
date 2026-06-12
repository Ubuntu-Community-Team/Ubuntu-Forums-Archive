---
title: "Ubuntu 20.04"
date: 2020-06-23
forum: New to Ubuntu
---

### Post by val-valiant on 2020-06-23
Hi 

Have recently installed 20.04 and the first time you open any app its extremely slow. Computers more then capable Pavilion 15 with 16Gb ram and a 256 Gb ssd. whats the go? 

Thanks

---

### Post by dino99 on 2020-06-23
open a terminal, and run 'journalctl -b' to know about error (red lines) and warning (yellow lines) to help you understand that issue

---

### Post by val-valiant on 2020-06-28
> **dino99 said:**
> open a terminal, and run 'journalctl -b' to know about error (red lines) and warning (yellow lines) to help you understand that issue

Ok done that 

have no idea what any of that means. 

I have 

Yellow ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid Length but zero Address: 0x0000000000000000/0x1 (20190816/tbfadt-615)

Red Initramfs unpacking failed: Decoding failed

Yellow pci 0000:00:00.2: can't derive routing for PCI INT A

Yellow Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: EISA: Cannot allocate resource for mainboard
Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: Cannot allocate resource for EISA slot 1
Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: Cannot allocate resource for EISA slot 2
Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: Cannot allocate resource for EISA slot 3
Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: Cannot allocate resource for EISA slot 4
Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: Cannot allocate resource for EISA slot 5
Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: Cannot allocate resource for EISA slot 6
Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: Cannot allocate resource for EISA slot 7
Jun 28 14:07:53 val-HP-Pavilion-Notebook kernel: platform eisa.0: Cannot allocate resource for EISA slot 8

yellow r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control

yellow ATPX version 1, functions 0x00000003

yellow thermal thermal_zone1: failed to read out thermal zone (-61)

yellow kvm: disabled by bios

Actually this goes on and on and on multiple yellow and red issues ill go back to windows thanks this is soooooooooo slow shame

---

