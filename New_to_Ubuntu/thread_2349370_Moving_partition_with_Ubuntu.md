---
title: "Moving partition with Ubuntu?"
date: 2017-01-13
forum: New to Ubuntu
---

### Post by primuspaul on 2017-01-13
I just downloaded the latest Ubuntu install disk and put it on a USB flash drive. I got tired of the problems I was having with Mint and wanted to move to a more popular (and more supported) OS so obviously I picked this. I have some stuff I want to keep on the old drive, so I figured I'd use Ubuntu install disk to resize the old partition and install a Ubuntu partition next to it, allowing me to copy whatever info I need from the mint partition to the new Ubuntu partition I will be using. It's a 250GB modern SSD on SATA and it's resizing a partition that spans the entire thing but only uses 65GB so there's plenty of room. It seems to be stuck, though the red HD lamp is lit. Do I just wait? How long can it take?

Ok, it finally came back and works. Now I have a different problem: I create an EXT4 primary in the new free space but I get no root selected when I go to install.

I decided to do / as the option and it installed, but when I booted the drive, I can select Mint, but where is Ubuntu? I don't see the option to boot to it.

The prior GRUB boot menu contained the mint installation and also an XP installation that is on a different hard drive.

Ok, fixed with a grub command to recreate the list. I then ran into some trouble reordering the GRUB list with grub customizer: it had no effect. I had to use grub doctor (I think) to recreate it.

---

