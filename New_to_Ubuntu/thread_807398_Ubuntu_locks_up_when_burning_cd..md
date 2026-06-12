---
title: "Ubuntu locks up when burning cd."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by luke949 on 2008-05-25
Hi!
  When trying to burn a cd, ubuntu locks up and I can't do anything whatsoever. I can't move my mouse nor go back to the login window. I tried using Brasero and CD/DVD Creator. Both have locked up Ubuntu. I'm using an ATAPI CD-RW52XMAX.

Thanks

---

### Post by Sinkingships7 on 2008-05-25
> **luke949 said:**
> Hi!
  When trying to burn a cd, ubuntu locks up and I can't do anything whatsoever. I can't move my mouse nor go back to the login window. I tried using Brasero and CD/DVD Creator. Both have locked up Ubuntu. I'm using an ATAPI CD-RW52XMAX.

Thanks

I can't really help fix the lock-ups, or tell you why it's happening, but I can tell you that when you hard reboot you computer as a result of these lock-ups, you risk damaging your file system. I can also tell you how to safely kill all processes and reboot the system safely.

When you get one of these lock-ups, hold down alt+printscrn keys, then press, in this order, R E I S U B.


Hope this helps in the future :]

---

### Post by luke949 on 2008-05-25
alright cool, ill keep that in mind next time my system locks up, thanks!

---

### Post by xenocide13 on 2008-05-25
my system has been locking up when i try to start anything at all but when i do alt print screen REISUB nothing happens what is that supposed to do?

---

### Post by spiderbatdad on 2008-05-25
> **luke949 said:**
> Hi!
  When trying to burn a cd, ubuntu locks up and I can't do anything whatsoever. I can't move my mouse nor go back to the login window. I tried using Brasero and CD/DVD Creator. Both have locked up Ubuntu. I'm using an ATAPI CD-RW52XMAX.

Thanks

Seems more like a general hardware issue than an issue with the software or your particular cd-writer. You can try burning from the command line with cdrecord to see if any error come up...or run one of the burning programs you've used from the command line.
I would read the output of dmesg (run in the terminal) to look for problems in hardware detection during the boot process. Many of these issues can be fixed by adding parameters to the grub/kernel line like: pci=routeirq or lapic

---

### Post by diablo75 on 2008-05-25
If your hard drive and the burner are on the same IDE channel, you might consider opening your case up and moving the burner to the other port.  You might also check to see if your BIOS is up to date by visiting the manufactures website and seeing what the latest version number they have posted is.

---

