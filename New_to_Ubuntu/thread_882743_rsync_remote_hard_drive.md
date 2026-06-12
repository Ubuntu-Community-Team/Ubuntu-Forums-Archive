---
title: "rsync remote hard drive"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by sn0m on 2008-08-07
HI guys. I've got a laptop with cracked screen but otherwise going ok. I'm planing to plug a usb hard disk with respectable capacity in it and use it to back up documents every saturday evening from my two other linux machines.
Is that possible using rsync via samba, or what would be the best way to go about doing it.
Kind regards
Sokol

---

### Post by hyper_ch on 2008-08-07
either mount that usb disk in the laptop and then use nfs to mount the laptop into the local file directory OR install openssh server and use rsync over ssh to sync onto your mounted usb disk in your laptop or use SSHFS to mount the mounted usb disk in your laptop on your local computer.

---

