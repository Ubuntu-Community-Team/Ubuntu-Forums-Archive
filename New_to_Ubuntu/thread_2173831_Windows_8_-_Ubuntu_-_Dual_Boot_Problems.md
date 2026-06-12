---
title: "Windows 8 - Ubuntu - Dual Boot Problems"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by fatsheep on 2013-09-11
I just got an [Acer laptop]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834314150") with Windows 8 pre-installed.  I am planning on dual booting Ubuntu with it and using a separate NTFS partition to share data between operating systems.  

I was able to boot a Ubuntu USB drive (made with the Universal USB installer) using the 'nomodeset' boot option (otherwise I got a black screen).  However, Ubuntu could not detect any operating system on my computer so I had to manually create the partitions for Ubuntu.  I created an EXT4 partition (primary) mounted at "/" and a swap partition alongside my existing partitions (not sure if this is right but it is what I did).  

Installation went fine, but after rebooting I get shot straight into Windows 8 as if I never installed Ubuntu.  I did some reading about EFI, UEFI, and how to dual boot but that really just confused me so I figured I would ask for advice here.  

1.  **How can I get GRUB to be the boot loader? (since I currently can't get to Ubuntu at all)**  Also, if Ubuntu couldn't see my Windows 8 operating system during installation, will GRUB be able to boot to Windows?  I'm a little wary about anything happening to my Windows 8 partition since my laptop didn't come with an installation disk or key (guess I just have to hope my hard drive doesn't fail).  
2.  **Can (or should) I keep UEFI boot enabled in the BIOS and dual boot Windows 8**?  Or do I need to enable legacy mode?

Thanks in advance,

- currently confused Windows 8 user

---

### Post by Panderz on 2013-09-11
Have you tried "grub-install /dev/YourHardDrive"? Make sure it's installed to the actual device, not a partition. I.e., sda, not sda1/sda2/etc.

---

### Post by oldfred on 2013-09-11
With UEFI you install grub to efi partition, not MBR or PBR.

Did you install Ubuntu in UEFI mode or BIOS mode. How you boot installer is how it installs. And UEFI menu to boot flash drive should have given two choices UEFI or CSM/BIOS/Legacy.

Did you turn off fast boot in Windows? Is secure boot on or off?
Have you run Boot-Repair? Grub2 does not create correct chain load entries for UEFI, but Boot-Repair will.

If correctly installed in UEFI mode, you should just be able to go into UEFI menu or use one time boot key and choose ubuntu entry.

 Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)



       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Screen examples by other uses with UEFI. Yours may vary but should have similar entries.

---

### Post by fatsheep on 2013-09-11
> **oldfred said:**
> With UEFI you install grub to efi partition, not MBR or PBR.

Did you install Ubuntu in UEFI mode or BIOS mode. How you boot installer is how it installs. And UEFI menu to boot flash drive should have given two choices UEFI or CSM/BIOS/Legacy.

Did you turn off fast boot in Windows? Is secure boot on or off?
Have you run Boot-Repair? Grub2 does not create correct chain load entries for UEFI, but Boot-Repair will.

If correctly installed in UEFI mode, you should just be able to go into UEFI menu or use one time boot key and choose ubuntu entry.

 Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)



       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Screen examples by other uses with UEFI. Yours may vary but should have similar entries.

> **Panderz said:**
> Have you tried "grub-install /dev/YourHardDrive"? Make sure it's installed to the actual device, not a partition. I.e., sda, not sda1/sda2/etc.

I guess I did install it in UEFI/EFI mode since I got a screen that looks like the one here: [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode).  I did not change the settings to fast or secure boot.  I can if it is necessary.  I will reboot onto the Live USB drive and try boot repair.

---

### Post by fatsheep on 2013-09-11
Well I get an error when I try to boot the LiveUSB drive (which is strange because installation worked fine):

[ 26.773602]  mei 0000:00:16:0: init hw failure.
[ 26.773698] mei 0000:00:16.0: initialization failed.



So it looks like I have another problem to troubleshoot.

---

### Post by oldfred on 2013-09-11
A couple of other Acer. May be similar?
 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

Some of the very new hardware also requires additional boot parameters or settings in UEFI/BIOS.

These were not Acer but it may be Haswell related?

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

   Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Ubuntu on Laptop Toshiba Satellite P75 - Haswell
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

