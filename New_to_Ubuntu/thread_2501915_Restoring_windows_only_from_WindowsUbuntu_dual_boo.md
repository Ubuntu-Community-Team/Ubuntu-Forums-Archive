---
title: "Restoring windows only from Windows/Ubuntu dual boot"
date: 2024-10-25
forum: New to Ubuntu
---

### Post by digitig on 2024-10-25
All my attempts to get Ubuntu working on an ancient HP Pavilion laptop have failed, so I want to get it back t o a standard Windows 10 installation so I can sell it and get a more modern laptop to try to install Ubuntu on.

I went through all the process of installing dual boot, and when I start the laptop the Grub loader gives me the expected options. The option to load Windows still works fine [1]. The option to load Ubuntu fails. I've also tried running Ubuntu from a USB Stick, but it hangs (for what it's worth, I've also tried a Mint Cinnamon USB stick, and that hangs too, and now I'm hungry after typing "mint cinnamon". This laptop clearly doesn't like Linux).

So now I need to restore the boot to just the standard Windows and reclaim the Ubuntu partition. Unfortunately, I'm clueless about Grub (except typing that makes me hungry again) and partitions. And the Microsoft help tells me to use MS tools to mount the recovery partition and run tools from there that aren't there.

So I'm turning to you for help. Honest, I'm not abandoning you! I only want to get rid of Ubuntu so I can sell the laptop it's on and install Ubuntu on my next laptop!

So - how do I make this laptop look as if it has never seen Ubuntu, let alone had a liaison with it?

[1] Eventually. Even when this laptop was new and I was using it for work, I would get in to the office, start the computer, go and have second breakfast, unsuccessfully chat up a rather attractive colleague [2], make a coffee, and return to my desk to wait for it to start.

[2] We're still in occasional touch. I've not met their current partner yet.

---

### Post by tea for one on 2024-10-26
_Option 1_
Contact HP and see if they have a suitable Windows 10 image for your "ancient HP Pavilion laptop

_Option 2_
Boot into Windows
Remove Ubuntu partition(s)
Remove Ubuntu folder from ESP
Reboot

_Option 3_
Erase disk and install Ubuntu
Sell it with only Ubuntu installed

_Option 4_
Wipe the disk completely and sell it without an OS

_Option 5_
Download and Windows 10 ISO
Make a bootable USB
Install Windows 10 (your existing product key may/may not work?)

_Option 6_
Download a Windows 10 ISO
Make a bootable USB
Choose the "Repair" option from the Install screen

_Option 7_
Peruse Windows 10 forums for other suggestions

---

### Post by yancek on 2024-10-26
Don't you have an option to reset to factory default in the BIOS?  It may not work if you chose to delete some of the windows partitions, the Recovery partition.

---

### Post by grahammechanical on 2024-10-27
Have you tried searching the internet for Microsoft tools to repair the Windows boot loader?

[https://answers.microsoft.com/en-us/windows/forum/all/windows-10-boot-repair/d6bb23aa-2460-4fc0-b215-b1665016ac2d](https://answers.microsoft.com/en-us/windows/forum/all/windows-10-boot-repair/d6bb23aa-2460-4fc0-b215-b1665016ac2d)

It has a link to download the repair tool. It starts downloading the moment the link is clicked.

The Ubuntu ISO image when used in a TRY Ubuntu session has GParted that will allow you to remove the Ubuntu partitions. But first you need to get the machine booting from the Windows bootloader. Once you remove the Ubuntu partitions the Grub bootloader will be broken.

Assuming that you have a working Windows bootloader and the Ubuntu partitions are deleted You then need to expand a Windows partition to take up the now unallocated space on the drive. You also need to de-fragment the drive. You do that with windows tools.

Have you considered download a Microsoft ISO image that will give a trial edition of Windows 10? That ISO might just have the Microsoft tools you need.

[https://answers.microsoft.com/en-us/windows/forum/all/where-to-download-windows-10-home-edition-trial/9e21a37e-1bef-4d27-9209-c20067d6ed03](https://answers.microsoft.com/en-us/windows/forum/all/where-to-download-windows-10-home-edition-trial/9e21a37e-1bef-4d27-9209-c20067d6ed03)

Regards

---

