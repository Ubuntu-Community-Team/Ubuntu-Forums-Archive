---
title: "dual-boot Ubuntu with Windows 10"
date: 2016-09-03
forum: New to Ubuntu
---

### Post by enoorani on 2016-09-03
[FONT=trebuchet ms]I need to dual-boot Ubuntu with Windows 10. When dual-booting with Windows10, the Windows always took priority (it doesn't give me the option to chose the operating system) I used repair-boot and it says the issues have been resolved but i still have the same issue. I would appreciate if somebody could help me out![/FONT]

---

### Post by yancek on 2016-09-03
Boot repair has an option to Create BootInfo Summary.  Run it again and select that option and post a link to the output here.  That will show enough information so that someone might be able to help.  Also, take a look at the Ubuntu documentaion for dual-booting with windows 10 at the link below and compare what the page says to what you did.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mook765 on 2016-09-03
Information about the hardware you use will be very helpful too.

---

### Post by RobGoss on 2016-09-03
Is your machine UEFI and Legacy?

When dual booting with Windows you need to install Ubuntu in the same mode as Windows, if Windows is installed in UEFI then install Ubuntu the same way, If Windows is installed in Legacy then install Windows the same way

This might help you with your installation
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by enoorani on 2016-09-04
I've already had it written down!
Boot-Repair URL:
[http://paste2.org/ubxelvv7](http://paste2.org/ubxelvv7)

and my machine is an hp-envy laptop
Thanks!

---

### Post by coffeecat on 2016-09-04
> **enoorani said:**
> I've already had it written down!
Boot-Repair URL:
[http://paste2.org/ubxelvv7](http://paste2.org/ubxelvv7)

You might want to check that URL. This is what I get:

> 
Page Not Found

The requested URL /ubxelvv7 was not found on this server. The link you followed is probably outdated.

The paste you requested may have been removed at the request of it's creator, been deleted in garbage collection or never existed in the first place.

Please feel free to browse around from our home page


[Boot Repair](https://help.ubuntu.com/community/Boot-Repair) has an option to upload the boot info report to a pastebin at ubuntu.com. There is no need to use a third-party pastebin.

---

### Post by enoorani on 2016-09-04
[SIZE=2][FONT=arial]Thats what I get when I run the Boot-Repair commands:[/FONT][/SIZE]

[B][FONT=trebuchet ms]Boot successfully repaired.

Please write on a paper the following URL:
[http://paste2.org/Fd6HHneF](http://paste2.org/Fd6HHneF)


In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.


The boot files of [The OS now in use - Ubuntu 16.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi[/FONT][/B]

Thanks!

---

