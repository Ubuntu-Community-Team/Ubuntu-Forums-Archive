---
title: "Completely Removing Grub"
date: 2015-09-16
forum: New to Ubuntu
---

### Post by Quarkrad on 2015-09-16
Trying to help neighbour migrate to win10 so I disconnected my normal ubuntu HD (hd1) and did a clean install of win7 on a new HD (hd2).  When finished I connected another HD (hd3), that I use for Backup, so I could image my win7 HD.  To my suprise on a reboot I got the message error: no such device: C8Dxxx-etc....  Entering recue mode... grub rescue.   Initially I was confused as my 'Ubuntu' HD (hd1) was disconnected but then assumed(?) that at some time in the past when installing grub on hd1 it must have also installed itself on hd3 (when I disconnected hd3 the pc rebooted to win7).  So ....  if I disconnect hd2 and connect hd3 only and boot to a live cd how best to remove grub?   I would like to keep the data on HD3 so I'm guessing I just need to remove grub from the mbr.  Thanks.

---

### Post by jim_deadlock on 2015-09-16
Boot your Windows installation DVD and run repair, that will install MBR onto HD3 which will overwrite Grub.

Alternatively (for example if you don't have the Win DVD) you can boot the Ubuntu live DVD, install boot-repair, run it and fix Grub which will allow you to boot Windows from Grub. Same result more or less.

---

### Post by oldfred on 2015-09-16
Probably better to use Boot-Repair and also run the Summary Report to know what is where.

You can reinstall grub to Ubuntu drive's MBR if BIOS. 
If UEFI, then grub was in the ESP - efi system partition on sda drive, probably Windows.

With BIOS, grub remembers drive, by brand, model, serial number on where to reinstall. So best to reset that also.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

