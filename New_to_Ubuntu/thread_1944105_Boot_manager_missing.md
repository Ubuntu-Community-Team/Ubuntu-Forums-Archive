---
title: "Boot manager missing"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by devilindisguizz on 2012-03-20
I bought a new hard disk for my laptop.i thought i won't be needing drivers to install windows 7.I tried installing windows 7 using a usb but couldnt as i had no drivers.after i removed the usb it said **boot manager is missing press alt+ctrl+del**.i tried installing mint.it got installed but as soon as i removed the usb i got the same message again.then i tried installing ubuntu 10.10 it also got installed but as soon as i removed the cd it showed the same message again after the restart.....WHat should i do???

---

### Post by PhantomTurtle on 2012-03-20
You could try and repair Grub. Look Here: [https://sites.google.com/site/easylinuxtipsproject/grub]("https://sites.google.com/site/easylinuxtipsproject/grub")

---

### Post by critin on 2012-03-20
Did you format the new disk for Win7 through Windows?
Did you get utilities with the disk?

---

### Post by tushar maroo on 2012-03-21
install grub form a live ubuntu cd......that will repair your missing grub menu.
 this link can help you...
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by oldfred on 2012-03-21
Is this an error from BIOS or UEFI? 

Some BIOS systems will not boot without a boot flag on a primary partition which Windows has to have, but grub does not use. I usually suggest a boot flag on a primary partition even with Linux only installs just to avoid the issue with some BIOS.

If UEFI then it has to have an efi partition as the first partition.

Post this:

sudo fdisk -lu
and/or this if fdisk says gpt
sudo parted /dev/sda unit s print

---

### Post by d4m1r on 2012-03-21
> **oldfred said:**
> Is this an error from BIOS or UEFI? 

Some BIOS systems will not boot without a boot flag on a primary partition which Windows has to have, but grub does not use. I usually suggest a boot flag on a primary partition even with Linux only installs just to avoid the issue with some BIOS.

If UEFI then it has to have an efi partition as the first partition.

Post this:

sudo fdisk -lu
and/or this if fdisk says gpt
sudo parted /dev/sda unit s print


I think it is safe to assume it is BIOS, as it has 99.9% of the market.

Anyway, if you are looking to run Windows and any distro of linux, it is easiest to install Windows first THEN linux. Ubuntu's Grub (not sure what Mint uses) is MUCH smarter than Window's 7 boot manager.

---

