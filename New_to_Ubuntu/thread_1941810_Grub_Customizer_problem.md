---
title: "Grub Customizer problem"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-16
Using Ubuntu Lucid - Installed KDE desktop.
When running KDE desktop, ran Grub Customizer & unticked the 2 older kernels. 

Closed Grub Customizer. Next day on booting to KDE desktop, was not able to open Grub Customizer - message appeared "No Bootloader Found". Closed Grub Customizer & rebooted into Lucid. Same situation occurred on opening Grub Customizer. Selected option to create recovery root mountpoint, which sits on the desktop. Am unable to remove or unmount it. Am at a loss as to how to get out of this mess, & would appreciate help.

---

### Post by grahammechanical on 2012-03-16
First of all

Grub customizer has not deleted those two kernels. It only removes them from  the Grub menu.

Second: If you are able to boot into Ubuntu (whatever version or user interface) then there must be a bootloader.

Do you have other operating systems on this machine? Have you done anything in another operating system that has removed the Grub bootloader from the MBR (Master Boot Record) of the hard disk?

The first thing that Grub customizer does on loading is to retrieve the Grub Configuration file.

Regards.

---

### Post by Bumpalot on 2012-03-16
Thanks for the reply: Problem #1 How can I remove the grub-customizer_recovery_root_mountpoint from the desktop?
Can't unmount it, or delete, even in Terminal. 
bump@bumpyputer:~$ gksu grub-customizer
 *** initializing (w/o specified bootloader type)&#8230;
   * reading partition info&#8230;
   * Loading Framebuffer resolutions (background process)
   * Finding out if this is a live CD
     [running on an installed system]
     [checking the burg-mkconfig command&#8230; ]
     [not found]
     [using custom Grub2 configuration]
     [checking the  command&#8230; ]
     [not found]
Screen Message:
No Bootloader found
Do you want to select another root partition?

Am hesitant to reboot in case it screws up. Will appreciate any  suggestions.
*******Have reposted this due to lack of adequate response

---

