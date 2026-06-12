---
title: "[SOLVED] BIOS Bug?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by keiichidono on 2008-09-02
I updated Linux Mint Elyssa the other day and then restarted it, to no avail. It just gave me an error about a BIOS bug and just won't restart, that wouldn't be so bad if it didn't happen with LiveCD's too. I took a picture, can anyone give me any clues or is this computer totally screwed? I think I may have to try and update the BIOS or something but I'm totally lost on that.

[IMG]http://img440.imageshack.us/img440/5999/dscf2074uo6.jpg[/IMG]

---

### Post by Thingymebob on 2008-09-03
If the full message is:
```

MP-BIOS bug: 8254 timer not connected to IO-APIC

```
then try adding the noapic option to your boot options by editing /boot/grub/menu.lst and adding ***noapic*** to the end of each kernel line, it may also be worth adding it to the default options so as your system won't break next time the kernel is upgraded

You could add ***noapic*** to the kernel line in the grub boot menu at startup to get your system up again

**For Live CD**
press F6 at the boot menu and add ***noapic*** right before the final --

---

### Post by Lateforgym on 2008-09-03
Flaky BIOS is said to be a sign of of a battery going out. Might just want to keep that in mind if you have an old system.

---

### Post by keiichidono on 2008-09-03
> **Thingymebob said:**
> If the full message is:
```

MP-BIOS bug: 8254 timer not connected to IO-APIC

```
then try adding the noapic option to your boot options by editing /boot/grub/menu.lst and adding ***noapic*** to the end of each kernel line, it may also be worth adding it to the default options so as your system won't break next time the kernel is upgraded

You could add ***noapic*** to the kernel line in the grub boot menu at startup to get your system up again

**For Live CD**
press F6 at the boot menu and add ***noapic*** right before the final --
That's the full message but the problem is that my USB keyboard does not work so I can't enter F6 when booting a LiveCD but I have a USB to PS2 connector and a PS2 keyboard/mouse if all fails to use for the time being. I don't have grub load up at all when I turn on the computer because Linux Mint is the only and default OS. I think there is a way to replace GRUB using the LiveCD, do you know how?

---

### Post by Thingymebob on 2008-09-03
I thought Mint used grub as its bootloader (just about every distro uses either grub or lilo), just after 'post' you may get a message for a short period that reads 'Grub Loading.....' you need to press escape here to be able to see the boot menu.

I'd use the PS2 stuff you have to get your system working then put your USB keyboard back in

---

### Post by keiichidono on 2008-09-03
It uses grub but the delay before starting the default OS is set to "0". I think I might be able to boot into the LiveCD and try what the previous poster said by mounting the existing partition and editing the menu.lst. I'll give it a shot and report back.

---

### Post by keiichidono on 2008-09-03
It worked, thanks for all the help. :D

---

### Post by Thingymebob on 2008-09-03
No Problem, Don't forget to mark the thread as solved

---

