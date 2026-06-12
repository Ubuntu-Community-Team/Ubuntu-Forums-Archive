---
title: "Problems creating bootable USB"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by Anisaz on 2012-11-14
Hello,

I am trying to install Ubuntu from a bootable USB stick. However, it seems that it is written corrupted on the USB. I have tried both the ubuntu-12.10-desktop-i386 and the ubuntu-12.04.1-desktop-i386 ISO files. I have tried Universal-USB-Installer-1.9.1.5, YUMI-0.0.7.9 and the latest version of LiLi. Sometimes, I would get "**syslinux error: No DEFAULT or UI configuration directive found". **Other times, I would get "invalid or corrupt kernel image". Looking at the USB contents, the syslinux folder and some other folders would display really strange contents, with folder names being parts of a phrase and the next folder or file being a continuation of that phrase. Other times, the syslinux folder would be empty.

I have tried it on a USB stick formatted with FAT and FAT32. I have scanned the USB stick for errors and it came out all right. I have checked the md5sum of the .iso files and it was correct.

What could be the problem?

I should add that I want to install it to an Asus Eee Pc that has no optical drive, so I can only use a USB stick.

---

### Post by pkadeel on 2012-11-14
> **Anisaz said:**
> Hello,

I am trying to install Ubuntu from a bootable USB stick. However, it seems that it is written corrupted on the USB. I have tried both the ubuntu-12.10-desktop-i386 and the ubuntu-12.04.1-desktop-i386 ISO files. I have tried Universal-USB-Installer-1.9.1.5, YUMI-0.0.7.9 and the latest version of LiLi. Sometimes, I would get "**syslinux error: No DEFAULT or UI configuration directive found". **Other times, I would get "invalid or corrupt kernel image". Looking at the USB contents, the syslinux folder and some other folders would display really strange contents, with folder names being parts of a phrase and the next folder or file being a continuation of that phrase. Other times, the syslinux folder would be empty.

I have tried it on a USB stick formatted with FAT and FAT32. I have scanned the USB stick for errors and it came out all right. I have checked the md5sum of the .iso files and it was correct.

What could be the problem?

I should add that I want to install it to an Asus Eee Pc that has no optical drive, so I can only use a USB stick.
[S]The problem is probably with the ISOs. Have you checked their md5 hashes? if not then consult the following links.[/S]
Sorry didn't read your post properly.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by jaymee126 on 2012-11-14
> I have tried it on a USB stick formatted with FAT and FAT32

try to format in NTFS or if it is possible in ext2

---

### Post by squakie on 2012-11-14
I would stongly recommend you use unetbootin to create the flash.  There are versions available for Windows and for Linux, so you shouldn't have a problem running it somewhere.  It does require net access (unless you already have the ISO, but I would recommend letting it do the download).  I haven't had that fail for me if that's the option you want.  If you have a running Ubuntu system, I believe you can create the same thing via the boot disk creator (I forget the exact name - I'm sure someone else can help you on that route).  With unetbootin I *think* it does the formatting as well, so you shouldn't have to worry about that.

---

### Post by newb85 on 2012-11-14
> **squakie said:**
> I believe you can create the same thing via the boot disk creator (I forget the exact name - I'm sure someone else can help you on that route).

It's called Startup Disk Creator.  As squakie said, that's only helpful from a working Ubuntu system.

---

### Post by Anisaz on 2012-11-14
Formatting it in NTFS didn't work, so I figured the USB stick must be broken. I bought another one and I managed to install the image on it without the funky folder names.

However, now the computer won't boot from it. It is detected in BIOS as UEFI USB or something like that, but when I restart, the computer skips to the next boot option.

I tried both NTFS and FAT with the new USB stick. Unetbootin does not offer Ubuntu 12.10 as an option and I did not get the option to format in ext2.

Is there something else I could try?

---

### Post by Cheesemill on 2012-11-14
Use Unetbootin but select your 12.10 image manually by browsing to the .iso file instead of selecting it from the drop-down list.
Just click on the 'Diskimage' radio button then on the browse button '...' to select your ISO.

FAT32 always works for me when creating bootable USB's, the only times I've had problems is when I haven't been using Unetbootin to create them.

---

### Post by I2k4 on 2012-11-14
I've tried the three Windows installers you listed and have had consistent good results from the Pendrive Universal.  Yumi seems focused on multibooting from the USB and has a long multiclick boot selection sequence, and LiLi takes a very long time churning for the Live USB to boot.  

You don't say if you are letting the Pendrive installer format for you.  There is a dialog tick box for that and I'd suggest using it instead of formatting through Windows.

I was going to mention that I recently for the first time had a thumb drive go bad on me, which was confusing, but see you've got a new one now.

---

### Post by Anisaz on 2012-11-14
I've tried the bootable USB on a Lenovo laptop and it boots normally into Ubuntu. I've also tried an older Asus laptop and it doesn't work either. It seems that the problem is with Asus. I've e-mailed Asus and I'll wait for their answer.

---

