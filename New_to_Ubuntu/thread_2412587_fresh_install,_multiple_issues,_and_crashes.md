---
title: "fresh install, multiple issues, and crashes"
date: 2019-02-14
forum: New to Ubuntu
---

### Post by chadwitk on 2019-02-14
going to run a dual boot with win 8 on 2 different drives.
Download 18.04, follow the tutorial to make a bootable usb

First attempt the demo ran great on the usb stick, install ran, created log in etc, updates ran, etc.   re-start then login screen is extremely laggy, enter my password, hit enter, and it crashes as if I hit the reset button.  Black screen, then splash screen, rinse and repeat...
Next day I start over with the usb, after a bunch of screwing around I get it to re install, login works fine, as does everything else.  I'm playing around getting familiar with it while updates are loading in the background.  Updates install I restart.  
This time login works ok, but when I click on "help" or "settings" icon it crashes just like the day before.  login screen is laggy, but works getting me back to the point that it crashes when I try help, or settings, more things may crash it, but I don't feel like testing everything to see what works..

Suggestions???

---

### Post by oldrocker99 on 2019-02-15
The first bootup from a new install is always slow, the first time, even on a SSD. It's a lot faster after that.

Reboot with the USB, and select "Verify." It may find an error. Read this:[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0).

It is always possible that the .iso download is faulty, and that page will show how to verify the download. You may have to reinstall with a verified download.

---

### Post by oldfred on 2019-02-15
What brand/model system?
What video card/chip?
Some need boot parameters to work well or if nVidia, the nVidia driver installed.

Also have you updated UEFI and if SSD, SSD firmware? That is required even if not dual booting.
But if you update UEFI, you will have to redo the UEFI settings you changed, as some will revert to defaults.

---

### Post by chadwitk on 2019-02-15
Home built system, been running win since new
msi z77a-gd65 mo bo
EVGA 1070TI video card
16g ram
500g samsung 850 ssd for windows
128g samsung 840 ssd for ubuntu
Haven't tried dual boot yet, I only plug in the drive I want to boot from

---

### Post by oldfred on 2019-02-15
If you installed in UEFI boot mode, UEFI forgets the boot entry when a drive is unplugged. It changes it to some sort of default parameters.
Most systems seem to find Windows, but not Ubuntu. You then have to use  efibootmgr to add entry again or use Boot-Repair to reinstall grub. Or manually reinstall grub.

If BIOS boot it should just work if correct drive selected. But newer UEFI systems may need settings to match.

Samsung typically have needed firmware updates.

---

### Post by chadwitk on 2019-02-24
well, I finally got the mobo bios update to work..  (automatic my ass)  and now ubuntu boots and works without crashing, just working on getting the dual boot to work.  when I set the bios to uefi the machine boots into ubuntu only, when I set it to legacy, it boots to windows only.  
working through the uefi install thread, slowly  I'm a little nervous about loosing my windows drive as its got a lot of stuff I don't want to loose (even though I backed it up)  I've already had to repair the master boot record a couple times

---

### Post by richard378 on 2019-02-24
From the Ubuntu install with both drives connectedtype on the command line: sudo update-**grub**

Then you can set the default boot drive to Ubuntu and the Grub Ubuntu boot loader sould give you options on chosing your boot.

For the time error in windows after duel booting I suggest this article: [https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/)

---

### Post by oldfred on 2019-02-24
UEFI & BIOS are not compatible.
If you installed in differnent boot modes, you can only dual boot from UEFI menu, not from grub. Grub can only boot other installs in same boot mode. And if Windows it must be working & not hibernated or fast start up on as that sets hibernation flag.

If Ubuntu on separate drive and UEFI/gpt, you can convert to BIOS by adding a 1 or 2MB unformatted partition with the bios_grub flag and reinstalling the BIOS version of grub. Often easier with Boot-Repair and best to boot in mode you want. If install drive is MBR partitioned, you can just reinstall grub.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

With 2 drives, do not run auto fix from Boot-Repair. It wants to install grub to every drive, but you want to keep a Windows boot loader on the Windows drive. Only use advanced mode in Boot-Repair.

---

