---
title: "grub repair did not work. Now can't boot windows 8, just Linux"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by joselitux on 2014-07-30
Hi folks


After installation my grub is a complete mess. Now I've got 5 options. First two options for linux and the rest are various supposed windows 8 choices.

What can I do? I need desperately to log into windows 8

here my grub-repair info

[http://paste2.org/KpNeZj8N](http://paste2.org/KpNeZj8N)


Thanks in advance

---

### Post by yancek on 2014-07-30
Are you able to boot to Elementary?  What happens when you select any windows 8 option?  You have efi entries for both windows and Linux but you also show Grub on the mbr.  Did you select to install Elementary in efi mode?  I don't use efi or gpt partitioning, but I don't think that is correct.  I'm sure someone will come along who has more knowledge.

---

### Post by joselitux on 2014-07-30
hi yancek

yes, i'm able to boot to Elementary, but none of the Windows 8 options worked. "signature error" is shown.
i've installed Elementary as usual, booting from cd, not uefi mode.

regards

---

### Post by oldfred on 2014-07-30
New systems have both UEFI and BIOS boot modes. And in UEFI mode you can have secure boot on or off. Best to have it off.
And in Windows to dual boot you need to have fast boot or always on hibernation off.

It looks like you have grub installed to the gpt protective MBR to boot in BIOS mode. You do not show an efi entry in your fstab to mount the efi partition to correctly install in UEFI mode. Boot-Repair can convert install to UEFI or convert to UEFI with secure boot or the signed versions of grub & kernel. 

You should be able to from UEFI menu, select UEFI on or BIOS/CSM/Legacy off and boot Windows from that menu. Since Ubuntu is in BIOS mode it cannot boot Windows in UEFI mode. You can only dual boot from grub menu systems that are installed in the same boot mode.

Since Windows is in UEFI mode, you should alway boot in UEFI mode not BIOS mode. And how you boot installer is how it installs.

       Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)


 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

      
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

### Post by CJ_Hudson on 2014-07-30
Personally in this instance I would re-install Windows 8, assuming you have enough time, the installation disc and a valid code-key, then re install Ubuntu from a CD or DVD ROM (download and burn it on a helpful friend's computer if that was your only computer, unless you already have an appropriate copy,) then run Boot Repair ([http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)) from a CD ROM (burn to a CD ROM at the same time you burn Ubuntu,) to re instate the post POST boot menu choice. It might only take about a day or so.

---

### Post by oldfred on 2014-07-30
If you are booting Linux in BIOS mode then you do get errors as UEFI & BIOS are not compatible.
You have to boot from UEFI menu or one time boot key so you are getting a total reboot in correct mode.

Grub can only boot other systems installed in same boot mode. They also cannot be hibernated or needing chkdsk.

---

