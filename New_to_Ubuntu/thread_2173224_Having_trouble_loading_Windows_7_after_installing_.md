---
title: "Having trouble loading Windows 7 after installing Ubuntu"
date: 2013-09-08
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-09-08
I have three hard drives hooked up to my PC right now.  I had Windows 7 installed on one of the harddrives and I had data one of the hard drives.  Then I unhooked both of those harddrives and installed Ubuntu 12.04 on on the third harddrive.  I pluged in the other two harddrives, and when I select the harddrive that has Windows 7 on it, I get Ubuntu.

How can I boot Windows 7?

---

### Post by ImTroyMiller on 2013-09-08
Looks like updating Grub did it.

---

### Post by ImTroyMiller on 2013-09-08
Uh oh, now it won't load Unbuntu regardless of which drive I boot from via BIOS.

---

### Post by oldfred on 2013-09-08
Do not run auto repair. It just installs grub to every MBR so you boot grub no matter what drive BIOS is set to boot from. Better to have Windows boot loader in Windows drive. You can uncheck auto and check update MBR and in advance choose which system goes into which MBR.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

