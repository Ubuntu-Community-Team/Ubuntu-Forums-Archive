---
title: "uefi+legacy questions"
date: 2020-01-11
forum: New to Ubuntu
---

### Post by xbccoffee on 2020-01-11
Hello. I used to use linux for a couple of months, but I still would consider my experience very little or none.

I want to dual boot kubuntu with a uefi windows 10 laptop.

It currently is in uefi mode.

I have heard that the option uefi+legacy is a better option to boot and use linux on. 

My question is:

If I create a bootable usb with etcher in uefi mode, will it boot in uefi+legacy? If not, should i create the usb in uefi+legacy mode or just boot from full uefi mode?

---

### Post by CatKiller on 2020-01-11
> **xbccoffee said:**
> I have heard that the option uefi+legacy is a better option to boot and use linux on. 

Nope. Legacy emulates the old BIOS, but UEFI is just better. Maybe 15 years ago or so there were teething problems with the very first implementations.

Using Windows 10 in UEFI mode constrains you to not use Legacy in any case. Fully UEFI for both of your dual boot OSes is what you're after.

---

### Post by xbccoffee on 2020-01-11
Highly appreciate the timely response. Thank you.

---

### Post by oldfred on 2020-01-11
More info, if interested.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

