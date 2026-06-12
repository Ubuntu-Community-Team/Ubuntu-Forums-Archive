---
title: "Gentoo Network Install..."
date: 2009-01-20
forum: Other OS Talk
---

### Post by icanfly0307 on 2009-01-20
Hi,
   Is there a network install option for Gentoo? By network install, I mean downloading the packages from the internet and installing them locally on my laptop. My CD drive is broken, so that's a bad thing there. But still, I have an existing Linux installation, so if I can boot into the Gentoo intaller off of that, it would be great. Thanks for your help... :)

---

### Post by LinuxGuy1234 on 2009-01-20
> **icanfly0307 said:**
> Hi,
   Is there a network install option for Gentoo? By network install, I mean downloading the packages from the internet and installing them locally on my laptop. My CD drive is broken, so that's a bad thing there. But still, I have an existing Linux installation, so if I can boot into the Gentoo intaller off of that, it would be great. Thanks for your help... :)

Good news. Gentoo can be installed from a another Linux distribution. But you need a partition ready for Gentoo.

(ALL STEPS NEED TO BE DONE AS ROOT)

Chapters 1-4: skip.

Chapter 5:
Mount the partition you've like to install Gentoo on:
```
mkdir /mnt/gentoo
mount /dev/partition /mnt/gentoo
```
Continue.

Chapter 6: Don't do the Optional: Selecting Mirrors part.
Chapter 7 & 8: Normal. You can copy over your config files in chapter 8.
Chapter 9: Normal.
Chapter 10: Normal. Make sure to add a entry for the host distro, unless you don't want it. After doing this chapter, exit the chroot (exit) and then reboot.
Chapter 11: Normal.

---

### Post by kk0sse54 on 2009-01-20
You might want to check this out, [The Gentoo Linux alternative installation method HOWTO]("http://www.gentoo.org/doc/en/altinstall.xml")

---

