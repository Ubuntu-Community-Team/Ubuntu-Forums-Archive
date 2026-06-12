---
title: "Planning on installing Ubuntu on a new hard drive but UEFI motherboard."
date: 2014-02-28
forum: New to Ubuntu
---

### Post by shadowofsolidus on 2014-02-28
Hi, I'm planning on installing Ubuntu on a new hard drive and not the current one that has Windows installed. But the motherboard I'm using is UEFI. Will I encounter problems?

---

### Post by Gordonbp531 on 2014-02-28
Not if you install 64 bit 13.10.....

---

### Post by mastablasta on 2014-02-28
if board is certified for windows 8, then no. you may have driver issues which are not conected with UEFI. hard to say from the information provided.

---

### Post by shadowofsolidus on 2014-02-28
> **mastablasta said:**
> if board is certified for windows 8, then no. you may have driver issues which are not conected with UEFI. hard to say from the information provided.

It's an ASRock Z77 Extreme4 motherboard.

---

### Post by Bucky Ball on 2014-02-28
It's just a different way of going about it. Here's some light reading to get you started:

oldfred's tips:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Managing Everything UEFI:
[http://www.rodsbooks.com/efi-bootloaders/index.html](http://www.rodsbooks.com/efi-bootloaders/index.html)

EFI Bootloader Installation:
[http://www.rodsbooks.com/efi-bootloaders/installation.html](http://www.rodsbooks.com/efi-bootloaders/installation.html)

A Quick Installation Guide:
[http://www.rodsbooks.com/linux-uefi/#preparing](http://www.rodsbooks.com/linux-uefi/#preparing)

Be best to research installing on separate drives under UEFI. Incidentally, motherboards are not generally 'UEFI' and that's it. You have a choice. But if Win is installed in UEFI, you MUST install Ubuntu in UEFI. I would imagine this applies whether you install to the same disk or another. 

Main points, at least for an install on the same disk, are:

1/ Switch off fastboot and secureboot in the BIOS;
2/ Change Win8 'faststart' settings from within the Win8 OS:
[http://www.pcmag.com/article2/0,2817,2417361,00.asp](http://www.pcmag.com/article2/0,2817,2417361,00.asp)

You could also unplug the Win8 drive when you are installing. I *think* each drive needs to have an EFI partition, but only one per drive. Not sure if your Ubuntu install on the second drive will be added to the EFI partition on the original drive containing Win8. If you have a look in Gparted from a Live Ubuntu desktop you will see the EFI partition on the Win disk. It will be FAT partition and not big, between 100-500Mb. Then again, with 13.10, if it sees an EFI partition it may just add itself, regardless of which disk it's on. You could give it a try and see what happens. As you are installing on two separate disks you have little chance of overwriting Win8 and if Ubuntu adds itself to the EFI partition on the Win drive, great. If it doesn't, it *should* automagically create an EFI partition on the Ubuntu drive. If it doesn't, you could try again and create one manually. 

Just a note, choose 'Something Else' when you get to the partitioning sections of the install. 

Hopefully someone will jump in that knows about installing in UEFI with Win on one and Ubuntu on the other. As I say, I can get you through the single disk install but the two disk setup I'd be largely guessing. Good luck. ;)

---

### Post by shadowofsolidus on 2014-02-28
> **Bucky Ball said:**
> It's just a different way of going about it. Here's some light reading to get you started:

oldfred's tips:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Managing Everything UEFI:
[http://www.rodsbooks.com/efi-bootloaders/index.html](http://www.rodsbooks.com/efi-bootloaders/index.html)

EFI Bootloader Installation:
[http://www.rodsbooks.com/efi-bootloaders/installation.html](http://www.rodsbooks.com/efi-bootloaders/installation.html)

A Quick Installation Guide:
[http://www.rodsbooks.com/linux-uefi/#preparing](http://www.rodsbooks.com/linux-uefi/#preparing)

Be best to research installing on separate drives under UEFI. Incidentally, motherboards are not generally 'UEFI' and that's it. You have a choice. But if Win is installed in UEFI, you MUST install Ubuntu in UEFI. I would imagine this applies whether you install to the same disk or another. 

Main points, at least for an install on the same disk, are:

1/ Switch off fastboot and secureboot in the BIOS;
2/ Change Win8 'faststart' settings from within the Win8 OS:
[http://www.pcmag.com/article2/0,2817,2417361,00.asp](http://www.pcmag.com/article2/0,2817,2417361,00.asp)

You could also unplug the Win8 drive when you are installing. I *think* each drive needs to have an EFI partition, but only one per drive. Not sure if your Ubuntu install on the second drive will be added to the EFI partition on the original drive containing Win8. If you have a look in Gparted from a Live Ubuntu desktop you will see the EFI partition on the Win disk. It will be FAT partition and not big, between 100-500Mb. Then again, with 13.10, if it sees an EFI partition it may just add itself, regardless of which disk it's on. You could give it a try and see what happens. As you are installing on two separate disks you have little chance of overwriting Win8 and if Ubuntu adds itself to the EFI partition on the Win drive, great. If it doesn't, it *should* automagically create an EFI partition on the Ubuntu drive. If it doesn't, you could try again and create one manually. 

Just a note, choose 'Something Else' when you get to the partitioning sections of the install. 

Hopefully someone will jump in that knows about installing in UEFI with Win on one and Ubuntu on the other. As I say, I can get you through the single disk install but the two disk setup I'd be largely guessing. Good luck. ;)



thanks! It's Windows 7 btw.

---

### Post by Bucky Ball on 2014-02-28
So you're saying that Win7 is installed in UEFI?

---

### Post by shadowofsolidus on 2014-02-28
> **Bucky Ball said:**
> So you're saying that Win7 is installed in UEFI?


Yes.

---

### Post by Gordonbp531 on 2014-02-28
> **Bucky Ball said:**
> It's just a different way of going about it. Here's some light reading to get you started:

Main points, at least for an install on the same disk, are:

1/ Switch off fastboot and secureboot in the BIOS;
2/ Change Win8 'faststart' settings from within the Win8 OS:
[http://www.pcmag.com/article2/0,2817,2417361,00.asp](http://www.pcmag.com/article2/0,2817,2417361,00.asp)


Absolutely not necessary at all.
I installed Ubuntu on my Windows 8 Lenovo without changing ANY of the settings at all. It installed and runs just fine.

---

### Post by shadowofsolidus on 2014-02-28
> **gendibal said:**
> Absolutely not necessary at all.
I installed Ubuntu on my Windows 8 Lenovo without changing ANY of the settings at all. It installed and runs just fine.

Did you install it on a separate hard drive?

---

### Post by shadowofsolidus on 2014-02-28
nevermind, just found out that my Windows 7 OS is installed in BIOS legacy mode.

[http://www.eightforums.com/tutorials/29504-bios-mode-see-if-windows-boot-uefi-legacy-mode.html](http://www.eightforums.com/tutorials/29504-bios-mode-see-if-windows-boot-uefi-legacy-mode.html)

---

### Post by Gordonbp531 on 2014-02-28
No, but Bucky Ball was talking about the same drive...

---

### Post by oldfred on 2014-02-28
You can install Windows 7 in UEFI mode, but Windows 7 DVD installer only installs in BIOS boot mode. You can convert to flash drive and install some changes to make it work with UEFI. 

If you want to easily dual boot you have to have both Windows and Ubuntu in the same boot mode, or both BIOS or both UEFI. Once you start to boot you cannot switch to the other boot mode, or you cannot change boot with grub if not in same boot mode. You can use UEFI/BIOS or one time boot key to boot, but some UEFI/BIOS need settings changed like turn on BIOS/Legacy or turn off UEFI type settings to change boot mode.

       Some have issues with Asrock.
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

If Windows is BIOS, you need Ubuntu in BIOS mode. But if a separate hard drive I would use gpt partitioning as Ubuntu will boot in BIOS or UEFI boot mode from gpt partitioned drives. Windows only boots from gpt with UEFI and both Windows & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.

I would also include an efi partition at beginning of drive for future use in case you want to try UEFI later. The efi partition should be first or near beginning of drive, so difficult to add later and it does not take much room, maybe 300MB plus or minus. But with BIOS and gpt you need a 1 or 2MB unformatted partition with the bios_grub flag for grub2 to install correctly.


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by shadowofsolidus on 2014-02-28
> **oldfred said:**
> You can install Windows 7 in UEFI mode, but Windows 7 DVD installer only installs in BIOS boot mode. You can convert to flash drive and install some changes to make it work with UEFI. 

If you want to easily dual boot you have to have both Windows and Ubuntu in the same boot mode, or both BIOS or both UEFI. Once you start to boot you cannot switch to the other boot mode, or you cannot change boot with grub if not in same boot mode. You can use UEFI/BIOS or one time boot key to boot, but some UEFI/BIOS need settings changed like turn on BIOS/Legacy or turn off UEFI type settings to change boot mode.

       Some have issues with Asrock.
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

If Windows is BIOS, you need Ubuntu in BIOS mode. But if a separate hard drive I would use gpt partitioning as Ubuntu will boot in BIOS or UEFI boot mode from gpt partitioned drives. Windows only boots from gpt with UEFI and both Windows & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.

I would also include an efi partition at beginning of drive for future use in case you want to try UEFI later. The efi partition should be first or near beginning of drive, so difficult to add later and it does not take much room, maybe 300MB plus or minus. But with BIOS and gpt you need a 1 or 2MB unformatted partition with the bios_grub flag for grub2 to install correctly.


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)


What kinds and how much partitions do I need to make?

---

### Post by oldfred on 2014-02-28
The minimum is / and swap. We often suggest smaller / and larger data or separate /home partitions.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

