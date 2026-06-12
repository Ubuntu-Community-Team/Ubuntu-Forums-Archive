---
title: "Bootable USB and free space"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by MutsX on 2012-10-21
I'm fairly new to Ubuntu, and I have a question. Today, I installed Ubuntu 12.10 on my 4 gb USB stick. It works perfectly fine, but I was wondering: since Ubuntu doesn't require the full 4 gb, is it possible to Use the other space to save documents, photos, etc?

At this point, it recognizes my PC's HDD partitions and the Ubuntu OS portion of my USB. My goal is to boot Ubuntu from the USB and save my documents on the same USB stick, so that I can take the USB with me and don't have to rely on internet to access my files.

---

### Post by oldfred on 2012-10-21
Welcome to the forums.

It is called persistence.

Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

---

### Post by MutsX on 2012-10-21
Thanks, that was what I was looking for! 
Created 2 new questions:

1) Live CD option is not possible with 12.10 due to the size? Therefore I have to use 12.04?

2) Is it possible to partition the USB drive in windows (before or installing ubuntu on it), instead of using the live CD options mentioned in the links of the previous comment? (because I have no other Linux PC)

---

### Post by oldfred on 2012-10-21
I now only have Linux, so not sure. Most of the installers overwrite the entire flash drive.

My system did let me install from one flash drive to another flash drive.

The older versions or the lightweight versions of Ubuntu like Lubuntu or Xubuntu should fit on CD, but I have not tried.

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

I like to have several versions of Ubuntu, gparted and some other repairCDs. I now have several flash drives and put multiple ISO on one flash drive and boot with grub2 loopmount feature. I used to use a lot of CDs when upgrading as I then wanted the latest version of everything.

---

### Post by newb85 on 2012-10-21
If you're looking to create a persistent Live USB of 12.10 using Windows, you're probably best off looking here.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

This way, I don't believe you'll need to burn Ubuntu to a CD or DVD.

*Note: I haven't personally used this installer, but I've heard good reports from others on this forum who have.*

---

### Post by MutsX on 2012-10-22
I wanted to say: "I did use pendrivelinux to get Ubuntu on my usb, but it is not persistent", but then (while checking the link to make sure it was the same pendrive)I noticed a fourth step in the pendrive installation, namely: persistence. So I'm trying that now, hoping that it will solve my problem! If so, thank you all very much!

---

### Post by MutsX on 2012-10-22
Works fine now thanks!

Only one minor issue left:
when i boot up ubuntu it keeps asking whether i want to try ubuntu or instal it.
is there a way to disable this and directly boot ubuntu?

---

### Post by black veils on 2012-10-22
open terminal, copy-paste:
```
sudo apt-get remove ubiquity
```press Enter, then let it process.


this removes the ubuntu installer, so you wont have that wizard. if you at some point want to install ubuntu from that usb stick:
```
sudo apt-get install ubiquity
```

---

