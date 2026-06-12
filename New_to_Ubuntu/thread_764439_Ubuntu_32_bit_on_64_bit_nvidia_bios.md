---
title: "Ubuntu 32 bit on 64 bit nvidia bios?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by tw1859 on 2008-04-23
thanks

---

### Post by Tatty on 2008-04-23
You should be able to run 32bit ubuntu on an x64 machine.  x64 was designed to be backwards compatible with 32bit applications.

But to be honest ubuntu 64bit is pretty much on an equal footing now with the 32bit edition.  The only problem that really affects people as far as im aware is getting java to work properly with it.  But that should be fixed soon as java is being released open source.

---

### Post by tw1859 on 2008-04-24
Nice, thank you. Look forward to operating with ubuntu. Does it have anything like bitlocker. Saw some neat programs I want to try like pgp on the toolbar. Wow, I am almost ready for install, thanks for the advise.

---

### Post by Chayak on 2008-04-24
> **tw1859 said:**
> Nice, thank you. Look forward to operating with ubuntu. Does it have anything like bitlocker. Saw some neat programs I want to try like pgp on the toolbar. Wow, I am almost ready for install, thanks for the advise.

You can create an encrypted partition to run your system off of but you need to use the alternate install CD and your /boot must be on an unencrypted partition for it to boot though I have put the /boot on a usb thumb drive and booted off of that.

---

### Post by Paqman on 2008-04-24
> **tw1859 said:**
> Does it have anything like bitlocker.

Truecrypt can encrypt anything from a whole drive to a single file. Plus it's cross-platform, so you can have encrypted data that you can read from Ubuntu or Windows.

---

### Post by tw1859 on 2008-04-24
Thanks people...:)

---

### Post by tw1859 on 2008-04-24
Chayak, Not sure what your talking about.

---

### Post by Chayak on 2008-04-24
No, if you use the alternate install CD then when it comes to partitioning it will give you the option to create a LUKS encrypted partiton instead.  It'll ask for the passphrase before it will boot.  The /boot mountpoint will remain unencrypted though you can install that to a usb stick and boot your computer using that.

A setup I've used in the past has a small windows parition that will boot by default and then my encrypted linux partitions for / and swap.  If the computer is booted normally then windows will show up.  When I want to boot into my linux system I use my thumbdrive as the boot order in the bios will use it first.  I enter the correct passphrase and I'm in linux.

---

