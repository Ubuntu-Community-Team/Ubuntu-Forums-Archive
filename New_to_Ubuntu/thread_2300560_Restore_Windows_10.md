---
title: "Restore Windows 10"
date: 2015-10-26
forum: New to Ubuntu
---

### Post by Charlie_Lin on 2015-10-26
I am new to this forum and quite frankly Linux distributions in general. I booted Ubuntu 15.10 from the live CD and decided to install it to the hard drive. Unfortunately I decided to let the installer carve out half of my Windows 10 partition and use it as the Ubuntu one. What I should have done, reading other posts, is to manually partition it before installing the distro on it. Anyway after it finished installing and rebooting I was presented with the GRUB bootloader. It presented me to boot either Ubuntu or the Windows boot manager (on sda2/dev). When I tried to boot into Windows 10 I was presented with the "Inaccessible Boot Device" BSOD. I can boot into Ubuntu just fine.

 In Ubuntu I downloaded Boot Repair via the terminal (a laborious one). I selected default settings and let the application do the "repairing". However, when I booted into GRUB, I t presented with even more options related to Windows, and none of them booted in Windows 10. Would someone please tell me how to restore access to Windows 10!?!?

 Here is my boot log.[http://paste.ubuntu.com/12943097](http://paste.ubuntu.com/12943097)

---

### Post by yancek on 2015-10-26
Your boot repair shows an EFI partition and the proper files for both windows and Ubuntu and the grub.cfg file (the menu you see on boot) has a proper entry for windows.  I did notice a number of messages "  The NTFS partition is in an unsafe state" and "NTFS signature is missing".  The first is because you left windows 10 hibernated when you installed and booting into Ubuntu or any Linux, it will not mount a partition that is hibernated.  Not sure what effect that has on booting but if you are getting the message " Inaccessible Boot Device" BSOD" after selecting windows from the menu, I don't think there is much to be done from Ubuntu as at that point you are on the windows system.  I don't use UEFI so just have a general knowledge so you might try googling that message you got while you wait for someone with more expertise in this area.

---

### Post by leunam12 on 2015-10-29
Did you try booting from the Windows10 installation media and doing the repairs from there?

---

### Post by Charlie_Lin on 2015-10-31
Pre-installed OEM Windows 10 computer, so no idea how to create a OEM recovery disk from the recovery partition (OEM partition). So no.

---

### Post by coffeecat on 2015-10-31
Generally speaking - or at least with the machines I've had experience with - you can't create an OEM recovery disk from the recovery partition. That has to be done from the manufacturer's utility in Windows, that is while running Windows. Which, of course, is not possible now. However, any half-decent OEM will provide a way of booting into the recovery partition from which - so long as the OEM has done a proper job - you should be able to run various Windows repair utilities apart from the nuclear option of restoring back to factory condition.

Usually, booting into the recovery partition is effected by pressing one of the F keys shortly after booting up. The actual key varies from manufacturer to manufacturer and sometimes between different models. The manual should be able to tell you - except that it's probably on a pdf file somewhere in your damaged Windows C: partition. But it should also be on the net somewhere. You could search for your make and model. It might be helpful to post those details too as someone here might have knowledge of your particular machine.

---

### Post by yancek on 2015-10-31
Most manufacturers who sell pre-installed windows systems will offer you a full installation disk at an extra cost of course.  If this is a new computer, you may still be able to do that?
As far as the recovery disk, my experience is that when you first boot windows you are prompted to create a recovery disk.  You can also do it at any later time but of course, that requires being able to boot windows which you can't.  When you finally do get it booted, I would suggest you do that.  You might have better luck trying a windows forum.

---

### Post by DK1993 on 2015-11-01
The best advice in this situation if you cannot access that recovery partition is to try to use the recovery tools that are available on the Windows 10 Installation ISO. You can legally obtain it for making a bootable usb at Microsoft's website: [https://www.microsoft.com/en-us/software-download/windows10ISO/](https://www.microsoft.com/en-us/software-download/windows10ISO/)

The only caveat to this is that you would potentially in turn lose any information/data that is stored on that partition and also you run the risk of destroying your Ubuntu installation as well. As far as a product key for this, it is not necessary as this is located in the motherboard (as long as said motherboard is UEFI compliant).

---

### Post by Charlie_Lin on 2015-11-07
New info: my computer upgraded to Windows 10 via the Media Creation Tool from Windows 8.1, which was a preinstalled one

---

### Post by oldfred on 2015-11-07
You should be able to directly boot Windows from the UEFI boot tab or perhaps the one time boot key often f10 or f12, check your manual.

Should be essentially the same for Windows 10. Not sure how they have moved things around.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Mark Phelps on 2015-11-07
> **Charlie_Lin said:**
> New info: my computer upgraded to Windows 10 via the Media Creation Tool from Windows 8.1, which was a preinstalled one

OK ... so which OS version came preinstalled on the PC -- Win8x or Win10?

---

### Post by Frogs Hair on 2015-11-07
If the recovery option from the hard-drive is used it restores the original operating system and not Win 10. It is possible to upgrade and perform a clean installation if you have your OEM activation code and I used the linked script. I suggest upgrade and activation first only because it logs the device on MS severs. There have been activation problems reported as a result of a clean installation first. 

[http://www.howtogeek.com/206329/how-to-find-your-lost-windows-or-office-product-keys/](http://www.howtogeek.com/206329/how-to-find-your-lost-windows-or-office-product-keys/)

---

