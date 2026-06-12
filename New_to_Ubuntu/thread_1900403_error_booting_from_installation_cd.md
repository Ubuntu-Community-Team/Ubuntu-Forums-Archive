---
title: "error booting from installation cd"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by GlaDox on 2011-12-26
When I try to boot from the ubuntu installation cd (version 11.10), I get a screen full of text with the last line being the following:

*udevd[124]: '/sbin/modprobe -bv pci:v000010DEd00001247sv00001043sd00002050bc03sc00i00' [192] terminated bij signal 9 (Killed)*

Is my laptop not compatible with Ubuntu or am I doing something wrong? I burned the cd a second time and had the same problem.

Here are my laptop specs:
[SIZE=1]
[/SIZE][SIZE=1]**Model Name**            
X5QSF-S1123V
**Processor & Cache Memory **   
Intel Core i7-2630QM, 2.0GHz
**Operating System        **
Windows 7 Home Premium (64bit)
**Main Memory**            
1x DDRIII 1333 2GB / 1x DDRIII 1333 4GB
**Display                **
15.6" LED-backlit TFT LCD Display resolution: FHD 1920x1080 / 16:9 Display type: high brightnes(Typical 220-nit) 16ms high definition response time NTSC:45% Contrast Ratio:500:1 (Typical) Non-glare
**Video Graphics & Memory        **
NVIDIA® GeForce® GT 555M (N12E-GE2)
**Hard Drive            **
2.5" SATA 750GB 7200rpm
**Optical Drive            **
Super Multi with Double Layer[/SIZE]

---

### Post by yeats on 2011-12-26
Did you MD5SUM the ISO you downloaded and check it against the list?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by 2F4U on 2011-12-26
For nVidia cards you can try the nomodeset grub kernel parameter. But I would rather suspect either a bad dowload (verify the checksum as suggested) or a bad burn.

---

### Post by khelben1979 on 2011-12-26
Try to burn a new image file with the lowest possible burning speed from your CD burning software.

What software are you using for burning down the image file and what are the brand of the CD-R discs? I would recommend [K3b]("http://en.wikipedia.org/wiki/K3b").

---

### Post by GlaDox on 2011-12-27
Download:
I checked the MD5sum for the iso-file and it was a perfect match.

CD:
I burned the iso with CDBurnerXP. The brand of the cd's is EMTEC.

I tried burning Ubuntu 10.04 to a cd and it booted succesful. I burned the cd with Ubuntu 11.10 twice and it gave an error upon booting with both of them.

---

### Post by asusn55 on 2011-12-28
Same problem with same laptop except that I tried to install Ubuntu with Wubi.exe

---

### Post by asusn55 on 2011-12-29
I managed to install ubuntu.

You have to press [esc] just before installing ubuntu.

Choose the ACPI-workarounds option.

---

### Post by asusn55 on 2011-12-31
I can only boot Ubuntu when I add the following parameters:
nomodeset -> works but wrong resolution
pci=noacpi -> works but no keyboard at all

someone know a real solution?

---

