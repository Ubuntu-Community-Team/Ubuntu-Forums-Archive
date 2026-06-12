---
title: "RAID 1 Confusion"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by MockY on 2008-05-27
I have 2 discs in hardware raid 1. In Windows, this is detected as one disc, which is what it is when properly configured. But when I boot Ubuntu from the live cd and run the installer, it lists both discs as independent, and not as 1. Why is this and what do I do from here?

---

### Post by quelx on 2008-05-28
Ubuntu needs drivers (if they exist) for your raid controller, what you have is probably a software raid, CPU power is used to manage the array and software keeps data in order, unlike a hardware raid where all of that is done by a separate raid CPU.

[http://linux-ata.org/faq-sata-raid.html](http://linux-ata.org/faq-sata-raid.html)

---

### Post by MockY on 2008-05-28
I specifically said that I do have a hardware raid and not a software.
I will check out the site nonetheless.

---

### Post by quelx on 2008-05-28
> **MockY said:**
> I specifically said that I do have a hardware raid and not a software.
I will check out the site nonetheless.

If you are using the raid on your Asus board it is definitely *not* hardware raid.

A hardware raid card starts at $100 and I've only seen server boards with true hardware raid onboard, otherwise it was a expansion card.

---

