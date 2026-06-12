---
title: "PCI IDE adapter help"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by PermNoob on 2012-07-10
So I am trying to get my old pentium II up (deshutes) and running.  debating staying with ubuntu on it or moving over to arch (bad past experience, but probably the smartest move).

anyways before I can go that far, I need to get a bunch of old hard drives into it to recover their data, since this PCI adapter does not work in my only other pc, it fails to boot with the just the card installed.

best I know how to start, here is the output of lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF


I do belive it is not listed?  that IDE thing is likely on the MOBO, not in a pci slot, correct?

---

