---
title: "Windows Overwriting MBR"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by tarun.winlin on 2008-08-11
Hi Guys,

I recently had my friend install ubuntu along with WinXP on my box.

I had both WinXP & ubuntu running on a 50G partition each.

After these 2 were successfully installed, I had around 300G of unpartitioned space left on my HDD. Unfortunately, I was not aware of the windows disk management & went into WinXP recovery console to partition the rest of the HDD & format it for NTFS.

And sure, when I rebooted the box, it does not gives me the GRUB boot loader, it just boot windows straight off. I am pretty sure, WinXP over wrote the MBR.

What should I do to get the GRUB boot loader back in place?

---

### Post by echo6 on 2008-08-11
Boot a Ubuntu livecd and re-install grub.

grub /dev/hda
root (hd0,1)
setup (hd0)
quit

Note in grub (hd0,1) means first drive in your BIOS boot order and the ,1 means the 2nd partition on that drive because Grub counts from 0.  When you type in setup (hd0) it should detect the presence of the grub boot loader files on the partition you specified.

For a further example see here under Command line section
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

