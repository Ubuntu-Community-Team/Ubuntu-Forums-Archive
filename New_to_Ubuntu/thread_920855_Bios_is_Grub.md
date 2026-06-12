---
title: "Bios is Grub ?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Gost-Taras on 2008-09-15
Does ubuntu use bios ?

What is grub is it like bios but for unix like systems ?

thank you

---

### Post by Mornedhel on 2008-09-15
BIOS is the firmware for your motherboard (roughly speaking). Thus, it is motherboard-specific and every OS relies on it at some point.

GRUB is a boot loader that lets you choose an OS to boot from a list. It also happens to be the default boot loader installed by Ubuntu when multiple OSes are installed. It starts after the BIOS and does the same thing as Windows' boot loader, which you might have used if you have a recovery partition or multiple Windows versions installed.

---

### Post by Tatty on 2008-09-15
Basically the BIOS of a system is the very first part which loads when you switch it on.  It is attached to the motherboard and stored on a ROM chip.  It performs all the fundamental operations of checking what hardware is present, switches it all on, and then it searches your drives for a boot manager to boot an operating system.

GRUB is a boot manager.  On a typical system it is stored on the hard drive and it will list all your operating systems, giving you an option to boot one of them.

The basic workflow is this:

Switch On -> Bios Loads -> Boot Manager (grub) loads -> Operating System Loads

---

### Post by kansasnoob on 2008-09-15
> **Gost-Taras said:**
> Does ubuntu use bios ?

What is grub is it like bios but for unix like systems ?

thank you

BIOS is used by the system board (motherboard). BIOS = Basic Input Output System.

GRUB has nothing to do with BIOS! GRUB is a bootloader > Grand Unified Bootloader to be exact.

All systems are reliant on BIOS whether you use LILO, GRUB, or NTLDR.

---

### Post by Gost-Taras on 2008-09-15
So ubuntu does uses bios but how can i find out what make or version of bios do i have ?

---

### Post by Tatty on 2008-09-15
> **Gost-Taras said:**
> So ubuntu does uses bios but how can i find out what make or version of bios do i have ?

It should tell you your BIOS version when you first switch your computer on.  Usually you can press one of your function keys F1-F12 (which one it is varies between motherboards) to get into your bios settings when you first switch your computer on.

Are you having some BIOS related issues?

---

### Post by kansasnoob on 2008-09-15
What are you trying to accomplish?

---

### Post by houbysoft.xf.cz on 2008-09-15
Yes, it would help that you would say what you're trying to do. But for the BIOS info, it usually shows up when you start your computer, but blinks away quite fast. So if you want to see some info, you can just start your PC, press the Pause key when the info shows up, write it down on a paper or something, and then, when you're done, hit any key or Enter or space (it depends on your BIOS) to continue booting.

---

### Post by Gost-Taras on 2008-09-16
Thanks guys,

i was just trying to find out more information about bios and linux

---

