---
title: "New User Boot Firmware Bug"
date: 2018-10-05
forum: New to Ubuntu
---

### Post by jguizar5 on 2018-10-05
Im new to Ubuntu i was trying to install it on a second drive on my laptop since so I can use it but after it finished installing and i restart my computer after selecting ubuntu from the boot screen i get this:
[IMG]http://i67.tinypic.com/2vl2mq8.jpg[/IMG]
I have done some research on it and cant really find a fix for it.

---

### Post by oldfred on 2018-10-05
What brand/model system?
What video card/chip?

I get several ACPI errors and they are just ignored.

Have you updated UEFI to latest version from vendor for your model system?

---

### Post by jguizar5 on 2018-10-06
> **oldfred said:**
> What brand/model system?
What video card/chip?

I get several ACPI errors and they are just ignored.

Have you updated UEFI to latest version from vendor for your model system?
I have a Dell i557 with a GTX1050 and yes i have made sure i have done all updates for it.

---

### Post by oldfred on 2018-10-06
Is that i5570 or i5577?
Are you using nomodeset. You need that to boot live installer & first boot after install or until you install the nVidia proprietary driver from Ubuntu's repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Dell needs drives changed from RAID or Intel SRT to AHCI. If dual booting with Windows you need to add the AHCI driver first into Windows.

       
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 
    
More general UEFI install instructions in link below in my signature. Best to review that.

Older thread, usually newer versions of Ubuntu include many fixes.
       Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

---

### Post by jguizar5 on 2018-10-06
its an i5577 which concerned me since after looking for the compatible ones mine isn't on the list. 
I planned on having this go smoothly since i needed ubuntu for a class project. 
From what i can tell i think I am better off completely removing it and starting over.
Thanks for your help i really appreciate it and will come back when i start again.

---

### Post by Yellow Pasque on 2018-10-06
The ACPI error can be ignored. It would be nice if Dell would fix their BIOS/EFI to make it go away, but don't hold your breath.
If it really bothers you, you can try disabling TPM (Trusted Platform Module) in your EFI if you have the option, or try blacklisting tpm_crb.

Reference: [https://patchwork.kernel.org/patch/9585671/](https://patchwork.kernel.org/patch/9585671/)

---

