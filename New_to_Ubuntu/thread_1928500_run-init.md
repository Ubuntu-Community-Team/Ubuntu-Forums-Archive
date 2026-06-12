---
title: "run-init:"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by prateek vijaywargiya on 2012-02-20
Due to some problems in windows 7 i have reinstall. After that i am unable to access Ubuntu 11.10 so i have upgraded it using Ubuntu 11.10 and then after successfull upgradation bootloader comes up... bt when i select the Ubuntu 11.10  from grub loader then after that on the black screen this message comes up:

run-init: /sbin/init: Exec format error...

Please help me in resolving this problem...

---

### Post by Cheesehead on 2012-02-20
Grub loads the kernel and a minimal system into RAM, then uses that minimal system to create the main system (root, devices, /sys, etc).

This kind of error occurs when te minimal system tries to start the first real-system process (called 'init'), but fails becasue init is missing from the expected location. That often means a problem with your /boot/grub/grub.cfg or /etc/fstab. It may be pointing to the wrong disk or partition...or, depending upon how you upgraded, a partition that has been overwritten.

Seeing the rest of the error messages would be very helpful.

Either way, [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) has complete instructions on how to recover from the problem.

---

### Post by skestle on 2012-02-23
What other error messages? This is all that appears after grub selection.

I got this after I upgraded Ubuntu 11.10 32 to 64 bit (where the second hard drive boots)

---

