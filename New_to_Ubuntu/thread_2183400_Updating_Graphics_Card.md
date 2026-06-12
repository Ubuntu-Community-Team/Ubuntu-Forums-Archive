---
title: "Updating Graphics Card"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by Luke_Patzer on 2013-10-24
I want to update my graphics card but I have no idea how. :(
I would appreciate any help I can get.

Here are the stats:

Intel® G33 x86/MMX/SSE2

 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrate
d Graphics Controller (rev 02) (prog-if 00 [VGA controller])
        Subsystem: Dell Inspiron 530
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ff00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fd700000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915

I would appreciate any help possible! :D

---

### Post by papibe on 2013-10-24
Hi Luke_Patzer.

If I were you, I'd open the computer and look for the PCI slots available. If you have a [PCI Expressx16]("http://en.wikipedia.org/wiki/PCI_Express") slot, you could almost any modern card.

The installation is pretty straight forward. After it's done, you may need to get into the BIOS to tell the computer to use the card instead of the integrated graphics.

As for Ubuntu, you may need to delete (or rename) your config file:
```
/etc/X11/xorg.conf
```
The worst case scenario would be to boot into a black screen. That it usually solved by booting using the nomodeset option (read [here]("http://ubuntuforums.org/showthread.php?t=1613132")).

I hope that helps. Let us know how it goes.
Regards.

---

### Post by Luke_Patzer on 2013-10-24
Thanks! I'll look into this.

---

### Post by Luke_Patzer on 2013-10-24
I tried looking for my xorg.conf file but I don't have one. :confused: But I do have a xorg.conf.failsafe file. Are they the same?

---

### Post by papibe on 2013-10-24
> **Luke_Patzer said:**
> ... but I don't have one...
Then one thing less to worry about ;)

---

### Post by deadflowr on 2013-10-24
> **Luke_Patzer said:**
> I tried looking for my xorg.conf file but I don't have one. :confused: But I do have a xorg.conf.failsafe file. Are they the same?

Nope, it's not the same.

You're card uses the open source drivers so it doesn't need an xorg.conf file.
(The xorg developers have worked hard so that it is not needed anymore).
Generally, close source drivers still do need that file. Or seem to work better with it.

For what I know, the xorg.conf.failsafe file is exactly what it states, a failsafe.
I believe it points to a generic vesa driver, which will load if all else fails.

---

### Post by Luke_Patzer on 2013-10-25
Sweet thanks! :guitar:

---

