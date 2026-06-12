---
title: "Boot problems"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by eckhardk on 2012-09-13
I am encoungtering a weird problem: I have a dual-boot Ubuntu 11/Windows installation, after running fine for 8 months it crashed. Ubuntu refused to reboot. It also refused to boot or re-install from a memory stick (the one I had installed it from in the first place) and from a live CD. I installed a new hard disk and put both Ubuntu and Windows on it. On BOTH disks, and with or without the NVidia GeForce 570 video card I encounter the same problems:

Windows boots OK from both hard disks
Ubuntu boots from both hard disks only when I choose "recovery mode" and then
normal boot. But then networking is extremely slow.
Ubuntu does NOT boot directly from the grub menu, it hangs at the maroon screen.

I *think* it is a hardware problem, but the manufacturer of course blames it on
Ubuntu, so I need to narrow it down further. Has anybody had an experience like that ?

---

### Post by Bashing-om on 2012-09-13
eckhardk; Hi !

 Sounds to me like two issues.
1. Not booting from external sources: Is the boot priority set correctly in bios to boot the desired medium first ?

2. Booting: from the recovery mode of ubuntu run in terminal:
```
sudo update-grub
```  to regenerate the grub menu.

   See if this does not resolve the situation.
[INDENT]Kind regards <== BDQ
[/INDENT]

---

