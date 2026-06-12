---
title: "Grub Rescue Error"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by ajdrew06 on 2013-01-23
Hi All,

Ubuntu 12.04 will not boot on my laptop. I keep getting the following error.

error: unknown filesystem.
grub rescue>

I am able to run a live-cd. I have tried using boot-repair-disk.iso; however, it says something to the effect of the boot repair was successful and to restart the computer... I restart the computer, and I get the same error.

Please advise.

-drew

---

### Post by elgordodude on 2013-01-23
That's not a lot to go on, but I'll take a wild guess.

Is it a mac? Did you install ubuntu on to an HFS partition? Grub is generally less than thrilled with non-nix filesystems, but it tends to work with FAT and NTFS. HFS tends to throw it for a loop.

Alternatively tell us some more about the laptop, like the model. BIOS settings probably aren't an issue as grub seems to be okay, but does it need to be fixed from grub or is a reinstall doable?

---

### Post by ajdrew06 on 2013-01-24
nevermind... harddrive crashed =(

---

