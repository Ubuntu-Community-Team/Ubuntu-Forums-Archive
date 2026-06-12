---
title: "Install Problem On Old PC"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Chip Nuttall on 2008-09-07
[EMAIL="pilarchip1@mac.com"]pilarchip1@mac.com[/EMAIL]

I am new to Ubuntu. I live on a small island in the Philippines and I am trying to help some of the teachers with their old computers by trying to install Ubuntu for them. The current computer configuration is as follows:
Motherboard ASUS P3V133
Ram PC 133 512 Meg (new)
HD 15.3 GB Seagate U10 Model ST315323A
Bios Award Medallion V6.0 ACPI BIOS Rev 1002 Beta 05
CPU Intel Pentium III 933 MHz
Cache memory 256K
CD Compaq LTN485
Graphics SIS 6326 AGP 8MB video memory BIOS Ver 1.25 supports VESA BIOS 2.0

Ubuntu Menu Options show when booting from alternate ubuntu CD but then hangs when I choose "Install"

If I choose F6 Boot Options, delete quite and add noapic loading starts and continues until the following entry:
init[1]: segfault at 00000001 eip h7f2e687 esp bfcc26f8 error 4

then this same entry just keeps repeating until I reboot.

The other parameters I have tried; acpi=off results in a "hang"/ nolapic the same "hangs"/ edd=on results in a 'hang" FATAL/ lapic pci=routeirq also resuts in a "hang".

I really want to learn to install Ubuntu on these old computers and help these dedicated teachers and their students so any help will be greatly appreciated!

I have no trouble loading Ubuntu on my own notebook, a VooDoo Envy 515.

Warmest Regards,
Chip Nuttall
[email]pilarchip1@mac.com[/email]
:)

---

### Post by kerry_s on 2008-09-07
sounds like a bad burn. try the check disk option.
burn slow 4x for the best results.

---

