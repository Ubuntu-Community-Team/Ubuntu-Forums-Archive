---
title: "[SOLVED] Booting with &amp;quot; profile&amp;quot; added to kernel?"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-08-28
I was just curious what exactly adding " profile", at the end of the kernel line in GRUB does?

---

### Post by unutbu on 2008-08-28
It makes a list of all the files needed to boot and places that list it /etc/readahead. Knowing which files are going to be needed allows the kernel to keep the hard drive busy while the CPU is loading a driver, for example.

When you boot with the profile option, the boot may take an extra 25 seconds. Subsequent boots without the profile option may be faster. If your /etc/readahead is already correct, you won't see any gain in boot speed.

See [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by slughappy1 on 2008-08-28
Awesome, thanks.

---

