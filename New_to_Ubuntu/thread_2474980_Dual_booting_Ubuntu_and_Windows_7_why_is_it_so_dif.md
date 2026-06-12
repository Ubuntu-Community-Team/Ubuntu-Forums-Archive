---
title: "Dual booting Ubuntu and Windows 7: why is it so difficult?"
date: 2022-05-13
forum: New to Ubuntu
---

### Post by funonfourlegs on 2022-05-13
Hay everyone, new Linux user here!

So I've finally decided to dive into Linux and start off my journey with a dual boot setup on one of my desktop computers. Unfortunately, I'm off to a rather rocky start.

My goal is to get my 5-year old desktop to dual boot Windows 7 and Linux side by side. Originally I was set on Mint Cinnamon for an easier transition from the Windows world. Ubuntu was my runner up choice, and has become the number one choice as a consequence of my experiences with the Mint forums.

The stumbling block is this: after installing any Linux distribution, my computer absolutely refuses to give me the option to boot into it, recognizing only Windows as a valid OS. The boot menu never shows any OS besides Windows, and the BIOS menu never shows any Linux OS as an option. The desktop in question is an Acer Extensa that came shipped with Windows 7 Pro. I've tried all of the following, and keep in mind I only ever had one instance of Linux installed on my hard drive at a time:

* Made sure Linux was booting in UEFI mode, just like my Windows side is.
* Checked that the Linux distro and my Windows are both 64 bit.
* Installed Linux on my hard drive after manually partitioning plentiful free space, and setting up mount points for root and swap.
* Allowed Linux installer to make its own decisions for installing side by side with Windows.
* Installing Linux Mint on an external USB drive that I bought just for this purpose.
* Downloaded that Linux Boot Repair utility and employed it on both Mint and Ubuntu installations.
* Changed the BIOS settings in every way that seemed like it had even a remote chance of accomplishing something.
* Used bcdedit from the Windows side to try to make it boot the Mint OS (following someone's advice. This bricked my computer, and I had to reinstall Windows from the recovery partition to fix it).

I've spent a number of hours searching online for solutions, but everything I've encountered either didn't work, has impossible instructions (e.g. select menu options that don't exist in my BIOS), or contains lots of confusing shell commands that edit the boot partition (don't want to brick my system again!)

Has anyone else ever had this much trouble getting a simple dual boot setup? I really want to learn Linux and get away from being dependent on Windows. But I've hit a huge brick wall and cannot continue without help from someone with expertise, and perhaps a little patience. :redface: If anyone wants to throw me a life vest, it would be much appreciated!

---

### Post by Impavidus on 2022-05-13
5 years is quite young for a system than came with Windows 7 preinstalled, given that Windows 7 had already reached end of mainstream support by then. A reason not to use Windows 7 anymore, at least not on line.

With Windows in UEFI mode, Linux should be installed in UEFI mode too. You got that. Ubuntu works with secure boot on, but may require some tweaking and on some hardware it can get quite tricky, but I think Windows 7 doesn't even support secure boot, so I assume it's off anyway. But it may be good to check.

Next, use Windows partitioning tools to get unallocated space on the hard drive, reboot Windows to let it run its checks, then use the Linux live disk to create the Linux partitions. But my experience is that on older Windows versions, resizing the Windows partitions from the Linux live disk usually works. Then install Ubuntu and it's supposed to work.

You already found boot repair. Could you share the boot info summary with us? It may contain some useful details.

---

### Post by tea for one on 2022-05-13
> **Impavidus said:**
> You already found boot repair. Could you share the boot info summary with us? It may contain some useful details.
Yes, this is a good suggestion.

Have you backed-up your personal data?
Is Windows in hibernation?
Does your Acer PC have any Trust/Supervisor setting within UEFI?

---

### Post by grahammechanical on 2022-05-13
> The boot menu never shows any OS besides Windows,

What boot menu is this? Any Microsoft boot menu will not show any operating system other than a Microsoft OS. Linux uses a boot menu called Grub (GRand Unified Bootloader). Grub will detect Windows boot loaders and place an entry for them in its boot menu.

If the Grub boot menu is not appearing then it could be because Grub has not been installed or is not installed in the right place. The Ubuntu installation process will ask us to confirm a location where to install Grub. It should not be installed into a partition.

If the hard drive has a GPT partitioned table and Windows is installed in UEFI mode then there should be an EFI system partition (ESP) that will have the Windows boot files in it. That is the place to tell the Ubuntu installer to put the Grub boot files.

Regards

---

### Post by funonfourlegs on 2022-05-13
Although this Windows 7 machine does support secure boot, I turned it off early on in my dual booting quest. I just made sure and it is still off.

I already know how to create partitions; I made the initial free space partition while Windows is running. Each time I (re)installed Linux, I set up its partitions with the Linux installer.

So I just ran Boot Repair again. First there was a message that (incorrectly) stated "boot successfully repaired". Then the big data log:

```

boot-repair-4ppa125                                              [20220513_2224]


============================= Boot Repair Summary ==============================






/usr/share/boot-sav/bs-cmd_terminal.sh: line 177: warning: command substitution: ignored null byte in input
ping: google.com: Temporary failure in name resolution


Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda7,
using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file  restore-efi-backups




/boot/efi added in sda7/fstab
rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
Mount sda1 on /mnt/boot-sav/sda7/boot/efi


================= Reinstall the grub-efi-amd64-signed of sda7 ==================


grub-install --version
grub-install (GRUB) 2.06-2ubuntu7


efibootmgr -v from chroot before grub install
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0001,0004,0005,0000,0003
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,1ecadc8f-adb2-4e33-babe-d85e6bf9cc8c,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0003  ST500DM002-1BD142    BBS(HD,,0x0)..BO
Boot0004* UEFI: General USB Flash Disk 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,MBR,0xb02aa,0x800,0x1d19800)..BO
Boot0005* General USB Flash Disk 1100    BBS(HD,,0x0)..BO


uname -r
5.3.0-28-generic


grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda7/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bootx64.efi


grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.


efibootmgr -v from chroot after grub install
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0001,0004,0005,0000,0003
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,1ecadc8f-adb2-4e33-babe-d85e6bf9cc8c,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0003  ST500DM002-1BD142    BBS(HD,,0x0)..BO
Boot0004* UEFI: General USB Flash Disk 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,MBR,0xb02aa,0x800,0x1d19800)..BO
Boot0005* General USB Flash Disk 1100    BBS(HD,,0x0)..BO
Warning: NVram was not modified.


chroot /mnt/boot-sav/sda7 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-30-generic
Found initrd image: /boot/initrd.img-5.15.0-30-generic
Found linux image: /boot/vmlinuz-5.15.0-25-generic
Found initrd image: /boot/initrd.img-5.15.0-25-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi


Unhide GRUB boot menu in sda7/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.


Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04 LTS entry (sda1/EFI/ubuntu/shimx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.


If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi


============================ Boot Info After Repair ============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/grubx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/memtest.efi 
                       /efi/OEM/Boot/bootmgfw.efi /efi/OEM/Boot/bootmgr.efi 
                       /efi/OEM/Boot/memtest.efi


sda2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda7: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32800 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys




================================ 2 OS detected =================================


OS#1:   Ubuntu 22.04 LTS on sda7
OS#2:   Windows 7 on sda3


============================ Architecture/Host Info ============================


CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)




===================================== UEFI =====================================


BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled.


efibootmgr -v
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0001,0004,0005,0000,0003
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,1ecadc8f-adb2-4e33-babe-d85e6bf9cc8c,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0003  ST500DM002-1BD142    BBS(HD,,0x0)..BO
Boot0004* UEFI: General USB Flash Disk 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,MBR,0xb02aa,0x800,0x1d19800)..BO
Boot0005* General USB Flash Disk 1100    BBS(HD,,0x0)..BO


728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   sda1/Boot/fbx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda1/Boot/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/Boot/mmx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   sda1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
46fa9b43b373b3ff72acb627b2ba150b   sda1/Microsoft/Boot/bootmgfw.efi
69629f5ac8184ac29f442fb9d33d45a3   sda1/Microsoft/Boot/bootmgr.efi
9cdfbae08da935c0b9c77f01bb2807c6   sda1/OEM/Boot/bootmgfw.efi
c79876d32448cd0ec360d7660ea310d9   sda1/OEM/Boot/bootmgr.efi
92be7aa505b7ccc713bf1682c2af708a   sda5/Boot/bootx64.efi
9cdfbae08da935c0b9c77f01bb2807c6   sda5/Microsoft/Boot/bootmgfw.efi
c79876d32448cd0ec360d7660ea310d9   sda5/Microsoft/Boot/bootmgr.efi
44bc871d97c1ff326407ea5422586b95   sda5/Microsoft/Boot/cdboot.efi
bb4232c3623e3addb19d6a3df36d4580   sda5/Microsoft/Boot/cdboot_noprompt.efi




============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda4    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda5    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda7    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios


Partitions info (2/3): _________________________________________________________


sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot
sda7    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda3    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda4    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda5    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda7    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: A8322F7A-9173-4FBD-83B4-EF940CEEBC30
          Start       End   Sectors   Size Type
sda1       2048    206847    204800   100M EFI System
sda2     206848    239615     32768    16M Microsoft reserved
sda3     239616 548599807 548360192 261.5G Microsoft basic data
sda4  918568960 919592959   1024000   500M Windows recovery environment
sda5  919592960 976773119  57180160  27.3G Windows recovery environment
sda6  548599808 564600831  16001024   7.6G Linux swap
sda7  564600832 918568959 353968128 168.8G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 14.6 GiB, 15623782400 bytes, 30515200 sectors
Disk identifier: 0x000b02aa
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 30515199 30513152 14.6G  c W95 FAT32 (LBA)
Disk zram0: 479.6 MiB, 502910976 bytes, 122781 sectors
Disk zram1: 479.6 MiB, 502910976 bytes, 122781 sectors
Disk zram2: 479.6 MiB, 502910976 bytes, 122781 sectors
Disk zram3: 479.6 MiB, 502910976 bytes, 122781 sectors


parted -lm (filtered): _________________________________________________________


sda:500GB:scsi:512:4096:gpt:ATA ST500DM002-1BD14:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:281GB:281GB:ntfs:Basic data partition:msftdata;
6:281GB:289GB:8193MB:linux-swap(v1)::;
7:289GB:470GB:181GB:ext4::;
4:470GB:471GB:524MB:ntfs:Basic data partition:hidden, diag;
5:471GB:500GB:29.3GB:ntfs:Basic data partition:hidden, diag;
sdb:15.6GB:scsi:512:512:msdos:General USB Flash Disk:;
1:1049kB:15.6GB:15.6GB:fat32::boot, lba;
zram3:503MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:503MB:503MB:linux-swap(v1)::;
zram1:503MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:503MB:503MB:linux-swap(v1)::;
zram2:503MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:503MB:503MB:linux-swap(v1)::;
zram0:503MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:503MB:503MB:linux-swap(v1)::;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL             PARTLABEL
sda                                                                                                         
&#9500;&#9472;sda1 vfat     6043-CB3F                            1ecadc8f-adb2-4e33-babe-d85e6bf9cc8c ESP               EFI system partition
&#9500;&#9472;sda2                                               bfcb93e1-d403-40f6-92b6-5a0049f55cff                   Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     CA367DA2367D8FE5                     8e342960-1f32-464c-b248-c408e2eee1a6 Acer              Basic data partition
&#9500;&#9472;sda4 ntfs     0EA0A270A0A25E49                     5105168b-0768-41f5-886a-e3b1572262aa Recovery          Basic data partition
&#9500;&#9472;sda5 ntfs     0E2AC9BC2AC9A157                     559d03d2-50ad-4381-b264-141a2da554f7 Push Button Reset Basic data partition
&#9500;&#9472;sda6 swap     0f4bd64f-866b-4064-a618-d5a91946d976 e61965b0-ba29-4b71-9903-a28af5c1eaa7                   
&#9492;&#9472;sda7 ext4     05aef5c6-349a-4aae-8256-a3620346b456 1353a194-500f-4683-8256-93086fa3490b                   
sdb                                                                                                         
&#9492;&#9472;sdb1 vfat     B68C-E15D                            000b02aa-01                          BOOT-REPAIR       
zram0                                                                                                       
zram1                                                                                                       
zram2                                                                                                       
zram3                                                                                                       


df (filtered): _________________________________________________________________


       Avail Use% Mounted on
sda1    52.5M  45% /mnt/boot-sav/sda1
sda3   158.2G  39% /mnt/boot-sav/sda3
sda4   487.9M   2% /mnt/boot-sav/sda4
sda5     3.6G  87% /mnt/boot-sav/sda5
sda7   149.1G   5% /mnt/boot-sav/sda7
sdb1    13.7G   6% /cdrom


Mount options: __________________________________________________________________


sda1   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda3   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sda4   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sda5   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sda7   rw,relatime
sdb1   ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 05aef5c6-349a-4aae-8256-a3620346b456 root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda7/boot/grub/grub.cfg (filtered) ======================


Ubuntu   05aef5c6-349a-4aae-8256-a3620346b456
Ubuntu, with Linux 5.15.0-30-generic   05aef5c6-349a-4aae-8256-a3620346b456
Ubuntu, with Linux 5.15.0-25-generic   05aef5c6-349a-4aae-8256-a3620346b456
Windows Boot Manager (on sda1)   osprober-efi-6043-CB3F
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sda7/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=05aef5c6-349a-4aae-8256-a3620346b456 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
# swap was on /dev/sda6 during installation
UUID=0f4bd64f-866b-4064-a618-d5a91946d976 none            swap    sw              0       0
UUID=6043-CB3F  /boot/efi       vfat    defaults      0       1


======================= sda7/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


==================== sda7: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 391.356521606 = 420.215865344  boot/grub/grub.cfg                             1
 274.029834747 = 294.237294592  boot/vmlinuz                                   1
 272.535152435 = 292.632391680  boot/vmlinuz-5.15.0-25-generic                 2
 274.029834747 = 294.237294592  boot/vmlinuz-5.15.0-30-generic                 1
 272.535152435 = 292.632391680  boot/vmlinuz.old                               2
 275.053787231 = 295.336755200  boot/initrd.img                                1
 274.405372620 = 294.640525312  boot/initrd.img-5.15.0-25-generic              1
 275.053787231 = 295.336755200  boot/initrd.img-5.15.0-30-generic              1
 274.405372620 = 294.640525312  boot/initrd.img.old                            1


===================== sda7: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18683 Apr 15 21:50 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15 21:50 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15 21:50 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15 21:50 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15 21:50 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19 13:21 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15 21:50 40_custom
-rwxr-xr-x 1 root root   215 Apr 15 21:50 41_custom


=========================== sda7/etc/grub.d/35_fwupd ===========================


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


====================== sdb1/boot/grub/grub.cfg (filtered) ======================


Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)


========================= sdb1/syslinux.cfg (filtered) =========================


DEFAULT loadconfig


LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/


==================== sdb1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


================== sdb1: Location of files loaded by Syslinux ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1




=============================== StdErr Messages ================================


File descriptor 63 (pipe:[40270]) leaked on lvs invocation. Parent PID 1805: /bin/bash



```

---

### Post by funonfourlegs on 2022-05-13
> **tea for one said:**
> Yes, this is a good suggestion.

Have you backed-up your personal data?
Is Windows in hibernation?
Does your Acer PC have any Trust/Supervisor setting within UEFI?

My personal data is indeed backed up, don't worry.
I'm not activating hibernation when I turn off the computer.
Haven't seen any settings in the UEFI menu that would give me extra privileges, and I've dug through that menu like an archaeologist.

---

### Post by funonfourlegs on 2022-05-13
> **grahammechanical said:**
> What boot menu is this? Any Microsoft boot menu will not show any operating system other than a Microsoft OS. Linux uses a boot menu called Grub (GRand Unified Bootloader). Grub will detect Windows boot loaders and place an entry for them in its boot menu.

If the Grub boot menu is not appearing then it could be because Grub has not been installed or is not installed in the right place. The Ubuntu installation process will ask us to confirm a location where to install Grub. It should not be installed into a partition.

If the hard drive has a GPT partitioned table and Windows is installed in UEFI mode then there should be an EFI system partition (ESP) that will have the Windows boot files in it. That is the place to tell the Ubuntu installer to put the Grub boot files.

Regards

As you have pointed out, the menu I'm speaking of must be Microsoft's boot menu, and not GRUB. I must admit, I've been confused about where exactly GRUB is supposed to fit in within this whole picture, and how exactly the power on and boot up sequences have to be altered in order to support dual booting. The tutorials I've found online don't explain this very well.

Now, I'm a bit confused about what you're saying with GRUB and partitions. Your 2nd paragraph sounds like "don't put the GRUB booter in a partition", but your 3rd paragraph sounds like "DO place the GRUB booter inside the partition that contains the Windows boot files."

Am I taking something out of context?

---

### Post by grahammechanical on 2022-05-13
The installer will give us options where to put Grub. It will default to the front of the drive. This goes back to the days before UEFI systems. In the days of BIOS systems boot loaders were installed in the Master Boot Record (MBR) of the drive and not into a partition. The MBR was always at the front of the drive in a small amount of unallocated space before the first partition. So, selecting sda or nvme0n1 if the drive is an SSD on a UEFI system is not correct. In my opinion.

On UEFI systems it is true that Grub is installed into a partition but it is the special partition created for boot files - the EFI System Partition or ESM.  

For clarity nvme = non-volatile memory express. Second generation of Solid State Drive (SSD). nvme0n1p1 = first nvme drive and the first partition. Older SSD's show up as sda. I am guessing that the problem might be caused by Grub being installed to the default location and not to the ESM partition. Or we might be tempted to install Grub into the partition that Ubuntu is installed in. Some new users worry about mixing Ubuntu boot files with the Windows boot files. But this is not a problem as both coexist peacefully.

Regards

---

### Post by funonfourlegs on 2022-05-13
So, just to be 100% clear before I do anything... when setting up Linux partitions, there's that drop down menu that says

"Device for boot loader installation:"
which by default points to /dev/sda which means no partition is selected for its destination. So I'm going to change that and point it to the Windows EFI system partition, which on my machine is /dev/sda1.

Then what will happen is that GRUB will overwrite the stock Microsoft boot menu, but that doesn't matter because it will have become obsolete at this point.

All correct?

---

### Post by tea for one on 2022-05-14
You have used an old version of boot-repair [COLOR="#FF0000"]boot-repair-4ppa125[/COLOR].
Can you use a live session of Ubuntu, download the current version of boot-repair [COLOR="#0000FF"]4ppa200[/COLOR] and create a new report?
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)

---

### Post by nico-suricata on 2022-05-14
Hello funonfourlegs,


Maybe your bootloader needs to be 32bits and uefi ? 
About that, a linux Mint Topic is maybe a clue : 
The Acer Extensa 5630** "works fine with Mint 15 32-bit Cinammon**, but not with Mint 16 either Cinammon or KDE. When trying to boot from a 16 DVD it stalls just displaying the Mint logo. Any ideas?"
[https://forums.linuxmint.com/viewtopic.php?t=154093](https://forums.linuxmint.com/viewtopic.php?t=154093)


32 bits UEFI with 64 bits systems : 
[https://wiki.debian.org/UEFI](https://wiki.debian.org/UEFI)
« Support for mixed-mode systems: 64-bit system with 32-bit UEFI &#8212; Using the 32-bit UEFI x86 support, ... form) include the UEFI boot ... »


[https://linuxiumcomau.blogspot.com/2017/04/creating-personalized-ubuntu-mint-and.html](https://linuxiumcomau.blogspot.com/2017/04/creating-personalized-ubuntu-mint-and.html)
« the issue of requiring a 32-bit bootloader to boot a 64-bit OS arose »


Maybe switch the 64 bits bootloader with a 32 bits bootloader : 
[https://github.com/nguyentumine/AIO-Boot/blob/master/EFI/BOOT/grubia32.efi](https://github.com/nguyentumine/AIO-Boot/blob/master/EFI/BOOT/grubia32.efi)
I didn't test the file...


Hope that will help :-)


Kind regards


Nicolas
[URL="https://psathul.wordpress.com/2019/05/09/how-to-install-linux-on-32-bit-uefi-systemnetbooks/"]
https://psathul.wordpress.com/2019/05/09/how-to-install-linux-on-32-bit-uefi-systemnetbooks/[/URL]

---

### Post by yancek on 2022-05-14
More recent Acer computers require a Supervisor password to be created in the BIOS firmware and Trust to be enabled before it will boot other than the preinstalled OS which in your case if a UEFI install of windows 7.  I would first look for that option in the BIOS ffirmware, it may or may not be there but it is a simple thing to check.

If you look at the efibootmgr output near the top of the boot repair output, you will see that Ubuntu is listed as 0000 and windows as 0001.  With ubuntu as 0000, you should be able to change the order to 0000 to boot Ubuntu from the BIOS firmware.
  
If you look at the boot repair contents for sda1 at the top of the boot repair output, you also see the standard Ubuntu Grub boot files as well as the windows files.

If you leave the default for the bootloader install as sda, it should put the Ubuntu UEFI boot files in the EFI partition which you can see is what happened.  I think you can select the EFI partition (sda1) and it will do the same but I've never tried this although I've seen posts here that say it also works.

> Then what will happen is that GRUB will overwrite the stock Microsoft  boot menu, but that doesn't matter because it will have become obsolete  at this point.
 

No it won't.  If you mount sda1 from your live Ubuntu installer, you will see a directory there for windows which is called Microsoft and one for Ubuntu which is called ubuntu and they will contain the files for each OS to boot.

---

### Post by funonfourlegs on 2022-05-14
Update on what I've tried now:

* Set up a supervisor password in BIOS. All that did was make me enter passwords every time I accessed the Microsoft boot menu or enter BIOS mode.
* Installed Linux boot loader to sda1 (the partition with the Windows EFI thing). Still can't boot up Linux, so I...
* Then used the newer Boot Loader utility, boot-repair-4ppa200 to try to fix it.

The desktop still stubbornly refuses to allow a boot up into Ubuntu.

I'm afraid the material regarding 32-bit UEFI coexisting with 64-bit OS is a little above my level to go about trying stuff myself.

But here is the boot repair data dump, regardless:

```

boot-repair-4ppa200                                              [20220514_2149]


============================= Boot Repair Summary ==============================












Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda7,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups




rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
Mount sda1 on /mnt/boot-sav/sda7/boot/efi


Unhide GRUB boot menu in sda7/etc/default/grub


======================== Reinstall the grub-efi of sda7 ========================


chroot /mnt/boot-sav/sda7 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7
modprobe: FATAL: Module efivars not found in directory /lib/modules/5.3.0-28-generic
chroot /mnt/boot-sav/sda7 modprobe efivars


chroot /mnt/boot-sav/sda7 efibootmgr -v before grub install
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0001,0004,0005,0000,0003
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,1ecadc8f-adb2-4e33-babe-d85e6bf9cc8c,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0003  ST500DM002-1BD142    BBS(HD,,0x0)..BO
Boot0004* UEFI: General USB Flash Disk 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,MBR,0x4b51d37,0x800,0x1d19800)..BO
Boot0005* General USB Flash Disk 1100    BBS(HD,,0x0)..BO


chroot /mnt/boot-sav/sda7 uname -r
5.3.0-28-generic


chroot /mnt/boot-sav/sda7 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda7/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bootx64.efi


chroot /mnt/boot-sav/sda7 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.


chroot /mnt/boot-sav/sda7 efibootmgr -v after grub install
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0001,0004,0005,0000,0003
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,1ecadc8f-adb2-4e33-babe-d85e6bf9cc8c,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0003  ST500DM002-1BD142    BBS(HD,,0x0)..BO
Boot0004* UEFI: General USB Flash Disk 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,MBR,0x4b51d37,0x800,0x1d19800)..BO
Boot0005* General USB Flash Disk 1100    BBS(HD,,0x0)..BO
Warning: NVram was not modified.


chroot /mnt/boot-sav/sda7 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-30-generic
Found initrd image: /boot/initrd.img-5.15.0-30-generic
Found linux image: /boot/vmlinuz-5.15.0-25-generic
Found initrd image: /boot/initrd.img-5.15.0-25-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi


Unhide GRUB boot menu in sda7/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi




============================ Boot Info After Repair ============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/grubx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/OEM/Boot/bootmgfw.efi /efi/OEM/Boot/bootmgr.efi


sda2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda7: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32800 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys




================================ 2 OS detected =================================


OS#1:   Ubuntu 22.04 LTS on sda7
OS#2:   Windows 7 on sda3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller from Intel Corporation
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: R01-B0 from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to boot.repair@gmail.com.
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0001,0004,0005,0000,0003
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,1ecadc8f-adb2-4e33-babe-d85e6bf9cc8c,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0003  ST500DM002-1BD142    BBS(HD,,0x0)..BO
Boot0004* UEFI: General USB Flash Disk 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,MBR,0x4b51d37,0x800,0x1d19800)..BO
Boot0005* General USB Flash Disk 1100    BBS(HD,,0x0)..BO


728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   sda1/Boot/fbx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda1/Boot/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/Boot/mmx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   sda1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
46fa9b43b373b3ff72acb627b2ba150b   sda1/Microsoft/Boot/bootmgfw.efi
69629f5ac8184ac29f442fb9d33d45a3   sda1/Microsoft/Boot/bootmgr.efi
9cdfbae08da935c0b9c77f01bb2807c6   sda1/OEM/Boot/bootmgfw.efi
c79876d32448cd0ec360d7660ea310d9   sda1/OEM/Boot/bootmgr.efi
92be7aa505b7ccc713bf1682c2af708a   sda5/Boot/bootx64.efi
9cdfbae08da935c0b9c77f01bb2807c6   sda5/Microsoft/Boot/bootmgfw.efi
c79876d32448cd0ec360d7660ea310d9   sda5/Microsoft/Boot/bootmgr.efi
44bc871d97c1ff326407ea5422586b95   sda5/Microsoft/Boot/cdboot.efi
bb4232c3623e3addb19d6a3df36d4580   sda5/Microsoft/Boot/cdboot_noprompt.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda4    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda5    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda7    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios


Partitions info (2/3): _________________________________________________________


sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot
sda7    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda7    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: A8322F7A-9173-4FBD-83B4-EF940CEEBC30
          Start       End   Sectors   Size Type
sda1       2048    206847    204800   100M EFI System
sda2     206848    239615     32768    16M Microsoft reserved
sda3     239616 548599807 548360192 261.5G Microsoft basic data
sda4  918568960 919592959   1024000   500M Windows recovery environment
sda5  919592960 976773119  57180160  27.3G Windows recovery environment
sda6  548599808 564600831  16001024   7.6G Linux swap
sda7  564600832 918568959 353968128 168.8G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 14.6 GiB, 15623782400 bytes, 30515200 sectors
Disk identifier: 0x04b51d37
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 30515199 30513152 14.6G  c W95 FAT32 (LBA)
Disk zram0: 479.6 MiB, 502910976 bytes, 122781 sectors
Disk zram1: 479.6 MiB, 502910976 bytes, 122781 sectors
Disk zram2: 479.6 MiB, 502910976 bytes, 122781 sectors
Disk zram3: 479.6 MiB, 502910976 bytes, 122781 sectors


parted -lm (filtered): _________________________________________________________


sda:500GB:scsi:512:4096:gpt:ATA ST500DM002-1BD14:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:281GB:281GB:ntfs:Basic data partition:msftdata;
6:281GB:289GB:8193MB:linux-swap(v1)::;
7:289GB:470GB:181GB:ext4::;
4:470GB:471GB:524MB:ntfs:Basic data partition:hidden, diag;
5:471GB:500GB:29.3GB:ntfs:Basic data partition:hidden, diag;
sdb:15.6GB:scsi:512:512:msdos:General USB Flash Disk:;
1:1049kB:15.6GB:15.6GB:fat32::boot, lba;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL             PARTLABEL
sda                                                                                                         
&#9500;&#9472;sda1 vfat     6043-CB3F                            1ecadc8f-adb2-4e33-babe-d85e6bf9cc8c ESP               EFI system partition
&#9500;&#9472;sda2                                               bfcb93e1-d403-40f6-92b6-5a0049f55cff                   Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     CA367DA2367D8FE5                     8e342960-1f32-464c-b248-c408e2eee1a6 Acer              Basic data partition
&#9500;&#9472;sda4 ntfs     0EA0A270A0A25E49                     5105168b-0768-41f5-886a-e3b1572262aa Recovery          Basic data partition
&#9500;&#9472;sda5 ntfs     0E2AC9BC2AC9A157                     559d03d2-50ad-4381-b264-141a2da554f7 Push Button Reset Basic data partition
&#9500;&#9472;sda6 swap     daa79100-6c17-487b-818a-13a451898ed0 f7e3913b-fb8b-467f-9903-dd04b560c83d                   
&#9492;&#9472;sda7 ext4     7c197f24-3c40-498e-a3df-600b9703513e 91ba02ac-ca82-4a78-9152-a6fc97bcb76f                   
sdb                                                                                                         
&#9492;&#9472;sdb1 vfat     16A2-953A                            04b51d37-01                          BOOT-REPAIR       


Mount points (filtered): _______________________________________________________


            Avail Use% Mounted on
/dev/sda1    52.5M  45% /mnt/boot-sav/sda1
/dev/sda3   158.3G  39% /mnt/boot-sav/sda3
/dev/sda4   487.9M   2% /mnt/boot-sav/sda4
/dev/sda5     3.6G  87% /mnt/boot-sav/sda5
/dev/sda7   149.1G   5% /mnt/boot-sav/sda7
/dev/sdb1    13.7G   6% /cdrom


Mount options (filtered): ______________________________________________________


/dev/sda1   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda7   ext4            rw,relatime
/dev/sdb1   vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 7c197f24-3c40-498e-a3df-600b9703513e root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda7/boot/grub/grub.cfg (filtered) ======================


Ubuntu   7c197f24-3c40-498e-a3df-600b9703513e
Ubuntu, with Linux 5.15.0-30-generic   7c197f24-3c40-498e-a3df-600b9703513e
Ubuntu, with Linux 5.15.0-25-generic   7c197f24-3c40-498e-a3df-600b9703513e
Windows Boot Manager (on sda1)   osprober-efi-6043-CB3F
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sda7/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=7c197f24-3c40-498e-a3df-600b9703513e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=6043-CB3F  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda6 during installation
UUID=daa79100-6c17-487b-818a-13a451898ed0 none            swap    sw              0       0


======================= sda7/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda7: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 413.358131409 = 443.839913984  boot/grub/grub.cfg                             1
 273.779834747 = 293.968859136  boot/vmlinuz                                   1
 272.475154877 = 292.567969792  boot/vmlinuz-5.15.0-25-generic                 1
 273.779834747 = 293.968859136  boot/vmlinuz-5.15.0-30-generic                 1
 272.475154877 = 292.567969792  boot/vmlinuz.old                               1
 274.803787231 = 295.068319744  boot/initrd.img                                1
 274.155372620 = 294.372089856  boot/initrd.img-5.15.0-25-generic              1
 274.803787231 = 295.068319744  boot/initrd.img-5.15.0-30-generic              1
 274.155372620 = 294.372089856  boot/initrd.img.old                            1


===================== sda7: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18683 Apr 15 21:50 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15 21:50 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15 21:50 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15 21:50 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15 21:50 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19 13:21 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15 21:50 40_custom
-rwxr-xr-x 1 root root   215 Apr 15 21:50 41_custom


=========================== sda7/etc/grub.d/35_fwupd ===========================


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


====================== sdb1/boot/grub/grub.cfg (filtered) ======================


Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)


========================= sdb1/syslinux.cfg (filtered) =========================


DEFAULT loadconfig


LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/


==================== sdb1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


================== sdb1: Location of files loaded by Syslinux ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

```

---

### Post by funonfourlegs on 2022-05-14
Right now I just want to say that I really appreciate all of your efforts to help me out. I'm sorry my computer is so difficult. However, I will give Ubuntu a serious try whether or not I'm able to dual boot that one desktop.

Because it is not my only - or best - machine, I am willing to just wipe it clean and make it Linux only. I'll wait and see if we have more suggestions to try first now that I've posted an updated Boot Repair log.

I do have one question though: is it possible to have the Linux installer keep the Windows Recovery partitions intact while it reformats everything else? (If not, then to heck with it, I'll just wipe it clean).

---

### Post by tea for one on 2022-05-15
Not making much progress yet, but let's explore a bit more.

The boot-repair report is missing line numbers so I can't point to the exact location.

[COLOR="#0000FF"]modprobe: FATAL: Module efivars not found in directory /lib/modules/5.3.0-28-generic
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)[/COLOR]
You have installed Ubuntu 22.04 with kernel 5.15.0-30-generic, yet used Bionic with kernel 5.3.0-28 in your live boot-repair session. 
Generally, it is better to use the same live session as the installation. Whether this is crucial, I’m not sure. 
Worth trying again with a 22.04 live session?

[COLOR="#0000FF"]Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.[/COLOR]
Did you try this?

Another consideration, it is possible that Ubuntu 22.04 is not suitable for your PC and a lighter flavour (Lubuntu/Xubuntu) may be better.

Lastly, why do you wish to keep Windows 7 Recovery partitions?
Windows 7 has been unsupported since January 2020.
Rather than trying to retain the recovery partitions, you could:-
[LIST]
[*]Remove the Ubuntu partitions via Windows
[*]Run checkdisk
[*]Clone the drive using your preferred software.
[/LIST]

---

### Post by yancek on 2022-05-15
Setting the supervisor password and enabling trust was a guess on my part and doesn't appear to be the problem so you can simply remove/Clear it.

You should have  Boot Options in your BIOS boot menu which in turn should have an OS Boot Mgr option.  Do you see this and if there is an arrow to the left, there will be several options which should include Ubuntu.  Do you see this and have you tried booting this way?

If you want to keep the windows recovery partitions you can do that by using the manual (called Something Else in Ubuntu) install option and simply select the partitions you want to install to or unallocated space if you remove partitions. 

As suggested above, you should use the 22.04 usb (as that is what you installed) for boot repair and use the 2nd option described on the boot repair site as it is kept more up to date that the iso.

You indicate you cannot boot Ubuntu but haven't indicated what method you are using to try to boot it.  Selecting it from the BIOS firmware or Boot Options?

---

### Post by funonfourlegs on 2022-05-17
Some things came up that I have to take care of, but I'll try the latest round of suggestions in this thread as soon as I can. I'll report in to let you all know how it turns out.

---

### Post by harry101ca on 2022-05-23
Hi, I have been having the same issue with my computer, it started after installing version 22.04. I still haven't found a solution although I have been able to dual boot using the boot menu which is the F9 key on my HP computer. Once I enter the boot menu there is an option to boot to choose Ubuntu and also the windows bootloader.

---

### Post by oldfred on 2022-05-23
Acer typically required user to set "trust" in UEFI when Secure Boot is on. 
Often an "unknown" entry is created which then can be renamed to "ubuntu" and trust set.
Some have had to have UEFI updates to have correct UEFI settings. Make sure latest UEFI firmware from Acer is installed.

HP does not use "trust" but does not seem to recognized efibootmgr settings to set boot order.
With HP, then you have to go into UEFI settings (not menu) and change boot order there.
Again many have had to update UEFI firmware from HP.

Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)

---

### Post by funonfourlegs on 2022-05-28
Thought I should let you guys know how things turned out. I tried several of the newer suggestions, including getting the latest version of boot repair utility while in USB loaded Linux, then running it. Also, installing XUbuntu to see if the desktop handles a lighter OS better. And digging around in the BIOS menu even more.

The Acer desktop obstinantely refused to acknowledge the existence of Linux. But... I did make a good discovery by trying XUbuntu; it appears to be a better suited OS than regular Ubuntu (details at the end of this post **).

So, I decided to teach Windows a lesson. I revved Linux up and bulldozed the hard drive with it *. Deployed the auto-install and let Linux wipe everything clean and have its way with the drive. It's now a single-boot system and it actually loads up Linux, without any hassle. XUbuntu has got internet, functioning audio, gamepad and so on, and I've started installing Steam games and they are working as well as I'd expect for a system of this caliber. Some games need some special launch options or different versions of Proton to work correctly, but the Proton Database has proven to be useful for this task.

Thank you all for your assistance and for being patient with such a noob. Although I did not wind up with a dual boot setup, you guys did help me find a more suitable version of Ubuntu for my rig, and the discussion on this thread has given me better understanding of the technical aspects of these systems.


* If anyone's wondering why I didn't try to keep the Windows 7 partitions, it's because A) I didn't find any online tutorial that describes how to manually set up a proper boot loader partition for Linux installations, B) Windows 7 is outdated for programs I'll be running such as Parsec, and C) I created a Windows 7 system recovery DVD in case I want it in the future.

** Regular Ubuntu sometimes caused weird display glitches where my monitor would display all colors in various shades of blue. I tried a different monitor and everything was shades of red instead! Never heard of anything like that happening, and it seems to be a rare occurance. But XUbuntu doesn't give my old rig that problem, so it became the chosen OS. Although... now that I've got one version of Linux fully operational, I'm probably going to try other distros and see what works best for gaming. Preferably something related to Ubuntu in case I need advice from this community in the future. (And I probably will!)

---

