---
title: "Trying to set up dual boot Windows 10 and Ubuntu 14 LTS"
date: 2015-09-28
forum: New to Ubuntu
---

### Post by Kevin_Nauta on 2015-09-28
Hey there

I recently bought an HP 15 something something laptop, and an extra SSD (Kingston 300V). After swapping the two out, I installed windows 8 on the laptop, and upgraded it to windows 10.
Today in class, the professor told us that for programming in C++ he recommended to use a linux distro. Dualboot or VM didn't really matter but as my laptop isn't the best of the best I'd rather have it dualboot.

So I grabbed my Ubuntu 14.4 bootable USB stick, rebooted and spammed F2. Brought me in some repair screen.
F8 and Delete didn't get me into BIOS either. Then I googled, and turns out I had to hold shift while pressing restart. So I did, and selected to boot from USB.

EFI something not compatible. Now I selected some .efi myself and somehow found my way into the BIOS menu, where I set the boot order from USB stick, then USB harddrive, then OS launcher, then the rest, but it didn't do any good.

When I then tried to get back into the bios, the route I had taken earlier didn't work (it wouldn't let me in the BIOS anymore). Oh well, besides the boot order I didn't change anything at all.

I downloaded the newest version of Ubuntu 14.4, apparently 14.04.3, and using pendrivelinux.com I installed it on the USB stick. Shift+restart, boot from usb, no luck.

I also read somewhere that BIOS installs in a UEFI way don't really work out, so I guess at this point it's a user-problem, i.e. I'm doing something wrong.
Or it's simply impossible to dualboot windows 10 and another OS... Any help?

---

### Post by corneliuss2 on 2015-09-28
1. Use Ubuntu x64. Put it on USB with Rufus and select **GPT partition scheme for UEFI**
2. Restart Windows using Advanced StartUp. See here: [http://www.makeuseof.com/tag/how-to-access-the-bios-on-a-windows-8-computer/](http://www.makeuseof.com/tag/how-to-access-the-bios-on-a-windows-8-computer/)

---

### Post by Bucky Ball on 2015-09-28
UEFI installs work out fine and if Windows is installed in EFI, then Ubuntu should be, too.

You need to boot into Windows and switch off hibernation to start with, and/or faststart, whatever that is called. You'll see it when you're there.

You need to boot to the BIOS, not to a selection of boot devices, and switch off secureboot in there prior to the Ubuntu install.

If you get to the option on the USB with 'Try Ubuntu', choose that and make sure it is working live. If it is and you're happy, there is an icon on the desktop to install.

---

### Post by oldfred on 2015-09-28
If you installed Windows yourself, did you install in BIOS/MBR mode or UEFI/gpt mode?

You just need to be sure to install Ubuntu in the same boot mode. And both Windows & Ubuntu install in the boot mode that you use to boot install media. From UEFI boot menu you should get two boot options for DVD or flash drive installer, one UEFI and one not or BIOS.

With Windows you do have to make sure you have turned off its fast startup. And if newer UEFI system, you should also turn off fast boot in UEFI which is a different setting than fast start in Windows. If fast boot is on, you may have difficulty getting into UEFI to change settings or choose what to boot.
You also often have to change UEFI settings. Best to have secure boot off, fast boot off, USB ports on or allows boot from USB ports and perhaps other settings.

---

