---
title: "Win8 boots directly with Ubuntu boot drive present (BIOS, not UEFI)"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by friedrich.fs.sachs on 2013-12-07
Hi,

I have a a strange problem with trying to boot into Ubuntu with a live USB drive.

I am running Win8 (8.1), and after I boot, with the drive created by UUI, I boot straight into Win8 despite external drives being prioritized in my BIOS settings.

This is an 'old' computer from 2008, so theres no UEFI/secure boot issue here, which unfortunately is the only issue I get when I google the problem. The system has indeed booted fine from USB to Ubuntu on Win7 about a year ago. 

Can Windows really interfere with the early boot process? I am using the same BIOS and computer, just another USB drive.

Any help is greatly appreciated.

Thanks :)

---

### Post by oldfred on 2013-12-07
Best to see details.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If grub is correctly installed in external drive and you set BIOS to boot from external I do not see how Windows could interfere.

---

