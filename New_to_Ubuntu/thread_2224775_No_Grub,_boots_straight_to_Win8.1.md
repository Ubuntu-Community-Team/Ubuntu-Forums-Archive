---
title: "No Grub, boots straight to Win8.1"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by michael161 on 2014-05-18
[http://paste.ubuntu.com/7482022](http://paste.ubuntu.com/7482022)

I'm trying to install Ubuntu 14.04 on a Sony Vaio with Win 8.1.  After running boot-repair from a live usb I get
An error occurred during the repair.

You can now reboot your computer.

And when I boot up I don't get a boot menu. It just boots right into Windows.  There seems to be a lot of error messages throughout the log but it none of them seemed to be important enough to abort the repair so I'm not sure how to pick out what's important

---

### Post by LastDino on 2014-05-18
Have you turned off secure boot?

---

### Post by oldfred on 2014-05-18
You are showing grub legacy (0.97) installed in the MBR of the drive. Not sure that even works with new systems although it is still in repository.
You should have grub2 which is either grub-pc(BIOS) or grub-efi(UEFI). And since Windows is UEFI, it is generally better to have Ubuntu boot in UEFI mode.
If both systems are not installed in same boot mode, you can only boot from UEFI menu not from grub. As once stared booting in one mode and are at grub menu you cannot change to to other boot mode.

You show two boot flags which make for two efi partitions. Systems only work with one.
Use gparted an remove boot flag from sda3. It looks like fstab tried to use that as the efi partition, I assume that from Boot-Repair trying to install, but confused with grub legacy, two efi partitions and Windows hibernation.

Boot-Repair also said you left Windows hibernated probably with fast boot still on. You need to turn that off if dual booting.

Most desktop installs do not need a separate /boot partition. It just becomes one more partition to manage and keep track of size & use. It may fill with kernels if you do not regularly houseclean, but you should remove old kernels even if not a separate /boot partition.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

