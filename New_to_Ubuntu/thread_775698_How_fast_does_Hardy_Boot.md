---
title: "How fast does Hardy Boot ?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by dptxp on 2008-04-30
How fast does Hardy boot compared to previous distros ? Is it faster ?

---

### Post by omns on 2008-04-30
Considerably, but I haven't used Ubuntu since 6.06

---

### Post by DJ_Peng on 2008-04-30
It's definitely faster than Gutsy, but I don't have a time I can give you. I do know that I tend to get a lag with Compiz turning on, although I suspect that's more due to my older Nvidia card.

---

### Post by skymera on 2008-04-30
i had a boot of 20 seconds then add login around 35-40 seconds altogether.

But it all depends on your filesystem, hard drive speed, and how much you've tweaked.

---

### Post by kneewax on 2008-04-30
Interesting, I was about to post a question about this when I saw this thread.  If anything Hardy boots slower for me than Gutsy did.  I haven't timed it - but from Cold boot I'd say it takes 20 seconds to display the Ubuntu bouncing bar and a further 40 seconds or so before I get a login screen (and no, Grub isn't set to some ludicrously high default, it spends 2seconds on the Grub Loader)

I run a Centrino 2.3Ghz 1GB DDR laptop, so its not super beefy, but is respectable enough.

---

### Post by hermes0710 on 2008-04-30
45 secs overall

---

### Post by pt_lam on 2008-04-30
Seems a little bit slower, but still ok for me.

---

### Post by rjsec4ever on 2008-04-30
Sadly, I have to Alt-F1 to get Ubuntu to boot, after GRUB chooses it.But as long as you don't install too many startup stuff, it runs pretty decent.

---

### Post by mivo on 2008-04-30
Definitely faster for me than 7.04 and 7.10. 20s before even the upsplash screen appears seems unusually long. I'd go into Grub and temporarily remove *nosplash* and *quiet* from the boot options and see if the system hangs at some point before it gives up trying and moves on. (Escape, "e"dit, then "b"oot.)

---

### Post by BattlePanic on 2008-04-30
After upgrading from Gutsy to Hardy I found that my system now takes much longer to boot.  I turned off the splash screen so I could see what was taking longer.  It looks like the problem has something to do with my disk drives.  Here is the portion of my dmesg log where there is a long pause before the boot continues.

```
[   20.364938] ata_piix 0000:00:1f.1: version 2.12
[   20.364955] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   20.374194] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   20.374876] scsi0 : ata_piix
[   20.384315] scsi1 : ata_piix
[   20.393696] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   20.402788] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   20.497802] usb 1-1: USB disconnect, address 2
[   20.737895] ata1.00: ATA-6: TOSHIBA MK1031GAS, AA204A, max UDMA/100
[   20.747012] ata1.00: 195371568 sectors, multi 16: LBA48 
[   20.756149] ata1.01: ATAPI: MATSHITAUJ-840D, 1.00, max UDMA/33
[   20.765353] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   20.781754] ata1.00: configured for UDMA/100
[   20.853137] Clocksource tsc unstable (delta = -20955635479 ns)
[   20.862386] Time: hpet clocksource has been installed.
[   20.873398] usb 1-1: configuration #1 chosen from 1 choice
[   20.883025] usbcore: registered new interface driver hiddev
[   20.892823] ata1.01: configured for UDMA/33
[   20.902057] ata2: port disabled. ignoring.
[   20.902178] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1031GA AA20 PQ: 0 ANSI: 5
[   20.913128] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.00 PQ: 0 ANSI: 5
```

Also, the timestamps don't give a accurate reflection of how long this is actually taking.  I'd say the pause is between 20 and 30 seconds and occu.

I tried reverting to the kernel used by Gutsy, and it does indeed boot faster, although using the old kernel break my video drivers and probably a few other things too since Hardy wasn't built for that kernel version.

I don't know much about the kernel nor interpreting the log files.  If anyone has run into a similar issue and can shed any light please let me know.

---

### Post by vexorian on 2008-04-30
I have noticed it is faster than feisty, plus the disk check is done in graphic mode which is cool!

---

### Post by master5o1 on 2008-04-30
t<60s

Ubuntu on my grandma's computer boots so much quicker than XP on her other laptop...
(hmeh)

---

### Post by crjackson on 2008-04-30
I've only installed the 32 bit version on my system listed below.  It boots at about the same speed that my 64-bit Gutsy version did.

---

### Post by newb1e on 2008-04-30
34s, 4-5 sec slower than Gusty.

---

### Post by zaussome on 2008-04-30
z

---

### Post by dptxp on 2008-05-01
I am waiting for my CD from shipit.
I guess it will take about same time to boot as the older versions.

---

