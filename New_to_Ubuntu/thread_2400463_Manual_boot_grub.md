---
title: "Manual boot grub"
date: 2018-09-06
forum: New to Ubuntu
---

### Post by Phil Binner on 2018-09-06
While loading Ubuntu 18.4.1 from a USB stick I got a message "Executing 'grub-install/dev/sda' failed.  This is a fatal error"

I had the option to change the device to sda1, sdb or sdb1, but all of these failed also. I was forced to accept to continue without a boot file, and was instructed to create one manualy.

The installation then said it had completed, and to remove the install tion media and reboot, but doing this produced nothing.  To this stage the in stallation had taken less than 5 minutes, so I suspect it's only part way through.

This is cobbled together desktop on an old ASUS motherboard, but it was running Xubuntu happily untill I let it update, and then it still ran but it had taken away support for Cairo Dock and Kody.

So where do I go next, and how do I manuall install a boot grub file.

Thank you in anticipation

---

### Post by oldfred on 2018-09-06
Is drive newer gpt partitioned? If so you need a 1 or 2MB unformatted partition with bios_grub flag.

Otherwise:
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

