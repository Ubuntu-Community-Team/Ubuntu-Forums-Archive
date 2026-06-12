---
title: "removing, changing GNU GRUB"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by bayon on 2013-03-08
Hello, i installed ubuntu 12.10 along with XP pro. I am planning to delete ubuntu. I want to remove the GNU GRUB or at least change the order of operating systems, so that the XP would be the first in list and would load automatically.  I do not have CD drive.  I came across some ways to remove the GRUB, but im not sure, if they will not damage my XP installation.  So, what you would suggest as the easiest way to solve the problem?  Thankyou.

---

### Post by jsabina1 on 2013-03-08
To change the default boot you should change this file:

[COLOR=#000000][FONT=Arial]/boot/grub/grub.cfg.

and on [/FONT][/COLOR][COLOR=#FF0000][FONT=Arial]GRUB_DEFAULT=0
put the number in which position is xp[/FONT][/COLOR]

---

### Post by oldfred on 2013-03-08
jsabina1's suggestion will work as long as you keep the Ubuntu partition. As grub in the MBR has to find the grub files including grub.cfg in the Ubuntu partition.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by bayon on 2013-03-09
to restore XP bootloader, i used XP Recovery Console [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)  I deleted ubuntu deleting the partition of ubuntu.  Thanks for help, everyone!

---

