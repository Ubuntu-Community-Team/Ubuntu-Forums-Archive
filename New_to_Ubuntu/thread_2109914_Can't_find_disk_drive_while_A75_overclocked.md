---
title: "Can't find disk drive while A75 overclocked"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by agent00skid on 2013-01-28
I'm running an AMD A6-3500 on a A75 chipset, and am overclocking using the base clock.

Unfortunately, Ubuntu can't find my hard drive when the overclock is in effect.

I have no such problem with Windows 7, and GRUB2 also works without problems.

---

### Post by Mark Phelps on 2013-01-29
I've been doing overclocking for a long time and never encountered a problem accessing hard drives -- so, this is puzzling.

How is the hard drive connected -- PATA? SATA? SATA II? SATA III?

If SATA, is it IDE or AHCI?

Also, you said that GRUB2 works but Ubuntu can't find your hard drive.  Given that GRUB2 stores its code on your hard drive, Ubuntu must be able to find it in order to boot.

So, how are you looking for the drive in Ubuntu, such that you can't see it?

---

### Post by agent00skid on 2013-01-29
It's a SATA 2 hard drive on a SATA 3 port. And set to AHCI.

I have checked the dmesg from a bootable USB with and without overclock. And this is one of the only difference I find.

At standard clock:
[    8.417742] ata6: SATA link down (SStatus 0 SControl 300)
[    8.417817] ata2: SATA link down (SStatus 0 SControl 300)
[    8.417895] ata4: SATA link down (SStatus 0 SControl 300)
[    8.417963] ata3: SATA link down (SStatus 0 SControl 300)
[    8.418028] ata5: SATA link down (SStatus 0 SControl 300)
[    8.589563] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

Overclocked:
[    6.492442] ata5: SATA link down (SStatus 0 SControl 300)
[    6.492497] ata6: SATA link down (SStatus 0 SControl 300)
[    6.492548] ata4: SATA link down (SStatus 0 SControl 300)
[    6.492598] ata1: SATA link down (SStatus 0 SControl 300)
[    6.492649] ata3: SATA link down (SStatus 0 SControl 300)
[    6.492699] ata2: SATA link down (SStatus 0 SControl 300)

Besides that, xhci_hcd doesn't seem to be present either when overclocked, though I have no idea what that means.

---

### Post by Mark Phelps on 2013-01-29
It's apparent that the SATA port is down when overclocking.  On my Mobo, the STA 3 ports can be configured separately from the other ports. It looks like, unless there is a setting specific to the SATA 3 ports, that you will have to choose between overclocking and SATA 3.

---

### Post by agent00skid on 2013-01-29
I'm just confused by the fact that it's up all the way, until Ubuntu takes over.

Edit: Or quite a few things actually. From my limited testing, Windows seems to be the odd one out. Still find it curious that GRUB works.

---

### Post by Mark Phelps on 2013-01-30
> **agent00skid said:**
>  Still find it curious that GRUB works.

Yeah ... that is confusing.  My guess would be that GRUB loads some kind of generic driver that works, but is probably low performance, but when Ubuntu then starts us, it loads (or tries to load) a USB 3 driver -- and that fails.

---

