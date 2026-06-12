---
title: "Fails to boot after installing nvidia drivers after Ubuntu 22.04"
date: 2023-11-30
forum: New to Ubuntu
---

### Post by asimovjr on 2023-11-30
Whenever I install nvidia driver, I can't reboot. Ubuntu gets stuck on the load screen. Then I have to use recovery mode root to purge nvidia for ubuntu to work. But again when I install Nvidia driver the problem repeats itself.
I ran the boot-repair too, here the report, [https://paste.ubuntu.com/p/NPyckGMDHW/](https://paste.ubuntu.com/p/NPyckGMDHW/)

```

boot-repair-4ppa2056                                              [20231130_1314]


============================= Boot Repair Summary ==============================










modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-37-generic
ls: cannot access '/sys/firmware/efi/vars': No such file or directory


Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p5,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file




nvme0n1p5/boot/efi not empty


Unhide GRUB boot menu in nvme0n1p5/etc/default/grub


===================== Reinstall the grub-efi of nvme0n1p5 ======================


grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-37-generic
modprobe efivars


efibootmgr -v before grub install
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000
Boot0000* Windows Boot Manager    HD(1,GPT,1ed7d016-3c9e-476e-8f81-4603bf895847,0x800,0x82000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,GPT,1ed7d016-3c9e-476e-8f81-4603bf895847,0x800,0x82000)/File(EFIUBUNTUSHIMX64.EFI)


uname -r
6.2.0-37-generic


grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/nvme0n1p1
mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.efi
cp /boot/efi/efi/ubuntu/grubx64.efi /boot/efi/EFI/Boot/bootx64.efi


grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.


efibootmgr -v after grub install
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000
Boot0000* Windows Boot Manager    HD(1,GPT,1ed7d016-3c9e-476e-8f81-4603bf895847,0x800,0x82000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,GPT,1ed7d016-3c9e-476e-8f81-4603bf895847,0x800,0x82000)/File(EFIubuntushimx64.efi)


update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-37-generic
Found initrd image: /boot/initrd.img-6.2.0-37-generic
Found linux image: /boot/vmlinuz-6.2.0-36-generic
Found initrd image: /boot/initrd.img-6.2.0-36-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...


Unhide GRUB boot menu in nvme0n1p5/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (nvme0n1p1/efi/ubuntu/grubx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi




============================ Boot Info After Repair ============================


 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => libparted MBR boot code is installed in the MBR of /dev/sda.


nvme0n1p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/cbmr_driver.efi


nvme0n1p2: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme0n1p3: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe


nvme0n1p4: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


nvme0n1p5: _____________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        




================================ 2 OS detected =================================


OS#1:   Ubuntu 22.04.3 LTS on nvme0n1p5
OS#2:   Windows 10 or 11 on nvme0n1p3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: GA107M [GeForce RTX 3050 Mobile] TigerLake-H GT1 [UHD Graphics] from NVIDIA Corporation Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.2.0-37-generic root=UUID=04dd6f3f-7624-4c40-9cc3-409aa89576d5 ro quiet splash vt.handoff=7
df -Th / : /dev/nvme0n1p5 ext4  228G  137G   80G  64% /


===================================== UEFI =====================================


BIOS/UEFI firmware: FX506HCB.313(5.19) from American Megatrends International, LLC.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000
Boot0000* Windows Boot Manager    HD(1,GPT,1ed7d016-3c9e-476e-8f81-4603bf895847,0x800,0x82000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,GPT,1ed7d016-3c9e-476e-8f81-4603bf895847,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)




============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sda    : notGPT,    no-BIOSboot,    has-noESP,     usb-disk,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


nvme0n1p5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


nvme0n1p5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


nvme0n1p5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: D046E12B-3BC6-44CE-8896-4B40A93E0C4F
              Start        End   Sectors   Size Type
nvme0n1p1      2048     534527    532480   260M EFI System
nvme0n1p2    534528     567295     32768    16M Microsoft reserved
nvme0n1p3    567296  294306446 293739151 140.1G Microsoft basic data
nvme0n1p4 294307840  513110015 218802176 104.3G Microsoft basic data
nvme0n1p5 513110016 1000214527 487104512 232.3G Linux filesystem
Disk sda: 28.9 GiB, 31029460992 bytes, 60604416 sectors
Disk identifier: 0x452cecf6
      Boot Start      End  Sectors  Size Id Type
sda1        2048 60604415 60602368 28.9G  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:31.0GB:scsi:512:512:msdos:hp x765w:;
1:1049kB:31.0GB:31.0GB:fat32::lba;
nvme0n1:512GB:nvme:512:512:gpt:INTEL SSDPEKNU512GZ:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:151GB:150GB:ntfs:Basic data partition:msftdata;
4:151GB:263GB:112GB:ntfs:Basic data partition:msftdata;
5:263GB:512GB:249GB:ext4::;


blkid (filtered): ______________________________________________________________


NAME        FSTYPE   UUID                                 PARTUUID                             LABEL      PARTLABEL
sda                                                                                                       
&#9492;&#9472;sda1      vfat     BE05-D694                            452cecf6-01                          PD         
nvme0n1                                                                                                   
&#9500;&#9472;nvme0n1p1 vfat     3CF3-8F61                            1ed7d016-3c9e-476e-8f81-4603bf895847 SYSTEM     EFI system partition
&#9500;&#9472;nvme0n1p2                                               b94ab024-0e9e-4a62-a875-e8811f7f9820            Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     E6CEF569CEF53283                     9aac859f-cfa9-4fea-a987-b3d8e27cb0d2 OS         Basic data partition
&#9500;&#9472;nvme0n1p4 ntfs     9050082F50081F1A                     5babdddb-f361-42b2-96c5-2cad5b0b781a New Volume Basic data partition
&#9492;&#9472;nvme0n1p5 ext4     04dd6f3f-7624-4c40-9cc3-409aa89576d5 8c36e115-cb9e-4e99-8e8a-bf5fa72a48f1            


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/nvme0n1p3            54G  61% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4          68.3G  35% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5          79.5G  60% /
/dev/sda1               28.5G   1% /media/harsh/PD


Mount options (filtered): ______________________________________________________




=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================


search.fs_uuid 04dd6f3f-7624-4c40-9cc3-409aa89576d5 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


=================== nvme0n1p5/boot/grub/grub.cfg (filtered) ====================


Ubuntu   04dd6f3f-7624-4c40-9cc3-409aa89576d5
Ubuntu, with Linux 6.2.0-37-generic   04dd6f3f-7624-4c40-9cc3-409aa89576d5
Ubuntu, with Linux 6.2.0-36-generic   04dd6f3f-7624-4c40-9cc3-409aa89576d5
Windows Boot Manager (on nvme0n1p1)   osprober-efi-3CF3-8F61
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


======================== nvme0n1p5/etc/fstab (filtered) ========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=04dd6f3f-7624-4c40-9cc3-409aa89576d5 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=3CF3-8F61  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


==================== nvme0n1p5/etc/default/grub (filtered) =====================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


================= nvme0n1p5: Location of files loaded by Grub ==================


           GiB - GB             File                                 Fragment(s)
 288.021675110 = 309.260918784  boot/grub/grub.cfg                             1
 284.534332275 = 305.516412928  boot/vmlinuz                                   1
 404.646480560 = 434.485850112  boot/vmlinuz-6.2.0-36-generic                  2
 284.534332275 = 305.516412928  boot/vmlinuz-6.2.0-37-generic                  1
 404.646480560 = 434.485850112  boot/vmlinuz.old                               2
 390.044918060 = 418.807541760  boot/initrd.img                                4
 404.164428711 = 433.968250880  boot/initrd.img-6.2.0-36-generic               5
 390.044918060 = 418.807541760  boot/initrd.img-6.2.0-37-generic               4
 404.164428711 = 433.968250880  boot/initrd.img.old                            5


=================== nvme0n1p5: ls -l /etc/grub.d/ (filtered) ===================


-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 16  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom
```

---

### Post by grahammechanical on 2023-11-30
Boot Repair does not fix boot problems caused by proprietary video drivers. The video driver does not load until after the Grub boot loader has done its job.

Advanced Options for Ubuntu>Recovery mode>Resume will load to a login screen using an open source video driver.

How are you installing this Nvidia driver? Is it through Software and Updates>Additional Drivers tab?

What video card do you have? Nvidia usually stops providing video drivers for its video cards that have become old. I have found that the open source video driver has progressed sufficiently to be a useful alternative for proprietary video drivers.

Regards

---

### Post by ajgreeny on 2023-11-30
To help us help you please run command
**inxi -Fzx**
in terminal and copy back here the complete output using Code Tags

See my signature below for a **how-to ** on code tags.

---

### Post by Yellow Pasque on 2023-12-02
> **grahammechanical said:**
> What video card do you have?

Looks like an Intel/Nvidia Hybrid (Optimus) setup:
```
Video: GA107M [GeForce RTX 3050 Mobile] TigerLake-H GT1 [UHD Graphics] from NVIDIA Corporation Intel Corporation
```

---

### Post by MAFoElffen on 2023-12-04
Next time you suspect you have a booting problem, which this time you do not (wrong nomenclature)... Run the boot-info script without running the repair itself. With what the boot-repiar information said, you actually tried to repair it! When there is a problem, please have us take a look at the report, before doing a repair.

Next, what is happening is that it is booting, but not loading the Graphics layer, and drivers, as you noted. Therefore not a booting problem. Using the right tools for the job, would have been to run the UbuntuForums 'system-info' script in my signature line, and post the URL where the report uploaded, with has an endepth sections on reporting graphics hardware, diaply capabilities, and it the GPU's have drivers loaded.

But you already have given almost enough information to go off of...

What is missing is the complete picture of what you have done and what happens... Such as which versions of NVidia drivers have you tried? next, what make & model of laptop is it?

Why do I ask that? Because that Perfect storm combination of both Nvidia GPU and Intel iGPU does have some quarks were it only works with "some" NVidia driver versions... Next, which version of Ubuntu are you running? Because in a certain range of kernels, the opensource nouveau driver is broken for that GPU. Next that combination does work best if you use X11, instead of Wayland for your graphics engine.

A lot of those details would have been answered if you ran the system-info report. But no matters. Please fill in the blanks.

---

