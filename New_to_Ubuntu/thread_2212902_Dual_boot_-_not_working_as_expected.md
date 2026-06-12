---
title: "Dual boot - not working as expected"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by p4ra on 2014-03-23
Hello everyone,

I am fighting with dual-boot setup all day long and I am exhausted, that's why I am here.

What I am trying to achieve is the following:

1. setup Windows 7 Professional on 1st HDD SSD - done
2. setup Ubuntu 12.04 on 2nd HDD (classic SATA 250 GB HDD) - done
3. load automatically Windows boot loader instead of GRUB - cannot get this to work

I have followed exactly this tutorial:

[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

Step by step and still, it does not seem to work for me.

Please, any ideas?

Thank you.

---

### Post by oldfred on 2014-03-23
Is your system UEFI or BIOS? And did you install both in same boot mode?

Best to see details:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by p4ra on 2014-03-24
oldfred, I figured it out. I installed all over again Windows, then Ubuntu. Then booted into the Windows, used EasyBCD and instead of GRUB, I am using Windows Boot Loader.

---

