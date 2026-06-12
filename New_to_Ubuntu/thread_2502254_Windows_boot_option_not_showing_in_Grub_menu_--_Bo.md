---
title: "Windows boot option not showing in Grub menu -- Boot Info attached"
date: 2024-11-07
forum: New to Ubuntu
---

### Post by amar-mscb on 2024-11-07
Hi All,

I have a Lenovo G40 laptop. On this I recently installed Ubuntu 24.04.1 LTS version along with the previously installed Windows 10.

I followed the manual partitioning method for creating /root, /home, swap and other partitions while installing Ubuntu and I did NOT do anything to the Windows partitions except changing the mount point of "EFI system partition" to "/boot/efi" by following a guide on internet.

However, after installing the Ubuntu I do not get the option on Grub menu to boot into the Windows. Any help in fixing this issue will be much appreciated.

To be honest, I have very little knowledge about how the operating systems work although I have been a user of Ubuntu for many years for my works. In past I had successfully installed the previous version of Ubuntu on this laptop with dual boot with windows by following a similar procedure from internet guides.

Below I attach the "Boot info summary" generated on the laptop by running the "Boot repair" program

Many thanks in advance!
Amar

###########################################################################
###########################################################################

boot-repair-4ppa2081                                              [20241107_1450]

============================== Boot Info Summary ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda9: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


================================ 2 OS detected =================================

OS#1 (linux):   The OS now in use - Ubuntu 24.04.1 LTS on sda5
OS#2 (windows):   Windows 8 or 10 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: HD Graphics 5500 from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.8.0-48-generic root=UUID=1ff43d80-d7a6-47b9-b0be-896f374c981f ro quiet splash vt.handoff=7
df -Th / : /dev/sda5      ext4   92G   11G   76G  13% /

===================================== UEFI =====================================

BIOS/UEFI firmware: B0CNA0WW(1.170) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot enabled according to mokutil - Please report this message to [email]boot.repair@gmail.com[/email].
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,2003,2001,2002
Boot0000* EFI Network 0 for IPv4 (C8-5B-76-36-6F-10) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(c85b76366f10,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0001* EFI Network 0 for IPv6 (C8-5B-76-36-6F-10) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(c85b76366f10,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0003* ubuntu	HD(1,GPT,ae1d65ea-f03d-4af7-a98e-9aba530dd411,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi) File(.ä’)
Boot0004* ubuntu	HD(1,GPT,ae1d65ea-f03d-4af7-a98e-9aba530dd411,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi) File(.ä’)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda5	: is-os,	64, apt-get,	signed grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB
sda4	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda9	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda10	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda7	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda3	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda6	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB

Partitions info (2/3): _________________________________________________________

sda5	: isnotESP,	fstab-has-bad-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ext4
sda4	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot, ntfs
sda9	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, vfat
sda10	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ext4
sda7	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ext4
sda3	: isnotESP,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ntfs
sda1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, vfat
sda6	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ext4

Partitions info (3/3): _________________________________________________________

sda5	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda4	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda9	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda10	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda7	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda3	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda6	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 9339D128-51DF-4FDC-9767-B78649431F5A
          Start        End   Sectors   Size Type
sda1        2048     206847    204800   100M EFI System
sda2      206848     239615     32768    16M Microsoft reserved
sda3      239616  314085492 313845877 149.7G Microsoft basic data
sda4   518887424  519921663   1034240   505M Windows recovery environment
sda5   519921664  715235327 195313664  93.1G Linux filesystem
sda6   715235328 1105860607 390625280 186.3G Linux filesystem
sda7  1105860608 1301174271 195313664  93.1G Linux filesystem
sda8  1301174272 1308987391   7813120   3.7G Linux swap
sda9  1308987392 1953521663 644534272 307.3G Linux filesystem
sda10  314087424  518887423 204800000  97.7G Linux filesystem
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:512:gpt:ATA WD Blue SA510 2.:;
1:1049kB:106MB:105MB:fat16:EFI system partition:boot, esp, no_automount;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres, no_automount;
3:123MB:161GB:161GB:ntfs:Basic data partition:msftdata;
10:161GB:266GB:105GB:ext4::;
4:266GB:266GB:530MB:ntfs::hidden, diag, no_automount;
5:266GB:366GB:100GB:ext4::;
6:366GB:566GB:200GB:ext4::;
7:566GB:666GB:100GB:ext4::;
8:666GB:670GB:4000MB:linux-swap(v1)::swap;
9:670GB:1000GB:330GB:fat32::;

blkid (filtered): ______________________________________________________________

NAME    FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                              
â”œâ”€sda1  vfat     A00D-D3F7                            ae1d65ea-f03d-4af7-a98e-9aba530dd411       EFI system partition
â”œâ”€sda2                                                b283f7b8-4c3d-40e7-975e-54a6ea5c5bfb       Microsoft reserved partition
â”œâ”€sda3  ntfs     BEC65C4DC65C07D3                     1ed51435-a38d-4a9c-97be-e098b5eddc11       Basic data partition
â”œâ”€sda4  ntfs     EE647A7C647A477D                     a35aa546-3362-4c5f-84ad-4d5001e4a35e       
â”œâ”€sda5  ext4     1ff43d80-d7a6-47b9-b0be-896f374c981f cd4e7757-36a0-42d1-9ec6-e0e64d6edfb9       
â”œâ”€sda6  ext4     e99f6dcd-c2bd-4f82-a123-687a7eccfa80 a8d12010-740a-407c-bcca-1fadab64b893       
â”œâ”€sda7  ext4     386efdca-6d87-444d-8038-453eaef654a7 1e0c3131-d163-4ee2-9907-e34d1507c1fa       
â”œâ”€sda8  swap     d7230dee-0967-40b0-ba7b-2e9dd01cd420 fa53152b-d415-4b25-b1de-438df7edfe16       
â”œâ”€sda9  vfat     9F9A-1178                            8e14eef6-6511-42e9-9cfe-38b8f2655263       
â””â”€sda10 ext4     3349df53-a443-442c-8c99-6c955d73a30e 7fe41102-47b4-47d6-b5a4-5790009eeaaa       

Mount points (filtered): _______________________________________________________

                        Avail Use% Mounted on
/dev/sda10              90.7G   0% /confs
/dev/sda3              116.8G  22% /mnt/boot-sav/sda3
/dev/sda4               88.1M  83% /mnt/boot-sav/sda4
/dev/sda5               75.6G  12% /
/dev/sda6              159.1G   8% /home
/dev/sda7               86.4G   0% /BACKUP
/dev/sda9              307.3G   0% /VFAT
efivarfs                47.6K  47% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/sda10             ext4            rw,relatime
/dev/sda3              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5              ext4            rw,relatime
/dev/sda6              ext4            rw,relatime
/dev/sda7              ext4            rw,relatime
/dev/sda9              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 1ff43d80-d7a6-47b9-b0be-896f374c981f root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             vmlinuz-6.8.0-48-generic                       1

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   1ff43d80-d7a6-47b9-b0be-896f374c981f
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during curtin installation
/dev/disk/by-uuid/1ff43d80-d7a6-47b9-b0be-896f374c981f / ext4 defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
/dev/disk/by-uuid/A00D-D3F7 /boot/efi vfat defaults 0 1
# /home was on /dev/sda6 during curtin installation
/dev/disk/by-uuid/e99f6dcd-c2bd-4f82-a123-687a7eccfa80 /home ext4 defaults 0 1
# /BACKUP was on /dev/sda7 during curtin installation
/dev/disk/by-uuid/386efdca-6d87-444d-8038-453eaef654a7 /BACKUP ext4 defaults 0 1
# /VFAT was on /dev/sda9 during curtin installation
/dev/disk/by-uuid/9F9A-1178 /VFAT vfat defaults 0 1
# /confs was on /dev/sda10 during curtin installation
/dev/disk/by-uuid/3349df53-a443-442c-8c99-6c955d73a30e /confs ext4 defaults 0 1
/swap.img	none	swap	sw	0	0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 291.504035950 = 313.000075264  boot/grub/grub.cfg                             1
 262.970954895 = 282.362912768  boot/vmlinuz                                   1
 262.970954895 = 282.362912768  boot/vmlinuz-6.8.0-48-generic                  1
 262.970954895 = 282.362912768  boot/vmlinuz.old                               1
 258.658821106 = 277.732794368  boot/initrd.img                                1
 258.658821106 = 277.732794368  boot/initrd.img-6.8.0-48-generic               1
 258.658821106 = 277.732794368  boot/initrd.img.old                            1

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

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

The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
sda5,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

LegacyWindows detected. Please enable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB). 

Confirmation request before suggested repair: __________________________________

LegacyWindows detected. You may want to retry after deactivating the [Separate /boot/efi partition:] option.
Are you sure you want to continue anyway?

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 24.04.1 LTS entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !

---

### Post by oldfred on 2024-11-07
You need your Windows repair/recovery flash drive  or installer with repair tools. And booted in UEFI boot mode for UEFI repairs.
You show no Windows boot folder & files in the ESP.

You have an old BIOS boot loader of Windows in MBR that will never work. Not sure how you got that? That is why Boot-Repair says legacy Windows found. But rive is gpt, so Windows has to be installed in UEFI boot mode.

It looks like you reformatted the ESP to FAT16.
While FAT16 supposedly was allowed by UEFI for external drive, FAT32 is the standard.
Best to reformat your ESP, do total reinstall grub in UEFI mode with Boot-Repair's advanced mode and use Windows repairs to reinstall its boot loader.

---

### Post by yancek on 2024-11-07
I noticed a vfat partition (sda9) which seems to have no purpose.  Maybe created during the install of Ubuntu to be used as an EFI partition but since sda1 is an EFI partition and already existed, that was used.  I wondered why you had windows code in the MBR on a GPT disk since that won't work as pointed out above.  If the suggestions by oldfred do not work for some reason, may note of exactly what you did and post back.

---

