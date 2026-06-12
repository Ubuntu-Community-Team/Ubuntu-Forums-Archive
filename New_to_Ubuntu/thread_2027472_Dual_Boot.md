---
title: "Dual Boot"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by SoulReaver16 on 2012-07-16
I got interested in Ubuntu and wanted to try it out. Though, I do not want to make it my main OS. Right now I am using Windows 7 64 Bits.
I saw some ways to do it, but for some reason it looked a bit too risky. I recently bought this laptop for $700 and do not want to lose it.
Is there perhaps any easy way to do it without the risk of doing anything wrong and losing your laptop?

---

### Post by MG&amp;TL on 2012-07-16
> **SoulReaver16 said:**
> I got interested in Ubuntu and wanted to try it out. Though, I do not want to make it my main OS. Right now I am using Windows 7 64 Bits.
I saw some ways to do it, but for some reason it looked a bit too risky. I recently bought this laptop for $700 and do not want to lose it.
Is there perhaps any easy way to do it without the risk of doing anything wrong and losing your laptop?

You won't 'lose' the hardware, you'll just need to fix and/or reinstall replace Windows if something goes wrong (which it rarely does).

If you're worried about it, try Wubi (Windows UBuntu Installer), which installs like any normal Windows application and does not partition your disks.

---

### Post by lukeiamyourfather on 2012-07-16
> **MG&TL said:**
> You won't 'lose' the hardware, you'll just need to fix and/or reinstall replace Windows if something goes wrong (which it rarely does).

If you're worried about it, try Wubi (Windows UBuntu Installer), which installs like any normal Windows application and does not partition your disks.

That's a great way to try it out. If you find you like it and use it a lot consider doing a native install (more reliable and higher performance).

---

### Post by oldfred on 2012-07-16
Wubi is one way to try out Ubuntu. It is just a file in the NTFS partition and uses the Windows boot loader, then becomes an emulation of full Ubuntu. But it relies on Windows & NTFS, so not intended for long term use.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can install to another hard drive or even a flash drive. On a flash drive are several ways to install. One is just the installer which is just like the CD and is just for installing. But with a flash drive you can also modify it slightly to allow some data to be saved, this is called persistence. If you have a larger (8GB or more) flash drive you can actually do a full install. Full install on flash is not speedy but functional. Sometimes the lightweight versions work a bit better as they do not have to load as much data.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by dragonboss on 2012-07-16
There isn't anything you can do that will make you "lose" the laptop, apart from throwing it from a high place. If you want to try ubuntu, you can, after downloading the iso file from [here]("http://www.ubuntu.com/download"):

a) Burn it to a disc and boot from disc without installing or changing the computer's data.

b) Make a bootable USB drive which is the same as above, but no cd.

c) Install to a usb drive which only puts ubuntu on the flash drive and you can use it by booting to the usb drive, this also makes no changes to your system, unless you delete or download files to your harddrive.

d) Install a virtual version in windows using Virtualbox or other software of your choice.

e) Install alongside Windows which basically divides your harddrive into two parts, you can choose which is bigger, and when you start the computer a list appeaars for you to choose whether you want Windows or Ubuntu.

f) You can take a limited tour of ubuntu [here]("http://www.ubuntu.com/tour/en/")

---

### Post by SoulReaver16 on 2012-07-16
I think I'll use wubi. Last time I tried to split my hard drive (on another laptop) it completely failed and I had to completely re-install windows (It took me 3 hours to find the damn CD) and lost all my files. It also took me hours to splitstream sata files which allowed me to install windows but screw my wireless adapter.

---

