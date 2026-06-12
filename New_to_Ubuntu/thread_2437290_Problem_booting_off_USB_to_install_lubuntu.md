---
title: "Problem booting off USB to install lubuntu"
date: 2020-02-21
forum: New to Ubuntu
---

### Post by daveeboy-e on 2020-02-21
Hi,

I have a Lenovo Ideapad S130 with a 32Gb drive that's being annihilated by the size of Windows 10's footprint and I can't upgrade the hard drive, nor add an M2 drive coz it's missing the socket for it, so I thought I'd install a light Linux OS instead.

I've used Rufus to create a boot USB, I've disabled secure boot and fast boot, and USB boot is enabled, but every time I restart holding down shift and select the USB to boot off my machine boots Windows instead.

The stick is a USB 3 Sandisk and I've tried the default settings in Rufus to create it, and tried both FAT32 and NTFS. I've tried another Sandisk USB and a PNY one too, and the same thing happens.

Any help and advice would be *hugely* appreciated, it's really frustrating!

Thanks,

Dave

---

### Post by CelticWarrior on 2020-02-21
The default settings iof Rufus is likely the problem. You need to select GPT/UEFI.

---

### Post by westie457 on 2020-02-21
Your ISO is probably missing an important file to boot from.

Have a look at this guide for what is needed. [https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec](https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec)

I have used this guide to install to a Lenovo Miix 3 and it works.

---

### Post by daveeboy-e on 2020-02-21
Thanks both, I'll try those suggestions.

D.

---

### Post by CelticWarrior on 2020-02-21
> **westie457 said:**
> Your ISO is probably missing an important file to boot from.

Have a look at this guide for what is needed. [https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec](https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec)

I have used this guide to install to a Lenovo Miix 3 and it works.

@westie457 **No, the guide you mentioned is NOT applicable**. The [Lenovo Ideapad S130]("https://www.lenovo.com/gb/en/laptops/ideapad/s-series/Lenovo-ideapad-S130-11IGM/p/88IP10S1075") is NOT one of those with a 32-bit UEFI.
The problem is likely what I mentioned just before your post.

---

### Post by guiverc on 2020-02-21
You haven't said what release of Lubuntu, and I don't know your device. To check the USB write was valid, I would boot it on another box and perform the 'Check disc for defects' on that box. If it doesn't boot & work on that box too, I'd blame the write (ie. rufus).  Possibly helpful in writing the ISO image is [https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020)

I'll also provide some details from Lubuntu's manual - [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html)
Chapter 1.2 Booting the Image - [https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html](https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html)
Chapter 1.3 Installation - [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

---

### Post by daveeboy-e on 2020-02-21
Thanks for the suggestions all &#8211; I've followed both the Lubuntu manual guide to creating a boot disk (FreeDOS), and tried UEFI:NTFS (which gives me GPT as the partition scheme and UEFI as the target system) and no joy with either, I still get the same thing that the machine just boots Windows.

---

### Post by CelticWarrior on 2020-02-21
Reading the whole thread I'm confident in saying nobody suggested NTFS. No, that is an absurd for a Linux live USB. You either keep it as FAT32 with the already mentioned GPT and UEFI -or- you select the DD option.

Alternatively you can use Balena Etcher that works very reliably (and should do the same as Rufus' DD option).

But nothing we're suggesting will work if your ISO is corrupt, of course.

---

### Post by oldrocker99 on 2020-02-21
When the menu on the session menu, there is an option to verify the ,ISO. It can tell you if you need at do it again.

+1 for Balena Etcher, the best USB burner available, IMHO.

---

