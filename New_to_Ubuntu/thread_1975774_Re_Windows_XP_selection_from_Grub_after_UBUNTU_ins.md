---
title: "Re: Windows XP selection from Grub after UBUNTU install just reboots PC (back to Grub"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by darkod on 2012-05-07
With this setup I am surprised you can boot ubuntu at all. The bootloader on /dev/sda is all weird.

What editing did you do in the GRUB file exactly? Are you talking about direct editing of grub.cfg or what?

To install correctly grub2 on the MBR of /dev/sda you should boot ubuntu and in terminal try:
sudo grub-install /dev/sda

---

