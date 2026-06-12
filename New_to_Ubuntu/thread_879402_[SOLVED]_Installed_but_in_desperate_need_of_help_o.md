---
title: "[SOLVED] Installed but in desperate need of help on old Emachine"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by grtwhiterhyno on 2008-08-04
Just installed 8.04 Hardy Heron on an old E machine, really old.  On board video and sound.  I was assured that Heron would do all that XP Proff. would do and do it well.  My problem is video related I believe.  When I move my mouse around, over buttons, through windows, and drop-down menus, a little square forms around it distorting the display.  I am also running slower, but I think this just may be another symptom of the same problem.  Please, for the love of God, will someone help me!

---

### Post by PurposeOfReason on 2008-08-04
Could you post the exact specs of this machine?

---

### Post by grtwhiterhyno on 2008-08-04
How do you look them up?  I do not have them memorized. Thank you for helping me though, or at least trying to.

---

### Post by dhughes on 2008-08-04
Sounds like your video card is way underpowered, just a guess, go to System> Preferences> Appearance> Visual Effects to NONE

---

### Post by perlluver on 2008-08-04
> **grtwhiterhyno said:**
> How do you look them up?  I do not have them memorized. Thank you for helping me though, or at least trying to.

type lspci in the terminal.  Applications>Accescories>Terminal.  Post the output here.

---

### Post by grtwhiterhyno on 2008-08-04
This was the return on lspci:

00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:09.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
01:0d.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
01:0e.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

---

### Post by perlluver on 2008-08-04
> **grtwhiterhyno said:**
> This was the return on lspci:

00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:09.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
01:0d.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
01:0e.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

Make sure in System>Preferences>Appearance That effect are turned off.

---

### Post by grtwhiterhyno on 2008-08-04
SUPER SWEET!! Changing the appearance visual effects settings may have done it. No more boxes, moves better, but not where it probably should be, still better. I knowticed there is a way to leave thank yous, do tell me how.  And mark as solved.

---

### Post by perlluver on 2008-08-04
> **grtwhiterhyno said:**
> SUPER SWEET!! Changing the appearance visual effects settings may have done it. No more boxes, moves better, but not where it probably should be, still better. I knowticed there is a way to leave thank yous, do tell me how.

The blue thing with a yellow star on the left, next to qoute, sorry.

And mark as solved if you are all better in thread tools, at the top of the posts.

---

### Post by grtwhiterhyno on 2008-08-04
How do I mark this as solved in the forum?

---

### Post by perlluver on 2008-08-04
> **grtwhiterhyno said:**
> How do I mark this as solved in the forum?

All the way at the top of all of our posts.  Thread tools, mark as solved.

---

