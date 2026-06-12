---
title: "grub problem"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by Brianret on 2013-01-24
I have installed ubuntu 12.10 and later partitioned my hard drive and installed windows 7 which from reading posts I now know that this is the wrong way! I have consequently lost my boot file and my pc will only boot into windows.
The boot file must still be there in Ubuntu, how can I restore it so that I have a choice to boot either win 7 or ubuntu?

---

### Post by oldfred on 2013-01-24
Super grub is good for booting into your system but just a sudo update-grub will not install it to MBR.

From your install once booted, run this.

       sudo grub-install /dev/sda
    
       [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

