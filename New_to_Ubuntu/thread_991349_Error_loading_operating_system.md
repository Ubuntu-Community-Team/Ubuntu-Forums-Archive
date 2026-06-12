---
title: "Error loading operating system"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by laurielegit on 2008-11-23
Ok, this is a problem that has disabled my whole computer. It started when I tried to install windows XP. I inserted the disk and started the computer. When I got to the partition editor I tried to create a new partition in my unpartitioned space but when I asked the installer to use the partition it claimed that it was not the correct type. At this point it could see the partition table. I then rebooted with a Gparted CD. Gparted decided that I had a totally blank disk. I then took out Gparted and rebooted the computer, thinking to just give up and explore other avenues to using windows software. It was then that I was shocked to find that that the computer had a problem: "Error loading operating system". I then used my fedora live cd to check that I hadn't lost any data, and it seems that no files have been changed. I have no idea what has happened, so I turn to you for help. 

Thanks,

Laurie

---

### Post by oldos2er on 2008-11-23
Trying to install Windows probably wiped out your MBR. You can use either an Ubuntu Live CD or Super Grub Disk to restore grub.

---

### Post by caljohnsmith on 2008-11-23
Sounds like it could be a hardware issue, but maybe it is a problem with a corrupt partition table. How about opening a terminal (if you use the Ubuntu Live CD, it is under Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -l
```
And then to check the HDD partition table, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

