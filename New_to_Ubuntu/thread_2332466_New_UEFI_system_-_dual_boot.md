---
title: "New UEFI system - dual boot"
date: 2016-07-31
forum: New to Ubuntu
---

### Post by juren on 2016-07-31
I am experiencing similar issues trying to get 16.04 to work on a new UEFI AMD  PC running Windows 10.

Here's the dump I get from bootrepair:  [http://paste.ubuntu.com/21699547/](http://paste.ubuntu.com/21699547/)

Both the installation and rootrepair report that I am running in "legacy" even though I have downloaded the 64bit image of 16.04 which I thought was UEFI compatible.  Infact during the install I can see some EFI files being copied.

Any help would be appreciated.

Thanks,

Jim

---

### Post by oldfred on 2016-07-31
Moved to your own thread. Boot issues are almost always unique and your are not the same as thread you posted in. That is considered hijacking. And then thread can get confusing as we do not know who is posting about what issue.

You have installed Ubuntu in BIOS boot mode on gpt partitioned drive. But Windows is in UEFI boot mode.

How you boot install media  UEFI or BIOS is how it installs. You should have two choices in UEFO for flash drive UEFI:name and name (BIOS boot) where name is brand or label of flash drive. 

You can use Boot-Repair's advanced options to totally un-install grub-pc (BIOS) and install grub-efi-amd64(UEFI) to convert to UEFI boot. Make sure Internet is working as it has to download new copy of grub.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by juren on 2016-08-01
A major obstacle now appears to be turning off the UEFI Secure Boot.  

Early builds of Windows 10 have a "UEFI Firmware Settings" menu in the Settings >> Advanced area of Windows.  That menu seems to have been dropped from the latest builds of Win10.  

Is there a Plan B for turning off UEFI Secure Boot?

---

### Post by oldfred on 2016-08-01
UEFI Secure boot is a setting in UEFI, not in Windows.
And many systems now do not call it Secure boot, but just "Windows" or "other". But fine print often says if installing Windows 7 you must use "Other" as Windows 7 is not enabled for Secure boot.

This was from my Asus motherboard. Every UEFI is somewhat different.
And some do not open these settings unless you set a password in UEFI. But never lose that password or remove it after system fully configured.

Also make sure UEFI is most current version from vendor. And document all the changes you make in UEFI. I had many changes. And update to new UEFI resets to defaults so I have to redo my changes. So far within a year I have had 3 new UEFI versions.

---

