---
title: "Install Ubuntu on UEFI"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by siddharth007 on 2013-07-31
Hey folks!! I have a Sony vaio e-series laptop which came with pre-installed Windows 7 Home basic edition.I wanted to install Ubuntu 12.04 alongside Win 7 (dual boot).However since the bios mode is UEFI,i coudn't do so.I have a couple of questions here

[LIST]
[*]Is it possible to install Ubuntu via USB boot disk if i change the bios mode from UEFI to "legacy". (Hopefully i can do it from bios setup).
[*]If this is possible,will it affect the windows installation?
[/LIST]

Need your help guys. I don't want to mess up with the existing installation.

---

### Post by dongatto on 2013-07-31
Hi,

There's a nice tutorial here, I don't know if you've read it:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you still have questions, tell them. :) As for the current ones, the short answers are:
 * Depends on your BIOS, but your hard drive has to be booted in UEFI mode. You may or may not be able to set this separately.
 * It will not affect your Windows installation.

---

### Post by oldfred on 2013-07-31
Many systems have UEFI/BIOS with Windows 7 in BIOS mode. Only a few with Windows 7 used UEFI.

But then with Ubuntu you may be booting in UEFI mode as that is offered. You do need to have Windows and Ubuntu booting in the same mode.

If drive is gpt partitioned and you have an efi partition you are in UEFI mode. 

If you have MBR(msdos) partitioning and just have the hidden 100MB boot and main install with recovery partition and vendor tools using the remain 4 MBR primary partitions then you have BIOS install.

How you boot install media (both Windows & Ubuntu) is how it installs.

---

