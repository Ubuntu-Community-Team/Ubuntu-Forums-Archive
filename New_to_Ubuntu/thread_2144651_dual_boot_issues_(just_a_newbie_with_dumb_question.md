---
title: "dual boot issues (just a newbie with dumb questions)"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by CampingCake on 2013-05-13
i've always been a windows user but wanted to try ubuntu so i made a bootable usb stick and loaded up ubuntu. but now i cant load windows 7 anymore. i have 2 hard drives in my pc one with windows on it and one with ubuntu 13.04 64. now when i load i load into a choice screen with four choices two for ubuntu and two for windows. the windows ones will not load i keep getting cannot find errors.

first windows option = windows uefi bkpbootmgfw.efi
error not found = efi/microsoft/boot/bkpbootmgfw.efi

second option = windows boot uefi loader
error not found = efi/boot/bkpbootx64.efi

also im having issues with my mouse and keyboard not working once and a while i ahve to unplug and plug the mouse back in before either start to work again

---

### Post by fantab on 2013-05-13
If your windows was booting with UEFI then so should Ubuntu. I suspect that you may have installed Ubuntu in NON-UEFI mode. You have to post the output of BOOTINFO Script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

