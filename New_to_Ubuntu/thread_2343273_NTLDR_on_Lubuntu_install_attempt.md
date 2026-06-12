---
title: "NTLDR on Lubuntu install attempt"
date: 2016-11-14
forum: New to Ubuntu
---

### Post by truthreigns-hotmail on 2016-11-14
I have burned a copy of lubuntu 16.10 using "Free Iso Burner".  I am trying to install on a Compaq Presario.  I get the NTLDR message, same with Lubuntu 16.04.1 downloaded from a different source and burned using "Free Iso Burner".  However, Parted Magic also on DVD boots fine.

---

### Post by oldos2er on 2016-11-14
Please post the computer's hardware specs.

---

### Post by truthreigns-hotmail on 2016-11-16
I have a 120 GB SATA HD, 2 GB of RAM, I installed a different mother board and a new CPU (AMD 64FX-55) ; think i am having overheating problems.  I researched them both carefully to make sure they were compatible with this Compaq R4000.   I usually document everything but can't find the name and model # of the mother board and I don't know how to find it using Parted Magic, which seems to be my only resource.

---

### Post by truthreigns-hotmail on 2016-11-16
Last night I ran Gparted and Testdisk and Erase Disk.  I did a secure erase of the HD, then I added the DOS partition and created a 512 MB swap partition and a single 111.29 GB primary partition.  Using Testdisk I wrote a new MBR.  I booted into the BIOS and made sure I had the CD drive set for first boot option.  I really thought that would fix it.  Now I get 1234F on booting up.

---

### Post by oldfred on 2016-11-17
I believe the testdisk boot loader is a Windows type that uses boot flag.
So what partition has boot flag.
But that would only be for internal drive.
In BIOS you have to choose to boot external drive. And if computer is about 10 years or older it may have USB ports but they are not bootable, only CD is bootable.

Grub does not use boot flag and you really should be installing grub to MBR, so it is used as boot loader.

---

### Post by truthreigns-hotmail on 2016-11-18
I was able to install grub.  When I boot now I get grub, but i really don't know how to use it.  I am just following recipes here.  I am pretty amazed that I was able to install grub. Am I supposed to be able to use grub to install the Lubuntu iso?

---

### Post by oldfred on 2016-11-18
No, you install grub as part of installing system.
You should be booting flash drive with the syslinux boot loader flash drive uses for BIOS.
After you install you will have grub on hard drive.

How old is system? Older BIOS may not boot flash drive.
Do you have latest BIOS from vendor for your system?

If parted magic works from DVD, use DVD to install Ubuntu.

Also if older system, but newer large hard drive, be sure to use a smaller / (root) like 25GB and a larger /home or data partitions. Some old BIOS only boot from first 137GB of a drive, so default install of / over entire drive may have boot files anywhere on drive. 
Make sure drive is set to AHCI, not IDE nor RAID. If you do not have AHCI it definitely is an old system.

---

### Post by truthreigns-hotmail on 2016-11-18
120 gb ata hd

---

