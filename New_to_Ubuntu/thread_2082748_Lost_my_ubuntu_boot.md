---
title: "Lost my ubuntu boot"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by SupermanNC21 on 2012-11-10
I bought window 8 and tried to install it on my windows 7 partition, but my cpu doesn't support PAE/NX so i couldn't install it and now i lost my whole Ubuntu boot mode it boot now only for my windows 7 partition.

---

### Post by oldfred on 2012-11-10
If your Ubuntu install is ok, you just need to reinstall grub2's boot loader to the MBR.


[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

