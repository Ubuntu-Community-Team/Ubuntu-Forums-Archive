---
title: "mmc0: error -110 whilst initialising SD card"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by smiley1962 on 2011-10-12
got a problem getting my sdcardreader to mount, any help apreciated.

output dmesg:
mmc0: error -110 whilst initialising SD card

---

### Post by techvish81 on 2011-10-12
> **smiley1962 said:**
> got a problem getting my sdcardreader to mount, any help apreciated.

output dmesg:
mmc0: error -110 whilst initialising SD card

it may not have got proper driver especially for your cardreader, coz 
it recognises both of my card reader and works like a charm.

---

### Post by smiley1962 on 2011-10-12
Not sure about that, i did an upgrade and it worked in natty.
lspci gives me: SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)

I will try to see what output a livecd gives me.

Tried the livecd 9.10, gave the same output of lspci.

The live cd recognized the sd card properly, and mounts/unmounts it.

---

### Post by smiley1962 on 2011-10-12
102.496028] mmc0: Timeout waiting for hardware interrupt.
[  102.496035] sdhci: =========== REGISTER DUMP (mmc0)===========
[  102.496042] sdhci: Sys addr: 0x00000000 | Version:  0x0000c002
[  102.496048] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[  102.496054] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[  102.496060] sdhci: Present:  0x01f70000 | Host ctl: 0x00000005
[  102.496067] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[  102.496073] sdhci: Wake-up:  0x00000000 | Clock:    0x00000000
[  102.496078] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
[  102.496085] sdhci: Int enab: 0x00ff00c3 | Sig enab: 0x00ff00c3
[  102.496091] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[  102.496097] sdhci: Caps:     0x03f532b2 | Caps_1:   0x00000000
[  102.496103] sdhci: Cmd:      0x00000102 | Max curr: 0x00ffffff
[  102.496108] sdhci: Host ctl2: 0x00000000
[  102.496110] sdhci: ===========================================


more output dmesg.

---

