---
title: "sddm not working on Ubuntu 20.04"
date: 2020-12-22
forum: New to Ubuntu
---

### Post by tech-woofaa on 2020-12-22
I have installed Ubuntu 20.04 with lubuntu-desktop on a Raspberry Pi 4.

Whenever I choose to use sddm, the booting sequence stops after cloud-init is completed. I have to access another tty and login via startx.

I have no such problems when using gdm3 or lightdm. I have also tried sudo remove sddm then install it back but to no avail.

---

### Post by guiverc on 2020-12-22
Known issue; [URL="https://github.com/wimpysworld/desktopify/issues/19"]https://github.com/wimpysworld/desktopify/issues/19

(Sorry I have nothing further to offer)
[/URL]

---

### Post by tech-woofaa on 2020-12-22
Thanks for your reply.
Initially it looks like a software issue, but now it looks like a hardware-specific issue.

---

