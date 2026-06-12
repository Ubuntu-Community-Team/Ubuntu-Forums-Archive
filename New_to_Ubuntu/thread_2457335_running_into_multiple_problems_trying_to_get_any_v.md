---
title: "running into multiple problems trying to get any version of ubuntu on an acer spin"
date: 2021-01-30
forum: New to Ubuntu
---

### Post by rspitzy on 2021-01-30
When I ran the installation for kubuntu on the laptop a fatal error occured with grub saying: [COLOR=#242729][FONT=Consolas]Cannot install grub on /dev/mmcblk1: fatal error during installation[/FONT][/COLOR]   
After this I decided to get a fresh install of the iso file and try to restart the computer, but when I did a new set up would pop up when the acer logo was on screen called GNU GRUB... I'm extremely new to linux computers and have no idea how to get out of this and then to boot from the drive. I have tried a couple things like exiting, but then it will say there is no boot order and looking at the drives with ls (see attachment). I would really like to make it possible to boot into kubuntu and have a working desktop again and any help would be appreciated.[ATTACH=CONFIG]287869[/ATTACH]

---

### Post by simon-webb on 2021-02-01
Hi there. GRUB is the boot loader: it is what you want to see after a successful install (it's what loads Linux, or Windows, or whatever you tell it to load once it's installed)...but it should just be presenting you with a menu of boot options, not crashing to a prompt. In any case, something's seriously wrong if your *installer* (i.e. when booting from the USB) is crashing to GRUB! It's unusual for the installer itself to crash like that. Are you sure you don't have a faulty USB stick or some other issue that's corrupting the installer? Maybe try a different USB drive? Normally you should be able to boot the installer to a live desktop to try out the OS: if the installer itself can't boot, something's seriously wrong.

---

### Post by ActionParsnip on 2021-02-01
Is it a dual boot or is Ubuntu the only OS on the system?
Are you using UEFI?

---

