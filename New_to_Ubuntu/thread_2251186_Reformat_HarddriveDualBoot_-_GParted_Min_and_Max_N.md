---
title: "Reformat Harddrive/DualBoot - GParted Min and Max Numbers Are The Same"
date: 2014-11-02
forum: New to Ubuntu
---

### Post by CityGirlLuv on 2014-11-02
I have to reformat my harddrive as I'm going to install Windows 7 Home  Premium back onto my computer (for school purposes, I attend school  online and my proctoring needs to be through Windows), but I'm also  wanting to keep my Ubuntu 14.04 so I'd like to do a dualboot. I'm having  an issue that I'm very stumped from. It involves freeing up space. The  minimum space is the same exact number as the maximum space. I'm also  using GParted. Luckily, I don't have any important documents on here  yet, so if I have to remove Ubuntu and do a fresh install, I am willing  to do that. This all came about as I just bought a new harddrive a few  weeks ago. I had already backed up everything from previously. I've  taken some screenshots (which you can view below) on what's going on  exactly.

[ATTACH=CONFIG]257706[/ATTACH][ATTACH=CONFIG]257707[/ATTACH]

Thanks in advance, 

CGL

---

### Post by grahammechanical on 2014-11-02
There is nothing "going on" as you put it.

Partition sda1 has 887.82GiB unused space. That means you can shrink sda1, which is a primary partition, by the way and then move it to the right. That will leave unallocated space in front of sda1 in which to create a partition or partitions for Windows 7.

We resize by either grabbing the arrow and moving it to the left or click the down arrow on the New Size box. That will create Free space following sda1. You could turn that free/unallocated space into a partition for Windows but it might be best to move sda1 to the right so that Windows can have its partition at the from of sda1. It will most likely be called sda3. Do not worry about that either. 

Regards

---

### Post by CityGirlLuv on 2014-11-02
Here's the issue I'm running into. I'm unable to resize anything. I can't move the arrow, nor type in a newer number. It's as if I can't do anything at all. The down arrow is greyed out.

---

### Post by coffeecat on 2014-11-02
That's because you can't resize a mounted partition, in this case your root partition. You can't resize the root partition of a system you are running. If you want to resize sda1, you will have to use gparted from the live session, either a live DVD or USB.

A couple of very large caveats. Resizing a partition from the left takes a very long time - hours and hours. Also, if you install Windows after Ubuntu on an mbr partition table system - such as yours - the Windows bootloader will overwrite grub in the mbr, meaning that you won't be able to boot into Ubuntu. Until you re-install grub from the live session, that is. It's a fairly easy fix, but one you need to be prepared for.

You mention being willing to remove Ubuntu first. To be honest, the time it takes to re-install Ubuntu compared with the time it is going to take to shrink your sda1 partition means that redoing the partitions, installing Windows first, followed by re-installing Ubuntu is probably going to be a lot quicker. Plus, you won't need to worry about Windows overwriting the grub bootloader.

If you do, be aware that there is a bug or design fault with the 14.04 Ubuntu installer that leads to some people losing their Windows partition. I'm a bit hazy about the details, but you can avoid this by choosing the "something else" option at the partitioning stage of the installer.

---

### Post by oldfred on 2014-11-02
The little key says it is mounted and you cannot unmount the partition you are running from. 
So to edit partition you need to use Ubuntu live installer which has gparted or download a gparted liveCD.

You said it is a newer system, so it may be both UEFI and BIOS. Since you have MBR partitioning, Windows will only install in BIOS boot mode.
In BIOS boot mode Windows will install to one primary formatted NTFS partition with the boot flag. Default install is two primary partitions, one 100MB boot/repair and main install. That is so you could encrypt or perhap repair main install. But better to have repairCD or flash drive for Windows anyway. But if installed in one partition you must have that repairCD.

---

### Post by Impavidus on 2014-11-03
If you decide to wipe your Ubuntu system before installing Windows and reinstalling Ubuntu, best to make a backup of your entire home directory (after clearing some caches), not just of your important files. After reinstalling Ubuntu (same version as you have now), you can restore the backup from your live session. That should save you a few hours reconfiguring all your applications and DE. Also run```
dpkg --get-selection > packages.txt
```to create the file packages.txt with a list of all installed packages on your current Ubuntu system and save it to an external drive, along with the rest of your home directory. On the new installation, run```
sudo dpkg --set-selections < package.txt
sudo apt-get deselect-upgrade
```to install these packages. This should reinstall all software you had in just a few minutes.

---

