---
title: "Wine games are very slow."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by TheXantor on 2008-06-24
Whereas they really shouldn't be, according to my system specs and how well the games run for other Wine users.  I have a 3.20 GHz dual core, a GEforce 8800 GT (I installed the drivers for this using Envy, if this matters.).  I'm running Hardy Heron, I've heard other versions may be better, but I'm OK with this right now. If there's anything else anybody needs to know, just ask and I'll post it.  

Here's my lspci:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
**01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)**
03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

It looks as if it detects my video card...

---

### Post by sydbat on 2008-06-24
Any games in particular? It could be wine is not fully compatible (yet) with the game(s) you are trying to run.

---

### Post by Xerp on 2008-06-24
Which Wine version, which game, and what is the expected fps? Often you have to make tweaks on a game-by-game basis.

---

### Post by sydbat on 2008-06-24
How easy is wine to tweak?

---

### Post by TheXantor on 2008-06-24
The games I've tried: Garrysmod and Half-Life 2.  The expected FPS for Garrysmod varies from 80 to 100 depending on the map size and what im doing on that map.  Of course, I don't need it to give me results that good.  I just need it to playable.  Half-Life 2 is probably around the same, although I've never tested that.  I'm running wine 1.0, and its easy to tweak, just run winecfg.

---

### Post by barney385 on 2008-06-24
I don't want windows anywhere near my Ubuntu install.

I dual boot XP, and not very often...

:smile:

---

### Post by TheXantor on 2008-06-24
I've been looking to get out of windows for nearly two years now, i was just never advanced enough to understand Linux.  Although i enjoy playing some games on my computer.

---

### Post by barney385 on 2008-06-24
> **TheXantor said:**
> I've been looking to get out of windows for nearly two years now, i was just never advanced enough to understand Linux.  Although i enjoy playing some games on my computer.

I'm a noob also, but I'm very glad I made the switch. As I get use to Ubuntu, I'm amazed how much easier it is to use.

I wish I hadn't waited so long to be honest...

Happy Ubuntuing :smile:

---

### Post by TheXantor on 2008-06-24
Hey, guess what, I fixed this by running Steam  WINEDEBUG="fixme-all" wine Steam 

Run that from the directory you installed steam, by the way.  Everything is now FASTER than what i got in Winblow.  I also messed around a bit in Terminal and Steam, but i don't think i can help anyone there.

---

### Post by Methuselah on 2008-06-24
Is direct rendering enabled?

```

glxinfo | grep "direct rendering"

```

If it's not Yes, you'll get no 3D acceleration in wine.
Also, if it's yes and compiz (3D desktop effects) are running, wine games will be slow.

---

### Post by TheXantor on 2008-06-25
So, I disable Compiz Desktop Effects?  Ok, I'll try doing that.

I get no options for Anti-Aliasing in my games as well, any way to fix that?  Or should i just override it from the nVidia X-Server?

---

