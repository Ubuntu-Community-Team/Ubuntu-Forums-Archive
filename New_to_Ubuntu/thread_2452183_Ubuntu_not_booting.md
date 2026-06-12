---
title: "Ubuntu not booting"
date: 2020-10-18
forum: New to Ubuntu
---

### Post by patoramos on 2020-10-18
erase Windows and now Ubuntu does not boot.
I guess the problem is in the grub

I attached the grub.cgf

---

### Post by yancek on 2020-10-18
Which version of windows was installed on the computer?
Your post is a bit cryptic, more information will be needed before you can get help.  The best way to get that information is to boot the Ubuntu install media and if you can get online, go to the site at the link below and get the boot repair software.  Use the 2nd option described on that page to use the ppa and download and install it.  When you run boot repair according to the instructions on the page, select to Create BootInfo Summary and do NOT try to make any repairs.  When boot repair finishes, it will give you a link which you should post here for help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ActionParsnip on 2020-10-18
Boot to the Ubuntu install media and on the live CD desktop you can chroot to the installed OS and reinstate GRUB

---

### Post by grahammechanical on 2020-10-18
Do you get a Grub boot menu? Was Ubuntu installed on the same hard disc as Windows? You may need to enter the UEFI settings utility and set it to point to the Grub boot loader in the EFI boot partition. How did you erase Windows? If you have erased the EFI boot partition then the computer does not have a bootloader to run.

This is why we say that you need to give us more information.

>     set root='hd0,msdos2'

That means Grub is looking to the first hard disc and the second partition to find Linux/Ubuntu


Regards

---

