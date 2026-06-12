---
title: "installing ubuntu 18.04 alongside windows 7 professional - boot problems"
date: 2019-03-18
forum: New to Ubuntu
---

### Post by janlegein on 2019-03-18
On an older laptop Fujitsu P771 with a 64 bit i7 CPU, I'm trying to install Ubuntu 18.04 alongside windows 7 professional. I updated the UEFI to the latest version before trying to install ubuntu, reinstalled windows to start from a clean computer. 

Resized the partition on the C-drive to 60gb for windows and 60gb unallocated, using windows partition tool.
Windows 7 has no fast boot or secure boot to be disabled, I think. All threads I find are with windows 8.  

Installed a USB bootable stick from the ubuntu *.iso file using rufus in several modes, but always get the same boot problem stating: 

Could not get fio for li->DeviceHandle: Invalid Parameter
Failed to find fs: Invalid Parameter
Failed to load image \EFI\BOOT\grubx64.efi: Invalid Parameter
start_image() returned Invalid Parameter

I've spent a week searching forums, read all about uefi, bios, but am pretty new to all this, so if anybody could point me in the right direction, I would be grateful

---

### Post by yancek on 2019-03-18
A default windows 7 install will not be UEFI although you can do that.  Did you, when you re-installed windows 7, do so using UEFI?  Do you have an EFI partition?  You can verify this from the Ubuntyu install usb by opening a terminal and running the following command:

```
sudo parted -l
```

One thing you might do is to try to boot the usb on another computer if you have one available to see if it works/boots.

When you used windows Disk Management to shrink the windows partition, did you reboot windows and run chkdsk?  Not necessary but a good precaution to verify that it still boots.

---

### Post by janlegein on 2019-03-18
> **yancek said:**
> A default windows 7 install will not be UEFI although you can do that.  Did you, when you re-installed windows 7, do so using UEFI?  Do you have an EFI partition?  You can verify this from the Ubuntyu install usb by opening a terminal and running the following command:

```
sudo parted -l
```

One thing you might do is to try to boot the usb on another computer if you have one available to see if it works/boots.

When you used windows Disk Management to shrink the windows partition, did you reboot windows and run chkdsk?  Not necessary but a good precaution to verify that it still boots.

I reinstalled windows 7 from the disk, without doing anything special. Just wanted to remove all the old stuff from the laptop. So probably not UEFI. I tried the Ubuntu disk on a new Nuke PC, it worked fine. Sadly enough I don't get to the point where the Ubuntu USB opens a terminal, it stops before that. 

Did not run a chkdsk, will do that. But Windows boots without a problem.

So how do I prepare the startup USB stick for not UEFI? 

a. Do I use Rufus 3.4 or Rufus 3.4 Portable (as it's a laptop)? b. Which partition settings in Rufus? I assume MBR with BIOS or UEFI target system - standard FAT (or NTFS?) and 64kb clustersize c. Is ubuntu-18.04.2-desktop-amd64.iso the correct iso file?

---

### Post by oldfred on 2019-03-18
Standard Ubuntu installer is both BIOS & UEFI.
It is in your UEFI that you should have two entries, one usually "UEFI-flash" and other "flash" which is the BIOS boot. And "flash" is name or label of your flash drive.

You get grub menu if booting in UEFI mode and you get purple accessiblity screen with two tiny icons at bottom in BIOS mode. With BIOS you have to quickly press the famous "any" key to get boot options or add with f6 boot parameters.

---

### Post by SeijiSensei on 2019-03-18
You might have told Rufus to use UEFI. Try writing the USB stick without it.

---

### Post by janlegein on 2019-03-18
> **SeijiSensei said:**
> You might have told Rufus to use UEFI. Try writing the USB stick without it.

U mean try writing the USB stick without using rufus, or telling rufus not to use uefi?

---

### Post by janlegein on 2019-03-18
Solved, settings in rufus 3.4 (not p-version) adjusted to MBR (target system Bios or UEFI) advanced property Add fixes for old BIOSes enabled, format options file system NTFS with default cluster size.

Thank you!

---

