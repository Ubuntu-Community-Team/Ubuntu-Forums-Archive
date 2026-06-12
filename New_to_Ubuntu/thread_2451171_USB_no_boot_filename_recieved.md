---
title: "USB no boot filename recieved"
date: 2020-09-28
forum: New to Ubuntu
---

### Post by bob1111 on 2020-09-28
I made a bootable USB stick on windows [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

I got to step 4 here          [https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive](https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive)

I pressed f10 as my computer was starting and I went to the boot menu and clicked the boot device, I got "no boot filename received"

---

### Post by Impavidus on 2020-09-29
It appears something went wrong when creating the live disk. Did you check the .iso for errors after download (can be skipped if downloaded via torrent)? How have you created the bootable disk? Your first link doesn't work.

---

### Post by bob1111 on 2020-09-29
I have fixed the link for how I created the bootable disk. I have not checked the .iso for errors.

---

### Post by ActionParsnip on 2020-09-29
If you use torrents then you don't have to check the integrity. The torrent protocol checks data as it downloads

---

### Post by bob1111 on 2020-09-29
I have installed BitTorrent, but I am a laymen. I don't know what to do.

---

### Post by CelticWarrior on 2020-09-30
BitTorrent is a 20 years old technology. Not knowing how to use is almost the same of not knowing what a smartphone is...
But don't worry. The torrent suggestion was regarding the downloaded ISO integrity that is guaranteed if this technology is used instead of the "normal" download. Users here in cases such as yours tend to mention the possibility of a corrupt download that although possible is so rare nowadays (and users typically notice when there's a problem during the download process).

I'm 99% sure the problem is not the ISO you downloaded but the specifics of 1) using Rufus and 2) settings on the target computer. So, here goes another history lesson: Almost all computers from the last decade have UEFI, the new motherboard firmware, instead of the old (1981) BIOS. And since 2012 Microsoft mandated that all manufacturers provide preinstalled Windows in UEFI mode and GPT partitioning.

So, finally, **your non-booting USB was likely made with the Rufus' default settings, the settings that works for old BIOS only**. Unfortunately the official tutorial doesn't mention this detail - it needs "UEFI/GPT" - nor it mentions a lot of other small details that users NEED to know *before* attempting to install Ubuntu, like disabling Secure Boot and Fast Boot and in some cases changing the SATA mode to AHCI where the default is "RAID" or Intel RST.

---

