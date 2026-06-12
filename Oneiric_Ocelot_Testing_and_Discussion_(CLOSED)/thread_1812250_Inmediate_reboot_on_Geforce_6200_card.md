---
title: "Inmediate reboot on Geforce 6200 card"
date: 2011-07-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by phoogkamer on 2011-07-26
Hello,

I am running Oneiric on a Dell DV051 with an internal Intel graphics card and a PNY Geforce 6200 PCI card on a PCI slot. When booting the install cd with the Auto function in BIOS enabled (using the Geforce card) then I see the purple screen with the keyboard and ubuntu icon below. After that it reboots. When running on the Intel internal card, there is no problem. Installed Oneiric on the interal card and installed the nvidia driver.
lsmod | grep nvidia shows me the loaded nvidia module, External drivers program shows the nvidia-current enabled, but not in use. When booting into ubuntu with the Geforce card enabled it shows grub. I edited the kernel line and removed quiet splash. Then booted, but the only thing I see is "Loading, please wait" in a flash and then it reboots. Does anyone have any idea how to solve this?

Regards,

Peter

---

### Post by cariboo on 2011-07-26
When booting from the Live CD, press any key when you see the little man & keyboard, press F6 and select nomodeset, then boot normally.

I've always had to use nomodeset/safe graphics mode with 6200 chipsets.

---

