---
title: "Ubuntu to Hard Drive"
date: 2016-06-11
forum: New to Ubuntu
---

### Post by Carl_Hennigar on 2016-06-11
I have Ubuntu installed and running in a VM. I would like to have it in a spare hard drive that I have but do not know how to do this. whenever I go to install it ends up in my VM. The spare drive I have is a empty 500 GB and I am running Windows 7. Any help would be appreciated.

---

### Post by Drone4four on 2016-06-11
To install Ubuntu natively on the bare metal (instead of virtually in a VM) you have to download the iso and then burn it to USB. From there you reboot your computer.  You'll prolly have to flip a switch in your BIOS to instruct your computer to boot off your USB drive.  If you've never accessed your BIOS before, it  might be intimidating if this your first time.  Googling, 'install ubuntu from usb youtube' might help.

Welcome to our Ubuntu community, my friend. =D

---

### Post by ajgreeny on 2016-06-11
In theory it is possible but to be perfectly honest, having read this thread, [http://askubuntu.com/questions/32499/migrate-from-a-virtual-machine-vm-to-a-physical-system](http://askubuntu.com/questions/32499/migrate-from-a-virtual-machine-vm-to-a-physical-system) it seems to me that it is much more straightforward to do a clean install to hard disk using DVD or USB and then from the VM copy all the config files and folders that may be necessary.

I presume you have set up drag and drop or bidirectional clipboard from VM to host, which will make this all relatively simple.

---

### Post by JayKay3OOO on 2016-06-11
Like everyone else says, but use the free version of reflect to make a backup image of your Windows hard drive (from windows) in case you accidentally install Linux to your windows drive instead of your other hard drive.

There also use to be an application called wubi, found opening the ubuntu CD that could install Linux inside windows like an application

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

This is how I first ever installed Linux, back when they still shipped physical ubuntu disks for free.

---

### Post by ajgreeny on 2016-06-11
Forget about using wubi; it is no longer supported and you will not get any support from forum.users nowadays.
Do a "proper" dual boot to partitions on your hard drive and you will get better performance and support from.here.

---

### Post by oldfred on 2016-06-12
Is Windows UEFI or BIOS, most Windows 7 systems were BIOS installs on MBR partitioned drives.
If new drive is not going to ever have Windows installed in BIOS mode, use gpt partitioning. Ubuntu can boot from gpt with either BIOS if you have bios_grub partition or with UEFI if you have the ESP - efi system partition. I normally add both in case drive might be in another system, so I do not have to totally repartition.

If BIOS you have to use Something Else and specify to install grub to external drive, sdb, sdc or whatever it is, not the default sda. If UEFI you have to and an ESP on sda, or it will not correctly install.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 

You can use this, but if BIOS, you need the bios_grub partition which is 1 or 2MB unformatted with bios_grub flag if using gparted. If using gdisk it is code ef02.
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
I normally like to have swap at end of drive, if you have 4GB of RAM or more and do not hibernate, you may never use swap. And having it somewhere in middle of drive can make it more difficult to resize or move partitions.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

