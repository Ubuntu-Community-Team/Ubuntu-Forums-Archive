---
title: "Dual Boot on separate hard drives"
date: 2016-03-02
forum: New to Ubuntu
---

### Post by guzzos on 2016-03-02
Hello I am intermediate in Ubuntu and I would like to have Ubuntu in one hdd and Windows 10 on the other.  In fact I already have both OS installed and working on separate drives.  I have a third drive which I want to use as a boot menu.
I choose this method due to the mess with the UEFI and Bios stuff between Windows and Ubuntu.
Any ideas on how can I achieve this.  Of course if it is possible.

---

### Post by grahammechanical on 2016-03-02
To avoid the mess between UEFI & BIOS the location of Grub is less important that having Windows 10 & Ubuntu installed in the same mode. Another consideration is the partitioning table used on the hard drives. With Windows 10 I am sure that GPT is needed. Ubuntu can make use of both GPT partitioning or MSDOS partitioning.

I do not think that installing Grub to a third hard drive will solve any mess. To start with, Grub will need to look for its considerations file in the /boot/grub folder of the Ubuntu partition. I suppose that is possible but if Windows 10 is installed in EFI mode & Ubuntu is installed in BIOS/CSM/Legacy mode then we still have a mess with UEFI & BIOS.

Regards.

---

### Post by oldfred on 2016-03-03
When I had BIOS I had multiple installs on several drives.

With UEFI, I also have multiple installs on two drives, but only Windows system has only one drive.

Best to always use just UEFI or just BIOS when booting. And if UEFI best if all drives use gpt partitioning.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Some disconnect one drive to install cleanly to another drive, but important to use just one method UEFI or BIOS.
And best to make sure Windows is in SATA 0 and Ubuntu in SATA1. Do not skip ports or when you plug in flash drives, drive may change.

---

### Post by guzzos on 2016-03-04
Thanks a lot for your replies. I will give a try installing Ubuntu in uefi mode since I assume the windows instalation is in UEFI.
This way I will have the same type of installation.  I have windows 10 installed in a SSD drive and the data (My Documents) resides on another drive (D:/).  I hope windows works with this setup.

Regards,
Gustavo

---

### Post by guzzos on 2016-03-20
Ok, I followed your instructions regarding the SATA order my first volume which is Windows 10 is in SATA0 and my second volume which is Ubuntu 15.04 is in SATA1.  Both installations are in UEFI mode.
I have a MOBO Asrock ZZ Extreme 4.  I disabled fast boot and Intel Rapid Start bla bla.  The MOBO has a (F11) boot menu option when booting, which I though could be used to select the boot device, but I does not works.  I press F11 and nothing happens.

Having this setting what should I do to have a boot menu like rEFIt to select which OS to boot.

Thanks in advance for any info.

---

### Post by oldfred on 2016-03-20
The rEFIt application is not maintained anymore, but a fork rEFInd is what you now want.
       Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

Whatever key gives boot menu from UEFI for you motherboard should show all boot options whether UEFI or BIOS.

And for rEFInd to work best to have working install.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by guzzos on 2016-03-20
Wao, thanks a lot for your valuable information.  \\:D/
I installed refind and finally everything works fine.  Prior to your recommendation I was trying to achieve this with rEFIt, it was driving me crazy.  Didn't know it was dropped since 2010.

Again thanks a lot for your help!!!:D

---

