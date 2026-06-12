---
title: "Dual boot 10.04 and 12.04"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by phil66 on 2012-07-11
I have 10.04 installed with grub 2 to mbr
I also have two other distro's which use grub 2 boot manager

What I want to do is install 12.04 to a partition then have it use 10.04 grub 2 as its boot manager.

The other distro's have grub installed to the /root partition and display in grub 2 

Is it possible to install 12.04 in the same manner and continue to use 10.04 boot manager.

---

### Post by NikTh on 2012-07-11
> **phil66 said:**
> 

Is it possible to install 12.04 in the same manner and continue to use 10.04 boot manager.

Of course it is. You must pick "something else" and after you specify the partition that 12.04 will be installed , then be careful to specify a partition that grub will be installed. DO NOT choose mbr , but another partition like /dev/sda1 or /dev/sdb1 or even to Usb (if you install ubuntu through LiveUsb). 

After installation finish you must boot to 10.04 and run ```
sudo update-grub
``` to recognize the new Ubuntu 12.04 installation.

---

