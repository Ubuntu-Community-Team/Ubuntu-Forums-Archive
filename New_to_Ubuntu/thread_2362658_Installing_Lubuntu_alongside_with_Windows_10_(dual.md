---
title: "Installing Lubuntu alongside with Windows 10 (dual booting) is it safe ?"
date: 2017-05-31
forum: New to Ubuntu
---

### Post by ashi97 on 2017-05-31
Hello,

I want to dual boot LUbuntu 16.04.2 and Windows 10, but I am bit confused and have the following queries,

[LIST=1]
[*]Is it Safe to install ?  I am having this doubt because newer version of windows 10 come with UEFI booting mode and I have read some articles that there are some problems with Ubuntu in this mode. I thought the same problems might apply to LUbuntu after all LUbuntu is a Ubuntu flavor.
[*](**biggest concern**) I am having 256 GB SSD in which windows 10 is installed and I don't want to install Lubuntu in it. Before I had tried to dual boot windows 10 and Ubuntu by clicking on "*something else"* option in the installation window and had installed successfully in HDD but when I restarted it, the grub menu did not load instead it went directly to windows 10. Is it possible to install LUbuntu in my HDD while keeping Windows 10 in SDD? If yes please guide me to achieve it.
[*]Should I change the boot order after we install for the first time so that the grub menu is loaded?
[/LIST]

---

### Post by yancek on 2017-05-31
There should not be any problem installing Ubuntu/Lubuntu in UEFI mode.  The most frequent problem I see posted by users trying to do this is not informing themselves in advance on the difference between UEFI/MBR.  If one system (windows) is UEFI, then any other systems you install should also be UEFI or you will have problems booting.  I would suggest that you read the Ubuntu documentation below on dual booting UEFI.  Should be pretty much the same for Lubuntu.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Yes you can install Lubuntu to a separate drive.  You need to be familiar with drive/partition naming conventions for Linux.  I believe the default for an EFI install will install the Lubuntu efi code to the same drive on which you have windows if there is already an EFI partition existing.  You might wait for someone more familiar with that process to post.

---

### Post by oldfred on 2017-05-31
To your first question: Is it safe to keep running Windows 10? :)
You asked on an Ubuntu forum where some have eliminated Windows and others keep Windows for one or two applications but do not particularly like it.

If you install Ubuntu to a second drive you must use Something Else install option. And second drive should be gpt partitioned.
Gpt is the standard partitioning used with UEFI, your Windows system is gpt partitioned. MBR(msdos) is 35 years old from original PC and has many kluges to allow it to work with newer systems.

Be sure to install in UEFI boot mode, but you can install in BIOS boot mode even on gpt drive. But UEFI & BIOS are not compatible and then you can only dual boot from UEFI boot menu, often f10 or f12 when first starting system. And you may have to change UEFI settings to turn on/off UEFI or on/off CSM/legacy modes.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
Many do dual boot Windows & Ubuntu on same SSD without issue.
But some brands make it more difficult than others. They actually violate UEFI standard to use description to boot . And only valid description is "Windows Boot Manager". But many work arounds depending on configuration. UEFI should just install and let you choose which system is default boot. Dell usually does, HP & Sony do not. Other may vary.
What brand/model system? Also what video card/chip as that also can require driver issue easily worked around (if you know) to initially boot.

If you can change boot order and both systems are in UEFI boot mode, then grub will boot working Windows.
If Windows is hibernated or if damaged by abnormal shutdown and needing chkdsk, grub will not boot it. You then may boot from UEFI or from your Windows repair flash drive.

If you cannot boot now.
       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ashi97 on 2017-06-01
I [SIZE=1][/SIZE]have Omen by HP - W 249TX- 17.3-inch Laptop and there are steps for dual booting it in the internet but it didn't work out for me can you please tell me the steps to dual boot the system. Thank you!!

---

### Post by oldfred on 2017-06-01
HP is one of those that is not UEFI dual boot friendly.

Most with HP have to copy /EFI/ubuntu/shimx64.efi & rename to /EFI/Boot/bootx64.efi. That is a fallback or hard drive boot entry.
Boot-Repair now does this if you check in Advanced Options the 'Use the standard efi file'.
And many HP already have an UEFI setting to boot hard drive so that then will boot ubuntu. If not we can use efibootmgr to add a hard drive entry.

To see current UEFI boot entries.
sudo efibootmgr -v

Post link to summary report from Boot-Repair.
If you need details on new UEFI entry I can post that, or you can read ahead as it is somewhere in link in my signature.

Older threads, before Boot-Repair auto copied files. Users manually copied.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

