---
title: "blank screen while booting"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by santispor on 2008-06-10
Hi all, 

  I have been trying to configure a kernel souce tree for my project. I have ubuntu 2.6.15.51-386 (draper drake) kernel installed and running. For my project, I downloaded the source files for the kernel 2.6.24.2 from kernel.org, configured and compiled. I also updated the /boot/grub/menu.lst for the new kernel. When I restarted the system and selected the new kernel option, It started booting, but went blank (greenish screen). I waited for 5- 10 min and then tried Ctrl+Alt+F1. It gave me a black screen with cursor blinking (no command prompt). I then had to switch down and restart ubuntu. Ubuntu is working fine. Below is the menu.lst entry for the new kernel.
---------------------------------------------
title    Linux, kernel 2.6.24.2y
root     (hd0, 2)
kernel   /boot/vmlinuz-2.6.24.2y root=/dev/sda3 ro quiet splash
initrd   /boot/initrd.img-2.6.24.2y
savedefault
boot
-------------------------------------------
I am new to kernel programming. I do not know how to proceed from here.  Please can anybody help me. 
I am using sony vaio FJ series laptop with intel centrino processor(1.86Ghz, 1 GB RAM).
Thanks in advance

---

### Post by cprofitt on 2008-06-10
Try removing quiet and splash from your kernel line. I had to do that in old kernels or I would get the symptoms you are describing.

---

