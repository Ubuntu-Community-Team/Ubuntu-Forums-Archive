---
title: "Installing Ubuntu on harddrive with truecrypt partion."
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Thoroniul on 2012-07-23
I want to install an ubuntu partition on a harddrive that currently has an encrypted windows partition. I want it set up so that when my computer boots i can choose whether to boot windows or ubuntu. It currently uses the truecrypt bootloader to run windows, but i know that it will be messed up if I try to install grub. I want to carefully plan this out before i do it to save myself from headaches trying to fix my computer later.

I set aside about 70gb before i encrypted my system partition. So i don't need to worry about re-sizing encrypted windows partitions.

Instructions on how to install Ubuntu this way would be appreciated. I'm not a total beginner at Linux, but i really have no idea what to do when it comes to boot-loaders and partitions.

---

### Post by mastablasta on 2012-07-23
you could install grub to second partition and then choose in BIOS which OS to boot.
 
well i am sure there is a better solution...

---

### Post by Thoroniul on 2012-07-23
I cant touch anything in my bios. Its an hp laptop :(, and i don't know how to unlock it.

---

### Post by Bufeu on 2012-07-23
> **Thoroniul said:**
> I cant touch anything in my bios. Its an hp laptop :(, and i don't know how to unlock it.When the computer starts, try clicking the "Esc"-button until BIOS opens (it must before the OS starts to boot!). If ESC don't work, try spam F1-F12.

---

### Post by Thoroniul on 2012-07-23
I know how to open the bios. I don't think the bios can choose which OS to boot on my laptop.

---

### Post by Bufeu on 2012-07-23
> **Thoroniul said:**
> I know how to open the bios. I don't think the bios can choose which OS to boot on my laptop.
There's a program for this for Ubuntu, called *grub-costomizer*, [http://askubuntu.com/a/100246](http://askubuntu.com/a/100246).

---

### Post by Thoroniul on 2012-07-23
I'm trying to follow the instructions here. [http://pzolee.blogs.balabit.com/2010/07/grub2-and-truecrypt-windows-linux-dual-boot-system/](http://pzolee.blogs.balabit.com/2010/07/grub2-and-truecrypt-windows-linux-dual-boot-system/)

But i don't know how to install grub onto the linux partition.

---

