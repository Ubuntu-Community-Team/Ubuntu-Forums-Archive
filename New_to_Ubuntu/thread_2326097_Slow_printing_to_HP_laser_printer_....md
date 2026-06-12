---
title: "Slow printing to HP laser printer ..."
date: 2016-05-28
forum: New to Ubuntu
---

### Post by cwmoser on 2016-05-28
Installed Ubuntu Mate 16.04 and setup printing for HP2420 laser printer.
Using LPT1 as output port.

Printing was fast under Ubuntu Mate 15.10, but extremely slow - like 10 minutes - to print
something like my Harbor Freight email coupons, color but my printer is black & white.

Is there a tweak that fixes this?

---

### Post by cwmoser on 2016-05-28
I think I figured it out:

System -> Administration -> Printers -> HP2420 shows the Device URI:  parallel:/dev/lp0
and the Make and Model as "HP LaserJet 2420 Postscript[en] (recommended)

I changed the Make and Model to "HP LaserJet 2420 - CUPS+Gutenprint v5.2.11 [en]

Now prints fast like before.
Apparently Postscript is slow.

---

