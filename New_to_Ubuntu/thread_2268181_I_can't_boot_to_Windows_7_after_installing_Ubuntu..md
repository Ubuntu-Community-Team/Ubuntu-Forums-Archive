---
title: "I can't boot to Windows 7 after installing Ubuntu."
date: 2015-03-06
forum: New to Ubuntu
---

### Post by Boyke_Julianto on 2015-03-06
Hi,

I was installed Ubuntu 14.10 alongside my Windows 7. And everything was going well until I realized that after I was installed Ubuntu, I have some trouble on my Windows 7, such I can't use my external speaker when I played media player or streaming on YouTube, my internet connection become unstable, etc. So, I decided to uninstall Ubuntu, and I was using EasyBCD to do that. And the problem appear, I can't boot Windows anymore, it's always take me to Windows Boot Manager that shows boot problem because some files was missing. I try using Windows Installation CD to repair as said on boot menu, but it always take me to GRUB Menu. I have set boot to CD, but it doesn't work. So, what should I do to take my Windows back?

Thank you.

---

### Post by sotiris2 on 2015-03-06
Is the Windows Installation CD tested to be good? 

Also I think you need to press any key on a keyboard or it will skip booting and boot from the next boot option which is the hard drive with grub.

It's not technically possible for ubuntu/grub to prevent you from booting from cd since that is handled by bios. It's also quite unlikely that ubuntu caused the changes in windows.

---

### Post by yancek on 2015-03-06
> So, I decided to uninstall Ubuntu, and I was using EasyBCD to do that.

You can't uninstall Ubuntu with EasyBCD.  All you can do is remove the Ubuntu entry from the EasyBCD menu.  The steps to take in your situation, if you were using the Ubuntu Grub bootloader to boot both windows and Ubuntu is to first, use your windows CD/DVD to install its code to the master boot record.  Were you previously using the Ubuntu/Grub bootloader to boot both windows/Ubuntu or were you using EasyBCD.  Then you would reboot to verify it works, then go to Disk Management in windows and format the partition on which you had Ubuntu.  Ubuntu/Linux is an operating system, not an application so you can't "uninstall", you simply re-format the partition to use again.

If a windows boot file is missing then you somehow have overwritten it and you need to reinstall the windows bootloader.

Installing a second operating system on a computer on a second partition is not going to have any effect on your speakers.

---

### Post by Mark Phelps on 2015-03-06
If you were using Startup Repair from the Win7 DVD, you need to know that it rarely fixes the problems in one pass.  In nearly all cases, it takes three passes to repair the startup problems.  So, my suggestion is that you reboot from it again and run it three times.'

After that, you should be able to then boot directly into Win7.

---

