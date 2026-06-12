---
title: "How do I boot from CD with Grub installed (dual boot Windows 7 and Ubuntu 11.10)"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-03-09
I have dual boot on all of my computers, this one is Windows 7 and Ubuntu 11.10. I also have a old laptop without a hard drive and am trying to boot up in Puppy Linux to make a bootable USB for it. My BIOS is set to boot from CD first but it will not do it. It goes straight to GRUB and only gives me the options of Ubuntu 11.10 or Windows 7. How do I add the option of booting from CD to a computer that has the GRUB installed from loading Ubuntu 11.10?

---

### Post by Grenage on 2012-03-09
Greetings.

The boot order is handled by the computer's BIOS, so you don't need to worry about grub.  Do any CDs boot correctly?  The most common causes of this problem are:

1) The BIOS boot order is incorrect.
2) The CD being used has a defect (physical or data corruption).
3) The CDROM drive has a problem.

Sometimes it's a 'quirk', and selecting a "boot selection" prompt at boot time (if it exists) will work.

---

### Post by theducksfan2010 on 2012-03-09
> **Grenage said:**
> Greetings.

The boot order is handled by the computer's BIOS, so you don't need to worry about grub.  Do any CDs boot correctly?  The most common causes of this problem are:

1) The BIOS boot order is incorrect.
2) The CD being used has a defect (physical or data corruption).
3) The CDROM drive has a problem.

Sometimes it's a 'quirk', and selecting a "boot selection" prompt at boot time (if it exists) will work.
My boot sequence in the BIOS is correct, USB, CD, HDD. Based off of your response, I went and downloaded the puppy .iso again and re-burned onto a new CD. Got a boot up off of the CD. Thank You!

---

