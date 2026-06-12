---
title: "have windows 8.1 want to dual boot off a toshiba external hard drive"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by nc2hike on 2013-11-17
have windows 8.1 want to dual boot off a toshiba external hard drive. i downloaded it and can't do anything with thew file. when i try to access the file the computer ask what file to open it with. the only grub i know of is bait. thus i'm here. cant see how to enter c-mos to tell computer to look at usb.  don't want to install it direct as the schmucks don't give backup disks with new computers. and i bet warranty will be voided. dont have a cd or usb stick that can handle a file the size of ubuntu. if there is a way to look up the answer that would be nice. but every parameter i've attempted hasn't come close. mostly see win 7 ref. i miss dos

---

### Post by oldfred on 2013-11-17
Is Windows 8.1 pre-installed and UEFI with secure boot or an install you did? If your install is it BIOS or UEFI?

You have to convert ISO to bootable disk and just copying it to a large USB drive will not work. Best to have flash drive that you can then install (extract & make bootable) ISO into and use that to install to external drive.
If Windows is UEFI besure to use gpt partitioning on external drive and install Ubuntu in UEFI mode. Also best to have an efi partition on external drive so it could boot without internal, even if you install grub2's boot files to the internal drive.

Second drive installs are a bit more complex, but several example of users with UEFI that did install to a second drive in link in my signature.

---

### Post by nc2hike on 2013-11-18
thank you. good info. i'll need to see if i have a non destructive partition manager. will check into that after work tomorrow

---

### Post by oldfred on 2013-11-18
Normally when you use the flash drive installers they erase & reformat the entire flash drive.

This claims to do a frugal install to a hard drive. But not sure how that works.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If Windows is UEFI, you really want to install Ubuntu in UEFI boot mode not BIOS and then you need gpt partitioning. Not sure if you can create a gpt drive and add a partition and then will unetbootin use that??

It actually is not difficult, but not really for beginners to install grub to any drive, and make a partition with as many ISO versions as you want and directly boot from grub.
But I do not know how to install grub to a drive except from Ubuntu.

---

### Post by electrohandyman501 on 2013-11-18
If your machine is pre-installed with W8 you are probably ok, what speed is your usb interface. Hopefully it's SS-USB3.0 
You won't be happy trying to boot a drive with USB2.0. It will work, but it will be slow, slower than booting from a thumb drive.

---

### Post by electrohandyman501 on 2013-11-18
Another option to consider. Does your bios boot screen show you an "f-key" boot option? My dell uses F-12 for select boot device.(this is not the same as editing boot order in bios)
Some newer pc's will allow you to select the boot device on bootup, cd/dvd, usb, etc....
If so, you could just do the full install to the usb drive and use the "f-key" to select the usb boot instead of trying to modify your mbr of your internal drive.
For extra safety if you are comfortable opening the case, with power off, unplug your internal drive before you do your install. For sure nothing will be written the internal drive.
You will need a live cd to boot/install from, and you will need to "create cd from iso image" first........

When done you will still have your W8 on the internal drive and your alternate system on the external complete. You just then select the boot device thru the bios option as opposed to a modified mbr selection option.

---

