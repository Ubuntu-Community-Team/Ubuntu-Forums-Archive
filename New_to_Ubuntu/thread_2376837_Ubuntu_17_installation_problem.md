---
title: "Ubuntu 17 installation problem"
date: 2017-11-06
forum: New to Ubuntu
---

### Post by fugitiveom on 2017-11-06
Hi, people!

I have a problem during the OS installation.
After successful installation I get this error:
[ATTACH=CONFIG]277433[/ATTACH]

I tried to start Ubuntu without installation from the USB drive and checked partition list with the blkid - the UUID does exist!
I also tried to complete fsck - successful.

The keyboard doesn't work when I see the error (but it works during the installation process).

Please, help me :)

---

### Post by oldfred on 2017-11-06
What brand/model system?
What video card/chip?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by fugitiveom on 2017-11-06
No brand, hand-made computer :) 
NVIDIA GeForce GTX 1060 3GB, Intel Core i5-7500

---

### Post by yancek on 2017-11-06
Post the output of the boot info script requested above, the links are in the post by oldfred.

---

### Post by oldfred on 2017-11-06
UEFI or BIOS install? Report from Boot-Repair will tell us that and many more details.

But with nVidia you need nomodeset until you install the nVidia driver from either the repository (if new enough for your card) or from ppa to get very newest nVidia driver pre-configured for Ubuntu. Do not install directly from nVidia with its .run file.

---

### Post by fugitiveom on 2017-11-06
[http://paste.ubuntu.com/25905647/](http://paste.ubuntu.com/25905647/)
BIOS mode, dual with Win10

---

### Post by fugitiveom on 2017-11-06
just tried boot-repair 2 times:
1) Recommended options
2) Reinstall GRUB and install the lastest ver.

The same end...

---

### Post by oldfred on 2017-11-06
Windows 8 & 10 are really better with UEFI boot over BIOS/Legacy boot.
Grub only boots working Windows and sometimes Windows updates turn on fast start up or Windows needs chkdsk. Then grub will not boot Windows.
If you have the Windows repair disk or installer with repair console you may be able to fix Windows.
But often you have to temporarily reinstall the Windows  boot loader to allow all the Windows fixes.
With UEFI you can always directly boot Windows from UEFI boot menu.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
    
You have very new UEFI hardware, but have configured for the 35 year old BIOS/MBR. 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

But if you have installed & configured both systems, may not be worth effort to reinstall.

---

### Post by fugitiveom on 2017-11-07
Guys, i have no problems with booting the Windows i don't need to repair it. Only Ubuntu doesn't boot.
Btw when i installed Mint 18.2 instead of Ubuntu it was working fine. 
I can't change mode to UEFI because it's too hard for me to reinstall my Windows.

---

### Post by yancek on 2017-11-07
Are you still getting the same UUID error as you showed in your original post?  I don't see that :UUID in fstab, grub.cfg or blkid output.  They all show the UUID:   
f2fc178d-714c-4a1f-884f-40fc29628731 and the grub.cfg entries look correct.  Not sure where that UUID would be coming from?

---

### Post by fugitiveom on 2017-11-07
I'm sorry, mate. I reinstalled the OS.
The right UUID is here:
[ATTACH=CONFIG]277448[/ATTACH]

---

### Post by oldfred on 2017-11-07
Have your since turned off UEFI Secure Boot?
Report said this:
> SecureBoot maybe enabled.

Is drive set for AHCI in UEFI, not RAID nor IDE?

This user ended up, doing a chroot & rebuilding initramfs.
[https://ubuntuforums.org/showthread.php?t=2245053](https://ubuntuforums.org/showthread.php?t=2245053)

In Boot-Repair's advanced mode have you tried to full uninstall/reinstall of grub and install new kernel. That should force the rebuild?

---

### Post by fugitiveom on 2017-11-07
I use the BIOS mode, UEFI is completely OFF.

I tried Boot Repair this way (wrote yesterday):
just tried boot-repair 2 times:
 1) Recommended options
 2) Reinstall GRUB and install the lastest ver.

 The same end...

I read the post you linked. But I don't understand what to do :(

---

### Post by oldfred on 2017-11-07
Is drive set for AHCI?

---

### Post by fugitiveom on 2017-11-08
Yes, AHCI

---

### Post by oldfred on 2017-11-08
What brand motherboard.
My Asus required lots of settings, my Gigabyte still required some but not as many.
But each brand varies and it varies between AMD & Intel based motherboards.
       Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)

---

### Post by fugitiveom on 2017-11-08
I have my MSI B250M PRO-VD

---

### Post by oldfred on 2017-11-08
Possible solutions in these threads.
 MSI x299 SLI additional boot parameters
[https://ubuntuforums.org/showthread.php?t=2371556](https://ubuntuforums.org/showthread.php?t=2371556)
MSI Z170M Intel i7 6700 GTX 980TI 16.10 does not work, 16.04 does
[https://ubuntuforums.org/showthread.php?t=2357641](https://ubuntuforums.org/showthread.php?t=2357641)

---

### Post by fugitiveom on 2017-11-08
Sorry, mate, can't understand what exactly can be my solution?

---

### Post by oldfred on 2017-11-08
I do not have an MSI motherboard, but those users do.
And they post some things they tried which worked.

You may just need another boot parameter in grub.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by leunam12 on 2017-11-09
I have an MSI motherboard and I solved my dual-boot problems by disabling Fast Boot. Also I had to boot the live session from USB and chroot into the system drive and re-install GRUB that way because Boot-repair wasn't working.

Mount your system partition (X is the drive letter and Y is the partition number). ```
sudo mount /dev/sdXY /mnt
```
if you have a separate boot partition: ```
sudo mount /dev/<path to boot partition> /mnt/boot
```
Mount the critical virtual filesystems.```
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
```
chroot into system device.```
sudo chroot /mnt
```
Install GRUB (using the right drive letter and no partition number).```
grub-install /dev/sdX
update-grub
```
Exit (Ctrl+D) and reboot.

---

