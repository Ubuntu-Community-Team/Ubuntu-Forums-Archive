---
title: "UEFI Boot Issue Ubuntu 14.10 WIN 8.1 Sony Vaio"
date: 2015-03-21
forum: New to Ubuntu
---

### Post by karman2 on 2015-03-21
I try to get a dual boot installation to my pre-installed WIN 8.1. I disabled secure boot and installed Ubuntu from LiveCD. Installation passed successful. After restart bootmgr shows ubuntu but ubuntu won't start. Boot repair didn't help.
Excerpt of [http://paste.ubuntu.com/10647008/](http://paste.ubuntu.com/10647008/)
Who can help?


 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1356504 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

---

### Post by karman2 on 2015-03-22
The followin steps helped me:
Reboot your computer into Windows.
Open command prompt as administrator. Within the administrator's command prompt type the following command:

[FONT=courier new] bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
[/FONT]
After reboot grub started with several boot options including Windows and Ubuntu.
Both OS boot as desired now.
Solution is applicable for UEFI installation ONLY.

---

