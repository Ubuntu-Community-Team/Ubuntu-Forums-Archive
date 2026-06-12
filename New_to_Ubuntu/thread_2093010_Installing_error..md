---
title: "Installing error."
date: 2012-12-09
forum: New to Ubuntu
---

### Post by maartenpeels13 on 2012-12-09
I wanted to install Ubuntu 12.04 as soon as I read about it (today), and followed a tutorial on youtube. I tried installing the software from USB. I followed the instructions, but upon installing immediately from the startup screen, an error soon occured:

mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I am an absolute noob in this area, and have no idea what to do or what this means. Can anybody help me? Thanks already!

---

### Post by BrokenLines on 2012-12-09
Welcome to the family before anything!
Okay, so I had this problem at first as well a few months back when I install it. There are three things I would recommend you try (first off I am no expert, just trying to help you in ways that I can)
1) Try and reformat your usb and then make it bootable to Ubuntu again ( I prefer uNetbootin for that it's simple to download the iso and follow on screen instructions.)
2) Try booting from a live cd (can be usb just called live cd) it may just be something wrong and your hardware not compatible.
3) Try another distribution based on Ubuntu, not saying anything ill of it but there are much better and maybe it's just this version and you could try another one like 12.10 or something.
For me the first one worked right away, and I used the other two for my friends computer which had a similar issue. But I wish you the best of luck.

---

### Post by maartenpeels13 on 2012-12-13
I tried formatting and Lubuntu, now it says 'bootmgr missing' when i tried with lubuntu. What does that mean?

---

### Post by holycow131415 on 2012-12-13
When your bios screen pops up, tap one of your F keys to change to boot from usb. Your BIOS screen will tell you which button to tap. Sometimes its F12, it varies from system to system.

Another way is to go into your BIOS (usually is F2, but again read your BIOS screen), and make sure booting from USB is first on your boot order. I have mine as USB, CD drive, then hdd.

---

