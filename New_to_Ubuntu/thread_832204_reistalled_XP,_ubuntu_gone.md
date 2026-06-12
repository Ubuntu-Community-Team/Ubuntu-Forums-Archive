---
title: "reistalled XP, ubuntu gone"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-06-17
i just reinstalled windows XP, and now when i boot up the computer grub doesnt appear anymore. it just goes straight to windows. how do i make grub appear again? windows was/still is my first partition on the drive.

---

### Post by Duck2006 on 2008-06-17
From the live cd in the terminal.

sudo grub

find /boot/grub/stage 1

with what the find command comes back use in the next step, replace x and y

root (hdx,y)

setup (hd0)

quit

Some reading on reinstalling grub

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by hyper_ch on 2008-06-17
search the forum for "reinstall grub" --> that should give you a lot of threads telling you how to do it.

---

### Post by Biggy on 2008-06-17
> **waggingwabbit said:**
> i just reinstalled windows XP, and now when i boot up the computer grub doesnt appear anymore. it just goes straight to windows. how do i make grub appear again? windows was/still is my first partition on the drive.

try [Super Grub Disk]("http://supergrub.forjamari.linex.org/")

---

