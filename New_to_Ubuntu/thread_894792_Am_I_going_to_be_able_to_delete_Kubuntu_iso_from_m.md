---
title: "Am I going to be able to delete Kubuntu iso from my usb stick?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by TheMaxzilla on 2008-08-19
Hooah.

I'm going to reformat a few computers, but all of the CD's I have are filled up, and too small. I tried to a previous version of ubuntu from a CD, and it said I did not have permission. (from a vista). Will I be able to take the iso off of the USB dongle from Kubuntu, if it works?

And do I just stick it in the usb stick, or are there any preperations I should take?

---

### Post by linuxguymarshall on 2008-08-19
You can remove anything off any usb drive :) 

I think there is a guide. Google "Run Ubuntu ISO from flash drive" and see what comes of it

---

### Post by LowSky on 2008-08-19
previous editions of Ubuntu could not be install from inside Windows
You will need to boot from them
 If you do want to creat a flashdisk Live CD the follow the instructions on [http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

---

### Post by aysiu on 2008-08-19
Your post is a little confusing.

> I tried to a previous version of ubuntu from a CD, and it said I did not have permission. (from a vista). Permission to do what? Did you actually run the CD? Was it Vista or Ubuntu that said you don't have permission (and again, to do what)?

> Will I be able to take the iso off of the USB dongle from Kubuntu, if it works? Are you installing Kubuntu to a USB stick or trying to run Kubuntu off a USB stick?

What *exactly* are you trying to accomplish?

---

### Post by TheMaxzilla on 2008-08-19
> Permission to do what? Did you actually run the CD? Was it Vista or Ubuntu that said you don't have permission (and again, to do what)?
I made a Kubuntu Live CD and tried to reformat over my current partition. During the installation, it froze at 69% and said there was a problem of some sort. So I booted back into my brother's vista (where I originally burnt the cd) and tried to delete everything off of the cd, and it said I didn't have the permission to format the cd. So now my computer is OS-less. I don't have any CDs big enough to make another one, and can install it from another computer on my network.

All I want to do is put Kubuntu on my laptop via USB, and delete Kubuntu off of the USB when I'm done.

---

### Post by aysiu on 2008-08-19
Unless it was a CD-R, you usually can't delete things off a CD once it's burnt.

This should help you get Kubuntu to boot from USB:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Once it's installed, you should be able to easily delete the installation files from the USB stick.

---

### Post by TheMaxzilla on 2008-08-19
It was actually a CD-R.

Will the LiveUSB thing work with windows?

---

### Post by aysiu on 2008-08-19
> **TheMaxzilla said:**
> It was actually a CD-R.

Will the LiveUSB thing work with windows?
The instructions I linked to above allow you to make the bootable USB of Kubuntu from either Windows or Linux.

Whether you can boot from a USB stick or not is up to your computer's BIOS.

---

### Post by TheMaxzilla on 2008-08-19
My BIOS allows me to boot from a USB stick. Should the order be

1: USB
2: CD
3: HDD
4: FDD
5: something

Or should it be CD, HDD, etc, and Just select it to boot from the USB stick for that time.

---

### Post by aysiu on 2008-08-19
> **TheMaxzilla said:**
> My BIOS allows me to boot from a USB stick. Should the order be

1: USB
2: CD
3: HDD
4: FDD
5: something

Or should it be CD, HDD, etc, and Just select it to boot from the USB stick for that time.
The order should put USB first, but you can also select it to boot from USB for that one time only.

To make sure you don't get any freeze-ups, you may want to download Kubuntu's .iso through BitTorrent, as that is less likely to result in a corrupted download file. More details here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

