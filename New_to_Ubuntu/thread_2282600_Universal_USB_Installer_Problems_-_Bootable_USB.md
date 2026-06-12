---
title: "Universal USB Installer Problems - Bootable USB"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by Ambrosiaster on 2015-06-15
Hello,

I've used the Universal USB Installer program many times in the past, but I noticed that with the recent update to 1.9.6.0 the exact versions of the OSs aren't listed; instead, it just shows Ubuntu, etc. I've been trying to set up a USB drive for either Ubuntu or Xubuntu, but both failed with the same errors. Here's a screen shot - [http://i.imgur.com/LwYvsZd.jpg](http://i.imgur.com/LwYvsZd.jpg) - I'm not sure what the issue is here? 

Appreciate any help.

---

### Post by sudodus on 2015-06-15
There are several tool to make bootable USB drives. I suggest that you try another tool that you find from the following link, or a link from it.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You are welcome back, if you need more help.

---

### Post by Bucky Ball on 2015-06-15
You can choose your own .iso image. Step #1 to Ubuntu and click 'Browse' at step #2.

First, download the appropriate image> launch Universal USB Inst.> choose the .iso you downloaded. ;)

I prefer [Unetbootin]("http://unetbootin.sourceforge.net/") myself.

---

### Post by Ambrosiaster on 2015-06-15
I tried UNetbootin and now I'm getting a new error. When I plug the USB drive into the device, it says:

> error: file '/casper/vmlinux.efi' not found. unaligned pointer 0xc6cbc048. Aborted. Press any key to exit.

---

### Post by sudodus on 2015-06-15
I suggest that you use the current version of Unetbootin from the developer's PPA, not the version from Ubuntu's repository.

[https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa]("https://launchpad.net/%7Egezakovacs/+archive/ubuntu/ppa") 
```
sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin
```

That version works for me.

Edit:

By the way, which version of Ubuntu are trying?

Did you check the [md5sum of the iso file]("https://help.ubuntu.com/community/UbuntuHashes")?

---

### Post by Ambrosiaster on 2015-06-15
I'm using a Windows machine at the moment, as I got rid of my old Linux box. I'm trying Ubuntu 14.04 and even Xubuntu - same version. No luck.

---

### Post by sudodus on 2015-06-15
Did you check the [md5sum of the iso file]("https://help.ubuntu.com/community/UbuntuHashes")?

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to help.

-o-

Have you tried the USB boot drive in another computer?

If you still have problems to create the USB boot drive, you can try according to [https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by Ambrosiaster on 2015-07-02
I think it had something to do with the USB drive. I trashed it and just put the OS on a DVD-RW. Thanks all.

---

### Post by Bucky Ball on 2015-07-03
If your original support issue is solved please see the second link in my signature. Thanks.

---

