---
title: "i have windows 10 and linux mint and 2ant to install ubuntu"
date: 2018-11-08
forum: New to Ubuntu
---

### Post by xyddyx12 on 2018-11-08
Hi i am new in linux and i decided to install mint along with my windows 10. In my linux mint i already have swap home and root partition. I want to install ubuntu as my 3rd os so i will be familiarize both mint and ubuntu. My questions are how do i install ubuntu. Do i need to create swap partition again or i can use the swap from linux mint. Can i use the same home partition in my mint for ubuntu. Please guide me on this one as i am a new user and want to learn linux. Thanks.

---

### Post by oldfred on 2018-11-08
Do not share /home. User settings between systems may conflict.
You really only need / (root)

If both Windows & Mint are correctly installed in UEFI boot mode, then be sure to install Ubuntu in UEFI boot mode.
How you boot install media UEFI or BIOS is then how it installs.

If you want to share data you may want either or both extra partitions, one NTFS to allow sharing with Windows and/or ext4 for data you only want to share with Linux installs.

If not keeping data in /home you can have a / of 25GB and will not use a lot of it.

I believe that Mint may use /EFI/ubuntu for its UEFI boot. If so Ubuntu will overwrite that. And then os-prober will add Mint to Ubuntu's menu.
If you want Mint as default you have to reconfigure /EFI/ubuntu or reinstall grub. Updates my reset to that systems. So be sure to back up all of ESP 0 efi system partition.

New versions of Ubuntu do not use swap partition unless one already exists. It uses a swap file.
You can share swap if you do not hibernate, otherwise you have conflicts.

Otherwise install is just like any other install.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


See also link in my signature.

---

