---
title: "Dual Booting Ubuntu and Windows 7, upgrading to Windows 8"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by greenelf on 2012-10-30
Hi,
I am currently dual booting Ubuntu 12.10, and Windows 7. I would like to upgrade to Windows 8, but I heard there is a new bootloader for Windows 8. If I upgrade, will I encounter any problems with GRUB? Or will it work out of the box?

---

### Post by oldfred on 2012-10-30
Are you UEFI or BIOS? Only very new systems are UEFI.

If BIOS any Windows install will overwrite grub and you need your current version Ubuntu liveCD to reinstall grub2's boot loader to the MBR.

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you want a gui and is worth having anyway.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

Boot-Repair fixed BIOS boot Windows 8 & Ubuntu
[http://ubuntuforums.org/showthread.php?t=2056561](http://ubuntuforums.org/showthread.php?t=2056561)

---

### Post by greenelf on 2012-10-30
> **oldfred said:**
> Are you UEFI or BIOS? Only very new systems are UEFI.

If BIOS any Windows install will overwrite grub and you need your current version Ubuntu liveCD to reinstall grub2's boot loader to the MBR.

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you want a gui and is worth having anyway.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

Boot-Repair fixed BIOS boot Windows 8 & Ubuntu
[http://ubuntuforums.org/showthread.php?t=2056561](http://ubuntuforums.org/showthread.php?t=2056561)

I was able to install Windows 8, and GRUB is still there (I used the upgrader). Do you think the sleep corruption thing will affect me?

---

### Post by oldfred on 2012-10-30
You just have to be very careful not to modify anything in your Windows partition from Ubuntu. Linux NTFS driver exposes all the hidden files normally hidden in Windows.

I normally suggest setting in Ubuntu to make the Windows partition read only and use a shared NTFS data partition. But even then you cannot have any of the shared files open in Windows when you shut down.

---

### Post by Mark Phelps on 2012-10-31
> **greenelf said:**
> I was able to install Windows 8, and GRUB is still there (I used the upgrader). Do you think the sleep corruption thing will affect me?

If by the "sleep corruption" thing, you mean that changing stuff in the Windows partition(s) from inside Ubuntu while Windows is sleeping, ends up corrupting the Windows file system -- then YES.  

This is how Hibernation works in Windows and is likely to continue to work the same way.

---

