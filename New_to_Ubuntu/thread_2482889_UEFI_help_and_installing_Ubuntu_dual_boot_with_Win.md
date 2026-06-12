---
title: "UEFI help and installing Ubuntu dual boot with Win 10 ..."
date: 2023-01-13
forum: New to Ubuntu
---

### Post by cwmoser on 2023-01-13
I just purchased a new-to-me refurbished Lenovo T470s laptop.
Being a long Ubuntu user with hardware that does not use UEFI,
I think I need some advice.  

I want to install Ubuntu 22.04 along side Windows 10 - i.e. dual boot.
What is the process?  I can get to the BIOS by going through Win10 and that kinda sucks versus the "old way" of just pressing a key during boot.
Anyway, I have a bootable thumbdrive with Ubuntu install and need to figure out how to use it without borking Win10.
Also, can the Ubuntu gparted resize the NTFS partition in order to have an EXT4 partition?
Will Grub present a menu on boot so I can select either OS?

---

### Post by tea for one on 2023-01-13
Here is a little check list for dual booting.
The info was gleaned via an array of forum posts relevant to dual booting.
Not all are applicable in every case.

_General Observations for Dual Boot Windows 10 or 11 & Ubuntu Family_

Backup your data
Both systems in UEFI mode with GPT
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

_UEFI settings_

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast) 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Optane memory and storage
Remove Optane drive and reset UEFI to default
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

_Windows 10 settings_

Backup your data
Turn off Bitlocker (if installed)
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Windows 10 > Check via Disk Management > Right Click (C drive) > Properties > Volume > Partition Style
Windows 11 > Settings > System > Storage > Advanced Storage Settings > Disks & Volumes > Select Disk (C) > Partition Style
Check via Administrator Command Prompt > diskpart (press enter) > list disk (press enter) > Gpt starred or unstarred.
Install Windows 10 (or 11) in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows (Disk Management) tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
[https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10](https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10)
[https://ubuntuforums.org/showthread.php?t=2458373&page=2&highlight=rst+optane](https://ubuntuforums.org/showthread.php?t=2458373&page=2&highlight=rst+optane)
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)
Intel Memory and Storage Tool 
[https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux](https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux)
Target disk must not be part of Windows Storage Pool (conceptually similar to RAID)

_Ubuntu Family_

Boot into a live session in UEFI mode (how you boot determines the installation mode)
Check wifi, sound, graphics, mouse, touchpad etc
Use gparted to create a GPT (GUID Partition Table) if not already present.
Install Ubuntu in the free space previously created (or your own partition scheme e.g. separate root and home)
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Grub will find the EFI partition already used by Windows
Sometimes (although very rare) internet connection prevents clean installation

---

### Post by oldfred on 2023-01-13
Best to use Windows to shrink the NTFS partition. While gparted or installer can shrink it, sometimes there are errors almost always Windows related but then user blames Linux. NTFS always needs chkdsk after a resize, so reboot Windows after change.

Systems have keys to directly go into UEFI system settings & UEFI boot menu.  Download & check your manual for unique settings.
    Lenovo - F8, F10, F12 is shown on some sites.
Some Lenovo have there settings, may be in other models, just that users have posted issue. The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
UEFI update required for USB-C port issues 2017 thru 2019 models

Be sure to update UEFI firmware.

Newer system that is UEFI, need Ubuntu installed in UEFI boot mode.
Install:
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Some general install info in links in my signature, below.

Older info, only use 22.04 or 20.04.
[https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/](https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/)

---

### Post by cwmoser on 2023-01-13
Geesh ... Microsoft is making it difficult to switch to Linux.
A not so technical person would find this insurmountable.

---

### Post by cwmoser on 2023-01-13
Thanks for the great information.
I was able to shrink the NTFS partition using Win10.
Booted off the USB thump drive and installed Ubuntu
and set up a 1MB Reserved BIOS root area.
After rebooting, I don't have anything that allows me to select Ubuntu.
All I can get is Win10.
Any ideas?

---

### Post by tea for one on 2023-01-13
The BIOS boot area indicates that the installer was booted in Legacy mode.

Boot into Windows and remove the partitions created by Ubuntu.
Then, boot the Ubuntu installer in UEFI mode.
You can check during a live session via this terminal command:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

---

### Post by cwmoser on 2023-01-13
I get Legacy Mode when I enter that command trying out Ubuntu.

---

### Post by tea for one on 2023-01-13
Can you jump into your Lenovo UEFI settings and disable Legacy Boot?
Alternatively, when you boot the Ubuntu USB, you have to choose the boot mode i.e. UEFI followed by colon
Does this image help with boot mode choice?

---

### Post by oldfred on 2023-01-13
Some tools to make USB flash drive make only UEFI or only BIOS. Most are bootable in either mode.
But then in UEFI you have to choose UEFI boot mode. Often separate from default boot mode which is for installed system.
So you should have UEFI: XXX which is the UEFI boot entry you want or just XXX which is the BIOS boot entry you do not want, where XXX is name or label of flash drive.

---

### Post by cwmoser on 2023-01-14
Hey this has been very helpful.

**_Now my boot menu is:_**
ubuntu
Windows Boot Manager
NVMe0: INTEL SSDPEKKF256G7L
PCI LAN

I now can boot either Ubuntu or Win10 with Ubuntu the default.
Not sure what the 3rd item is, guessing its the Win 10 recovery partition.

Thanks very much for the help.  
Really like this Thinkpad 470s laptop especially with Ubuntu 22.04 on it.

---

### Post by oldfred on 2023-01-14
When you boot an external drive by name or label, you are booting using /EFI/Boot/bootx64.efi.
Now that same path & file exist for internal drives & most UEFI will offer to boot that.
But the bootx64.efi may be a copy of Windows .efi boot file or a copy of shimx64.efi after grub install. You just about have to compare file sizes to know. And now default mount of ESP using fstab uses umask=0077 which is no permissions for security reasons.

---

