---
title: "Install on Asus Zenbook 15"
date: 2019-06-22
forum: New to Ubuntu
---

### Post by spizzy84 on 2019-06-22
Hi there. 

Want to install ubuntu 18 bionic beaver

Got stuck on grub2 while installing. 

Asus zenbook 15

Please advise

---

### Post by Dennis N on 2019-06-22
The installer usually shows an error message when it doesn't finish. It would be useful to post what that says. Also, are you doing a UEFI install?

---

### Post by spizzy84 on 2019-06-23
Yes, uefi. And no message. It's just freezes on installing grub2.

I can access the try ubuntu without installing  and terminal and such.

Just when I try to install it always freezes.

---

### Post by spizzy84 on 2019-06-23
I tried this:
[https://askubuntu.com/questions/1126191/ubuntu-installation-hangs-at-installing-the-grub2-package](https://askubuntu.com/questions/1126191/ubuntu-installation-hangs-at-installing-the-grub2-package)

I tried :
[https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Sys doesnt want to mount

Thanks for replying

---

### Post by ajgreeny on 2019-06-23
I have no personal experience of such problems but have a good read through the information in the long thread at [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) in particular relating to requirements of Asus machines when booting with UEFI.

---

### Post by TheFu on 2019-06-23
I have an Asus F510UA UEFI 15" laptop. Don't remember any issues installing 16.04.5 with Ubuntu-Mate.  Didn't have to manually touch anything in the /boot/efi/ area or in the BIOS at all like I did on prior Toshiba laptops.

```
$ sudo find /boot/efi/
/boot/efi/
/boot/efi/EFI
/boot/efi/EFI/ubuntu
/boot/efi/EFI/ubuntu/fw
/boot/efi/EFI/ubuntu/fwupx64.efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/ubuntu/grub.cfg
/boot/efi/EFI/ubuntu/shimx64.efi
/boot/efi/EFI/ubuntu/mmx64.efi

```
are all the things under /boot/efi/ on my system.  Also, my system is using LVM and LUKS encryption.

The mounts with 'efi' in the name are:
```
$ mount|grep efi
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime) 
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

```

Sorry, I'm unwilling to touch 18.04.

---

### Post by jikaczmarski on 2019-06-23
Are you saying that you get through that second tutorial but the install gets hung up on ```
mount --bind /sys /mnt/sys
```
How far are you able to get in these tuts before things get weird?

---

### Post by Dennis N on 2019-06-23
It may be covered in some of the suggested links in previous posts, but two general pieces of advice I have seen regarding installing as UEFI dual boot with Windows 10:
1) disable Fast Boot from Windows before installing Ubuntu.
2) disable secure boot in UEFI.

---

### Post by spizzy84 on 2019-06-23
Until there. There it just says sys not found

---

### Post by spizzy84 on 2019-06-23
Done. And I want just linux to boot. No dual

---

### Post by spizzy84 on 2019-06-23
> **jikaczmarski said:**
> Are you saying that you get through that second tutorial but the install gets hung up on ```
mount --bind /sys /mnt/sys
```
How far are you able to get in these tuts before things get weird?

Just till the sys mount part. Doesnt mount it.

---

### Post by crip720 on 2019-06-24
Did your drive already have Windows on it or is this a blank drive, if it is blank, you will have to make a EFI partition on it first.

---

### Post by oldos2er on 2019-06-24
Changed title to better reflect question.

---

