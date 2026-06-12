---
title: "Ubuntu 22.04 won't boot after install"
date: 2024-07-17
forum: New to Ubuntu
---

### Post by baubetrieb on 2024-07-17
Hello everyone,

this is a post about my first experience with Ubuntu, so please be gentle if I don't give all the detail right away.

Last week I set up a bootable USB with Ubuntu 22.04 to install it on a completely formatted HDD disk. When turning on the PC with my boot medium inside I chose 'try or install ubuntu' and let the installer guide me through the process. After completing the installation I hit 'restart' and Ubuntu prompted me to remove the USB and hit Enter. So I did that and when my PC restarted it didn't boot Ubuntu but rather landed on the boot menu again. I tried selecting the HDD as the boot medium but after a short while it just returned to the boot menu.

Of course I searched the internet for my problem and found people with similar issues so i tried their solutions, but none of it worked. Also, I am afraid to have made everything worse in the process, while using gparted and the boot-repair as a first-time user.

I gave up trying myself and just pasted the boot-repair log to the following link to ask you for support: [https://paste.ubuntu.com/p/thxyYPYN3f/](https://paste.ubuntu.com/p/thxyYPYN3f/)

Any help will be greatly appreciated. If you have any questions or need me to provide something more, feel free to contact me :)

Kind regards

---

### Post by Rubi1200 on 2024-07-17
Welcome to the forums :-)

How old is the computer? You seem to have legacy BIOS, so prior to 2012.

Are you intending to only have Ubuntu installed?

Post the computer make/model with some specifications such as memory, graphics cards, hard-drive size.

Do you remember what you did with GParted?

---

### Post by yancek on 2024-07-17
The boot repair page suggests that if you are not familiar with bootloaders, you first use the boot repair script with the Create BootInfo Summary option and post the link here or at another forum for help.  This is a better choice, rather than going online and trying various solutions, especially if you do not make note of what 'solutions' you tried so you can post them when you need help so if you need help in the future, use boot repair in that way.

The boot repair output you posted shows you have a GPT drive on which it is normally recommended that an EFI install be done but you did not do that.  You selected to install in Legacy/CSM mode so do you have Legacy/CSM boot on in your BIOS firmware.  You have several drives, is the sda drive where you have Ubuntu set to first boot priority?  You have a BIOS_boot partition for the core.img file which is needed to boot in this manner on a GPT drive so it should boot if the settings are correct.

Since the new install of Ubuntu appears to be all you have, I would suggest that you reinstall and this time select to boot and install in UEFI mode if you have that option which you should unless the hardware is more than 12 years old.

---

### Post by baubetrieb on 2024-07-18
Hey, sorry for coming back to you so late.

The boot menu says *ASUS UEFI BIOS Utility* and the BIOS version is listed as 0806 x64 and Build Date as 01/20/2014. Since it's a computer I got for free from someone in my dorm, I don't have exact info on how old it might be.

I plan to only run Ubuntu. 

The tower has no logo or anything, so I can't really know the exact model.

It has

CPU:   Intel Core i5-4570 @ 3.2 GHz
GPU:   Some *Palit *Graphics Card I can't seem to find the model of, but I plan on removing it anyways
RAM:   24 GB (DDR3) @ 1.6 GHz
HDD:   2 TB        (WDC WD20EFRX-68EUZN0)
SSD:   250 GB    (Samsung Evo 840)


In GParted I deleted all partitions on both internal drives and then followed a guide to define a new boot/grub partition (if I'm scrambling something up, I apologize in advance) .I then restarted the PC and also booted from the external drive again, but ran into the same problem as before.

I hope this helps and thank you kindly for your time!

---

### Post by baubetrieb on 2024-07-18
> **yancek said:**
> The boot repair page suggests that if you are not familiar with bootloaders, you first use the boot repair script with the Create BootInfo Summary option and post the link here or at another forum for help.  This is a better choice, rather than going online and trying various solutions, especially if you do not make note of what 'solutions' you tried so you can post them when you need help so if you need help in the future, use boot repair in that way.

Thanks for the hint, I saw it too late and wasn't too careful with the PC because it's old and someone would have just thrown it away.

> **yancek said:**
> The boot repair output you posted shows you have a GPT drive on which it is normally recommended that an EFI install be done but you did not do that.  You selected to install in Legacy/CSM mode so do you have Legacy/CSM boot on in your BIOS firmware.  You have several drives, is the sda drive where you have Ubuntu set to first boot priority?  You have a BIOS_boot partition for the core.img file which is needed to boot in this manner on a GPT drive so it should boot if the settings are correct.

This is a great tip, thank you. I didn't really choose anything since I am not familiar with boot processes.

> **yancek said:**
> Since the new install of Ubuntu appears to be all you have, I would suggest that you reinstall and this time select to boot and install in UEFI mode if you have that option which you should unless the hardware is more than 12 years old.

I found an option which looked promising: Under *Boot->Secure Boot->OS Type *I can choose between *Windows UEFI mode* or *Other OS*. Is this the right setting?  For my previous tries it seems that *Other OS *was selected.

Thank you so much for your replies :)

---

### Post by ajgreeny on 2024-07-18
Disable secure boot!
It is not necessary and may be just complicating things for you and for the installation.

When you press the power button from a cold start there should be a keypress which allows you to choose the device from which to boot; on my machines that always shows two instances of the USB, one for UEFI and another without UEFI.

The manner in which you boot the USB will be the manner in which the OS is installed so assuming you get to that point choose the UEFI option then  for ease of installation allow the installer to use the whole disk.
From there it should do it all for you then tell you it has finished.

I have no  idea about that Windows UEFI mode as UEFI has nothing to do with Windows itself but is the hardware's firmware, used before the OS is installed.

---

### Post by yancek on 2024-07-18
I'm not familiar with Asus computers but if you tried the Other OS option before, you might try the Windows UEFI mode though I don't know why it would say windows.  On my laptop (HP) I use the F10 key to access the BIOS and the F9 key for one time boot options to for example, select to boot from a USB or external drive.  I expect the keys for your Asus will be different.  If you have that option and the computer is from 2014 it should certainly be UEFI capable.  I would think the current install would boot if you could set the drive on which you have Ubuntu to first boot priority in the BIOS firmware.

Additionally, since you have done a Legacy install of Ubuntu, there would have to be an option to set that on in the BIOS.  I'd just suggest you look for boot options when you access the BIOS and set the Ubuntu drive first.  That would be the 2TB drive.

---

### Post by baubetrieb on 2024-07-22
Hey all!

Thanks for helping me. After disabling secure boot I could select Ubuntu on my 2TB drive as the boot option and all worked out fine.

Have a nice week!

---

