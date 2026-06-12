---
title: "Boot up"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by kattou22 on 2008-09-20
oki, i want to install Ubuntu again on my new computer. What i definately dont want is to have it boot from grub or lilo. I want it to boot from a cd or anything else. Is there any way to do that.

---

### Post by Pro-reason on 2008-09-20
> **kattou22 said:**
> oki, i want to install Ubuntu again on my new computer. What i definately dont want is to have it boot from grub or lilo. I want it to boot from a cd or anything else. Is there any way to do that.

So what do you what exactly?  Without a bootloader, the computer will be worthless unless you have your CD or whatever.  Are you wanting to have another operating system on there (i.e. Windows XP) and use its bootloader?

If so, then yes, you can allow that bootloader to work, and only boot into Ubuntu when you insert something else.  The BIOS of your motherboard will have to be set up to boot from such media first.  You can install the GRUB bootloader to a CD or a USB flash drive, and have it point to the relevant boot files on your Ubuntu partition.

---

