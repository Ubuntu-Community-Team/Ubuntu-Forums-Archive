---
title: "First system corruption after update..."
date: 2008-11-20
forum: New to Ubuntu
---

### Post by pablolie on 2008-11-20
So I have been running a very Vanilla version of 8.10 for 2 weeks. This morning I went for the (stable and recommended) system updates... and the system no longer starts. It hangs with 
Start...
at the very beginning of the boot, obviously corrupted. The unfortunate aspect is that this was the "rogue" system I have at work -after happily using Ubuntu at home for a year- to *prove* to people around me how superior Ubuntu is. And I find myself havving to type this message from the Vista partition. Not good.
Boooo to those updates! It had never happened to me before!

---

### Post by philinux on 2008-11-20
Can you see grub loading. Can you press escape and boot into recovery mode?

---

### Post by pablolie on 2008-11-24
> **philinux said:**
> Can you see grub loading. Can you press escape and boot into recovery mode?

No, it hangs totally and utterly. After selecting the Ubuntu boot option (safe and Windows are the other options), all that happens is

Boot from (hd0,4) ext3
Starting up ...

and hangs there in the black screen. I may try to reinstall, or may just give up Ubuntu evangelism at work for now...

---

### Post by pablolie on 2008-11-24
> **pablolie said:**
> No, it hangs totally and utterly. After selecting the Ubuntu boot option (safe and Windows are the other options), all that happens is

Boot from (hd0,4) ext3
Starting up ...

and hangs there in the black screen. I may try to reinstall, or may just give up Ubuntu evangelism at work for now...

When I go for safe mode (instead of regular Ubuntu boot), it hangs after

checking if image is initramfs... <7> switched to high resolution mode on CPU1

...and that is that. Hangs.

---

