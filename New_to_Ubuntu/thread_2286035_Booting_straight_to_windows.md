---
title: "Booting straight to windows"
date: 2015-07-09
forum: New to Ubuntu
---

### Post by cyrus3 on 2015-07-09
Hello and i'm new to linux.

Anyways so i had windows 8.1 preinstalled and followed this tutorial: [http://www.tweaking4all.com/os-tips-and-tricks/uefi-dual-boot-windows81-ubuntu/](http://www.tweaking4all.com/os-tips-and-tricks/uefi-dual-boot-windows81-ubuntu/)    to install ubuntu alongside windows 8.1.

When i was done to test i shut down my pc and turned it back on but it went straight to windows. What gives?

---

### Post by oldfred on 2015-07-09
Did you go into UEFI and choose ubuntu entry? Does that boot?

What brand/model/video card/chip is your system?

Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by cyrus3 on 2015-07-09
I have an HP ENVY 17 Notebook PC

BIOS: Insyde F.65 2014-11-20

SMBIOS: 2.7

BIOS mode: UEFI

OS: Windows 8.1 6.3.9600 Build 9600 and also Ubuntu 15.04

I can go in bios and press f9 and then it shows all bootable mediums. I can select ubuntu from there but when i turn on the pc it doesnt show grub. Also there is no option in bios to change the bootable partiton. And a lot of options are grayed out.

---

### Post by limbenjamin on 2015-07-09
In your link ([http://www.tweaking4all.com/os-tips-and-tricks/uefi-dual-boot-windows81-ubuntu/](http://www.tweaking4all.com/os-tips-and-tricks/uefi-dual-boot-windows81-ubuntu/)), Step 7 shows you how to prevent it from happening. You might want to retry this step and do the boot repair.

[h=2]Step 7 &#8211; Getting Dual Boot Windows 8.x and Ubuntu to work[/h][FONT=abelregular]When we boot our computer at this point, it will go to Windows right away, which is not what you&#8217;d expect from &#8220;Dual Boot&#8221;. So we need to repair a few things.[/FONT][FONT=abelregular]If you screwed up and rebooted anyway: reboot your computer and boot from the Ubuntu USB stick.[/FONT]

---

### Post by oldfred on 2015-07-09
Boot-Repair used to do a rename of the Windows efi file to really boot grub/shim. But then Windows updates overwrite that rename, or grub updates to actual grub file to not update the copy in Windows. Or the fix only works for a short time.

Now either adding grub/shim to Windows BCD or copying grub into /EFI/Boot and renaming to bootx64.efi are suggestions. Both are work arounds and should not be required. Most HP systems have requried work arounds.

[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by cyrus3 on 2015-07-09
How do i get into efi partition?

---

### Post by oldfred on 2015-07-09
I thought several of the links showed details from Ubuntu live installer.

I copied this from the link in my signature below.

From live installer mount the efi partition on hard drive, lines with #  are comments only: Mount efi partition. check which partition is FAT32  with boot flag. Often sda1 or sda2 but varies.

        sudo mount /dev/sda1 /mnt
    
    only if /EFI/Boot not already existing, run the mkdir command,
        sudo mkdir /mnt/EFI/Boot
        sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
    
    # If new folder created, the bootx64.efi will not exist, skip backup command
    sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
    # make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
    sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi
# You may need new hard drive entry:
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
# confirm entries:
sudo efibootmgr -v

---

