---
title: "SIS VGA compatible controller"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by MooLoo on 2013-05-17
Hi There,

Recent install, having problems getting my monitor to display correctly.

Is anybody able to help please. At present the monitor is displaying large fuzzy lines from top to bottom when set at 1280X1024.   
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04)

---

### Post by sanderj on 2013-05-18
Is this a desktop and is the VGA card a separate device which you replace? If so, my advice is to replace the SIS card with something with an Intel or ATI/Nvidia chipset. Reason: SIS refuses to release drivers for Linux.

If not: did you Google "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP"? When I do that, there are workarounds posted.

Once again: if you can replace the hardware, replace it

---

