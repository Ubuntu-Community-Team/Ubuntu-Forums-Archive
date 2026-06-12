---
title: "[SOLVED] Boot Loader instead of grub?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-08-24
Can I use boot loader instead of GRUB? I've satisfied myself with the live CD and am read to go to a dual boot.

I think it might be called Boot.ini. On one of my systems I put separate OS XP on two different HDDs, then edited the boot loader so it would automatically load one or I could select another before 5 seconds are up. 

I see a lot regarding GRUB, but wouldnt it be just as simple to edit the boot loader? or is GRUB a better choice for some reason?


Thanks

---

### Post by OutOfReach on 2008-08-24
GRUB is an easier choice to save you from the frustrating work of editing the XP boot loader.

---

### Post by mrsteveman1 on 2008-08-25
NTLDR (the XP loader) and the one for Vista, cannot directly load the Linux kernel, nor can they pass initrd or root arguments to it at boot time.

The only loaders im aware of that work to load Linux are grub, grub2, lilo, and extlinux.

You can however chainload grub from the 2 windows loaders or chainload the Windows loader from Grub (which is what most people do).

Just install Ubuntu carefully and follow the directions on dual booting on the wiki here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by pi.boy.travis on 2008-08-25
GRUB is the best bootloader out there (in my opinion), and should chainload Windows without a problem.

---

### Post by Lateforgym on 2008-08-26
One last question. If I have multiple OS, can I set GRUB to auto load a specific OS after a few second wait or do I have to manually tell it which one to load?

Thanks.

---

### Post by pi.boy.travis on 2008-08-26
Yup.  Install the package startup manager via synaptic.

---

### Post by pmlxuser on 2008-08-26
> **Lateforgym said:**
> One last question. If I have multiple OS, can I set GRUB to auto load a specific OS after a few second wait or do I have to manually tell it which one to load?

Thanks.
Oh yeah thats possible even without installing the boot manager, you could edit /boot/grub/menu.lst file by changing the default OS

---

