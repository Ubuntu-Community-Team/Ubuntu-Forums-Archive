---
title: "PCI ACPI error - system startup - no display in monitor"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by janesh on 2008-12-01
Hi,

My Ubuntu "Feisty Fawn" desktop does not start up certain times. Though the CPU starts making noise there is no display in the screen. Even on attempting repeatedly it does not start. But certain times it starts fine. Not sure what the problem is, but I noticed the following errors during startup:

------------------------------------------------------------------------
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
* The chipset may have PM-Timer Bug. Due to workarounds for a bug
* this clock source is slow. If you are sure your timer does not have 
* this bug, please use "acpi_pm_good" to disable the workaroudn
PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPI0/TC0
PCI quirk: region 0400-04bf claimed by ICH4 GPI0
------------------------------------------------------------------------

Once I also got the following error:

------------------------------------------------------------------------
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routerirq". If it helps, post a report
------------------------------------------------------------------------

Could someone help me identify the problem?

Thanks.

Kind regards,
Jan

---

### Post by janesh on 2008-12-01
/atta[IMG]/home/janesh/temp/DSC01967.JPG[/IMG]

---

### Post by carml on 2008-12-01
Hi,me too I'm a new user of Ubuntu.I have Hardy Heron installed on my notebook,and when I have some problem I try to correct it by choosing the recovery option on startup.This way requires a internet connection avaible,try it if you can and let me now.

---

### Post by caljohnsmith on 2008-12-01
Just out of curiosity, is there some particular reason why you've decided to stick with Fiesty Fawn and not upgrade to at least Hardy or Intrepid? 

You could try adding that "pci=routerirq" option you showed in your post to your kernel line on start up and see if it helps. On start up when you get the Grub menu, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the line add "pci=routerirq"; press return to save the change, and "b" to boot Ubuntu. If that doesn't help, here are some other kernel options you could try adding to see if it helps your problem:
```
noapic nolapic acpi=off pci=noacpi irqpoll ide=nodma nopcmcia
```
You can experiment with those and see if it helps. Good luck and let us know how it goes.

---

