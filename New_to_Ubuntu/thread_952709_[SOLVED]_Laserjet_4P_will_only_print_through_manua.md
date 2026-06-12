---
title: "[SOLVED] Laserjet 4P will only print through manual feed"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by eatingganesh on 2008-10-19
I am at a total loss on this one. Whenever I print an Oo file or a test page from the printers dialog, the printer goes to manual feed. I have set everything for tray 1. I have double-checked everything in the printer menu directly (where the manual feed is set to OFF).

Is this a driver issue? I used the recommended driver in the printer setup dialog, which is HP LaserJet 4P - CUPS+Gutenprint v5.0.2 Simplified. I did try the other drivers provided for this printer, but they did the same thing.

Any ideas? feeding individual pages everytime I need something in print is driving me nuts (I'm a writer, so I print alot)!

Thanks in advance!

---

### Post by rustutzman on 2008-10-19
This usually is a printer config issue. You need to look at the paper handling menu in the printer setup menu.

Russ

---

### Post by eatingganesh on 2008-10-19
> **rustutzman said:**
> This usually is a printer config issue. You need to look at the paper handling menu in the printer setup menu.

Russ

Yeah, I did that. All is set for tray 1 and manual feed is turned off.

---

### Post by rustutzman on 2008-10-19
This may sound like a stupid question but are you sure that manual feed isn't tray 1? I often see it referenced as a tray and the first tray as tray 2.

Russ

---

### Post by oldsoundguy on 2008-10-19
I have a 6mp .. Manual feed is letter.  Tray 1 is auto feed letter, tray 2 is auto feed legal. (also check the CONTACT on the manual feed door as it will override the tray if it is not completely closed or if the contact is defective.

(that is, after all, and OLD laser (15 years old or older)!  I wore two of that model out!)

OR, it may be a cups issue.  Try installing an alternate driver from cups or using the HP toolbox (HPLIP) (install from Synaptic)

---

### Post by wyliecoyoteuk on 2008-10-19
On a HP4, tray1 IS manual feed, because some machines came without a cassette, so the cassette is tray2.
This is how the PCL commands address it.
(it is still the case on some more recent HP printers).

---

### Post by eatingganesh on 2008-10-19
oh crap, I knew that! Thanks for the helpful reminders Russ, OldSoundGuy and Wyliecoyoteuk!

---

