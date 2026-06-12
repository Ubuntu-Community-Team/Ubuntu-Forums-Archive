---
title: "Windows 7 BSOD after Ubuntu 14.04 Installation"
date: 2015-09-05
forum: New to Ubuntu
---

### Post by Pass._TECH on 2015-09-05
I'm totally new to Ubuntu and was really interested in it. I followed the tutorial on how to install it in dualboot with Windows 7 carefully on the official website, and gave it a try.

Ubuntu 14.04 is booting fine with GRUB, but after trying to boot on Windows 7, I got a BSOD. Repair tools did nothing so I searched on the internet.

I've found this thing called Boot Repair, but instead of giving more choices in GRUB (which didn't help at all), nothing changed. I got the ubuntu paste from Boot Repair here : [http://paste.ubuntu.com/12279582/](http://paste.ubuntu.com/12279582/)

If you could help, I'd be really happy ! I must miss something really stupid but as I said, it's the first time I installed Ubuntu in my life.

Note : I haven't made any restore point from my Win 7, and I can't figure out how to get this Windows Repair Kit CD (I know, I'm stupid)

---

### Post by yancek on 2015-09-05
Your computer has UEFI boot files, an EFI partition on sda2 with the boot files for both Ubuntu and windows and bootloader in the MBR for that device.  That's correct.  For some reason you also have Ubuntu EFI files on sda7 which isn't correct.  What's on the 2TB drive, is that another windows install or just data?  If it is windows, can you boot that?  Since you have the boot repair output, I would suggest waiting for someone else who has more knowledge of UEFI booting.  I don't know what you would do to repair these problems.

I also notice you 4 windows recovery environment partitions which is a bit odd.

---

