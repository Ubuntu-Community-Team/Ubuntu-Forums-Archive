---
title: "Struggling to boot from unetbootin made USB on Asus N56VZ UEFI"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by Dr-ROX on 2013-03-28
I'm struggling to boot Ubuntu from bootable USB I've made using unetbootin. In the older days, when booting laptop you could go into bios and set the boot device. Now I can't set one. There's no hotkey I could press during boot to open up BIOS. So I'm using Windows 8 special reboot > Troubleshoot > Advanced Options > UEFI Firmware settings, going to UEFI options and getting familiar blue BIOS window there. But if I'm setting up my Boot device to USB, it doesn't boot. Looks like it's searching EFI files on my USB. Is there any way of booting from regular bootable USB on these new laptops or USB should be made from ISO file using different tool than unetbootin? I have disabled secure boot and fastboot.

---

### Post by wojox on 2013-03-28
Have you exhausted the resources on the wiki? 
[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by Dr-ROX on 2013-03-28
I will try to make bootable CD, maybe that will work, but basically I can't get past step 3 on the first chapter, that tells to boot from removable media. On my laptop there's no options to boot from USB, though there's one to boot from CD.

---

### Post by oldfred on 2013-03-28
Did you download the 64 bit version? The 32 bit does not support UEFI booting.
Have you backed up Windows & the efi partition?
Have you made a Windows 8 repair flash drive?

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

      
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Other Asus, may be similar?

 Asus N56VJ-SH71-CD Shows default Windows partitons Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by Dr-ROX on 2013-03-29
I have found the solution. If someone won't be able to boot from any media on Asus N56 series laptops, do these steps:

On Windows 8:
    Press the Windows key + C, or swipe in from the right edge of the screen to open your Charms.
    Click Settings.
    Click Change PC Settings.
    In PC Settings, select General.
    Under Advanced startup, click Restart now. The system will restart and show the Windows 8 boot menu.
    In the boot menu, select Troubleshoot.
    In the Troubleshoot menu, select Advanced options.
    In the Advanced options menu, select UEFI Firmware Settings.
    Click Restart to restart the system and enter UEFI (BIOS).

In the BIOS screen:
    Go to Boot tab
    Select Launch CSM and make it Enabled. This will disable FastBoot and actually will enabl;e the ability to enter BIOS mode and boot from any device.
    Go to Security tab
    Select Secure Boot Control and make it Disabled.
    Save your settings.

Now restart the PC and during boot time hold Esc key, this should show good old time style boot menu where you select device. If you want to boot from USB flash, select the option with your USB flash name but WITHOUT UEFI word in it. That will boot from standard non UEFI flash drives.

---

### Post by oldfred on 2013-03-29
That will boot you in the standard BIOS mode. But if you install from that mode you will not be able to easily dual boot. Each time you want to change you have to go into UEFI/BIOS and turn it on or off.

Some systems will only install Ubuntu in BIOS mode. But the main difference is just grub-pc for BIOS and grub-efi for UEFI. Boot-Repair will convert a BIOS install to UEFI install if on gpt partitioned drive.

---

