---
title: "multi boot ubuntu error screen"
date: 2020-08-31
forum: New to Ubuntu
---

### Post by cktang11 on 2020-08-31
I have setup a multi boot which have ubuntu and windows to select.

when select the ubuntu , it pops the error screen as attached , I guess it is because it is graphic screen , right ? 

it works to boot to windows , or it alow work to boot to ubuntu recovery mode .

I tried to change the resolution , but it only support resolution 3840 x 2160 .

Would advise how to fix the boot error screen ?

thanks

---

### Post by oldfred on 2020-08-31
From recovery mode,  you should be able to install video driver.

Do you have nVidia?
You then need nomodeset until you install nVidia driver.

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

