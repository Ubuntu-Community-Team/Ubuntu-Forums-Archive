---
title: "booting directly to windows in dual boot"
date: 2014-10-10
forum: New to Ubuntu
---

### Post by bimal_murali_c on 2014-10-10
hi, im a newbie and a noob in the ubuntu scenario , so appologies if im doing anything wrong by posting this.
i installed ubuntu 14.04 in my windows 8 pre installed hp pavillion notebook. it has 500gb hdd 4gb ram and amd a8 processor with radeon graphics. i partitioned 100gb to install ubuntu , disabled fast boot and secure boot, installed ubuntu by creating swap area, root and home partition. after that i selected the efi partition as the "device for boot loader installation" . installation went well but after restart system boots to windows, to boot ubuntu i have to use boot options on powerin on, ie grub is not loading by default. by reading many posts in forum i ran boot repair with recomended settings, but still no grub. 
boot repair returned  " an error occured during the repair"  and " [http://paste.ubuntu.com/8526793/](http://paste.ubuntu.com/8526793/) " . it also said that the boot file of ubuntu is far from the start of the disk, so bios may not detect it, and to make a partition with gparted. 
any help is appreciated. thank you.

---

### Post by yancek on 2014-10-10
You have Syslinux boot code in the master boot record of the primary drive which has windows and Ubuntu.  That's not right.
You have a separate EFI partition but all the files there are for windows, no Ubuntu files.
You don't need to disable Secure boot but you need to install Ubuntu in EFI mode.  I've read a number of posts which indicate that HP makes it more difficult.  I don't use EFI myself so you'll need to wait for someone else to make suggestions in that regard.

---

### Post by oldfred on 2014-10-10
You must have run a Boot-Repair in BIOS/CSM/Legacy mode. Only use UEFI mode to boot.

You do have ubuntu in efi partition along with many HP files.

Boot-Repair seems to pick up some minor errors and reports that but the important reinstall of grub is ok, error code 0 is no error.

 Reinstall the GRUB of sda7 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

I have yet to see a newer UEFI based system have the far from start of drive issue. More common on old BIOS or USB drives in BIOS boot mode.

HP's seem to modify UEFI to look for Windows and only boot Windows. You need one of several work arounds. Some seem to work better on some systems than others, but rename bootx64.efi or rEFInd seem to be two of the better choices.

 Reinstall the GRUB of sda7 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

---

### Post by bimal_murali_c on 2014-10-11
thanks for the reply olfred
i tried renaming efi boot via boot repair it gave me this reply:
An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/8538258/](http://paste.ubuntu.com/8538258/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

You can now reboot your computer.


The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
 
so shall i do the partition?
also i tried the bcdedit method , didnt changed anything :(
now booting to linux using f9 after powering on and selecting ubuntu in boot options.
thanks a ton for the reply

---

### Post by bimal_murali_c on 2014-10-11
thanks for the reply yancek :)

---

### Post by oldfred on 2014-10-11
Glad it is working.

Boot-Repair picks up some misc errors that are not critical and reports that. There is an error that the "CD" now DVD or flash is oversize for example.
The far from start of drive is mostly old BIOS, and some USB external drive issue. Not seen an UEFI system that needed partitions moved.

---

### Post by bimal_murali_c on 2014-10-11
i didnt get you, grub is still not showing, nothing i done made grub visible at boot
what to do? 
thanks ....

---

### Post by oldfred on 2014-10-11
If your grub menu is not showing is it that it has not found Windows? If only one system in menu, it does not show menu. You can usually force showing menu with escape key with UEFI or shift key with BIOS.

You can run this from Ubuntu, to add Windows to grub menu if both are UEFI.

sudo update-grub

---

### Post by bimal_murali_c on 2014-10-13
grub menu not showing as in the system directly boots to windows unless i press f9 as soon as i press the power button. then from boot option if i select ubuntu it goes to grub then boots to ubuntu . the grub shows windows no problem in there.
thanks old fred....

---

### Post by oldfred on 2014-10-13
Because HP only wants to default Boot Windows some rename files:

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Other work arounds that others have posted:

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)

Most seem to change bootx64.efi to really be grub and then HP will let you set hard drive as boot. Windows may regularly reset it in UEFI especially if you do any maintenance in Windows. But then you just have to in UEFI reset to hard drive.

---

### Post by bimal_murali_c on 2014-11-04
tried manually renaming files in microsoft folder, this made grub visible , and could boot to ubuntu from grub but, then windows option in grub is not working :( , now system will boot only to ubuntu. so i reverted the changes , and now back to square one :(

---

### Post by oldfred on 2014-11-04
Did you rename bootx64.efi and make it actually be grubx64.efi? Then boot hard drive entry. The bootx64.efi is usually works and boots to grub. Standard Windows entry in UEFI and in grub (from os-prober) should work if Windows is bootable.

If you rename the Windows efi file bootmfgw.efi to be grub, you still have to create a new boot stanza to boot the renamed actual Windows file. This is what Boot-Repair did when grub2's os-prober did not create a UEFI boot entry and you had to manually create one anyway. 
The disadvantage is that then you can only boot Windows from the grub custom entry. UEFI and grub2's os-prober entry are the standard Windows name which just loops back to grub. And Windows updates overwrite the renamed file and you are back to only booting Windows. And the version that is renamed may then be an old version, so you have to keep track.

---

