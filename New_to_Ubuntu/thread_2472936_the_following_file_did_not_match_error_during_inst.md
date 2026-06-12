---
title: "the following file did not match error during installation...."
date: 2022-03-17
forum: New to Ubuntu
---

### Post by bakon2 on 2022-03-17
Ok, I was running Win12 on this acer latptop. I downloaded version 20.04 and got several errors while installing. I don't remember which ones they were.  After booting up it the Install Ubuntu21.-10 icon is on my desktop. When I try to install it I get this error:
the following file did not match its source copy on the cd/dvd: /target/usr/lib/x86_64linux-gnu/libicudata.so.67.1
I have tried to make a new usb bootable drive (using rufus) and re-download this but I get the same error each time...
I don't know what to do

---

### Post by GhX6GZMB on 2022-03-17
What's Win12?

Anyway, you don't "install" Ubuntu like a Win application. You _boot_ it, either from USB or DVD.
This means that you'll have to force your machine to boot from those. And that usually means changing BIOS or UEFI settings. On Acer it's normally pressing F12 during boot.

---

### Post by ActionParsnip on 2022-03-18
Did you at least MD5 test the ISO you downloaded to make sure it was healthy?

---

### Post by Impavidus on 2022-03-18
> **bakon2 said:**
> After booting up it the Install Ubuntu21.-10 icon is on my desktop.
So you run an Ubuntu 21.10 live disk.

> **ActionParsnip said:**
> Did you at least MD5 test the ISO you downloaded to make sure it was healthy?
You can do the same check on the dvd after burning and maybe, depending on the tool you used to create the live usb, you can do it on the live usb too.

---

### Post by ActionParsnip on 2022-03-18
Also, you could try 22.04. It is the next LTS and due for release next month

---

