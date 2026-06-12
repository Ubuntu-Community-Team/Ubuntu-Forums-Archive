---
title: "Grub resuce error Win7, ubuntu external"
date: 2014-11-08
forum: New to Ubuntu
---

### Post by lukas19 on 2014-11-08
So it have a small problem.

I have Win7 installed. I installed Ubuntu on my external hd. When the instalation finished and it rebooter the PC and I unpluged the external hd, the Windowns does not start and I get a Grube rescue message... Please help. I'm a noob.

---

### Post by westie457 on 2014-11-08
Welcome to the Forums lukas19.

Does the computer start with the external drive connected?

Can you select which drive to boot from using F12 (the usual button) to get to the one-time boot menu? Yours might be different.

---

### Post by oldfred on 2014-11-08
With an external drive you need to use Something Else to install as that is the only install option that lets you choose where to install grub2's boot loader. Default installs always install to sda usually your internal drive.

So you really want grub2's boot loader on external drive, external drive set as first in BIOS boot order and Windows boot loader in the MBR of internal drive and it set as second in BIOS boot order. Then if external is unplugged you directly boot Windows.

Grub has to find the rest of its boot code in the external drive. The MBR of a drive is tiny and just tells system where to go to find the rest of the boot code & menu.

You can use Boot-Repair. Plug in external & boot into Ubuntu. Or use live installer.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can easily install grub2's boot loader to the sdb drive:
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub


You can also use your Windows repairCD or flash drive to restore the Windows boot loader to the internal drive, but still need to install grub to external drive's MBR first.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

      How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Grub also remembers which drive you installed boot loader into by model/serial number. Best to update that info so if you get a major update from grub it correctly installs to the external drive.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
It will show drive model & serial number

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by lukas19 on 2014-11-08
Thank you for you rapid response.

I operate a notebook, don't know if it makes a difference. And, no, the external drive is unpluged. 

So first things first.
I launched the ubuntu from a bootable dvd, and choose instal ubuntu. Connected the external drive. Selected the Free Space available on the external drive. Selected the main disc space and the secondary area or something. Installed. At the end reboot. The ubuntu didnt load nor did windows. I went into bios and enabled the external device boot. Booted ubuntu. Happy face :) Rebooter the notebook, this time without external hd, and the windows does not boot. Grub rescue and ****. 

Thank you for the links and stuff, I will try it out as soon as possible, and will report you about my progress.

---

### Post by lukas19 on 2014-11-08
Ok. I've got it! 

My mistake was I didn't select during the instalation, the external hd as the boot location. I just uninstalled the ubuntu and installed it again with the right setting and it all runs just perfect! 

Thanks for the quick response.

---

