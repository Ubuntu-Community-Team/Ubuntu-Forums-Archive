---
title: "No Operating System found on USB - 14.04"
date: 2014-10-14
forum: New to Ubuntu
---

### Post by PopSmith on 2014-10-14
I successfully installed Ubuntu 14.04 from a Live DVD to my USB flash drive (Patriot Supersonic Boost XT 16GB) last night via the "Install Ubuntu" option on boot. I *believe *I chose the "Erase disk and install Ubuntu" option but I'm not entirely sure. I then rebooted, removed the DVD and updated the installation with:
```
sudo apt-get update
sudo apt-get upgrade
```

When I tried to boot the USB this morning I got a "No operating system found" error. My computer has UEFI but as far as I can tell it's set to legacy for the USB drive.

For what it's worth, I ran the boot repair and this was the outcome:

[pastebin.ubuntu.com/8560276]("http://pastebin.ubuntu.com/8560276")

Can I just repair/change something and be OK?

---

### Post by JeQhdMD on 2014-10-14
Did you already updates the UEFI setup so the boot order shows USB or removable flash drive first (instead of hard drive)?

---

### Post by grahammechanical on 2014-10-14
Is there a hard disk in that machine? Is there an operating system on it? Can you still load the OS on the hard disk? Did you direct the installer to install Ubuntu on the USB memory stick? Are you sure that it did not install Ubuntu to the hard disk? Did you choose to encrypt the /home folder? Is sda the USB memory stick or the hard disk?

Regards.

---

### Post by frank75 on 2014-10-15
sda is normally the internal hard drive with sdb being the first USB device that is found(then sdc, sdd, ect.) Make sure that the USB stick is large enough to do an install on(8GB or more wouldn't hurt anything) and make sure that you've actually done the install to the USB, i.e. sdb and not the internal hard drive, sda.  Also you need to make sure that you've pointed GRUB at sdb as well so you can boot to the new system that's installed on the USB stick.  While using a USB stick for install will work getting an old hard drive(SSD drives are awesome for this, even a small 16GB one works well) and putting it into an external enclosure works even better because they tend to be a bit faster then a USB stick and being an actual hard drive they just seem to work better.   Try and re-install the system onto the USB stick and while you're booted to the Live DVD use gparted or disks to format the USB stick to ext4 so it'll be ready to accept the new op system.  Hope this helps.

---

### Post by PopSmith on 2014-10-15
I just decided to reformat the drive and conduct some trial-and-error experiments. I only had the issue reoccur once (out of 4 re-installs). I believe it was caused by a corrupted file of some sort because the only time it happened was after the system got hung up on shutdown and I powered it off manually.

> **JeQhdMD said:**
> Did you already updates the UEFI setup so the boot order shows USB or removable flash drive first (instead of hard drive)?

I changed the BIOS to 1) UEFI USB 2) HDD 3) (non-UEFI) USB with no luck.

> **grahammechanical said:**
> Is there a hard disk in that machine? Is there an operating system on it? Can you still load the OS on the hard disk? Did you direct the installer to install Ubuntu on the USB memory stick? Are you sure that it did not install Ubuntu to the hard disk? Did you choose to encrypt the /home folder? Is sda the USB memory stick or the hard disk?

Regards.

*Technically*, yes. I disconnected the HDD (and SSD) (both power and the SATA cable) before running the Live DVD for Ubuntu so all Ubuntu could see was the USB drive. The /home folder *is* encrypted. sda is the USB as both the HDD and the SSD are disconnected from the motherboard.

> **frank75 said:**
> Try and re-install the system onto the USB stick and while you're booted to the Live DVD use gparted or disks to format the USB stick to ext4 so it'll be ready to accept the new op system.  Hope this helps.

I did this (after reading your reply) and it fixed the issue. I haven't come across it since.

Thanks for all the help, everyone!

---

