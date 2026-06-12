---
title: "usb hardisk not booting ubuntu"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by sanji765 on 2013-05-02
i rezised my portable usb hardisk(930gb ntfs drive to 900gb ntfs),and gave[COLOR=#ff0000] 5gb to swap,25gb to ext4 and mount "\",[/COLOR]i intalled ubuntu 13,using dvd,but [COLOR=#ff0000]it dosnt boot,when i try to boot from usb[/COLOR],my laptop is uefi capable,but secureboot is disabled(lenovo g580),why is it not booting,where do i write the boot loader(in the installation wizard i selected my usb device to intall bootloader),i have even tried to install the boot loader to the linux partation,even then its not booting,[COLOR=#ff0000]what am i doing wrong--?[/COLOR]

--i would like to install it to my internal hdisk also,but am afraid of screwing up

---

### Post by fantab on 2013-05-02
For UEFI to work you need to create a 250Mib (300MB) partition up in the front, meaning your first partition, and format it with FAT32 and you will put a 'boot' flag on it. . UEFI will ONLY work with 'GPT' partition table and not with 'msdos', which is what you very likely have. You may have to Delete all those partitions, including 900GB NTFS, and start over again. BACK UP your DATA First.

But before you hit that delete button in Gparted, enter your BIOS set up and check what sort of UEFI mode it is set to, 'UEFI', 'Auto' or 'UEFI & Legacy' etc... And change it to some thing that means "both" (UEFI and Legacy). Then, enable booting from USB and also change the HDD boot order to boot USB first. Try to boot your portable USb after that... if works great, if not then...

---

### Post by sanji765 on 2013-05-02
Both my internal and external hdisk is MBR ,i checked,i deleted the partations from my external disk,and partationed internal storage,for linux,still cant multiboot linux,i use windows 8 boot manager,tried esaybcd,everything in the book,i can only get in minimalistic bash or something like that,not to the login screen,why is linux so frusturating and why couldnt i boot linux from usb,after doing everything right,installed right,but dosnt boot,i dont think its the gpt issue,as i installed win8 myself,and didnt use gpt

---

### Post by oldfred on 2013-05-02
If you installed Windows 8 yourself, then you probably do not have gpt partitioning. Windows only boots from gpt with UEFI, so then you still are booting with BIOS/CSM if your system is UEFI capable.
       Compatibility Support Module (CSM), which emulates a BIOS mode 

Some BIOS do have issues with booting beyond 137GB on a drive, particularly on USB drives.

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

If you have Ubuntu installed somewhere post this, from live installer:


 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

