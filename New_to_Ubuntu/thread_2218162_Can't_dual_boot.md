---
title: "Can't dual boot"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by Delupara on 2014-04-19
So I wanted to dual boot using EFI but it just won't work >:(

I am using a burned cd of _Ubuntu 14.04 LTS_ and when I want to try Ubuntu without installation it loads for about 5 min then I only get a black screen

Here are my specs

MS windows 8.1 64-bit

AMD A4-5000 APU with Radeon HD Graphics 

4.0 GB RAM

AMD Radeon HD 8330

Using UEFI and secure boot is disabled

I really want _Professional Help_ Please because I've gone on other forums and they didn't or almost not helped me at all

---

### Post by Double.J on 2014-04-19
Hi there!

Welcome to the forums!

It is most likely a graphics driver issue. Are you able to boot using the nomodeset boot parameter?

At the grub boot menu (if there's no menu when you power on, hold shift at boot) select the entry you wish to boot from and press 'E' then add the phrase
```
nomodeset
```

let us know how you get on!

Jj

---

### Post by Delupara on 2014-04-19
Sorry I did all that and it told me: Unknown command 'nomodeset/

I'm not sure.... I think I did the wrong thing (Sorry I just suddenly recently had the craving for linux so I know nothing in it)

---

### Post by Double.J on 2014-04-20
Hi there, this is strange. Does this happen at the grub menu it's a list of things like:
```
ubuntu 14.04 lts
ubuntu 14.04 lts (recovery mode)
memtest
boot from hard drive
```

or are you at a command prompt? (Like being I an old MS-DOS computer? It may say something like 'busybox' in the top left corner?)

Jj

---

### Post by Delupara on 2014-04-20
Ok yes I was at the command promp

But I managed to get to the grub menu and i saw some coding at one point saying :   boot= casper    So i changed it to boot=nomodeset and it had some sort of seizure ans in implied something called "kernel" a lot of times.....

---

### Post by Delupara on 2014-04-21
Bump.... I still need help

---

### Post by jdeca57 on 2014-04-21
Ok, i'll try to give some input: read [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and normally, with those specs, there shouldn't be a problem.

---

### Post by oldfred on 2014-04-21
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Only a few systems will only boot installer in BIOS mode. And most of those only boot Windows in UEFI mode, so you have to install in BIOS mode and either live with booting from UEFI menu or modify/rename efi boot files so system thinks it is booting Windows but actually boots to grub menu.

What brand & model system?

---

### Post by WoodenWalker on 2014-04-21
Hello jeremie5, I am new to the forums but not a new Ubuntu member. What type of system are you attempting to install on? Also, EFI boot seems to be a bit clunky with Ubuntu installs, in my personal experiences, but it can be done.

---

