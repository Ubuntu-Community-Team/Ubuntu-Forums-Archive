---
title: "Help!  Dual head, 7.10, two nVidia legacy cards"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by zerhacke on 2008-05-13
Hello.  I'm used to answering things in the ABT section and here I am asking a question.

I have two nVidia legacy cards, one a Riva TNT AGP and one a Riva TNT 64 PCI.  I am attempting to set up a dual head setup but cannot do it.

If I place the AGP card as the primary display adapter in BIOS I get absolutely no video output after GRUB leaves the screen.  The second monitor then activates showing the Video BIOS splash and that's it.  It just sits there.

If I place the PCI card as the primary display adapter in BIOS it boots up just fine - though the AGP monitor is dead.  I am typing this post with this setup.  I have used the Screens and Graphics utility in System - Administration menu and it sees the second video adapter but the only options I am given are that the card is either disabled or Primary, and if I set it to primary the other screen dies.  If I set the AGP device as primary both screens die.

I _know_ that both cards are working as Windows does dual head with this setup just fine.

The output of lspci is as follows:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:10.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
00:14.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)

The Ubuntu 7.10 install is a fresh install.  No updates have been done on it yet.

If any of you could help me with this, I would really appreciate it.  I am perfectly fine with using apt-get to get more software and am able to edit /etc/X11/xorg.conf if needed.

---

### Post by andrewski on 2008-06-11
I'd think you'd get better help in the "Hardware & Laptops" forum. (Sorry, I have no idea.)

---

