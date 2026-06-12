---
title: "how to remove ubuntu on multi-boot system?"
date: 2017-06-16
forum: New to Ubuntu
---

### Post by gil80 on 2017-06-16
hi all.
so after a bad experience with Ubuntu on my Alienware laptop, I would like to remove it completely.
however, I installed side by side with Windows 10.
When my laptop boots, I get this boot menu options to select the OS to load.

I reckon that using partition magic to remove Ubuntu will screw up the boot image, since the multi-boot menu is controlled by Ubuntu.

How can I safely remove ubuntu, claim the SSD space back for Windows partition and remove the multi boot menu, as if I never installed ubuntu?

---

### Post by oldfred on 2017-06-16
UEFI or BIOS?
If Windows 10, they you should be able to directly boot Windows from UEFI boot menu, often f10 or f12. And in UEFI you should be able to set Windows as default.

Once Windows is set as default in UEFI, you can remove Linux partitions, but Windows has a lot of partitions of its own, be careful not to remove those.
And you can remove UEFI entry for Ubuntu and the /EFI/ubuntu folder in the ESP - efi system partitions.
Details on doing those tasks are in link in my signature using Linux, but no idea how to do from Windows. Windows normally does not show ESP, you have to manually mount it.

---

### Post by gil80 on 2017-06-17
It's BIOS, not UEFI.

---

### Post by Geoffrey_Arndt on 2017-06-17
See here for step by step:

[http://www.everydaylinuxuser.com/2016/06/how-to-remove-ubuntu-from-dual-boot.html](http://www.everydaylinuxuser.com/2016/06/how-to-remove-ubuntu-from-dual-boot.html)

---

### Post by gil80 on 2017-06-17
> **Geoffrey_Arndt said:**
> See here for step by step:

[http://www.everydaylinuxuser.com/2016/06/how-to-remove-ubuntu-from-dual-boot.html](http://www.everydaylinuxuser.com/2016/06/how-to-remove-ubuntu-from-dual-boot.html)

Thank you very much! such a simple guide!

---

