---
title: "Selecting a partition on boot up"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by NigelSh on 2012-06-08
I've installed Ubuntu 1204 in a partitioned drive alongside another Linux Distro.

However I have found that I cannot select the other distro when booting up because the boot screen won't respond to the cursor keys.

Any clues?

---

### Post by coffeecat on 2012-06-08
Welcome to the forum.

Are you using a USB keyboard? It may be that you need to enable legacy USB support in the BIOS before the grub menu will respond to a USB keyboard.

**EDIT**: I should have added. If this is the problem, you'll need a keyboard with a PS/2 connector to be able to enter the BIOS to change the settings.

---

### Post by NigelSh on 2012-06-08
Thanks for the information. Yes, I do indeed use a usb keyboard. There's the added problem that the keyboard is shared with another computer via a Belkin FLIP device. I guess that I'll need a dedicated keyboard for the Linux machine to solve this one. (Oh dear, more clutter... :-))

---

### Post by coffeecat on 2012-06-08
> **NigelSh said:**
> I guess that I'll need a dedicated keyboard for the Linux machine to solve this one. (Oh dear, more clutter... :-))

**If** my hypothesis is correct, you'll only need the PS/2 keyboard for a few seconds to change the BIOS setting after which the USB keyboard should work just fine with the grub menu. The only proviso being the Belkin FLIP device. Is that a KVM switch? That *might* also be a complicating factor, but see how enabling USB support in the BIOS goes.

Good luck with the clutter! :)

---

