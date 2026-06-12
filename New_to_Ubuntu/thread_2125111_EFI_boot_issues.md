---
title: "EFI boot issues"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by gdy on 2013-03-13
I installed Ubuntu 12.10 the other day & have been happily playing with it, until I tried to boot into Windows 8.

When I tried the first time I got error Invalid EFI file path.

So I read and read and tried a few things, but all i can get now is the Windows boot logo but it freezes there.
Ubuntu loads fine :)

I have tried the boot repair ISO- it complained and told me to get the linux-secure-12.10 64 bit ISO.
I tried the boot repair and it failed also.

My laptop is an ASUS G75VW.

The error message is now complaining that sda1/EFI/grubx64.efi is missing & I have no clue how to progress.

[http://paste.ubuntu.com/5607181](http://paste.ubuntu.com/5607181)

Grateful for any help!

Cheers

---

### Post by ibjsb4 on 2013-03-13
I do not use EFI, but got some hits that may help you out.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=EFI%2Fgrubx64.efi+is+missing&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=EFI%2Fgrubx64.efi+is+missing&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2013-03-13
You have Windows in UEFI mode with gpt partitioning on sda.
And you have Ubuntu in MBR(msdos) mode on sdb.
Ubuntu will boot in BIOS mode from gpt or MBR drives.
And up until a recent post I thought you could not boot UEFI from a MBR drive, but I think a recent post did somehow make it work with UEFI on one drive and Ubuntu in MBR on another drive like you have. 
But better to have Ubuntu in UEFI mode from a gpt drive.

Do you have a lot of data in the NTFS partition on the MBR drive? There is a way to convert a MBR drive to gpt but I have never tried it. Backups would be vital.

Was this pre-installed Windows 8 with secure boot?
And do you have secure boot off? And fast boot off?

---

### Post by gdy on 2013-03-14
Thanks for the info... I upgraded from a bare Win7 install to Win 8 Pro. I do have a lot of programs installed on the Win 8 side which I would hate to lose.

 I have no idea about secure boot or fast boot- I have looked into the BIOS and didn't see anything called that.
I have played with the boot order in the BIOS but couldn't get it to magically work :)

Cheers

---

### Post by oldfred on 2013-03-14
You would have to install Ubuntu's grub-pc (BIOS) on the MBR of sdb. Then each time you changed booting would have to go into BIOS and either turn UEFI on to boot Windows or off to Boot Ubuntu. Not the easiest.

If you installed over Windows 7, your system does not have secure boot. But I thought all Windows 8 had fast boot as that is its hibernation. But I have seen fast boot settings in UEFI also which skip the UEFI boot at startup and then you only can get to UEFI/BIOS via Windows. I think that is only on new pre-installed Windows 8 systems.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

If you want Ubuntu in UEFI mode, you need a efi partition near the start of sdb. If Ubuntu is on a gpt partitioned drive and you want to boot in BIOS you need a bios_grub partition.

---

