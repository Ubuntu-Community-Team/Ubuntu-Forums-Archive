---
title: "Installing Linux Ubuntu 19.10 on Asus n550jk with windows 10"
date: 2019-12-15
forum: New to Ubuntu
---

### Post by gennaro90 on 2019-12-15
[COLOR=#242729][FONT=Arial]Hello everyone, I'm trying to installi Ubuntu 19.10 by following these steps:[/FONT][/COLOR]

[LIST=1]
[*]I downloaded the Ubuntu iso and i created a partition by using windows disk management;
[*]I created a bootable USB by using universal usb installer;
[*]I rebooted my PC by using the UEFI firmware settings (maybe this is the only way to access to the BIOS with an asus laptop);
[*]I ordered the boot peripherals: first USB, but the settings are not saved thus I changed three settings. (i) secure boot control: disables; (ii) fast boot: disabled; (iii) launch CSM: enabled. Now I am able to put first USB.
[*]There are two USB options in the BIOS' boot: (i) [UEFI: "USB brand's name"]; (ii) ["USB brand's name"]. If I put (i) as first, nothing happens, namely windows 10 is run. If I put (ii) as first, I am able to run the Ubuntu's live version, but there are other two problems: (i) there is a message which says that on my laptop there is not an operative system (neverthless there is windows 10); (ii) when I try to install ubuntu in the free space which I allocated at point (1), this message is showed:
[/LIST]


[COLOR=#242729][FONT=Arial]"The Partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as a Reserved BIOS boot area and should be at least 1MB in size..."
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Online I read that this error is due to the fact that I didn't use [UEFI:...] as first choice in the BIOS' boot, but, as I said, the [UEFI:...] option does not work.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Can you help me to overcome these stressful problems please?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thank you for your time.[/FONT][/COLOR]

---

### Post by yancek on 2019-12-15
If your windows partitions don't show in the installer, it is generally a result of the default 'hibernation' on windows 10 so that it appears to boot faster.  If you have disabled fastboot, look for anything related to hibernation in the BIOS and when booted into windows in the power options.  Countless sites online explaining it so I won't go into detail here.

Are you making the changes in the BIOS boot options or in the BIOS where it would be permanent?  Generall, you need to use a key combination to save the changes in the BIOS, ie. F10 then Enter is common.
A pre-installed windows 10 is almost certainly UEFI and if the disk is GPT, then windows would need to be UEFI installed.  Have you verified this as it is possible to install windows 10 in Legacy on an MBR disk?
If your windows 10 is EFI, disable Legacy/CSM in the BIOS.

Not much point creating a partition for Ubuntu on windows because a default windows will not be able to format it anyway so it is usually best to just have unallocated space available on which to install Ubuntu.

Below is a link to the Ubuntu documentation on dual booting UEFI with windows.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-12-15
How did you create Ubuntu live installer.
It seems some tools may may it either BIOS or UEFI, but not both as it is configured for both.

Also some systems require you to change USB settings. It may be specifically allow USB boot or just allow full USB support.

You can install in BIOS mode, but then to correctly install grub it needs a tiny 1 or 2MB unformatted partition for grub to correctly install. And then from Ubuntu you can convert install to UEFI boot.  Or even not install grub at all. 
But you need to have for both Windows (repair/recovery) and Ubuntu (live installer) bootable in UEFI mode to make repairs. So you do need to resolve why you cannot boot in UEFI boot mode.

Other Asus.Issues often common by brand as same or very similar UEFI used with just changes for features included. Bigger difference if Intel or AMD.
       ASUS TUF FX504GM  Intel i7 8750H & nvidia 1060
[https://ubuntuforums.org/showthread.php?t=2431147](https://ubuntuforums.org/showthread.php?t=2431147)
Asus ZenBook Pro 14 UX480 Black screen acpi=off required, but 19.10 not required
[https://askubuntu.com/questions/1138820/black-screen-after-grub-selection-boot-from-usb-live](https://askubuntu.com/questions/1138820/black-screen-after-grub-selection-boot-from-usb-live) 
    
Older versions of Ubuntu, newer may be better, but hardware issues could be the same.
       ASUS X540U pci=noaer instead of pci=nomsi and it also worked
[https://ubuntuforums.org/showthread.php?t=2391201](https://ubuntuforums.org/showthread.php?t=2391201)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)
Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)
Asus N550JX Installing 15.04 , boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)

Edit:
- Often best to have Secure boot off, but should not be required.
You cannot have CSM on with secure boot on. And normally do not want CSM on. Only a few systems (older Dell?) seemed to need CSM on, but still you had to boot in UEFI mode. My system requires 'UEFI only' as 'UEFI or CSM' option only booted in CSM/BIOS mode. Every UEFI varies.
- Fast boot in UEFI should be off. That assumes no system changes and immediately boots to previous configuration. UEFI writes configuration to drive for operating system.
- I always turn off Network boot as I will never use it and do not want UEFI looking for network

- And I have USB full support on. With Secure boot allowing USB boot would not be secure. So USB boot defaults to off. You have to turn it on.

---

