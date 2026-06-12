---
title: "Cannot boot to new install"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by ianpants69 on 2008-06-09
HI,

I have installed ubuntu on a partition on a SATA drive mounted via a PCI card which was created by the installer, within windows the partiton shows as healthy and bootable however i do not get the option to boot to Ubuntu, it simply boots straight to windows.

I have changed the BIOS but after a short pause and an error message it boots to Windows as per... any suggestions???

thanks I

---

### Post by cprofitt on 2008-06-09
It sounds as though:

A)  Grub was not installed (if you are still seeing the Windows boot loader that is the case

or

B)  Grub set Windows as the default boot and you are not getting an option (or it is going by too quick) to select a boot option

I am flagging this for the unanswered posts team.

---

### Post by meierfra. on 2008-06-11
```
and an error message 
```

What is the error message?

Boot from the Ubuntu LiveCD, open a terminal (Applications->Accessories->Terminal) and post the output of 

```
sudo fdisk -l
```
( l is a lowercase L)

---

