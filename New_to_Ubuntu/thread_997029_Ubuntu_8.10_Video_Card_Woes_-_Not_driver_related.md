---
title: "Ubuntu 8.10 Video Card Woes - Not driver related"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2008-11-29
I am trying to install drivers for my NVIDIA 6200 but I encountered a problem.  My machine has always had trouble with Linux but adding the boot parameter 'acpi=off' or 'noapic noalpic' has fixed it. Not this version. I had to do that and change (In the BIOS) my default video card from my PCI slot to the onboard video. If I don't do that then Ubuntu hangs on boot.
I am afraid to install the drivers for fear that when I reboot I will not be able to boot using my NVIDIA card and I will have to use integrated which will then not work because of the NVIDIA drivers. Anyone know of something to do?

---

### Post by linuxguymarshall on 2008-11-29
Anyone?

---

### Post by Olivier2371 on 2008-11-29
What version of the driver do you have?

Have you try to install "envyng".

It install my graphic driver without any trouble.

---

### Post by linuxguymarshall on 2008-11-29
I have installed Envy but have not used it to install the driver yet because I think that the OS and my BIOS will conflict and I will have trouble loading Ubuntu.

---

### Post by Olivier2371 on 2008-11-29
try running this command

lspci

---

