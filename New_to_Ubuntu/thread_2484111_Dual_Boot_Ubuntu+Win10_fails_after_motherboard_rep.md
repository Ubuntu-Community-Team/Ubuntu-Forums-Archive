---
title: "Dual Boot Ubuntu+Win10 fails after motherboard replace.  Ubuntu not listed in UEFI"
date: 2023-02-18
forum: New to Ubuntu
---

### Post by jcp161 on 2023-02-18
I had a functional dual boot system running on my Lenova X1 Thinkpad, Gen9.  The GRUB menu showed at launch and allowed me to select which OS I wanted.  My motherboard had to be replaced due to a problem with the USBC ports.  My original Ubuntu version was 20.04 but I upgraded it to 22 along the way - installed via USB stick.  I am still a novice with Linux but here is what I found so far:  Ubuntu doesn't show up in Lenova UEFI (hit enter during boot to access, then F1).  I tried the commonly reported solutions:  boot-repair, windows disable hibernate and fast startup, in windows bcdedit correctly shows boot manager option for Ubuntu \EFI\ubuntu\grub64.efi (I don't have secure boot enabled).  I booted from a live disk and did gparted - can successfully see my ubuntu partition - it just doesn't show up in the UEFI.  From live boot, ran boot-repair and got boot-info log file (attached).  I had to zip the log file to fit within limits but its not really that big.  I appreciate any help - I am at my wits end.  

Update:  One of the remarks in the attached zipped report suggested trying again with an option deselected.  I repeated the boot-repair method but did not do any advanced options - I simply did the recommended option.  The result is here:  [https://paste.ubuntu.com/p/MFyFDGmb4m/](https://paste.ubuntu.com/p/MFyFDGmb4m/)

---

### Post by yancek on 2023-02-18
Check lines 31 and 68 in boot repair.  Is the flash drive you are using the same one you used to originally install Ubuntu?  Boot repair indicates it is not efi compatible yet your efi partition on the nvme drive where Ubuntu is installed shows Ubuntu files in the efi partition (nvme0n1p1).  Did you boot in efi mode?  Is the iso you put on the flash drive the correct one, efi capable?

You might try to add the Ubuntu entry manually by using efibootmgr.  The link below explains the process, just scroll down the page.  You will obviously need to make changes from the example:  disk changed from 'sda' to 'nvme0n1', label from 'fedora' to 'ubuntu' and replace fedora with ubuntu in the section after loader.  You may be able to use grubx64.efi instead of the shim entry.  If that fails, post back with any errors or warnings you get.

[https://linuxconfig.org/how-to-manage-efi-boot-manager-entries-on-linux](https://linuxconfig.org/how-to-manage-efi-boot-manager-entries-on-linux)

---

### Post by tea for one on 2023-02-18
Line 18 - Do you want to remove the [hidden] flag of nvme0n1p1 ?
Line 19 - parted /dev/nvme0n1 set 1 hidden off
Line 276 - nvme0n1p1	: hidenESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot

Boot-repair is reporting that the ESP has a hidden flag.
You can remove the flag with Gparted in a live session.

---

### Post by oldfred on 2023-02-18
Also line 38
> [COLOR=#ff0000]Windows Boot Manager    [/COLOR]HD(1,GPT,00428509-7f26-490f-bf9d-1184a23a9ba5,0x800,0x82000)/File([COLOR=#ff0000]EFIubuntugrub64.efi[/COLOR])WINDOWS

Your Windows entry is using grub to boot.
Years ago this was a work around for early UEFI systems that had to have "Windows Boot Manager" as boot entry and user only had Ubuntu installed.

New Lenovo's are UEFI only. Not sure if yours is or not.But you should only be using UEFI/gpt.
Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

You should delete current Windows entry using grub. Where XXXX is current entry:
sudo efibootmgr -b XXXX -B
Create new Windows entry using Windows boot files. This assumes default first partition
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
or if first partition must be specified since nmve drive.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/nvme0n1 -p 1

Create Ubuntu boot entry using shimx64.efi which is part of grub.
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

Details also are in link by tea for one.

also see 
man efibootmgr

this shows entries as shown in Boot-Repair report
To confirm entries:
sudo efibootmgr -v

---

### Post by jcp161 on 2023-02-20
The flash drive was not the same.  In fact I hastily made it thinking it  was of little importance other than accessing Linux tools.  Note:  I  redid it the live version and chose the formatting to GPT and booting  w/UEFI.  I did standard repair from boot-repair.  Also, got rid of  hidden flag but no improvement.  Updated Log attached.  Thanks for the help!

---

### Post by tea for one on 2023-02-20
Can you double check some UEFI settings:-
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

---

### Post by oldfred on 2023-02-20
Boot-Repair will not delete the incorrect Windows entry nor create a new Windows entry.

You should be able to use efibootmgr, but have to resolve the reason it cannot write into your UEFI. 
Check all the settings that tea for one suggests.

---

### Post by jcp161 on 2023-02-20
Good call on these things:  Device Guard was disabled.  I saw a referenc to TPM only on the security chip section.  I set it to disabled.  I did not see the OS Optimized stuff.  Still not working althought I noticed now in Gparted (after last round of boot-repair w/proper live version) I do now see EFI and boot flags on the first partition, which I believe is GRUB?  The damn thing still won't load the GRUB window to select the OS, and Ubuntu still doesn't show up in UEFI boot order at all.  I have a coworker with a similar Lenova who dual boots - followed same process as I did, shipped with Windows, add Ubuntu via USB flash drive.  In his setup he clearly sees Ubuntu as a boot option.  Additionally, his system does not show "Windows Boot Manager" which mine does.  Is it possible this was created erroneously when the motherboard first initialized and just needs to be deleted?

---

### Post by oldfred on 2023-02-20
Will system let you create new Windows entry as per post #4?
If so then delete old one.
And then see if it creates an Ubuntu entry.

Some Lenovo systems have this setting:
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
[https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots](https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots)

Even if new motherboard, do you have latest UEFI/BIOS from Lenovo?
Check in UEFI and then on Lenovo site for your specific model.

---

### Post by jcp161 on 2023-02-20
I admittedly was a little hesitant on some steps in #4 - was afraid to break by not fully understanding.  However, I just tried this step to at least see if I could see Ubuntu afterwards in UEFI.  Doing this was enough to correct the problem.

"Create Ubuntu boot entry using shimx64.efi which is part of grub.
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1"

I now get GRUB menu asking me if I want Ubuntu or Windows.  To all who answered, you have really saved me - THANK YOU SO MUCH!  I had WIP on ubuntu and really needed it to function again!

---

### Post by oldfred on 2023-02-20
It should be p 1 for first partition where ESP is.
I assume that was typo in post?

Can you also do Windows entry as it shows its trying to boot grub.

---

### Post by jcp161 on 2023-02-20
You were right, not sure how I got the extra "1" in the copy /paste but I fixed it in case any one refers to it in the future.  To be clear, my issue appears to be resolved.  You are asking me to execute the modification to the Windows listing from #4?

---

### Post by oldfred on 2023-02-20
Windows will not boot from UEFI with that entry as it has grub in it.
Grub may correctly boot Windows as it looks for the correct files in the ESP.

But grub only boots working Windows. 
And sometimes you have to directly boot Windows from UEFI boot menu not grub.
Windows may need chkdsk or turn fast start up back on or other Windows issues that prevent grub from booting it.

Best to always have both a Windows repair flash drive and the Ubuntu live installer for repairs.
And have good backups for worst case events.

---

