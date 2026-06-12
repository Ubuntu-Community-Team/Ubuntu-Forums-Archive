---
title: "Can't install Ubuntu to hard drive"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by nathanielnavidson on 2008-08-14
I'm an extreme beginner to Linux.

I have a computer that has two blank hard drives.

I can use the live session of Ubuntu to start up the computer and that's what I'm making this post from.

When I go to install the software to the hard drive so I can have it as the operating system everything seems to work ok, but when I restart it's as if I hadn't done anything. Please help.

---

### Post by Gannon8 on 2008-08-14
Does it give any error messages, and did you remove the cd during shutdown?

---

### Post by nathanielnavidson on 2008-08-14
> **Gannon8 said:**
> Does it give any error messages, and did you remove the cd during shutdown?

No error message that I can see.  I don't believe the disc was removed during shutdown.  I'd be willing to reformat the drive and start again.  I don't have anything that needs saving.

---

### Post by Too Late on 2008-08-14
Well, the disc must be removed during shutdown (you will be prompted), otherwise it will start the LiveCD/installation process again during next boot.

---

### Post by Gannon8 on 2008-08-14
If you didn't remove the CD, the BIOS Will most likely boot to that. Remove the CD and try again.

If it STILL Didn't work, can you tell me if you are using IDE or SATA Drives?

---

### Post by nathanielnavidson on 2008-08-14
> **Gannon8 said:**
> If you didn't remove the CD, the BIOS Will most likely boot to that. Remove the CD and try again.

If it STILL Didn't work, can you tell me if you are using IDE or SATA Drives?

I believe they are SATA drives.  They show up as SDA and SDB

---

### Post by Too Late on 2008-08-14
IDE (or PATA) disks are also called sda, sdb and so on, at least in Ubuntu 8.04.

Of course, you should check that your hard disk is set as a booting device (preferably after optical drive, though), in BIOS.

---

### Post by Gannon8 on 2008-08-14
While your in the bios, look for a hard drive boot order option, and make sure the one you want to boot from is the first one.

BIOS's differ wildly, so I can't give you specific instructions.

---

