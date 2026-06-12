---
title: "Booting problems"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by kevlimzm on 2014-06-21
After trying to follow several guides in order to fix my computer, i probably screwed up alot of things. After trying to use boot-repair i got this [http://paste.ubuntu.com/7679211](http://paste.ubuntu.com/7679211)

As far as i know i have installed ubuntu on the computer, but for some reason it wont boot into the system, and the screen is stuck with a "please insert boot disk....".

If possible i would like to access the recovery partition, which seems to be at /dev/sda5 but after trying to use a windows 7  repair option, it keeps telling me its the wrong version (a sticker on the laptop tells me to use home premium, and i have tried a 32 bit and 64bit disk without luck), is it possible to boot into the partition from ubuntu?

A solution of either of the problems would really make my day, thank you!

---

### Post by LastDino on 2014-06-21
What did you select when you were installing Ubuntu? ''install alongside'', ''replace existing'' or something else?

Also, 

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
[B]=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda3	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt.
sda4	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.

sda	: GPT,	BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
1      1049kB  211MB  210MB   fat32           EFI system partition          boot
2      211MB   345MB  134MB                   Microsoft reserved partition  msftres
3      345MB   470GB  469GB   ext4
6      470GB   474GB  4194MB  linux-swap(v1)
4      474GB   474GB  4194kB  ext4                                          bios_grub
5      474GB   500GB  26.2GB  ntfs            Basic data partition          diag



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                             [/B]
```
This probably explains a little?

---

### Post by kevlimzm on 2014-06-21
I first installed it alongside, then when it kept showing me the "please insert boot disk" i wondered if it had installed at all. Then i made the sda4 bios grub and sda6 and installed a ubuntu again on the sda3 partition, while leaving sda1,2 and 5 untouched, since i didnt want to screw them up.

---

### Post by kevlimzm on 2014-06-21
About the code, my only guess is some kind of wrong format, but i don‘t know what caused it and im not clever enough to understand it.

---

### Post by LastDino on 2014-06-21
Your system seems to have EFI BIOS, please confirm that first. If it is that, then you needed to install both W7 and Ubuntu in same mode; Legacy/EFI to be able to dual boot them. That could ''probably'' explain the please insert the bootable disk error.

At this moment, if your sd5 is recovery partition, there is no trace of installed W7, you seem to have deleted it. Not gonna lie, this seems bit out of my league as there seem to be multiple things wrong. I've few ideas but I would rather wait for someone more knowledgeable to come along, especially; Oldfred.

Sorry for taking your time.

---

### Post by kevlimzm on 2014-06-21
Thank you very much for your replies! I apreciate all the help i can get! I am pretty sure i have a an EFI bios, since something like that was stated in the bios menu. I hope i more people would be able to help!

---

### Post by kevlimzm on 2014-06-21
Additional info! While reading here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) they talk about Bios booting up the CD in two screens, so far it has been booting up mostly as if BIOS has not been set up to boot the CD in EFI mode, however sometimes it boots up as if it has been set to boot in EFI mode. After trying to use boot-repair it now tells me my system boots up in legacy mode. I have tried searching the bios menu, but it says that UEFI is enabled.

---

### Post by oldfred on 2014-06-21
Some systems have UEFI  only, UEFI or BIOS, or BIOS only as boot option settings in UEFI. If secure boot is on, then it will only boot in UEFI mode.
Script did not show any efi files in the efi partition, But sometimes script does not find files even if there?
But if booting in UEFI only for hard drive then system will not boot. Or if efi partition does still have Windows efi files it will not boot as Windows is now gone.

In BIOS boot mode grub only installs correctly if you have a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive. So create that partition and use Boot-Repair to reinstall grub and you should be able to boot in BIOS mode.

If you want to use UEFI mode you can use Boot-Repair in advanced mode to uninstall grub-pc(BIOS) and install grub-efi (UEFI). Grub-efi may now be grub-efi-amd64 with 14.04 as internal file name. Not sure Boot-Repair has updated or if either name works.

Boot-Repair tried running fsck on the NTFS recovery partition. Linux tools do not do much on NTFS repairs. And after any resize a NTFS partition needs chkdsk from a Windows repair console or repair CD or flash drive.

---

### Post by kevlimzm on 2014-06-21
Thank you for your reply! I menaged to get it to work, by formatting the sda3 partition and reinstalling ubuntu into it, I dont really know what made it work, but some how it did! Thank you for your time!

---

### Post by oldfred on 2014-06-21
Be sure to set BIOS to boot from drive you install  Windows into before installing, or it may just install its boot loader and boot partition into what every drive is set as default. If another Windows all boot files will just be in the one install and grub will only find the one. If Ubuntu is default boot in BIOS It just may overwrite the first 100MB for its boot partition and corrupt Linux.

---

