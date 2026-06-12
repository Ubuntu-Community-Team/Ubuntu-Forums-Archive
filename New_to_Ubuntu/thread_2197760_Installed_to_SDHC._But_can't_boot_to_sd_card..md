---
title: "Installed to SDHC. But can't boot to sd card."
date: 2014-01-05
forum: New to Ubuntu
---

### Post by kurtbliss3 on 2014-01-05
I recently bough a 16gb SDHC card and installed Ubuntu on it but couldn't boot it. 
I thought I could install grub on my hp flashdrive to boot off my SDHC card. 
But couldn't figure it out so anyone know how to boot off a SDHC card if it doesn't apear in your BIOS' boot menu? (but can boot off of flashdrive)

**Specs/Devices:**
Netbook: acer ASPIRE ONE NAV50.
SD card: Installed Ubuntu 13.10 Desktop to SandDisk 16GB SDHC card.
Flashdrive: Cruzer flashdrive used to install linux. (with Ubuntu 13.10 installer on it)
Flashdrive: 1v65w hp flashdrive (short)


So anyway I could boot off my SDHC card even though it doesn't show up on my boot menu?

---

### Post by oldfred on 2014-01-05
Only some new systems boot from a flash drive. But unless correctly configured even those that will boot will not show it unless seen as a bootable device.
 Is flash drive booting an option with your BIOS? See computer manual or maybe an update to BIOS.

Sometimes plop will work.
[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

---

### Post by tfrue on 2014-01-05
I know one solution is to purchase an SD to USB adapter, but that defeats the purpose, I know. I tried this once but it was too much of a hassle to make it work, and I don't remember the site that I found, but still was too much to do just to simply boot from an SD card. It's more practical to boot from your internal HDD drive.

---

### Post by kurtbliss3 on 2014-01-05
Yeah, might as well use my flashdrive. 
Looks like grub could work but I kept getting this for entering "sudo fdisk -l" and got this for the drive I wanted to use "doesn't look like a partition table Probably you selected the wrong device". Dont want to install anything on my external drive so. 
I didnt find anyone on the net talking or any programs talking about allowing you to boot off a SDHC card so figure I'll give up and try flashdrive. Thanks

---

