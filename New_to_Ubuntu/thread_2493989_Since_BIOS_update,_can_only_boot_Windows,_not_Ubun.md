---
title: "Since BIOS update, can only boot Windows, not Ubuntu"
date: 2024-01-02
forum: New to Ubuntu
---

### Post by vermiou on 2024-01-02
Hello!

My PC has dual boot Windows/Ubuntu, but since a BIOS update that I did from Windows (it was proposed via a pop-up window and I accepted it), I can't choose between Windows and Ubuntu. Instead, Windows boots directly (there is no GRUB menu).

How can I put back the GRUB menu and be able to choose between Windows and Ubuntu again?

Thank you

---

### Post by MAFoElffen on 2024-01-02
What Brand and model of computer is it?

If you boot from an Ubuntu installer LiveUSB, what does this say (posted within CODE Tags):
```

sudo dmidecode -t 0
sudo efibootmgr -v

```

---

### Post by vermiou on 2024-01-02
Thank you for your answer

The PC is a Lenovo Legion 5 17ACH6H

The pop-up window was in fact from the software Lenovo Vantage that's built-in

Here is the output:

```

ubuntu@ubuntu:~$ sudo dmidecode -t 0
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.3.0 present.

Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
    Vendor: LENOVO
    Version: GKCN60WW
    Release Date: 03/07/2023
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 16 MB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 1.60
    Firmware Revision: 1.60

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,0000,0001,2001,2002,2003
Boot0000* ubuntu    HD(1,GPT,13f37f8b-20f0-4acc-8d7c-1ae590947af5,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0001* Linpus lite    HD(2,GPT,f45e2fa1-c5a6-4d79-876d-c8245af921e0,0x95f864,0x2754)/File(\EFI\Boot\grubx64.efi)RC
Boot0002* EFI PXE 0 for IPv4 (88-A4-C2-5E-5C-80)     PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(88a4c25e5c80,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* EFI PXE 0 for IPv6 (88-A4-C2-5E-5C-80)     PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(88a4c25e5c80,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0004* Windows Boot Manager    HD(1,GPT,13f37f8b-20f0-4acc-8d7c-1ae590947af5,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...-................
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

```

---

### Post by tea for one on 2024-01-02
The UEFI (bios) update has possibly made Windows the priority boot OS.
Can you access your UEFI settings and alter the Boot Priority order?

---

### Post by vermiou on 2024-01-02
Thank you for your answer!

Sure, how do I do?

EDIT: I managed to do it by myself! And the problem is now solved. Thank you! :)

---

### Post by tea for one on 2024-01-02
Well, it's difficult to give precise instructions because UEFI settings vary from PC to PC.

Anyway, let's see......
Power off PC, then tap F2 (for Lenovo) during power on.
Right arrow to Boot tab

Do you see Boot Priority Order?

At the bottom of the screen, more instructions to select, change values, save, exit etc.

Edit:  Well done - I was writing too slowly, I need to learn touch typing ;)
Don't forget to mark as solved via thread tools.

---

