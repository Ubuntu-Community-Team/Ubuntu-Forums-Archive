---
title: "Dual boot with windows 7 on second hard drive"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by Jordy_Gijbels on 2015-07-14
Hi all

I'm completely new to Ubuntu and Linux, so go easy on me. I always wanted to give it a go and I decided I should really start looking into it a bit more. Here's what I wanna do: I have been running W7, and I would like to get Ubuntu going on another hard drive. My current HDD setup is as follows:

-One small SSD for Windows only
-A second slightly bigger SSD for games I play most
- 2x 2TB HDD for bulk storage and such
Now, the second HDD has about 1.2 TB free, the rest is already used for general storage and it houses my iTunes install and a bunch of other windows programs. I was wondering if it would be possible to get Ubuntu running on this HDD in Dual Boot, without losing any of the data already on there. So I was wondering how to safely create the required partitions without accidentally removing any of the data. I already tried to give it a go, but I had some issues identifying the correct HDD since the install wizard only gives sda/b/c/d, and I wasnt sure which one was which. I also couldnt see the existing partition, so I was afraid that making one could make me lose my data. I already tried googling, but for the articles I found, they all assume that I am starting with a fresh HDD. Can anybody give me some more insight on how to best proceed with this?

Thanks

---

### Post by oldfred on 2015-07-14
If your data is valuable, you should have good backups. Hard drive will fail, just when not if.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

With multiple drives you need the slightly more advanced Something Else install option. It is the only option that lets you choose which drive to install the grub2 boot loader into. You want same drive as install.
 And you need to know a bit about partitions, but with several drives, I assume you know the difference between a drive and a partition even though Windows uses drive for both.

In Linux a drive is sda, sdb, sdc, sdd. A partition is part of a drive and uses numbers like sda1, sda2 etc.

With Linux the default install is / (root) & swap. Depending on how much you will use Ubuntu you can have / as small as 20 or 25GB and swap at 2GB. Often best not to make / too large, but then add data partition(s) or separate /home. You already have many data partition in NTFS format and Linux will read/write those ok, but best to make Windows NTFS system partition as read only to avoid issues.

Is Windows installed on newer system in UEFI boot mode and gpt partitioning, or in older boot mode BIOS with MBR partitioning? Install is basically the same, except for partitioning & how you boot installer. You must boot installer in mode you want to install & you need to boot in same boot mode Windows is install in, either UEFI or BIOS. If second drive is MBR, and Windows is UEFI with gpt, best to convert drive to gpt first.

I prefer to use gparted to manually create partitions in advance. Works not all that different than any gui partitioning tool.
       GParted partitioning software - Full tutorial 
[URL="http://www.dedoimedo.com/computers/gparted.html"]http://www.dedoimedo.com/computers/gparted.html

      [/URL]Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

    Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

After reviewing the install options come back with your specific issues.
Post this from Ubuntu installer booted in live mode and open terminal, and we can see if BIOS or UEFI and what partitions you have:
Copy & paste this into terminal and copy & paste output back. If longer and with several drives it will be use code tags or # icon in advanced froum editor.
sudo parted -l


    [URL="http://www.dedoimedo.com/computers/gparted.html"]
[/URL]

---

### Post by Jordy_Gijbels on 2015-07-14
As far as backups go for my important stuff (pics, music, etc) I'm already good. Everything is on a small NAS, and pics and music are also mostly on my phone, and I have a couple of important folders copied to every HDD in my computer. It's just that I really dont want to go through the hassle of reinstalling and figuring out everything for half a day to get it all going like it should :) 

It's still an older install with BIOS and MBR, not UEFI and GPT. I am going to look into gparted right now. Before I go any further, where do I put the bootloader if I still want the system to boot into windows by default? Or is there a way that I can choose between which system I want to boot on startup? Do I put the bootloader on the windows disk or on the Ubuntu disk? I had a look at the Grub2 installing article, and from what I can understand it should give me the option. I'm just still kinda confused on where I should put the bootloader best. Thanks already for the extensive information provided!

---

### Post by oldfred on 2015-07-14
Each drive has a MBR which can have a boot loader. And in BIOS you can choose which drive to boot by default and an order to use if default does not work.

You want grub installed to the same drive as Ubuntu, not to sda, which should remain with the Windows boot loader. So if grub does not work for any reason you can go into BIOS or one time boot key often f10 or f12 and directly boot Windows. And you want to change BIOS to boot drive that has grub/Ubuntu as first default.

But grub install defaults to sda, your Windows drive. And all auto install options automatically install to sda as most installs are one drive installs. Only with Something Else do you get an option on where to install grub and you want to change from drive that is sda to drive that you are installing Ubuntu. Some of above install instructions highlight the combo box at the bottom of the drive/partition selection screen on how to select a different drive.

Grub2's os-prober will find other installs and give you an option to boot Windows. But grub only boots working Windows and most fixes for Windows cannot be done from Linux, so best to also have a Windows repairCD or flash drive. Also Windows cannot need chkdsk nor be hibernated to boot from grub. The os-prober runs as part of every grub update to refresh list of bootable installs.

Even if you get boot loader install  wrong, it is easy to reinstall boot loaders. But with multiple drives do not run Boot-Repair's auto fix (always use advanced options)as that would install grub to every drive's MBR. Or use manual commands to reinstall a boot loader. You want to keep a Windows boot loader in the Windows drive. You can use your Windows repairCD or flash to restore a Windows boot loader, or various Linux tools to put in a generic Windows type boot loader.

Some also suggest disconnecting all other drives and only have the drive you want Ubuntu installed connected. Then you can use auto install option as only drive will be seen as sda, but when other drives connected it will change to sdb, sdc or whatever. But it will only create / & swap. And / will take up most of the unallocated space.
Only if you keep same SATA port order on motherboard will drives be in same order, so keep track if you decide to disconnect drives. Windows really must remain as sda or first drive or first SATA port to avoid issues. You do have to re-run grub update to then get grub to find Windows and add it to boot menu.

---

### Post by Jordy_Gijbels on 2015-07-15
Awesome, thanks for the assist! I got it working :) Now to start struggling with the netgear drivers, and that seems even more daunting than installing the OS in the first place...

---

### Post by oldfred on 2015-07-15
If the info helped you can change to solved.

If you cannot find info on your netgear drivers, post a new thread with details.
If wireless, run this script:
       [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)

---

