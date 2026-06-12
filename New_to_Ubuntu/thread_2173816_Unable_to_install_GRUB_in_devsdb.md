---
title: "Unable to install GRUB in dev/sdb"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by kier2 on 2013-09-11
I'm having trouble while installing Ubuntu (12.04 LTS) (overwriting win7). Afterwards, I encountered (similar to this one -> [http://askubuntu.com/questions/62051/unable-to-install-grub](http://askubuntu.com/questions/62051/unable-to-install-grub)):
```

'Unable to install GRUB in dev/sdb'
 Executing 'grub-install/dev/sdb'
 This is a fatal error!
```
 
 The installation finished and the PC was required to reboot.  Afterwards, I never got past the bios. Actually, just stuck to the bios.  I was unable to boot from any device (CDROM, HDD)
 
 I have also just tried using another hard drive just in case I have hardware issues.. but it's working smoothly. Although, I haven't tried installing Ubuntu on the hard drive I was referring to.
 
 P.S: I used a CD to install Ubuntu.

---

### Post by oldfred on 2013-09-11
Post link. If BIOS based system, if you do not want grub installed to the MBR of every drive, do not run auto repair. You can uncheck auto repair, check update MBR and in advanced choose which system to install a boot loader to which MBR.

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

### Post by kier2 on 2013-09-11
Hmm, I was not able to get past the BIOS screen. If I'm not able to fix the problem, I will try to install a win7 os first, then Ubuntu. Thanks, I'll respond tonight.

---

