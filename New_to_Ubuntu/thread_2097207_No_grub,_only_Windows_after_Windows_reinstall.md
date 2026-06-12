---
title: "No grub, only Windows after Windows reinstall"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by gakeraut on 2012-12-22
> **Bashing-om said:**
> Inphi; HI !

See if this will get you back up:
From a cold boot, when the grub menu appears, choose the "recovery mode" kernel to boot. In that next menu choose grub, See if that option repairs your grub.

[INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT]
hi there plz help me, 
i have a laptop dell vostro 1014, with triple boot xp & win 7 & ubuntu 12.04 LTS. 
i forgot my win 7 passwod, so i re-install a fresh copy of win 7. 
now the problem is my Ubuntu bootloader is gone & only xp+win 7 boot screen is appearing.
how can i overcome this problem,?? i want to use all 3 of my OS. specially ubuntu. 
plz help if you know.

thnx

---

### Post by oldfred on 2012-12-22
Moved to your own thread.
You were in this thread but it is not related to your issue.
[http://ubuntuforums.org/showthread.php?t=2097023](http://ubuntuforums.org/showthread.php?t=2097023)

       [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

    
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

