---
title: "Screen Resolution gone BLEWWWIE"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-11-01
This is Oneiric. I have a EVGA (nvidia) 9500GT video card. The monitor for this rig is an AOC 23" lcd screen. It has always worked perfectly with Linux-Ubuntu. That connection was from DVI#1 at the card output through a DVI to VGA converter, then from the VGA cable into the TV monitor. All worked as expected.

Today, using a DVI to HDMI converter (plug), I plugged the DVI#1 to the dvi to hdmi converter and then the hdmi cable into the TV monitor.

I cold booted back into Oneiric. But the screen resolution is as though I was in Windows "safe mode". The screen icons are 75% larger than before. Firefox runs "full screen" only, etc.

I ran the config "Display", but Oneiric does not detect this monitor, calling it "Unknown". Even after I clicked "Detect Display". That's strange, cause using the VGA input, Oneiric calls it by it's name: AOC 23 inch xxxxx. (no longer true, after re-setting the cable back into the VGA instead of HDMI, Oneiric cannot find this monitor, calling it Unknown).

I looked at Addition Drivers and have the "Recommended" one in use. No number is given only the words: (Version current). Version 173 and Version 173 updates are available.

Anyone have some experience like this? Anybody got a solution to restore my 'regular' screen attributes?

---

### Post by gsmanners on 2011-11-01
Any particular reason you aren't using the 280.13 driver? That works fine here.

---

### Post by anewguy on 2011-11-01
I have the same info come up for my 9500GT card.  I think what the op is saying is that the recommended driver from the additional drivers screen does not show that version of that driver.  When the op mentions the 173 driver, I'm sure it's like mine where the additional drivers screen shows that the driver version 173 is available, followed by the line showing the recommended driver (with no version given on the line).  The 173 driver is not marked for install, while the recommended driver is marked (e.g., the little circle is filled in).

So, the OP, and myself, might actually BE running the newer driver - it's just that the additional drivers screen doesn't show the version of the recommended driver.


ark-in-hollywood:  Love the "blewwie" thing!

Dave ;)

---

### Post by Mark_in_Hollywood on 2011-11-01
For:

gsmanners, who said:

Any particular reason you aren't using the 280.13 driver? That works fine here.


It is what the Upgrade installed. I have NOT touched the Additional Drivers, as everything is working.

To Mr. anewguy:

Yes, it gets way too difficult to describe each and every piece of nomenclature when describing the "Additional Drivers" page. Oneiric selected this, as far as I know.

---

