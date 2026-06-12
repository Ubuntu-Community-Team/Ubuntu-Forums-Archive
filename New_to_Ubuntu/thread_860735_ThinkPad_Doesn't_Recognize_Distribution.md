---
title: "ThinkPad Doesn't Recognize Distribution"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by CompBio on 2008-07-15
I'm trying to install Ubuntu on a Lenovo ThinkPad.  The machine had the Windows Vista installation files written to the HDD at the factory.  I want to wipe the disk and install Ubuntu, but I cannot get the machine to boot from the flash drive that has the Ubuntu distribution on it.

I've used the ThinkVantage and F1 keys to access the BIOS, but when it comes up, USB FDD shows as the primary boot device.  (I assume FDD is the flash device?)

The machine is a ThinkPad R61 with 3 flash drives.  It's also got a CD/DVD optical drive, but I have heard and read that I can use a flash drive to install Ubuntu.  I assume I'm doing something wrong with the BIOS access program.

I should mention that I have NOT installed Vista yet.  As soon as the Vista config screen comes up, I shut down the machine and start over.  I hate the idea that I would have to install Vista before I can remove it.  Is that the answer?

Many thanks for your insights.

---

### Post by phidia on 2008-07-15
You might want to check out the community [pages on installation]("https://help.ubuntu.com/community/Installation").
FDD btw I believe refers to floppy disk drive.
See if you can make a different selection in bios.

---

### Post by CompBio on 2008-07-15
> **phidia said:**
> You might want to check out the community [pages on installation]("https://help.ubuntu.com/community/Installation").
FDD btw I believe refers to floppy disk drive.
See if you can make a different selection in bios.

Thanks, that does look like a good resource.  I perused it but most of the instructions simply say "boot from the USB" without mentioning what to do if the computer won't do that.  Other options (e.g., syslinux) seem to require some version of Windows already installed.

Much of the information has to do with getting the files onto a flash drive.  I already did that using the 'dd' command (on a Linux machine) as recommended at another site.

I really thought I just had to set the correct boot order.  The current boot order is:

1. USB FDD
2. ATAPI CD0 DVD/CDRW
3. USB CD
4. ATA HDD0
5. PCI LAN
6. ATA HDD1
7. USB HDD

I've tried moving "USB HDD" and "USB CD" to the top of the list, with no luck.  Would it matter which USB port I put the flash drive into?

I suspect my best option at this point will be to drop back and punt: go back over to school, find a machine with a DVD burner and go that route. :sad:

---

### Post by phidia on 2008-07-16
IMO #7 usb hdd is the correct selection. You may not have the files on the drive correctly, and for a usb thumb drive to boot requires some other tweaks I think.

---

### Post by unutbu on 2008-07-16
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)
has instructions on how to install Linux on a flash drive. It looks to be more complicated than dd'ing the LiveCD onto the drive.

---

