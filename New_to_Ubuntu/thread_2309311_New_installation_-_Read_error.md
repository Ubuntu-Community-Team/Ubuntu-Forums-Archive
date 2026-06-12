---
title: "New installation - Read error"
date: 2016-01-09
forum: New to Ubuntu
---

### Post by atacht2015 on 2016-01-09
Hi, I'm hoping someone can help me. Please excuse my ignorance.


I have a laptop and have wiped XP from it with the 'erase and install' function whilst installing 14.04.3 LTS. I got a short error message at the end about a grub error and now when I boot it just goes to 'read error'.


I have tried to download a couple of tools but I can't connect to Wifi at the moment (on this laptop - I can download anything I need to a key and try that). I will fix the wifi when I have Ubuntu fully installed. 


The live CD works fine.


Any help would be gratefully received!!


Best,

Atacht

---

### Post by cogier2 on 2016-01-09
You don't say what the specs are for your XP machine. If you are installing Ubuntu may find that the Unity desktop is bit 'heavy' for your machine. You might try Ubuntu Mate, or Mint Mate which have 'lighter' desktops. Regarding the wifi there is a Driver Manager in the Linux Mint versions that can often sort this out for you. It used to be in Ubuntu but I'm not sure it's still available.

The read error may be as simple as the boot order being incorrect. Have a look in the BIOS and make sure the Hard drive is at the top of the boot order list, it may be trying to find an operating system on a CD/DVD or USB stick.

---

### Post by leunam12 on 2016-01-09
Boot the installation media again "Try Ubuntu", Open "Disks" program and go to the SMART data section and see if your hard drives has errors. If it doesn't, open Gparted and create a new partition table. Now create the partitions that you need (ext4), usually one for root "/", one for "Home", and another one for SWAP. Then go to Desktop and double-click install Ubuntu and chose "something else".

---

