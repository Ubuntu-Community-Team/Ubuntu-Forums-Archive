---
title: "Issues getting Ubuntu 12.04 LTS to dual boot with Windows 8"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by john16 on 2013-08-01
So I partitioned my hard drive, allocating 15 GB. Burned the package onto a CD and loaded the OS. 

I partiontioned the free space with a swap section of 1.5 GB..

Everything installed fine and then system had to restart in order for the installation to take full effect. 

Here's the problem: I can't get to Ubuntu without changing the boot priority to SATA CD (as with the initial installation) and cancelling the installation once everything loads. This manner, understandably resest all changes that I've made within the Ubuntu scheme. 

So here's what I need help on... I need to find a way so that I don't have to cancel the installation everytime I boot into Ubuntu. And accordingly, I need to find a way to effectively alter the boot configuration in order to dual boot smoothly.. I've also installed and tried to modifiy the boot order using easyBCD, with no success (trying GRUB and GRUB2).

---

### Post by oldfred on 2013-08-01
Is this a pre-installed Windows 8? And that is in UEFI mode. And did you then install Ubuntu in BIOS/CSM mode. To easily dual boot, both systems must be in same mode, so you need Ubuntu in UEFI mode.
Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Lots of detail info in link in my signature on UEFI.

---

### Post by stuart_hall2 on 2013-08-01
had same trouble with my lenovo that had win8x64 never did get it to operate right.

---

### Post by john16 on 2013-08-01
Yeah, it's a pre-installed Windows 8. I'm downloading Boot-Repair now...

---

