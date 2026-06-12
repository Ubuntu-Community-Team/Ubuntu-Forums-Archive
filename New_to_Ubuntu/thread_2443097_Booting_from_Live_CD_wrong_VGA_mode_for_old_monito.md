---
title: "Booting from Live CD: wrong VGA mode for old monitor"
date: 2020-05-11
forum: New to Ubuntu
---

### Post by zulunation on 2020-05-11
Hi,ALL

I have a bit old PC with 17inch monitor. It works fine with window 10 (not trolling).
I have created a boot USB flash with Ubuntu Live.
When I boot from flash i see very distorted image with selection (Try Ubuntu or Install Ubuntu) I press auto on my monitor but it does not help.
When i press try ubuntu the image disappear and "VGA mode not supported" comes.

I have figured out that there is vga = xxxx parameter which can be selected to force kernel to use appropriate resolution mode. But i don't know where to set up that parameter. I have a bootable USB flash with some files.

How can i force Linux on a live USB flash to use specified VGA mode?

Thanks

---

### Post by CelticWarrior on 2020-05-11
A bit old but how old exactly? BIOS or UEFI?

Assuming it's BIOS press F6 in the Grub menu and select 'nomodeset'. Then try booting the live session as usual.

Please post detailed hardware specification, namely the graphics, and the monitor itself and how is it connected.

---

### Post by zulunation on 2020-05-12
Hi,

Yes it's bios and VGA.
I have tried what you advised and it worked perfectly. Thanks a lot.

---

