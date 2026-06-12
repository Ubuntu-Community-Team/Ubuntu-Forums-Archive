---
title: "Restoring Windows to Grub Boot Menu"
date: 2014-10-08
forum: New to Ubuntu
---

### Post by josephmcollardubu on 2014-10-08
I am trying to use boot-repair to restore windows to my grub boot menu. It was eliminated when I was trying out Fedora. I never got rid of the actual partitions /dev/sda2 through 6. I do think that the Fedora installer destroyed some boot portions that were required to have it show in the boot menu.

I've re-installed Ubuntu and created a boot-info script here: [http://paste.ubuntu.com/8522958/](http://paste.ubuntu.com/8522958/)

It looks like boot-repair might be able to fix this but I'm unsure how to proceed. The "recommended repair" option did not fix it. Looking throught he advanced options I'm not sure what would help / hurt the situation so I've come here.

Any help is appreciated!

In the "Other options" of boot-repair the "Repair Windows boot files" option is greyed out and I cannot select it.

---

### Post by yancek on 2014-10-08
sda1 is an EFI partition and I see Ubuntu and Fedora EFI files there which would indicate a GPT/UEFI installation.  In that case you would not need any Grub code in the master boot record and you do have that.  It looks like you have mixed and mbr install with UEFI which is a problem.  Hopefully, someone with a little more knowledge of UEFI/GPT will post.

---

### Post by grahammechanical on 2014-10-08
Please read though this wiki page and note this section,

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I have no experience with UEFI but taking a wild guess I would say that Windows 8 is installed in legacy mode and Fedora and Ubuntu in EFI mode. I see this comment in the Boot Repair report as a clue,

> [COLOR=#BB4444]Grub-efi will not be selected by default because: no-win-efi[/COLOR]

If you look at sda2 you will see efi files for Fedora and Ubuntu but not for Windows. And this could be because they did not exist in the first place because Windows was installed in legacy mode.  Just a guess.

I have no idea how to fix this.

Regards.

---

### Post by oldfred on 2014-10-08
Only because you have the 128MB Microsoft Reserved partition, do I think your Windows is UEFI not BIOS. 

Windows only boots from gpt with UEFI so drive would also have to have been converted from MBR to gpt which is possible but less likely.

Fedora also uses a separate /boot partition and installs with LVM. Unless using entire drive as LVM there is little advantage to LVM.

You then are missing the Windows boot folder in the efi partition and your efi partition somehow got converted from FAT32 to FAT16. It may work as UEFI does allow FAT16 for small external devices, but recommends FAT32 for internal hard drives. I would first back up entire efi partition, delete it and then recreate it with gparted, add boot flag which with gpt makes it the efi partition and restore all the boot files.

You should have a Windows repair flash drive to fix or add back the missing folder in the efi partition for Windows.

       /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

You also have refind and fedora, but need to run Windows repairs to restore the /EFI/Microsoft/Boot folder. You may be able to find a backup copy of bootmfgw.efi in Windows and use a third party Windows repair tool to recreate /BCD file.

From a grub menu you only can boot installs that are in the same boot mode. So if you boot grub in BIOS you can only boot other installs in BIOS boot mode. Since Windows is UEFI, then usually better to have all installs in UEFI boot mode.

---

