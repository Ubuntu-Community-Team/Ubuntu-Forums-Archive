---
title: "Unable to find Windows after attempting dual boot."
date: 2024-11-19
forum: New to Ubuntu
---

### Post by adiwaka2 on 2024-11-19
**Hello,**

[B]I tried to install ubuntu on my 2022 Acer Predator Helios 300 following the tutorial: [https://www.youtube.com/watch?v=mXyN1aJYefc&t=9s](https://www.youtube.com/watch?v=mXyN1aJYefc&t=9s)

I am unable to access windows now as I get an error that effectively says there is no access to the windows boot drive. Following other guides, I have tried "disk vol" and in the "X: Windows". I can only see two volumes, one at 255 GB and another at ~495 GB. The second one is just an additional NVME drive. 

I am able to access the windows C drive from inside Ubuntu is that helps. 

Pasted below is the text I got from Ubuntu Boot-repair tool. [/B]
```

boot-repair-4ppa2081                                              [20241119_1702]

============================== Boot Info Summary ===============================

 => Windows is installed in the MBR of /dev/nvme0n1.
 => Windows is installed in the MBR of /dev/nvme1n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/cbmr_driver.efi 
                       /efi/Microsoft/Boot/SecureBootRecovery.efi 
                       /efi/OEM/Boot/bootmgfw.efi /efi/OEM/Boot/bootmgr.efi

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme0n1p5: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p6: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p7: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme1n1p1: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme1n1p2: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


================================ 2 OS detected =================================

OS#1 (linux):   The OS now in use - Ubuntu 24.04.1 LTS on nvme0n1p7
OS#2 (windows):   Windows 10 or 11 on nvme0n1p4

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GA106M [GeForce RTX 3060 Mobile / Max-Q] Alder Lake-P GT2 [Iris Xe Graphics] from NVIDIA Corporation Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.8.0-41-generic root=UUID=539492ba-b8c5-4d27-819b-dbf3c9a94c42 ro quiet splash vt.handoff=7
df -Th / : /dev/nvme0n1p7 ext4   81G   12G   66G  16% /

===================================== UEFI =====================================

BIOS/UEFI firmware: V1.11(1.11) from Insyde Corp.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0001,2001,2002,2003
Boot0001* Windows Boot Manager    HD(1,GPT,5e3bcfea-2416-4ecd-9ea8-f725ea96069f,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000034000100000010000000040000007fff0400
Boot0002* ubuntu    HD(1,GPT,5e3bcfea-2416-4ecd-9ea8-f725ea96069f,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
nvme1n1    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    34 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p7    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p4    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme1n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p7    : isnotESP,    fstab-has-bad-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
nvme0n1p6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
nvme1n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, 
nvme0n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, 

Partitions info (3/3): _________________________________________________________

nvme0n1p7    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme1n1p2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
nvme0n1p5    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: 56FCA379-04AA-4F06-9926-9ABF7EFAE766
             Start        End   Sectors   Size Type
nvme0n1p1      2048     534527    532480   260M EFI System
nvme0n1p2    534528     536575      2048     1M Microsoft LDM metadata
nvme0n1p3    536576     567295     30720    15M Microsoft reserved
nvme0n1p4    567296  441231359 440664064 210.1G Microsoft LDM data
nvme0n1p5 614967296  998117375 383150080 182.7G Microsoft LDM data
nvme0n1p6 998117376 1000214527   2097152     1G Windows recovery environment
nvme0n1p7 441231360  614967295 173735936  82.8G Linux filesystem
Partition table entries are not in disk order.
Disk nvme1n1: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 29BF0BCF-87D6-4180-9184-AFE8E23FDC65
         Start       End   Sectors   Size Type
nvme1n1p1    34     32767     32734    16M Microsoft reserved
nvme1n1p2 32768 976771071 976738304 465.7G Microsoft basic data

parted -lm (filtered): _________________________________________________________

nvme0n1:512GB:nvme:512:512:gpt:Micron_3400_MTFDKBA512TFH:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, esp, no_automount;
2:274MB:275MB:1049kB::LDM metadata partition:;
3:275MB:290MB:15.7MB::Microsoft reserved partition:msftres, no_automount;
4:290MB:226GB:226GB:ntfs:LDM data partition:;
7:226GB:315GB:89.0GB:ext4::;
5:315GB:511GB:196GB::LDM data partition:;
6:511GB:512GB:1074MB:ntfs:Basic data partition:hidden, diag, no_automount;
nvme1n1:500GB:nvme:512:512:gpt:MSI M371 500GB:;
1:17.4kB:16.8MB:16.8MB::Microsoft reserved partition:msftres;
2:16.8MB:500GB:500GB:ntfs:Basic data partition:msftdata;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL      PARTLABEL
nvme0n1                                                                                                   
&#9500;&#9472;nvme0n1p1 vfat     2E8F-8838                            5e3bcfea-2416-4ecd-9ea8-f725ea96069f ESP        EFI system partition
&#9500;&#9472;nvme0n1p2                                               e1a423db-d95b-11ee-b025-d2baab529ff6            LDM metadata partition
&#9500;&#9472;nvme0n1p3                                               cc8f19c7-ef0c-4de6-8fcb-2eaef580669f            Microsoft reserved partition
&#9500;&#9472;nvme0n1p4 ntfs     F28C90258C8FE289                     7dd71d20-ae2f-4fa2-b3c5-c55995ecaed2 Acer       LDM data partition
&#9500;&#9472;nvme0n1p5                                               e108073f-a5ea-11ef-b051-4c034ff0262b            LDM data partition
&#9500;&#9472;nvme0n1p6 ntfs     D006907D0690666E                     c85d59f3-67e0-4c2d-8b8d-d068b6a69c00 Recovery   Basic data partition
&#9492;&#9472;nvme0n1p7 ext4     539492ba-b8c5-4d27-819b-dbf3c9a94c42 af195034-1e93-41ba-9cd5-a6632cc7efb7            
nvme1n1                                                                                                   
&#9500;&#9472;nvme1n1p1                                               9127c03f-fd45-4b40-b7ba-d1112579df3d            Microsoft reserved partition
&#9492;&#9472;nvme1n1p2 ntfs     84FCBEB5FCBEA0BA                     3979951e-3067-4b0e-af6f-95016bc51956 New Volume Basic data partition

Mount points (filtered): _______________________________________________________

                        Avail Use% Mounted on
/dev/nvme0n1p4            42G  80% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p6           289M  72% /mnt/boot-sav/nvme0n1p6
/dev/nvme0n1p7          65.2G  14% /
/dev/nvme1n1p2         143.1G  69% /mnt/boot-sav/nvme1n1p2
efivarfs                    0  99% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p4         fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p6         fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p7         ext4            rw,relatime
/dev/nvme1n1p2         fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 539492ba-b8c5-4d27-819b-dbf3c9a94c42 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p7/boot/grub/grub.cfg (filtered) ====================

Ubuntu   539492ba-b8c5-4d27-819b-dbf3c9a94c42
Windows Boot Manager (on nvme1n1p1)   osprober-efi-2E8F-8838
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p7/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p7 during curtin installation
/dev/disk/by-uuid/539492ba-b8c5-4d27-819b-dbf3c9a94c42 / ext4 defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 during curtin installation
/dev/disk/by-uuid/2E8F-8838 /boot/efi vfat defaults 0 1
/swap.img    none    swap    sw    0    0

==================== nvme0n1p7/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

================= nvme0n1p7: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 218.639785767 = 234.762682368  boot/grub/grub.cfg                             1
 254.145503998 = 272.886657024  boot/vmlinuz                                   2
 254.145503998 = 272.886657024  boot/vmlinuz-6.8.0-41-generic                  2
 254.145503998 = 272.886657024  boot/vmlinuz.old                               2
 287.645503998 = 308.857008128  boot/initrd.img                                2
 287.645503998 = 308.857008128  boot/initrd.img-6.8.0-41-generic               2
 287.645503998 = 308.857008128  boot/initrd.img.old                            2

=================== nvme0n1p7: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5  2024 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4  2024 40_custom
-rwxr-xr-x 1 root root   215 Apr  4  2024 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p7,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 24.04.1 LTS entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)

```

---

### Post by oldfred on 2024-11-19
How did you get this?
> Microsoft LDM data
That is Windows dynamic partitions, used with old BIOS systems as Windows work around for the old MBR(msdos) 4 primary partition limit.
But Since 2012, Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives. With gpt you have a soft limit of 128 primary partitions, user adjustable for more, if needed.

You show both drives as gpt, so Windows can only be booted in UEFI boot mode. But you have old Windows BIOS boot loaders in gpt's protective MBR. That will never work, but is ok to leave as never should be used. Just never try to boot in old BIOS mode as it will just crash.

Older links on LDM. Not sure if still valid as that was primarily a BIOS configuration and links are now old.
[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) & 
[https://packages.ubuntu.com/search?keywords=ldmtool](https://packages.ubuntu.com/search?keywords=ldmtool)
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)
[https://askubuntu.com/questions/1227285/how-can-i-mount-a-microsoft-ldm-partition-in-ubuntu-18-04-lts-desktop](https://askubuntu.com/questions/1227285/how-can-i-mount-a-microsoft-ldm-partition-in-ubuntu-18-04-lts-desktop)

---

### Post by adiwaka2 on 2024-11-20
Another clue if it helps, I was trying to see what disks were visible to windows, and attached is what it sees. 

```
(c) Microsoft Corporation. All rights reserved.
X:\Windows\System32>diskpart

Microsoft DiskPart version 10.0.22621.1
Copyright (C) Microsoft Corporation.

On computer:

MININT-FM23U4B
DISKPART> select disk
Disko is now the selected disk.
DISKPART> list vol

Volume ###
Ltr
C
Label
Fs
Type
Size
Status
Info
Volume
Volume 1
D
Acer
New Volume
NTFS
Simple
292 GB
Healthy
NTFS
Partition
465 GB
Healthy
DISKPART>

```

---

### Post by adiwaka2 on 2024-11-20
Thank you for the swift reply, I had to look up a lot of it as most of it flew over my head. I tried searching the provided links, one seems dead and the other's seem to need the recovery from registry, which i don't have (pardon me if that is not the case, I'm completely new here). I have updated the drives that windows command prompt is able to see. Please see if it clears something more up.

---

### Post by grahammechanical on 2024-11-20
I do not read long posts. I do read posts that have long printouts for diagnostic purposes enclosed in quote tags, By quote tags we mean - put at the start of the text the left square bracket followed by the words QUOTE followed by the right square bracket. Then at the end of the text put the left square bracket followed by a right leaning slash followed by the words QUOTE and then the right square bracket. Or, when typing the post click the voice bubble icon that is on the panel above the editing box. That will put the quote tags into your posts and then paste the text between the tags.

Am I to assume that you can load into Ubuntu? Then run this command in a terminal.

```
sudo update-grub
```

Watch the printout. Does it include a reference to the Windows OS?

Regards

---

### Post by ajgreeny on 2024-11-20
Please use **Code-Tags** not quote tags for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

I have no idea where that information listed in post #3 came from but I have removed much white space from it and used code tags for it on your behalf as I did in post #1.

---

### Post by yancek on 2024-11-20
Running sudo update-grub would probably be the first option to test.  If you can navigate to the /boot/grub/grub.cfg file, you can check to see if there is a windows entry.  Probably not and if not, you won't be able to boot windows from Grub.  Before running the sudo update-grub command, you might check the file /etc/default/grub to see if you have this line in it:

>  GRUB_DISABLE_OS_PROBER=false

If not put it there.  You will need to edit that file as root (using sudo) to save the change then run sudo update-grub.  You have the correct files for windows to boot on the EFI partition so if this fails, it might be the problem referred to by oldfred regarding dynamic partitions.  Good luck with that.

---

### Post by adiwaka2 on 2024-11-20
> **ajgreeny said:**
> Please use **Code-Tags** not quote tags for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

I have no idea where that information listed in post #3 came from but I have removed much white space from it and used code tags for it on your behalf as I did in post #1.

Thank you for doing that for me. It was informative to know that code-tags were needed, I will use them in the future if/when I have another issue. As for information in in post #3, it came from running the > diskpart then disk vol in the windows command prompt, which I was able to access through the advanced trouble shooting tools. I was not able to find how to paste pictures. 

Thank you for your time.

P.S: I have tried using the code-tag, I don't know how they will turn out yet. I have also tried attaching a picture of the above mentioned command prompt.

---

### Post by adiwaka2 on 2024-11-20
> **grahammechanical said:**
> I do not read long posts. I do read posts that have long printouts for diagnostic purposes enclosed in quote tags, By quote tags we mean - put at the start of the text the left square bracket followed by the words QUOTE followed by the right square bracket. Then at the end of the text put the left square bracket followed by a right leaning slash followed by the words QUOTE and then the right square bracket. Or, when typing the post click the voice bubble icon that is on the panel above the editing box. That will put the quote tags into your posts and then paste the text between the tags.

Am I to assume that you can load into Ubuntu? Then run this command in a terminal.

```
sudo update-grub
```

Watch the printout. Does it include a reference to the Windows OS?

Regards

Thank you for the reply and advice, I am trying to use the code-tags now. When I ran ```
sudo update-grub
```, I am pasting the output in code tags. I was able to see, at the end, that the windows boot manager is visible. 

```
 Sourcing file `/etc/default/grub'
Generating grub configuration file ...
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
Found linux image: /boot/vmlinuz-6.8.0-49-generic
Found initrd image: /boot/initrd.img-6.8.0-49-generic
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
Found linux image: /boot/vmlinuz-6.8.0-41-generic
Found initrd image: /boot/initrd.img-6.8.0-41-generic
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
Found Windows Boot Manager on /dev/nvme1n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
Adding boot menu entry for UEFI Firmware Settings ...
done

```

---

### Post by adiwaka2 on 2024-11-20
> **yancek said:**
> Running sudo update-grub would probably be the first option to test.  If you can navigate to the /boot/grub/grub.cfg file, you can check to see if there is a windows entry.  Probably not and if not, you won't be able to boot windows from Grub.  Before running the sudo update-grub command, you might check the file /etc/default/grub to see if you have this line in it:



If not put it there.  You will need to edit that file as root (using sudo) to save the change then run sudo update-grub.  You have the correct files for windows to boot on the EFI partition so if this fails, it might be the problem referred to by oldfred regarding dynamic partitions.  Good luck with that.

Thank you for replying. I have tried to do as asked, i uncommented the os prober. Then ran sudo update-grub again, got the same result as pasted in **grahammechanical **reply**. **How do I go about if the issues is the windows dynamic partitions?

---

### Post by adiwaka2 on 2024-11-20
> **oldfred said:**
> How did you get this?

That is Windows dynamic partitions, used with old BIOS systems as Windows work around for the old MBR(msdos) 4 primary partition limit.
But Since 2012, Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives. With gpt you have a soft limit of 128 primary partitions, user adjustable for more, if needed.

You show both drives as gpt, so Windows can only be booted in UEFI boot mode. But you have old Windows BIOS boot loaders in gpt's protective MBR. That will never work, but is ok to leave as never should be used. Just never try to boot in old BIOS mode as it will just crash.

Older links on LDM. Not sure if still valid as that was primarily a BIOS configuration and links are now old.
[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) & 
[https://packages.ubuntu.com/search?keywords=ldmtool](https://packages.ubuntu.com/search?keywords=ldmtool)
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)
[https://askubuntu.com/questions/1227285/how-can-i-mount-a-microsoft-ldm-partition-in-ubuntu-18-04-lts-desktop](https://askubuntu.com/questions/1227285/how-can-i-mount-a-microsoft-ldm-partition-in-ubuntu-18-04-lts-desktop)

I have no Idea what > Microsoft LDM data is, or how I got it. I am not able to boot into windows at all.

---

### Post by oldfred on 2024-11-20
This is an Ubuntu forum.
Some users dual boot, but for best Windows support better to use a Windows forum.

Can you boot Windows directly from UEFI boot menu? Most can boot from UEFI menu when grub does not.
Grub only boots working Windows and that means, no fast startup, no bitlocker and no errors requiring chkdsk.

If you cannot boot Windows from UEFI boot menu, you need to use your Windows repair/recovery flash drive or Windows installer with repair console.

---

### Post by yancek on 2024-11-20
The link below to the microsoft site contains the line below:

> Dynamic disks have been deprecated from Windows and are no longer recommended. Instead 

So I don't know how you got that setup unless you were updating from an old windows system.  The microsoft site explains the process and you do need to back everything up and delete and reformat the partitions for a new install and I would follow those steps as it is the official microsoft site.

[https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-dynamic-disk-back-to-a-basic-disk](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-dynamic-disk-back-to-a-basic-disk)

---

### Post by adiwaka2 on 2024-11-21
I have tried windows  recovery, but it does not work. I want to completely remove windows and  Ubuntu from my laptop and do a complete clean window reinstall. Any  advice regarding this would be really helpful.

---

### Post by Quarkrad on 2024-11-21
Have you a copy/backup of your personal data?  Might be a good time, if you haven't, to boot to a 'live cd' environment and scrape off your data onto a memory stick.

---

### Post by tea for one on 2024-11-21
> **adiwaka2 said:**
> I have tried windows  recovery, but it does not work. I want to completely remove windows and  Ubuntu from my laptop and do a [COLOR="#0000FF"]complete clean window reinstall[/COLOR]. Any  advice regarding this would be really helpful.
As mentioned by Quarkrad, your first priority is to back up your personal data.

Correct me if I'm wrong, but I get the impression that you only require Windows now.
Therefore, boot into the Windows installer and let it do its work.
You can remove all partitions during the Windows install process and, in effect, start from scratch.

---

### Post by adiwaka2 on 2024-11-21
I have access to the drives from linux. So i got the files, pds, pics, videos etc onto a pendrive. So I boot into windows installer and do install windows with no other steps in between?

---

### Post by yancek on 2024-11-21
If your intention is to simply use windows, then the windows installer should re-create whatever partitions it needs, format them to a windows filesystem and install.
If you only want windows, did you try to do a factory reset in the BIOS?

According to the link in my last post to the Microsoft site explaining converting from dyanmic to basic disks, it requires deleting the affected partitions.  This would of course not include the current boot partition so if you thing you might want to keep Ubuntu, you could leave that alone.  I don't see which windows version you are using but I know that windows 10 had a Custom install option where you could select partitions or unallocated space on which to install which would allow you to leave Ubuntu on the computer.  If all you want is to install windows, you would probably get better information at the microsoft site or some windows forums.  The link below gives a basic description of the process and their are numerous other sites with that information.  If you don't feel comfortable with this just overwrite everything.

  [https://www.hp.com/us-en/shop/tech-takes/how-to-install-windows-11-from-usb](https://www.hp.com/us-en/shop/tech-takes/how-to-install-windows-11-from-usb)

---

