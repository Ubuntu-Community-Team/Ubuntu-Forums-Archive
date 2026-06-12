---
title: "cant boot without live usb"
date: 2024-04-21
forum: New to Ubuntu
---

### Post by christan22 on 2024-04-21
[LIST]
[*] 
[/LIST]


Hey sorry if this basic but having an issue booting and cant find a clear answer searching, could anyone advise please ?

```
*boot-repair-4ppa2075                                              [20240421_0634]*

*============================== Boot Info Summary ===============================*

* => No boot loader is installed in the MBR of /dev/nvme0n1.*

*nvme0n1p1: _____________________________________________________________________*

*    File system:       vfat*
*    Boot sector type:  FAT32*
*    Boot sector info:  No errors found in the Boot Parameter Block.*
*    Operating System:  *
*    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi *
*                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi *
*                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg*

*nvme0n1p2: _____________________________________________________________________*

*    File system:       BIOS Boot partition*
*    Boot sector type:  -*
*    Boot sector info: *

*sda: ___________________________________________________________________________*

*    File system:       iso9660*
*    Boot sector type:  Grub2 (v1.99-2.00)*
*    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of *
*                       sda and looks at sector 0 of the same hard drive for *
*                       core.img, but core.img can not be found at this *
*                       location.*
*    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.*


*================================ 1 OS detected =================================*

*OS#1:   Ubuntu 23.10 on nvme0n1p2*

*================================ Host/Hardware =================================*

*CPU architecture: 64-bit*
*Video: GA106M [GeForce RTX 3060 Mobile / Max-Q] Alder Lake-P Integrated Graphics Controller from NVIDIA Corporation Intel Corporation*
*Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)*

*===================================== UEFI =====================================*

*BIOS/UEFI firmware: E1583IMS.10F(1.15) from American Megatrends International, LLC.*
*The firmware is EFI-compatible, and is set in EFI-mode for this live-session.*
*SecureBoot enabled according to mokutil - Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].*
*BootCurrent: 0002*
*Timeout: 1 seconds*
*BootOrder: 0002,0001*
*Boot0001* ubuntu    HD(1,GPT,08129701-36f7-8447-8fec-d6a94b020494,0x1000,0x96000)/File(\EFI\UBUNTU\SHIMX64.EFI)*
*Boot0002* UEFI:  USB, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,GPT,abe6d9c1-d820-473f-9624-5e7897c4c498,0x938b58,0x2754)..BO*

*925029921cfc9e40f54f55d4cffbdd49   nvme0n1p1/BOOT/fbx64.efi*
*857e495f63f23c842e2b074e692b6e3a   nvme0n1p1/BOOT/mmx64.efi*
*1d99ff510dac8535d215797ad5e69230   nvme0n1p1/ubuntu/grubx64.efi*
*857e495f63f23c842e2b074e692b6e3a   nvme0n1p1/ubuntu/mmx64.efi*
*64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi*
*64349b3622c65f495a99dbf6102496e3   nvme0n1p1/BOOT/BOOTX64.efi*

*============================= Drive/Partition Info =============================*

*Disks info: ____________________________________________________________________*

*nvme0n1    : is-GPT,    hasBIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes*

*Partitions info (1/3): _________________________________________________________*

*nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far*

*Partitions info (2/3): _________________________________________________________*

*nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot*

*Partitions info (3/3): _________________________________________________________*

*nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1*

*fdisk -l (filtered): ___________________________________________________________*

*Disk nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors*
*Disk identifier: DF2D7E1B-840B-2E4F-B0FF-AB597FA7A89A*
*          Start        End    Sectors   Size Type*
*nvme0n1p1   4096     618495     614400   300M EFI System*
*nvme0n1p2 618496 1953520064 1952901569 931.2G BIOS boot*
*Disk sda: 28.64 GiB, 30752636928 bytes, 60063744 sectors*
*Disk identifier: ABE6D9C1-D820-473F-9626-5E7897C4C498*
*       Start      End  Sectors  Size Type*
*sda1       64  9669463  9669400  4.6G Microsoft basic data*
*sda2  9669464  9679531    10068  4.9M EFI System*
*sda3  9679532  9680131      600  300K Microsoft basic data*
*sda4  9682944 60063680 50380737   24G Linux filesystem*

*parted -lm (filtered): _________________________________________________________*

*sda:30.8GB:scsi:512:512:gpt: USB  SanDisk 3.2Gen1:;*
*1:32.8kB:4951MB:4951MB::ISO9660:hidden, msftdata;*
*2:4951MB:4956MB:5155kB::Appended2:boot, esp;*
*3:4956MB:4956MB:307kB::Gap1:hidden, msftdata;*
*4:4958MB:30.8GB:25.8GB:ext4::;*
*nvme0n1:1000GB:nvme:512:512:gpt:CT1000P5PSSD8:;*
*1:2097kB:317MB:315MB:fat32::boot, esp;*
*2:317MB:1000GB:1000GB:ext4:root:bios_grub;*

*blkid (filtered): ______________________________________________________________*

*NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                           PARTLABEL*
*sda         iso9660  2023-08-07-16-02-01-00                                                    Ubuntu-Studio 22.04.3 LTS amd64 *
*&#9500;&#9472;sda1      iso9660  2023-08-07-16-02-01-00               abe6d9c1-d820-473f-9627-5e7897c4c498 Ubuntu-Studio 22.04.3 LTS amd64 ISO9660*
*&#9500;&#9472;sda2      vfat     F7DB-4D56                            abe6d9c1-d820-473f-9624-5e7897c4c498 ESP                             Appended2*
*&#9500;&#9472;sda3                                                    abe6d9c1-d820-473f-9625-5e7897c4c498                                 Gap1*
*&#9492;&#9472;sda4      ext4     3b6ad57b-5d05-4401-ab30-86133b8f498d 13209367-df85-1d4f-8bca-f0e060c46dd0 writable                        *
*sdb                                                                                                                            *
*nvme0n1                                                                                                                        *
*&#9500;&#9472;nvme0n1p1 vfat     CB06-B7DB                            08129701-36f7-8447-8fec-d6a94b020494 NO_LABEL                        *
*&#9492;&#9472;nvme0n1p2 ext4     008eb5d4-765c-4d9e-959a-8842510bd69c e8b44546-be2c-9643-87b4-e7e744d7e480                                 root*

*Mount points (filtered): _______________________________________________________*

*                                                               Avail Use% Mounted on*
*/dev/nvme0n1p1                                                293.3M   2% /mnt/boot-sav/nvme0n1p1*
*/dev/sda1                                                          0 100% /cdrom*

*Mount options (filtered): ______________________________________________________*

*/dev/nvme0n1p1                                                vfat        rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro*
*/dev/sda1                                                     iso9660     ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8*

*=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================*

*search.fs_uuid 008eb5d4-765c-4d9e-959a-8842510bd69c root *
*set prefix=($root)'/boot/grub'*
*configfile $prefix/grub.cfg*



*Suggested repair: ______________________________________________________________*

*The default repair of the Boot-Repair utility would not act on the boot.*
```

---

### Post by tea for one on 2024-04-21
```
Partitions info (1/3): __________________________________________________ _______
nvme0n1p1 : no-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, not-far
```
nvme0n1p2 should appear in the partition info
```
nvme0n1p2 618496 1953520064 1952901569 931.2G BIOS boot
```
BIOS boot - very unusual, given that it should be your OS partition
```
The default repair of the Boot-Repair utility would not act on the boot.
```
Probably because boot-repair cannot access the necessary details from nvme0n1p2

Did something peculiar happen during the installation process?

It looks like you have zero data to backup and my gut feeling is that it would be quicker to re-install.
Also, disable Secure Boot in your UEFI settings so that you can use your GA106M GeForce RTX 3060 Mobile

---

### Post by jeremy31 on 2024-04-21
I would boot into the ISO and use GParted to remove the bios boot flag from nvme0n1p2 and see if it boots

---

### Post by oldfred on 2024-04-21
Please use Code tags with any text or code from terminal.
With Boot-Repair often better to just post the link it provides to the pastebin site.

A bios_grub partition is informatted. But your partition table shows nvme0n1p2 as ext4.
It is only required for grub in the very old BIOS boot mode on gpt partitioned drives. Not required with UEFI boot.

Follow jeremey31's suggestion.

---

