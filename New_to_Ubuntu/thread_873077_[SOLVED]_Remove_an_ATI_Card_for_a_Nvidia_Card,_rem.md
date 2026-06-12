---
title: "[SOLVED] Remove an ATI Card for a Nvidia Card, remove drivers first?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Sugi on 2008-07-28
I want to take out an AGP ATI 9600 SE 128 MB for an upgraded PCI Nvidia GeForce FX 5200 256 MB, but shouldn't I remove the drivers from the ATI card first?  But if so, How do I remove them?  I installed the ATI drivers from System > Administration > "Hardware Drives".

After that, Will ubuntu detect my Nvidia hardware and setup drivers ready for me when I check System > Administration > "Hardware Drivers"?

Specs:
8.04 Hardy
128MB ATI 9600 SE

Change for:
256MB Nvidia GeForce FX 5200 

Thanks,
Sugi

[B]Update:
Well, I disable the ATI drivers and restarted.  The x server booted up, so I powered down and removed my ATI card.  Then I installed the nvidia card.  Booted up and installed the nvidia drivers from "Hardware Drivers" within Hardy.  Everything works. :D

Thanks,
Sugi[/B]

---

### Post by waspbr on 2008-07-28
just go to System>Administration>Hardware drivers and just unselect the current drivers

---

### Post by Elfy on 2008-07-28
I think that you won't be able to install the new drivers until the cards is in. Disable old, shutdown, change card, reboot and install from hardware drivers - is the way I would do it. Could be wrong though..

---

### Post by Sugi on 2008-07-28
Would that be bad though, having video cards for both ATI and Nvidia at the same time?

First I installed the Ati Card in my Tower then Installed the ATI drivers from "Hardware Drivers".  But I became unpleased witht the ATI card, so I uncheck ATI drivers in "Hardware Drivers" and then I removed the ATI card and then switched the Nvidia Card into the Tower.  Next I installed the nvidia drivers.  Would that not cause problems within the system having both ATI drivers and Nvidia there?

---

### Post by Elfy on 2008-07-28
If you disable the ati before you change the card it should be ok. When you disable the driver it should chnage the xorg - check it

---

### Post by sydbat on 2008-07-28
This is not like Windows, where you have to completely (sic) remove the drivers so there is no conflict. Just disabling and uninstalling/reinstalling the physical cards should work. Ubuntu GNU/Linux is pretty smart for that kind of thing...in my experience with old ATI/Voodoo cards.

---

