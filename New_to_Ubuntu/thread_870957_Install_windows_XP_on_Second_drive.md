---
title: "Install windows XP on Second drive"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Unotforme on 2008-07-26
I currently have  HH 8.04 installed on my system (and nothing else), and unfortunately several of my devices just won't work (I need my video camera and my MP3 player!) I have two hard drives, so what I would like to do is install XP on my second HD (keeping Ubuntu on my first HD), so I can run my video editing software and use my MP3 player. Can you please direct me to a forum topic or web-link which details the process(es) involved? Thank you in advance.

---

### Post by overdrank on 2008-07-26
> **Unotforme said:**
> I currently have  HH 8.04 installed on my system (and nothing else), and unfortunately several of my devices just won't work (I need my video camera and my MP3 player!) I have two hard drives, so what I would like to do is install XP on my second HD (keeping Ubuntu on my first HD), so I can run my video editing software and use my MP3 player. Can you please direct me to a forum topic or web-link which details the process(es) involved? Thank you in advance.

[http://ubuntuforums.org/showthread.php?t=870936](http://ubuntuforums.org/showthread.php?t=870936)

:)

---

### Post by rockerphil on 2008-07-26
ok,first off you need to be sure that the second HDD is set to "Slave" look for a small switch on the back of the HDD and set it to "S" for Slave. then install it in your machine. now simply pop in the Windows disk and when it comes to the partitioning part of the installation simply choose the 2nd hard drive you're going to install it to. now, remember, when you install Windows it overwrites the MBR, so you're going to have to reinstall GRUB, this link should help

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

hope the info helps,

Phil

---

