---
title: "How to Dual boot ubuntu 13.04 and windows 8"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by Haroon_Gilani on 2013-08-14
HI all I wanted to dual boot Ubuntu with my windows 8.1    

but first Ubuntu installer doesn't detect my windows 8.1 partition plus I don't have space on my computer cuz all the 632 GB is used by windows 8.1 


Need help ASAP


Thnx in advance

---

### Post by Mark Phelps on 2013-08-14
Sorry, I don't have expertise with the newest PCs that have secure-boot, UEFI, and GPT partitioning -- but I can advise you NOT to use the Ubuntu installer to shrink down the Win8 OS partition.  Doing that risks corrupting the Win8 filesystem and rendering it unbootable.  Instead, use the Win8 Disk Management to do the shrinkage.

Also, BEFORE you do this, do yourself a favor and use the Win8 option to create and burn a Recovery Drive (it's actually a CD, but Windows calls it a drive).  That will give you the ability to restore Win8 boot loader, should it become corrupted from the dual-boot setup.

---

### Post by Haroon_Gilani on 2013-08-14
i installed windows 8.1 after using ubuntu 13.10 alpha 2 

dont know about any uefi secure boot but thnx for helping

---

### Post by oldfred on 2013-08-14
Did you manually install in BIOS mode not UEFI mode? New computers with Windows 8 pre-installed have UEFI and gpt partitioning.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Haroon_Gilani on 2013-08-18
Thnx for ur concern but your info is way to much to be able to handle by my 13 year old brain 

what i want to tell u is that the windows 8.1 i installed using a usb by default method and not any uefi secure boot but the problem i am facing when installing ubuntu 13.10 alpha 2 is that it shows that the complete hard disk is empty whereas windows 8.1 is installed on that hard drive but the partitioner does not show that ? 


That's my main problem

---

### Post by oldfred on 2013-08-18
If you installed in BIOS mode yourself, then you need to use Windows disk tools to shrink the Windows partition to make space for Ubuntu to install. Reboot Windows immediately so it can run its chkdsk and make repairs for its new size. Then make sure you have turned fast boot or hibernation off.
How many partitions are used?
Post this from Ubuntu live installer terminal.
sudo parted -l

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

