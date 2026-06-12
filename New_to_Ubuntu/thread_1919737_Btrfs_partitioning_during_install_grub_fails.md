---
title: "Btrfs partitioning during install grub fails"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by rgreener25 on 2012-02-03
When installing oneiric I want to set all partitions but the /boot to btrfs with /boot being ext2 so i run through the install and grub-install /dev/sda fails so then i try to install it to /dev/sda1 (/boot) and it fails. I don't know what's gone wrong. The drive is GPT if that helps

Here are the partitions
sda1 500mb ext2  /boot
sda2 6gb   swap  swap
sda3 200gb btrfs /home
sda4 30gb  btrfs /usr
sda5 30gb  btrfs /usr/local
sda6 30gb  btrfs /opt
sda7 5gb   btrfs /var
sda7 10gb  btrfs /tmp
sda8 8gb   btrfs /

Thanks in advance

---

### Post by rgreener25 on 2012-02-03
Oh and if it helps that's it there's no free space left

---

### Post by rgreener25 on 2012-02-03
Help Me?

---

### Post by rgreener25 on 2012-02-03
Could the boot partition be too small

---

### Post by rgreener25 on 2012-02-03
help I'm desperate I need my laptop

---

### Post by rgreener25 on 2012-02-03
i ran grub-install /dev/sda from terminal once installed and i got this [CODE]/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)

---

### Post by rgreener25 on 2012-02-03
i ran grub-install --root-directory=/mnt/main /dev/sda it said gpt has no bios boot partition

---

### Post by The Cog on 2012-02-03
I think I remember reading that with GPT drives, you need to create a partition for the bootloader. Sorry, but I don't know where I read this, and don't remeber how you label the partition as the bootloader partition, so you'll have to google for it. I'm sure I was reading how to set up a PC for btrfs booting though.

---

