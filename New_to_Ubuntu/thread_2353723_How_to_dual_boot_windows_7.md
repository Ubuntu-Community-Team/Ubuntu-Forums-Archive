---
title: "How to dual boot windows 7"
date: 2017-02-24
forum: New to Ubuntu
---

### Post by khan3 on 2017-02-24
I have Ubuntu 16. running on my laptop. My Laptop has a 256 ssd. I want to install windows 10 using 70gb of that ssd. How do i partition my ssd and dual boot windows.

thanks.

---

### Post by oldfred on 2017-02-24
UEFI or BIOS?

Windows only boots in BIOS mode from MBR partitioned drive with the 4 primary partition limit. And it must boot from a primary NTFS partition with boot flag.

Post this:
sudo parted -l

---

### Post by khan3 on 2017-02-24
@oldfred i know what BIOS is, but whats UEFI, i was hoping to have some sort of boot manager? 

 kay &#57520; ~ &#57520; sudo parted -l


Model: ATA WDC WD7500LPCX-6 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                          Flags
 1      17.4kB  134MB  134MB               Microsoft reserved partition  msftres
 2      135MB   750GB  750GB  ntfs         Basic data partition          msftdata


Model: Unknown (unknown)
Disk /dev/nvme0n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
 2      538MB   248GB  247GB   ext4
 3      248GB   256GB  8499MB  linux-swap(v1)

---

### Post by yancek on 2017-02-24
The information in your last post shows that both your drives are GPT which means you must use UEFI for windows.    Some general information on dual booting UEFI at the Ubuntu documentation site below.  I expect you will need to use the Custom install option with windows or you will likely overwrite your Ubuntu with windows.  I don't use UEFI so don't have any further suggestions.  Almost all links you will find with tutorials are installing Ubuntu/Linux after windows which is usually pre-installed.  Hopefully, some users who are more familiar with windows will post.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-02-24
Be careful with your Windows 7.
The DVD only installs in BIOS mode, and converts any gpt drive to MBR (incorrectly) and you lose all your data.
Make sure you have good backups.

Not sure if Windows 7 is even aware of NVMe drives, you may only be able to use Windows 10 that would have the newest drivers.
Microsoft did not want vendors of any new/different hardware to create drivers for older versions of Windows. Some are created as very large users still wanted Windows 7 to work.

You really need to convert the Windows 7 installer to UEFI, by copying to flash drive and moving some files around to make it UEFI bootable.
  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736) 

With UEFI you also have an UEFI boot menu to directly boot Windows or Ubuntu.
And from grub menu you can boot other systems installed in the same boot mode.

Definitions & links to full pages of explanation of terms like UEFI are at end of the UEFI install links in link in my signature.

---

