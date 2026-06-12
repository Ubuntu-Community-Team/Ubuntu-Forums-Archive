---
title: "Trying to move my Home directory failed"
date: 2018-11-21
forum: New to Ubuntu
---

### Post by luxocrypto on 2018-11-21
Hi,

I'm afraid I did something very wrong:
- I tried to move my home directory to another disk
- I followed this guide: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
- I rebooted the computer in the middle of the process (can't even remember why)
- computer won't boot anymore, not even with an Ubuntu USB stick nor a DVD...

- the Ubuntu 18.04 startup screen just hangs
- I tried booting from USB: Selected boot device not available
- I tried booting from a DVD: Selected boot device not available

Should I just install Ubuntu on another disk, clean install, and hook up my old drive and see if I can recover something?

---

### Post by oldfred on 2018-11-21
The reboot probably was the error.
You may just have an invalid entry in fstab which stops it from booting.

Can you boot to command line with Advanced options in the grub-submenu and recovery mode?
You can comment out with # as first char of any lines you added.
System will usually boot with a new default /home if old home not found.

sudo nano /etc/fstab

---

