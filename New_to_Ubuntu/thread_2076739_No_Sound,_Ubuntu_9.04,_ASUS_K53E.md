---
title: "No Sound, Ubuntu 9.04, ASUS K53E"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by Yue Han on 2012-10-26
I have installed Ubuntu 9.04 onto my ASUS K53E Laptop but there is no sound from the speakers.  From the terminal I typed "sudo aplay -l" and what followed was "no soundcards found..."  I also typed "lspci -v | grep -A7 -i "audio" and the following information was returned.
Audio Device: Intel Corporation Device 1c20 (rev 05)
Subsystem: ASUStek Computer Inc. Device 1b43
Flags: bus master, fast devsel, latency 0, IRQ5
Memory at dfc00000 (64-bit, non=prefetchable) [size=16k]
Capabilities: <access denied>
Could someone help me with this No Sound

---

### Post by newb85 on 2012-10-26
Welcome to the forums!

Your install of Ubuntu recognizes that your sound card is present, but has no drivers for it.

If I'm not mistaken, that's a fairly new machine.  And 9.04 is a *very* old release of Ubuntu.  Support for 9.04 ended October 2010.

Moving up to a newer release (like 12.04) will probably take care of your problem.

---

### Post by Yue Han on 2012-10-27
Hi Newb85

Yes, Ubuntu 9.04 is older than the ASUS K53E but I would still apprecaite any help toward solving this NO Sound issue.  Adding an additional driver, if possible, might be a helpful learning experince, both now and in the future.

Thank you.

Yue Han

---

### Post by westie457 on 2012-10-27
> **newb85 said:**
> Welcome to the forums!

Your install of Ubuntu recognizes that your sound card is present, but has no drivers for it.

If I'm not mistaken, that's a fairly new machine.  And 9.04 is a *very* old release of Ubuntu.  Support for 9.04 ended October 2010.

Moving up to a newer release (like 12.04) will probably take care of your problem.

^^^ What he said.

10.04 might have the driver as well, this is supported until April 2013 for the desktop edition. Though in all honesty go for 12.04.

---

