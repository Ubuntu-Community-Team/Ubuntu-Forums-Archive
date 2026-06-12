---
title: "Thinkpad x120e not booting with Ubuntu 12.10"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by sertua on 2013-03-15
Greetings,

I installed Ubuntu 12.10 on a Thinkpad x120e that was running Windows 7. All I get is "Operating System not found" when I boot.

I started to look for solutions here:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)
[http://ubuntuforums.org/showthread.php?t=1699238](http://ubuntuforums.org/showthread.php?t=1699238)

And then did some googling and tried many fixes for many hours. I haven't found a solution yet.

My last operation consisted of erasing my hard drive completely and re-installing Ubuntu 12.10. I then ran boot-repair. The log is here: [http://paste.ubuntu.com/5616505/](http://paste.ubuntu.com/5616505/)

I'm not a newbie to Ubuntu, I'm a regular user, but I don't have much technical knowledge of Linux.

I appreciate your help.

---

### Post by sandyd on 2013-03-15
**moved to absolute beginners section**

---

### Post by kurt18947 on 2013-03-15
I assume you're try to boot from a live USB?  I see that message every time I try to boot from a USB that was not formatted with Windows on one desktop machine.  That machine is running a Gigabyte board & AMD Athlon II processor.  A USB prepared with Gparted and Unetbootin will boot fine off a Thinkpad or older Gigabyte/AMD machine but not the machine with the Gigabyte/AMD785 chipset, I get the "Operating system not found" or "Boot Error" message.  A DVD will boot fine.   If I Format in Windows - a quick format is fine - then create the live USB with Unetbootin, it boots fine.  If you have or can get someone with Windows to do a quick format on your flash drive, it might be worth a try.  I've tried to find the difference between a live USB on a windows formatted flash drive and one that was not formatted with Windows.  I can't find anything obvious but there's *something* different.

---

### Post by sertua on 2013-03-15
Thank you Kurt for trying to help.

12.10 is on my hard drive.

Maybe I should point out that I have already successfully installed and configured dozens of Linux distros on many different PCs over the past four years.

---

### Post by sertua on 2013-03-17
Can anyone help?

Thanks in advance.

---

### Post by kurt18947 on 2013-03-17
I've never used this but Hirens boot CD is pretty regarded, I think.  This is for a USB drive.

[http://www.hiren.info/pages/bootcd-on-usb-disk](http://www.hiren.info/pages/bootcd-on-usb-disk)

---

### Post by sertua on 2013-03-17
Thanks Kurt.

I can boot on a usb drive with Ubuntu or any other distro, but the problem is with the one I install on my hard drive. I think this has to do with secure boot / UEFI but despite my extensive research and many attempts, I can't get Ubuntu to boot from the hard drive.

---

### Post by kurt18947 on 2013-03-17
> **sertua said:**
> Thanks Kurt.

I can boot on a usb drive with Ubuntu or any other distro, but the problem is with the one I install on my hard drive. I think this has to do with secure boot / UEFI but despite my extensive research and many attempts, I can't get Ubuntu to boot from the hard drive.

I think (never used it) that Hiren's boot USB is intended to fix problems with hard drive booting.  It's just installed on a USB drive instead of a CD.  Does the X120e have UEFI/secure boot?  I thought those technologies came to the fore after the X120e was released.  I hope you're able to solve your problem.  I use a 3rd party boot manager so have virtually no experience with with GRUB.

---

### Post by sertua on 2013-03-17
> **kurt18947 said:**
> Does the X120e have UEFI/secure boot?  I thought those technologies came to the fore after the X120e was released.  I hope you're able to solve your problem.  I use a 3rd party boot manager so have virtually no experience with with GRUB.

Yes it does. Sadly.

---

### Post by oldfred on 2013-03-17
If it was running Windows 7, it cannot have secure boot as only Windows 8 supported secure boot. Some Windows 7 systems used UEFI to boot, but most newer Windows 7 systems even with UEFI/BIOS used the BIOS mode to boot.

Best to see details. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by sertua on 2013-03-18
Hi Oldfred,

Boot-info is here: [http://paste.ubuntu.com/5616505/](http://paste.ubuntu.com/5616505/)

Thanks for your input.

---

### Post by oldfred on 2013-03-19
You are booting with UEFI.
Your efi partition still has Windows boot files, but you only have Ubuntu installed. So from UEFI menu the only UEFI entry that should work is ubuntu.

But Boot-Repair also converted it to a secure boot type which renames the Windows files. If your system was Windows 7 you should not need that. Do not know if that makes any difference with a system that does not have to have it?
You can remove the secure boot renaming by unchecking the secure boot option in Boot-Repair and rerunning it.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

to undo just do the opposite of this:

 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

---

