---
title: "Software not functioning appropriately"
date: 2022-06-28
forum: New to Ubuntu
---

### Post by prodyoyo on 2022-06-28
Good morning

So my problem started when I updated my azuracast it broke and I tried to re run the container but it wasn’t running but I somehow did some changes to the computer using chmod and chown and lost some permissions. 

I regain sudo permissions through recovery mode and than I had Ubuntu stuck on a login loop. After that I fixed that issue by deleting some folders and repairing that loop but somehow now I try switching to another user account and I get a black screen also don’t have audio, something about creating a key than I removed the key issue but most applications don’t run. 

Tried running additional drivers app tried boot repair tried loading Google chrome. When running virtual machine manager I can see that my Ubuntu-guest is showing up as shutoff when it used to show up on I am able to run it but that’s not normal. 

I don’t have access to my Ubuntu server portal showing up error 500. I am running portainer, nginx proxy manager, tonido server, storage server, and docker all working right now besides the server

---

### Post by Impavidus on 2022-06-28
There's very little detail in your post. You ran chmod and chown, but on which files or directories? If you run those commands recursively on some system directories, fixing it is hopeless.

How did you regain sudo permissions exactly? What directories have you deleted to fix your login loop? Without such details, the only thing we can suggest is to restore your system from a backup. But it's very well possible that with such details, our suggestion won't change.

---

### Post by ajgreeny on 2022-06-28
I suspect that if you ran chmod and chown on files and folders not in your own home you will have very little option but to reinstall the complete system.

I had never heard of azuracast but see that it is a radio related suite.  On what files and folders did you run chown and chmod?

Tell us in a great deal more detail and we may be able to help but at present we are just guessing what may have gone wrong.

---

### Post by prodyoyo on 2022-06-28
This is what I get when I go into my system through ssh my computer right now is on but black screen I am able to do commands I will give more details once I remember but this message did not open up before like this 



The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Web console: [https://savagexradio.lan:9090/](https://savagexradio.lan:9090/) or [https://192.168.1.242:9090/](https://192.168.1.242:9090/)


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

---

### Post by Impavidus on 2022-06-29
Commands you run in your terminal get normally stored in ~/.bash_history (but duplicate commands may get stored only once and if you use multiple shells, they may not get stored in order). If you run a root shell, they get stored in /root/.bash_history. When you use sudo, this gets logged in /var/log/auth.log. If you can find the commands you ran, we might be able to help.

---

### Post by prodyoyo on 2022-06-29
This is goin to get interesting now I am now able to go in cockpit and see the logs and from the looks of it i see a couple of user services not starting automatic and also am unable to start them manuel 
[https://storage.savagexradio.com/api/public/dl/tNWX5Q0c?inline=true](https://storage.savagexradio.com/api/public/dl/tNWX5Q0c?inline=true)
[https://storage.savagexradio.com/api/public/dl/ePi-G1Ax?inline=true](https://storage.savagexradio.com/api/public/dl/ePi-G1Ax?inline=true)

---

### Post by prodyoyo on 2022-06-29
[https://paste.ubuntu.com/p/V9gFgfNJhF/](https://paste.ubuntu.com/p/V9gFgfNJhF/)

---

### Post by prodyoyo on 2022-06-30
Im still stuck this is the last boot repair i did. 


boot-repair-4ppa200                                              [20220630_0529]

============================= Boot Repair Summary ==============================

User choice:

Is there RAID on this computer? no



Default settings: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p2,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04 LTS entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !

User settings: _________________________________________________________________

grub-probe: error: cannot find a GRUB drive for /dev/sda2.  Check your device.map.
grub-probe: error: cannot find a GRUB drive for /dev/sda2.  Check your device.map.
Please backup your data before this operation.
The settings chosen by the user will reinstall the grub-efi of
nvme0n1p2,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed:  use-standard-efi-file rename-ms-efi restore-efi-backups repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

fsck -fyM /dev/nvme0n1p1
fsck from util-linux 2.37.2

fsck -fyM /dev/nvme0n1p2
fsck from util-linux 2.37.2

fsck -fyM /dev/mmcblk0p1
fsck from util-linux 2.37.2
rm /mnt/boot-sav/nvme0n1p1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/nvme0n1p1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/nvme0n1p1/efi/Boot/bootx64.efi
Mount nvme0n1p1 on /mnt/boot-sav/nvme0n1p2/boot/efi

===================== Reinstall the grub-efi of nvme0n1p2 ======================

chroot /mnt/boot-sav/nvme0n1p2 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7
modprobe: FATAL: Module efivars not found in directory /lib/modules/5.15.0-25-generic
chroot /mnt/boot-sav/nvme0n1p2 modprobe efivars

chroot /mnt/boot-sav/nvme0n1p2 efibootmgr -v before grub install
BootCurrent: 001F
Timeout: 2 seconds
BootOrder: 0000,001B,0010,0011,0012,0013,0014,0015,0020,001F,001A,0019,001C,001D,001E,0021,0022,0023,0001
Boot0000* ubuntu    HD(1,GPT,7b43e4a9-4c64-4f32-a65a-5320ce91ea68,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0001* Linux-Firmware-Updater    HD(1,GPT,a676f2ac-a321-408d-8fa3-2583bcb76867,0x800,0x100000)/File(EFIubuntufwupdx64.efi)
Boot0010  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Regulatory Information    FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
Boot0015  ThinkShield secure wipe    FvFile(3593a0d5-bd52-43a0-808e-cbff5ece2477)
Boot0016  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0017  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0018  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0019* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot001A* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot001B* NVMe0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001C* NVMe1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a401)
Boot001D* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot001E* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot001F* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot0020* PXE BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0021* LENOVO CLOUD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri([https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi](https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi))
Boot0022  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot0023  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0024* USBR BOOT CDROM    PciRoot(0x0)/Pci(0x14,0x0)/USB(15,1)
Boot0025* USBR BOOT Floppy    PciRoot(0x0)/Pci(0x14,0x0)/USB(15,0)
Boot0026* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0027* ATAPI CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)

chroot /mnt/boot-sav/nvme0n1p2 uname -r
5.15.0-25-generic

chroot /mnt/boot-sav/nvme0n1p2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/nvme0n1p1
touch /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi.grb
cp /mnt/boot-sav/nvme0n1p2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
df /dev/nvme0n1p1
touch /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Microsoft/Boot/bootx64.efi.grb
cp /mnt/boot-sav/nvme0n1p2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Microsoft/Boot/bootx64.efi
df /dev/nvme0n1p1
mv /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p2/boot/efi/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/nvme0n1p2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme0n1p2 efibootmgr -v after grub install
BootCurrent: 001F
Timeout: 2 seconds
BootOrder: 0000,001B,0010,0011,0012,0013,0014,0015,0020,001F,001A,0019,001C,001D,001E,0021,0022,0023,0001
Boot0000* ubuntu    HD(1,GPT,7b43e4a9-4c64-4f32-a65a-5320ce91ea68,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0001* Linux-Firmware-Updater    HD(1,GPT,a676f2ac-a321-408d-8fa3-2583bcb76867,0x800,0x100000)/File(EFIubuntufwupdx64.efi)
Boot0010  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Regulatory Information    FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
Boot0015  ThinkShield secure wipe    FvFile(3593a0d5-bd52-43a0-808e-cbff5ece2477)
Boot0016  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0017  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0018  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0019* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot001A* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot001B* NVMe0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001C* NVMe1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a401)
Boot001D* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot001E* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot001F* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot0020* PXE BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0021* LENOVO CLOUD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri([https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi](https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi))
Boot0022  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot0023  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0024* USBR BOOT CDROM    PciRoot(0x0)/Pci(0x14,0x0)/USB(15,1)
Boot0025* USBR BOOT Floppy    PciRoot(0x0)/Pci(0x14,0x0)/USB(15,0)
Boot0026* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0027* ATAPI CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Warning: NVram was not modified.

chroot /mnt/boot-sav/nvme0n1p2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-41-generic
Found initrd image: /boot/initrd.img-5.15.0-41-generic
Found linux image: /boot/vmlinuz-5.15.0-40-generic
Found initrd image: /boot/initrd.img-5.15.0-40-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
grub-probe: error: cannot find a GRUB drive for /dev/sda2.  Check your device.map.

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04 LTS entry (nvme0n1p1/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/mmcblk0.
 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,2)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    offsetio extcmd macho elf file setkey gettext boot bufio verifiers crypto 
    terminal normal datetime date mmap drivemap blocklist regexp archelp newc 
    vga_text relocator video chain ntldr search_label search_fs_file 
    search_fs_uuid search keylayouts at_keyboard pci usb usb_keyboard gcry_md5 
    hashsum gcry_crc gzio xzio lzopio lspci fshelp ext2 xfs acpi iso9660 
    gcry_sha1 div udf exfat font diskfilter raid6rec zstd btrfs ventoy read 
    halt video_fb vbe linux linux16 test true sleep reboot echo bitmap 
    bitmap_scale gfxterm trig video_colors gfxmenu videotest videoinfo 
    functional_test videotest_checksum video_cirrus video_bochs vga minicmd 
    help configfile tr biosdisk disk ls tar squash4 pbkdf2 gcry_sha512 
    password_pbkdf2 all_video png jpeg part_gpt part_msdos fat ntfs loopback 
    gfxterm_background procfs gfxterm_menu smbios
    ---------------------------------------------------------------------------

mmcblk0p1: _____________________________________________________________________

    File system:       exfat
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/fwupdx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootx64.efi

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda1: __________________________________________________________________________

    File system:       exfat
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: /dev/sda1 already mounted or mount point busy.

sda2: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda2 and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04 LTS on nvme0n1p2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: TU117GLM [Quadro T1000 Mobile] CometLake-H GT2 [UHD Graphics] from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: N2VET38W (1.23 )(1.23) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - SecureBoot disabled
Platform is in Setup Mode - Please report this message to [email]boot.repair@gmail.com[/email].
BootCurrent: 001F
Timeout: 2 seconds
BootOrder: 0000,001B,0010,0011,0012,0013,0014,0015,0020,001F,001A,0019,001C,001D,001E,0021,0022,0023,0001
Boot0000* ubuntu    HD(1,GPT,7b43e4a9-4c64-4f32-a65a-5320ce91ea68,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Linux-Firmware-Updater    HD(1,GPT,a676f2ac-a321-408d-8fa3-2583bcb76867,0x800,0x100000)/File(\EFI\ubuntu\fwupdx64.efi)
Boot0010  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Regulatory Information    FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
Boot0015  ThinkShield secure wipe    FvFile(3593a0d5-bd52-43a0-808e-cbff5ece2477)
Boot0016  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0017  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0018  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0019* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot001A* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot001B* NVMe0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001C* NVMe1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a401)
Boot001D* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot001E* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot001F* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot0020* PXE BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0021* LENOVO CLOUD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri([https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi](https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi))
Boot0022  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot0023  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0024* USBR BOOT CDROM    PciRoot(0x0)/Pci(0x14,0x0)/USB(15,1)
Boot0025* USBR BOOT Floppy    PciRoot(0x0)/Pci(0x14,0x0)/USB(15,0)
Boot0026* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0027* ATAPI CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)

728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/BOOT/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/BOOT/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   nvme0n1p1/BOOT/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme0n1p1/BOOT/mmx64.efi
1bab7d81b802f84554a4a678e8ac8258   nvme0n1p1/ubuntu/fwupdx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   nvme0n1p1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme0n1p1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/ubuntu/shimx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
f62c28d9b477b6a1a7b1c991b2b6637d   nvme0n1p1/Microsoft/Boot/bootx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
mmcblk0    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    mmc-disk, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
mmcblk0p1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
mmcblk0p1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
mmcblk0p1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    mmcblk0

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: C6D17135-1EB5-476E-9A03-5E948DD61B53
            Start       End   Sectors  Size Type
nvme0n1p1    2048   1050623   1048576  512M EFI System
nvme0n1p2 1050624 500117503 499066880  238G Linux filesystem
Disk mmcblk0: 116.48 GiB, 125068902400 bytes, 244275200 sectors
Disk identifier: 0x00000000
          Boot Start       End   Sectors   Size Id Type
mmcblk0p1      32768 244275199 244242432 116.5G  7 HPFS/NTFS/exFAT
Disk sda: 28.65 GiB, 30765219840 bytes, 60088320 sectors
Disk identifier: 0xa382c0fd
      Boot    Start      End  Sectors  Size Id Type
sda1  *        2048 60022783 60020736 28.6G  7 HPFS/NTFS/exFAT
sda2       60022784 60088319    65536   32M ef EFI (FAT-12/16/32)
Disk mapper/ventoy: 3.4 GiB, 3654957056 bytes, 7138588 sectors
Disk identifier: A09DB2B8-B5F6-43AE-AFB3-91E0A90189A1
                      Start     End Sectors  Size Type
mapper/ventoy-part1      64 7129427 7129364  3.4G Microsoft basic data
mapper/ventoy-part2 7129428 7137923    8496  4.1M EFI System
mapper/ventoy-part3 7137924 7138523     600  300K Microsoft basic data

parted -lm (filtered): _________________________________________________________

sda:30.8GB:scsi:512:512:msdos:SanDisk Cruzer Snap:;
1:1049kB:30.7GB:30.7GB:::boot;
2:30.7GB:30.8GB:33.6MB:fat16::esp;
mapper/ventoy:3655MB:dm:512:512:gpt:Linux device-mapper (linear):;
1:32.8kB:3650MB:3650MB::ISO9660:hidden, msftdata;
2:3650MB:3655MB:4350kB::Appended2:boot, esp;
3:3655MB:3655MB:307kB::Gap1:hidden, msftdata;
nvme0n1:256GB:nvme:512:512:gpt:SKHynix_HFS256GD9TNI-L2B0B:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:256GB:256GB:ext4::;
mmcblk0:125GB:sd/mmc:512:512:msdos:SD SD:;
1:16.8MB:125GB:125GB:::;

Free space >10MiB: ______________________________________________________________

mmcblk0: 0.00MiB:16.0MiB:16.0MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                                   
&#9500;&#9472;sda1      exfat    4E21-0000                            a382c0fd-01                          Ventoy                 
&#9474; &#9492;&#9472;ventoy                                                                                                            
&#9492;&#9472;sda2      iso9660  2022-04-19-10-23-19-00                                                    Ubuntu 22.04 LTS amd64 
mmcblk0                                                                                                               
&#9492;&#9472;mmcblk0p1 exfat    01C3-8800                                                                 BlockChain             
nvme0n1                                                                                                               
&#9500;&#9472;nvme0n1p1 vfat     FDAD-E8C7                            7b43e4a9-4c64-4f32-a65a-5320ce91ea68                        EFI System Partition
&#9492;&#9472;nvme0n1p2 ext4     1d0825e4-66b0-42c6-92a0-e1e6e4dc500a 6c09d149-91da-4c20-b40b-2565fe51a6f6                        

Mount points (filtered): _______________________________________________________

                        Avail Use% Mounted on
/dev/mapper/ventoy          0 100% /cdrom
/dev/mmcblk0p1         106.7G   8% /mnt/boot-sav/mmcblk0p1
/dev/nvme0n1p1         500.7M   2% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2         152.6G  29% /mnt/boot-sav/nvme0n1p2

Mount options (filtered): ______________________________________________________

/dev/mapper/ventoy     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8
/dev/mmcblk0p1         exfat           rw,relatime,fmask=0022,dmask=0022,iocharset=utf8,errors=remount-ro
/dev/nvme0n1p1         vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p2         ext4            rw,relatime

============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
ventoy

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 1d0825e4-66b0-42c6-92a0-e1e6e4dc500a root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p2/boot/grub/grub.cfg (filtered) ====================

Ubuntu   1d0825e4-66b0-42c6-92a0-e1e6e4dc500a
Ubuntu, with Linux 5.15.0-41-generic   1d0825e4-66b0-42c6-92a0-e1e6e4dc500a
Ubuntu, with Linux 5.15.0-40-generic   1d0825e4-66b0-42c6-92a0-e1e6e4dc500a
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p2/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=1d0825e4-66b0-42c6-92a0-e1e6e4dc500a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=FDAD-E8C7  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=01C3-8800 /BlockChain auto defaults 0 0

==================== nvme0n1p2/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
  86.759593964 = 93.157404672   boot/grub/grub.cfg                             1
   3.198799133 = 3.434684416    boot/vmlinuz                                   1
  86.269111633 = 92.630753280   boot/vmlinuz-5.15.0-40-generic                 1
   3.198799133 = 3.434684416    boot/vmlinuz-5.15.0-41-generic                 1
  86.269111633 = 92.630753280   boot/vmlinuz.old                               1
  85.665035248 = 91.982131200   boot/initrd.img                                4
 115.375972748 = 123.884007424  boot/initrd.img-5.15.0-40-generic              2
  85.665035248 = 91.982131200   boot/initrd.img-5.15.0-41-generic              4
 115.375972748 = 123.884007424  boot/initrd.img.old                            2

=================== nvme0n1p2: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Apr 15 21:50 10_linux
-rwxr-xr-x 1 root root 43031 Sep  2  2021 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15 21:50 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15 21:50 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15 21:50 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21 00:12 35_fwupd
-rwxr-xr-x 1 root root   214 Sep  2  2021 40_custom
-rwxr-xr-x 1 root root   215 Apr 15 21:50 41_custom

======================== nvme0n1p2/etc/grub.d/35_fwupd =========================

#! /bin/sh
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      . /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
    chainloader ${EFI_PATH}
}
EOF
      fi
fi

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

---

### Post by Impavidus on 2022-06-30
I don't know about azuracast. Apparently it's some sort web radio software. From your screenshots, it looks like you run it on some server, which you access remotely using some tool I don't know ("cockpit") running on an apple system. You didn't actually tell us. And you somehow messed up permissions. That's what we know now.

Boot-Repair can fix or at least diagnose issues with the boot loader. There's no indication you have a problem with the boot loader. So, if you can't tell us more about the way those permissions were messed up, we can't offer more suggestions than to restore your entire system from a backup or to reinstall. We pointed you to the bash history and the right log file where this information might be found.

---

