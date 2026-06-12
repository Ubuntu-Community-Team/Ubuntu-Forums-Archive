---
title: "Can't use DVD drive - 14.04 LTS"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by Sipho411 on 2014-08-25
Hi i have a similar problem, only difference is that mine can load liveCD from boot. But if I boot into my ubuntu installation the dvd rom is not even listed in "/dev/[sr0|cdrom|dvd]", "sudo lshw" mentions nothing of the device. I went through "/var/[dmesg|syslog]" and nothing. When I load a disc into the drive, it spins and acts as if it's reading it but nothing happens. The problem started when I upgraded from 12.04 Lts to 14.04 Lts. I suspect the problem is in the kernel itself... I don't know what's causing this problem....Specs = (OS => GNU/Linux, Ditsro => Ubuntu 14.04.1 LTS, Processor => x86_64, kernel => 3.13.0-24-generic)

---

### Post by oldos2er on 2014-08-25
Post moved to its own thread.

---

### Post by dave131 on 2014-08-25
> **Sipho411 said:**
> Hi i have a similar problem, only difference is that mine can load liveCD from boot. But if I boot into my ubuntu installation the dvd rom is not even listed in "/dev/[sr0|cdrom|dvd]", "sudo lshw" mentions nothing of the device. I went through "/var/[dmesg|syslog]" and nothing. When I load a disc into the drive, it spins and acts as if it's reading it but nothing happens. The problem started when I upgraded from 12.04 Lts to 14.04 Lts. I suspect the problem is in the kernel itself... I don't know what's causing this problem....Specs = (OS => GNU/Linux, Ditsro => Ubuntu 14.04.1 LTS, Processor => x86_64, kernel => 3.13.0-24-generic)

Since this was split to its own thread I don't know the context of what preceeded your post.  So, I have to ask:  after you put a CD or DVD in the drive, does anything show in /media/<your userid> for the disk?

EDIT:  also, is this an internal or external drive?  CD-RW/DVD-ROM, DVD-RW?

---

