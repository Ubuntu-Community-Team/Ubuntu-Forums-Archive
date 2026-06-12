---
title: "Install to external drive"
date: 2017-10-03
forum: New to Ubuntu
---

### Post by Tony_Palermo on 2017-10-03
Yes I am trying to install to a USB stick and every time I do it puts the boot-loader on the internal drive.  At the bottom of the screen when I am making the partitions I do check to make sure I do have selected install the boot-loader to the external usb drive.  Is this a bug or am I doing something wrong?  The reason I am trying to install it to a USB stick is some of my friends don't have linux and I prefer to use it.

Any help would be great.

Tony

---

### Post by oldfred on 2017-10-03
With a BIOS install and using Something Else you can specify to install grub2's boot loader to the external drive.

But with UEFI, grub2 only installs to the ESP - efi system partition on first drive, usually sda.

You have to partition flash drive in advance & include an ESP or the FAT32 formatted partition with boot flag as first partition on flash drive.
Then you have to copy /EFI/ubuntu twice from sda to flash drive, once to /EFI/ubuntu and once to /EFI/Boot. Then rename /EFI/Boot/shimx64.efi to /EFI/Boot/bootx64.efi.

That is becuase grub only installs to sda, and UEFI only boots from /EFI/Boot/bootx64.efi for all external devices. And Ubuntu's version of grub/shim is hard coded to find /EFI/ubuntu/grub.cfg, so that folder & file must exist.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Please add to this bug report.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

More details in link in my signature.

 UEFI fast boot may interfere with USB boot.
It turns out the loading of USB drivers is somewhat slow. Fastboot with UEFI skips a lot of reinitialization, so you may not see a new device in a USB port.
UEFI fast boot, skips the old BIOS Power-on self-test (POST), assumes no changes to system

---

### Post by C.S.Cameron on 2017-10-04
Try unplugging internal drive before starting the install.

---

### Post by sudodus on 2017-10-05
> **C.S.Cameron said:**
> Try unplugging internal drive before starting the install.

+1

You may find some useful tips via the following link,

[AskUbuntu: Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by Tony_Palermo on 2017-10-09
Yes I think you are right the only way to install it to an external drive it sounds like is unplugging the internal drive.

---

### Post by oldfred on 2017-10-09
I do full installs to flash drives and do not unplug internal drives, but it requires copying the ESP entry to external. You also have to edit fstab to have external drive's ESP as mount. And since I only boot Ubuntu I have to backup my working install's /EFI/ubuntu folder as new install overwrites it.

And UEFI only boots /EFI/Boot/bootx64.efi which a standard install does not create. You still have to copy shimx64. efi to be that file in ESP on external drive.

---

### Post by sudodus on 2017-10-10
> **Tony_Palermo said:**
> Yes I think you are right the only way to install it to an external drive it sounds like is unplugging the internal drive.

Maybe not the only way, but an easy way, if it is easy to unplug the internal drive in *your* computer :-)

---

