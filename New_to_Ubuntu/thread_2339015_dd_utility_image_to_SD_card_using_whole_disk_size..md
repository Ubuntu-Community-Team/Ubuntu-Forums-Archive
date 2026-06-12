---
title: "dd utility image to SD card using whole disk size."
date: 2016-10-03
forum: New to Ubuntu
---

### Post by brock7 on 2016-10-03
I'm used dd utility to mount a .img.xz file to an SD card to allow me to boot Kali on my chromebook flip. 
Using instructions on kali.org I manage to get kali running on the chrome book flip *Hooray*
But the image mounts on 7 gb of space and makes the rest of my 64gb SD card invisible *Booo*

I want to take and existing file.img.xz file and mount it to a 64 gb SD card and to still be able to see and use all or most of the storage on the SD card. 
(64 gb is what I have right now. Eventually I will want to do this same thing on a bigger SD card.)

I tried using crouton to get ubuntu running but I was repeatedly frustrated by errors and problems. I got Kali running first try but now I need to be able to download and install programs.. That requires more than 7 gb.

any input or help i can get will be greatly appreciated.

---

### Post by Bucky Ball on 2016-10-04
Welcome. Do you want help with Ubuntu or Kali? They are not the same beast.

---

### Post by sudodus on 2016-10-04
The method to flash a compressed image file 'file.img.xz' works like you describe. It it extracted and cloned to the prescribed size on the drive, 7 GB, so that it will fit in an 8 GB pendrive or card, even if it is slightly undersized (smaller than the nominal size).

Depending on the file system, you might be able to expand it.

- If it is a read-only partition table and file system, for example iso9660 or a read-only version of udf, you will probably not be able to use the rest of the drive (but you can restore it to a regular storage drive, for example with ***mkusb*** and ***mkusb-nox***).

- If it is a read-write partition table and file system, for example linux {ext4, swap}, or Windows {FAT32, NTFS}, you can use ***gparted*** to expand the partitions and file systems.

See the following link: [Final system tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

> Move swap and grow root partitions

Move the swap partition and grow the root partition to use the whole drive. See this link

[GrowIt.pdf](http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf)


---

### Post by T2uiYKb7 on 2016-10-04
If your using a UEFI PC you can simply extract the .img.xz file to the root of the SD Card with any archive program or by command line. It will find the /efi/boot/bootx64.efi file regardless of the boot loader etc.

Obviously that doesn't help if your using BIOS.

**Edit: I'm guessing it's UEFI if it's a Chromebook.**

---

