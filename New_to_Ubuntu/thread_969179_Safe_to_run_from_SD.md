---
title: "Safe to run from SD?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by willmacleod on 2008-11-03
So Im thinking of running ubuntu/other distros I use from an SD memory card, but I'm wondering if the constant read/write would kill the sd card i use?

---

### Post by Zzl1xndd on 2008-11-03
I would suggest going with EXT2 as a file system if your gonna run from an SD card. EXT2 doesn't have journaling and should cut down on the number of writes.

---

### Post by Kellemora on 2008-11-03
Hi Will

I've never put my finger exactly on what kills SD cards or Smart Media, and can state almost positively that it's NOT associated with writing to them, since I have every client I work with on their own pair of SD cards, never had one go bad yet.

Nonetheless I have a wastecan full of dead ones from other uses.

Students use them to turn in their homeowork assignments and load music on them which they keep playing at concert hall pitch all day and night.  Never seem to have problems with them.
The frau's movie camera uses them, she's never had one go bad.
We use SD cards in a few of our still camera's, never had one die yet in that usage.
I have a couple in GPS units, have had one die already in that usage.  Only written to one time too.

But put one in a PalmPDA and an ice cube in that proberbial hot place will last longer.
Almost EVERY SD card I've killed so far, it died in the PalmOne!
And the SD card used in that application is only loaded one time also.  And rarely read from.

Must have something to do with voltage or static is all I can figure!
But the ones in the camera's are pulled, tossed in the bag, shoved into the computer to download from, erased, tossed back in the camera bags until needed next.
We've lost a few from Physical Damage, but that's about it.

I've been using an 8mb SmartMedia card, and you know how flimsy those things are!
To transfer log data from an environmental recorder to the computer once a week for like 5 years now.  When it does die, I'm sunk, I don't think you can buy anything that small anymore.  And the recorder can't use anything larger than 16mb.  Only needs about 250kb to last a whole month, hi hi........

In any case, I would use two, one as a backup!

TTUL
Gary

---

### Post by Krupski on 2008-11-03
> **Kellemora said:**
> Hi Will

I've never put my finger exactly on what kills SD cards or Smart Media, and can state almost positively that it's NOT associated with writing to them, since I have every client I work with on their own pair of SD cards, never had one go bad yet.

Flash memory, EEPROMS and EPROMS all work in the same way. Each memory cell is a field effect transistor with an insulated, floating gate.

To program a cell, a high voltage is applied to the outside of the insulated gate (by high voltage I mean 6 to 12 volts in a part that runs on 3.3 to 5 volts).

The electrons "tunnel through" the insulating oxide layer and get trapped in the FET gate.

When read, this gate is "on" (conducting).

If the chip is an EPROM, exposure to ultraviolet light ionizes the chip area and allows the trapped electrons to bleed out (erases the chip).

Flash and EEPROM apply a reverse voltage to the floating gate to "suck out" the trapped electrons, thereby erasing the cell.

Forcing electrons past the insulating oxide layer gradually degrades the layer and it becomes less and less of a good insulator after 10,000 to 1 million writes.

When the layer gets "leaky", the electrons can leak out of a programmed cell and a "0" bit change back into a "1" bit.

This is what everyone calls "wearout of flash memory".

Wearout is caused by erase / write cycles which are done in sectors (blocks) in a flash chip.

READING, however, is harmless. You can read flash forever and it won't hurt it.

It is WRITE cycles that wear out the chip.

In a camera or other use, the cells natural lifetime translates into decades if not centuries of use before the cells wear out.

But, when the flash holds an OPERATING SYSTEM, there can be constant writes to different areas in the normal course of the OS running.

However, don't worry... take the typical lifetime of a flash memory device, figure out how many write cycles it will see and you will find that it takes YEARS to wear out the chip when used to hold an operating system.

Short summary: Don't worry about it.

-- Roger

---

### Post by eldragon on 2008-11-03
you will probably be ok if you take the following precautions:

mount /tmp and /var as ramfs. how to do this...i wouldnt know. shouldnt be hard :D

those folders are the most written to, and they are usually garbage you dont need to keep.

---

