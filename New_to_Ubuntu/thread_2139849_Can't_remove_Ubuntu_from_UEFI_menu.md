---
title: "Can't remove Ubuntu from UEFI menu"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by DRatJr on 2013-04-28
I have tried multiple ways to delete it from the boot menu. Nothing works. I've tried running the "sudo efibootmgr -b # -B" in Linux, tried using EasyBCD and nothing. After reboot it still shows. Here is what EasyBCD shows:

Entry #1
Name: Windows Boot Manager
BCD ID: {4e2702ab-aae2-11e2-be9c-806e6f6e6963}
Device: \Device\HarddiskVolume2
Bootloader Path: \EFI\Microsoft\Boot\bootmgfw.efi


Entry #2
Name: ubuntu
BCD ID: {796aca68-afc3-11e2-beb4-806e6f6e6963}
Device: \Device\HarddiskVolume2
Bootloader Path: \EFI\Ubuntu\grubx64.efi


Entry #3
Name: UEFI: PNY USB 2.0 FD 1100
BCD ID: {796aca69-afc3-11e2-beb4-806e6f6e6963}
Drive: F:\
Bootloader Path: 


Entry #4
Name: Windows 8
BCD ID: {current}
Drive: C:\
Bootloader Path: \windows\system32\winload.efi



I just want to delete Ubuntu from the boot menu and remove all traces of grub. When I select the ubuntu entry to boot I get "error: unknown filesystem /(next line) grub rescue>"

I had ubuntu installed before, and uninstalled it and deleted its partition and merged it back with windows. the bootrec /fixmbr command has not worked either. Please help.

---

### Post by oldfred on 2013-04-28
Duplicate thread. Closed.
[http://ubuntuforums.org/showthread.php?t=2139312](http://ubuntuforums.org/showthread.php?t=2139312)

You have to delete \EFI\Ubuntu\grubx64.efi as I have told you in two other threads.

---

