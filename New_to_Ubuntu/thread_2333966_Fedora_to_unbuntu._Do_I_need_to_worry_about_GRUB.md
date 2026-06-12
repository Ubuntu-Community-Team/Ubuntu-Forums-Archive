---
title: "Fedora to unbuntu. Do I need to worry about GRUB?"
date: 2016-08-15
forum: New to Ubuntu
---

### Post by Delupara on 2016-08-15
I'm not sure if this is considered a new to ubuntu question, but I'm gonna assume so. I used to have fedora, which I grew tired of since it was constantly filled with bugs and the overall low ammount of support it got, but I'm still left with the grub associated to it. If I would install Ubuntu on my system will it overwrite GRUB? Or I will need to get rid of it before installing ubuntu? My guess is not, a boot file is pretty easy to overwrite so I don't think it would be an issue but I am asking here just in case Hell maybe its the same GRUB used in both distros.

#Quick edit, It would be assumed that the current GRUB is installed on uefi since my other OS is windows 10.

---

### Post by howefield on 2016-08-15
Ubuntu will install it's own grub and control the booting of the machine overwriting the Fedora boot loader.

I'd look for oldfreds posts in these forums for advice on installing to a UEFI machine if you are unsure as to what to do.

---

### Post by Delupara on 2016-08-15
Im pretty positive on what to do. [But I can't boot my burned dvd to start off with]("https://ubuntuforums.org/showthread.php?t=2333969"), so things wont go too far.

---

### Post by Dennis N on 2016-08-15
I would create the install media on a USB rather than DVD. I now only use a tool which employs dd to create the installer, like mkusb. These are most reliable. 

You need to boot it in UEFI mode to install the OS in UEFI mode.

In a UEFI system, Ubuntu will install a boot loader into it's own folder in your EFI system partition. It won't interfere with other boot loaders except for those installed by another Ubuntu based distro - those it will replace (includes any Ubuntu 'flavor' and also a Linux Mint distro which uses Ubuntu's installer). A new Ubuntu install will also create an entry for itself in first position in the UEFI boot manager's menu so it will boot to Ubuntu's grub by default. Ubuntu's grub can be used to boot most other distros present on the computer.

Old boot files from Fedora can be left alone. They won't cause a problem. If there is an old Fedora entry in the UEFI boot manager, you can remove that with the efibootmgr.

---

### Post by oldfred on 2016-08-15
I prefer USB installs, usually quicker.
If Windows is UEFI you want Ubuntu in UEFI boot mode, and how you boot flash drive UEFI or CSM is then how it installs.
You may need to turn on allow USB boot or UEFI USB boot setting in UEFI, And Windows may have turned on Secure boot. While you should be able to install with Secure boot on, often better to have it off.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by Delupara on 2016-08-15
> **oldfred said:**
> I prefer USB installs, usually quicker.
If Windows is UEFI you want Ubuntu in UEFI boot mode, and how you boot flash drive UEFI or CSM is then how it installs.
You may need to turn on allow USB boot or UEFI USB boot setting in UEFI, And Windows may have turned on Secure boot. While you should be able to install with Secure boot on, often better to have it off.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

I knew this, but thank you. My boot mode is uefi (that essentially applies to all my drives). as for usb I only have 1 64 gb usb and I cannot format it, so I cannot go that way.

> **Dennis N said:**
> I would create the install media on a USB rather than DVD. I now only use a tool which employs dd to create the installer, like mkusb. These are most reliable. 

You need to boot it in UEFI mode to install the OS in UEFI mode.

In a UEFI system, Ubuntu will install a boot loader into it's own folder in your EFI system partition. It won't interfere with other boot loaders except for those installed by another Ubuntu based distro - those it will replace (includes any Ubuntu 'flavor' and also a Linux Mint distro which uses Ubuntu's installer). A new Ubuntu install will also create an entry for itself in first position in the UEFI boot manager's menu so it will boot to Ubuntu's grub by default. Ubuntu's grub can be used to boot most other distros present on the computer.

Old boot files from Fedora can be left alone. They won't cause a problem. If there is an old Fedora entry in the UEFI boot manager, you can remove that with the efibootmgr.

I assumed as much, but you're never too careful am I right?

---

### Post by oldfred on 2016-08-15
Almost every flash drive I have is a bootable device for emergency repair.
Some I just install grub either BIOS or UEFI and copy an ISO or two for install or repair only. I use grub to directly boot ISO.
Some larger one's I have a full install of Ubuntu in a smaller partition as I do not add much extra software and also add some ISOs for install.
Then use extra space for data.

If you only have on flash drive, time to purchase another one or two. I live near a Microcenter and they have their housebrand flash drives behind counter. Every time I go they are cheaper, or cheaper for larger or then USB3, so I end up with a new flash drive every time I go to computer store. :)

---

### Post by Delupara on 2016-08-15
> **oldfred said:**
> Almost every flash drive I have is a bootable device for emergency repair.
Some I just install grub either BIOS or UEFI and copy an ISO or two for install or repair only. I use grub to directly boot ISO.
Some larger one's I have a full install of Ubuntu in a smaller partition as I do not add much extra software and also add some ISOs for install.
Then use extra space for data.

If you only have on flash drive, time to purchase another one or two. I live near a Microcenter and they have their housebrand flash drives behind counter. Every time I go they are cheaper, or cheaper for larger or then USB3, so I end up with a new flash drive every time I go to computer store. :)

Probably. But regardless I've installed it using the slow and unfavored method (Because I'm bowse like that).

However, There's something wrong. I now have 4 entries to boot from in my HDD (by selecting it from the boot menu accessed trough F12 at power up) here they are:

ubuntu (Brings me to GNU GRUB)
Fedora (Brings me to fedora Grub)
windows boot manager (Brings me to windows)
Ubuntu (Updated: brings me to the same GRUB menu as the other ubuntu)

Updated: Normal powerup does bring me to GNU GRUB (the ubuntu one)

So now I have 2 ubuntu entries, Fedora did not get overwritten and windows boot manager is still there???

I'm lost.

---

### Post by oldfred on 2016-08-15
Ubuntu normally has two entries, one grub and one shim. Where shim is the secure boot version or shim between secure boot and grub and the other is grub. But shim works with secure boot off.

UEFI NVRAM remembers entries. So if you do not have Fedora you may need to remove the entry in UEFI with efibootmgr. And UEFI may refind entries if you still have a /EFI/fedora folder in ESP - efi system partition. 

       Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu, similar for any entry
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

If issues with getting to correctly see ESP, then it may be the permissions of the mount in your install. Either use live installer or edit fstab by changing mount of ESP to defaults like 14.04 used to use.

 14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    [COLOR=#ff0000]defaults[/COLOR]        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1 


 sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab

sudo mount -a
if not errors then edit was ok, but remount does not remount the ESP, you have to reboot.

---

### Post by Delupara on 2016-08-16
Thanks, I'm not a complete noob but I did not know that UEFI had NVRAM, I assumed it was SRAM. Alright, thanks for the tip.

update: Yeah seems /EFI/fedora was still there, got rid of it.

I also wonder why I have a boot file and a toshiba file in efi.(My manufacturer), any Ideas???

---

### Post by oldfred on 2016-08-16
Many systems have a /EFI/Boot/bootx64.efi. That is a hard drive boot entry or fallback entry.
Most Windows machines it is just a copy of the Windows efi boot file. I copy shim to that file myself and for many systems that only boot Windows that is a work around to have them boot. And bootx64.efi is the file used to all all external drives.

Vendors also add .efi files to boot into recovery mode or other system utilities. HP has 5 or 10 and Boot-Repair adds all of them to grub filling the grub menu. Most do not need vendor utilities in grub, but you may need it to do vendor recovery or other vendor suggested fixes.

---

