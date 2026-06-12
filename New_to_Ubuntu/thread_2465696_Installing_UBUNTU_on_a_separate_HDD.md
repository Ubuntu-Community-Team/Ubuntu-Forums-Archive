---
title: "Installing UBUNTU on a separate HDD"
date: 2021-08-08
forum: New to Ubuntu
---

### Post by hkarthi on 2021-08-08
Hi All,

I am new to Linux and I have been thinking of dual boot my PC with Ubuntu and Windows. I already have Windows 10 on my SSD drive and I have a separate HDD on which I want to install Ubuntu. Is this possible? 

Although I am not sure if I understand correctly, Ubuntu install works with Secure Boot ON right? Or do I need to disable it before installing?

---

### Post by monkeybrain20122 on 2021-08-08
Yes, it will work. You may be able to keep secure boot on but disabling  it make life a lot easier IMO, also have to disable Windows fast boot and make sure you install the bootloader in your external drive or your Windows won't boot when the drive is disconnected.

---

### Post by hkarthi on 2021-08-08
Thank you! I am still on the fence whether to ditch Windows completely. Since I do play games, I don't want to move away from it (atleast for now). 

So when I install Ubuntu, I should make sure the bootloader is installed in the second drive and not in the SSD? 

If so, will the system recognize both OS and show me the option while booting up?

---

### Post by oldfred on 2021-08-08
UEFI or BIOS?
Most systems now are UEFI.
And if UEFI are both drives gpt partitioned?

I prefer to have an ESP - efi system partition on every drive, but Ubuntu's Ubiquity installer only installs into the first ESP, usually the Windows drive.
If you every want to separately boot the Ubuntu drive,it needs an ESP. If not, it does not really matter.

New versions now use grub to boot whether UEFI or BIOS. How you boot installer, is then how it installs, so be sure to boot in correct boot mode.
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tea for one on 2021-08-09
> **hkarthi said:**
> If so, will the system recognize both OS and show me the option while booting up?  [COLOR="#0000FF"] Yes, via UEFI boot menu[/COLOR]

Here is a little check list for dual booting.
The info was gleaned via an array of forum posts, where dual booting presented problems.

_General Observations for Dual Boot Windows 10 & Ubuntu Family_

Not all are applicable in every case.

Backup your data
Both systems in UEFI mode with GPT
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

_UEFI settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

_Windows 10_

Backup your data
Turn off Bitlocker 
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Install Windows 10 in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

_Existing Windows and then Ubuntu on Separate Disks_

De-activate, disconnect, isolate or physically remove existing OS drive so that only the target drive is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Boot each system independently via UEFI boot screen (ideal not cumbersome)
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have EFI partition
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)
De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

---

### Post by Autodave on 2021-08-09
Or you can do what I did.  Disabled Fast boot and Secure boot. I disconnected the Windows hard drive and connected a blank HD.  I installed Linux on that HD.  Then, reconnected the original HD to its original place on the mother board and moved the Linux drive to the next one.  Now, to boot to Windows, I just turn the machine on and Windows boots.  To boot to Linux,  I hit the proper key while booting to bring up the boot choices and then choose the Linux drive.

---

### Post by grahammechanical on 2021-08-09
> Although I am not sure if I understand correctly, Ubuntu install works  with Secure Boot ON right? Or do I need to disable it before installing?

Ubuntu will install with secure boot on because Canonical, the sponsors of Ubuntu, have arranged with Microsoft to have some boot code validated so that it will be accepted by the secure boot process.

Many on this forum recommend turning secure boot off. As stated, it makes life simpler. Recently there have been issues with Nvidia video drivers and secure boot. So, it just might be good advice to turn secure boot off.

> If so, will the system recognize both OS and show me the option while booting up?

The Linux boot loader is called Grub (GRand Unified Bootloader) and it will recognise the Windows boot loader and put an option to load Windows in the Grub boot menu.

If you set the UEFI to boot from the Ubuntu drive you will get a menu that will offer to load both Windows and Ubuntu. If you follow the advice to disconnect the Windows drive and then install Ubuntu after you have re-connected the Windows drive load into Ubuntu and run this command

```
sudo update-grub
```

You will need to enter your Ubuntu password. The command should produce a printout showing the operating systems detected which will include Windows.

Regards

---

### Post by hkarthi on 2021-08-14
Thank you for all your help!... got Ubuntu 20.04 installed and working just fine (except for the audio issues) ...

---

