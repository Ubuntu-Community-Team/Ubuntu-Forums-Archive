---
title: "Cannot boot from bootable media"
date: 2017-05-14
forum: New to Ubuntu
---

### Post by goonybird on 2017-05-14
Hello

I have a Windows 10 machine dual-booted with Ubuntu 16.04. 

Windows won't let me log in to my account and after trying lots of  suggestions and failing to solve the issue, I decided to start over and  re-install everything.

The problem I now have is that the machine won't boot from any bootable  disc. When I insert the disc and switch on the machine it fails to read  the disc and goes straight to the Grub boot options menu.

BIOS boot order is set to; 1.Optical drive - 2.HDD.

The boot discs are OK and work on other machines.

Any ideas why this is happening?

Any help will be greatly appreciated.

---

### Post by yancek on 2017-05-14
Does this happen with both the windows and Ubuntu disks?
What hardware are you using, specific manufacturer and model of the computer might help someone familiar with it to help you.
Were you using UEFI?

---

### Post by goonybird on 2017-05-16
Thanks for your reply.

Yep. _Any_ bootable disk.

Toshiba Satellite C70D. Purchased a couple of months or so before Windows 10 released. Came with Windows 8, upgraded to 10 then set up dual boot.

Not entirely clear on this UEFI business. Doesn't Windows automatically use that now? And isn't that amended by Grub when Ubuntu is set up?

---

### Post by oldfred on 2017-05-16
UEFI is not automatic.
How you boot install media for both Windows & Ubuntu is then how it installs.
UEFI boot menu should give two boot entries if UEFI Secure Boot is off. CSM/BIOS/Legacy is not considered secure boot, but you can install in UEFI mode with Secure Boot off.

Other Toshiba have needed a work around to boot Ubuntu once installed. But they seem to install ok.

If drive is gpt partitioned which it would be with Windows 8 pre-installed, then Windows will only install in UEFI mode. If you boot Windows install media in BIOS/CSM/Legacy mode it will install as BIOS requires MBR(msdos) partitioning.

 Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

---

### Post by goonybird on 2017-06-04
Sorry to take so long to reply - we have moved.

Thanks for the clarification oldfred.

Looks like UEFI then.

---

### Post by goonybird on 2017-06-28
Latest update: still grappling with this issue.

---

### Post by johndough2 on 2017-06-29
Hi

On my laptop the bios has 2 different states of booting and then a list of bootable items.

EG:  Secure Boot and Legacy Boot; then a list in both of the boot order.

As suggested above it is probably the option/need to select the appropriate one.

---

### Post by goonybird on 2017-10-29
Hi folks

Thanks for all your thoughts, all greatly appreciated though nothing seemed to work.

Just to lay this to rest, I have finally managed to resolve it. 

After a thorough back-up of files, I managed to do a factory re-set from within Windows. This took me back to Windows 8 and from there an upgrade to Windows 10. I am now in the process of setting up the dual-boot again.

Many thanks for offering your suggestions. 
I also understand the boot process a bit better as a result. :D

Thanks

---

