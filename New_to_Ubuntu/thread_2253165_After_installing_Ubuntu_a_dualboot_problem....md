---
title: "After installing Ubuntu a dualboot problem..."
date: 2014-11-17
forum: New to Ubuntu
---

### Post by mentox82 on 2014-11-17
Hello guys!
So I have installed and been using a Win 7, today I installed Ubuntu 12.04 (hoping for dualboot) and let it automatically make partition to install.
After installation only my Windows 7 could boot (there was not option to boot Ubuntu), therefore i ran Boot-Repair from usb (Ubuntu live) to create Grub.
Then I could only boot Ubuntu 12.04. Now, it seems to me my partitions are somehow ****** up.. i dont really now
Now this is what i have..
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd9fa2484

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2050047     1024000    b  W95 FAT32
/dev/sda2         2050048   206850047   102400000    7  HPFS/NTFS/exFAT
/dev/sda3       206850048   782645685   287897819    7  HPFS/NTFS/exFAT
/dev/sda4       782647294   976771071    97061889    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       782647296   968603647    92978176   83  Linux
/dev/sda6       968605696   976771071     4082688   82  Linux swap / Solaris



Anyway, thank you guys for some help ! :)

---

### Post by oldfred on 2014-11-17
Boot-Repair has the summary report so we can see details. Post link that it provides.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mentox82 on 2014-11-17
Here it is  [http://paste.ubuntu.com/9061746/](http://paste.ubuntu.com/9061746/)

---

### Post by oldfred on 2014-11-17
I see grub installed to the partition boot sector (PBR). Did you use Boot-Repair to reinstall grub to MBR so it will directly boot? Not sure if grub in MBR is current or an older version.

Grub2's os-prober cannot find Windows to add a boot stanza. It looks for bootmgr & BCD.
Your sda1 is now FAT32, was it always? Normal Windows has a 100MB NTFS boot partition with its boot files. You show bootmgr but not BCD. But script is showing a bunch of backup BCDs? I did not think Windows 7 would boot from a FAT32 partition in BIOS mode.

And you have /grldr which is grub4dos. That is an old copy of grub that is installed to the NTFS (FAT?) partition usually by EasyBCD to chain load a grub install in another partition.

If sda1 was originally NTFS you may be able just to change it back. But I would backup all data first just in case.
The partition table and the partition PBR or partition boot sector determine format with NTFS.
You may be then able to change partition type from b to 07 which is NTFS.

 change sda1 to type 07 - note spaces and see man sfdisk for more details.
sudo sfdisk --change-id /dev/sda 1 07

---

### Post by mentox82 on 2014-11-17
Thank you for your respond :) , 
  so I changed successfully sda1 to 07 (NTFS).. but I dont really see where are we heading now (sorry, I am not so much oriented in this stuff)

---

### Post by oldfred on 2014-11-17
Did you reinstall grub to sda not to a partition?

And then does Ubuntu boot?
If it has not found Windows, yet run this:
sudo update-grub

And if it has not found Windows it will auto boot directly with no grub menu.

If it does not boot you may need nomodeset or other boot options.
But if you need boot options because of video issues or other hardware, you will not get grub menu until it has found Windows.

You have to hold shift key from BIOS until menu appears. 
What video card/chip do you have?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by mentox82 on 2014-11-18
So i did reinstall grub to the sda (i think all the time when i installed it, I installed it to sda / I dont see there any other options/).
Yes Ubuntu does boot but not directly, I chose from grub menu where I can choose from Ubuntu or FreeDos(sda1)... so I dont have any problems related to booting to Ubuntu
... anyway my grub still cannot find Windows, sudo update-grub didnt help, i am desperate :/

---

### Post by oldfred on 2014-11-18
Grub really only boots working Windows. 
And grub2's os-prober has to find the correct Windows boot files.

I suggest using your Windows repair CD or Flash drive and run Windows repairs. If you run the auto fix in Windows you have to run it 3 times, but it will reinstall a Windows boot loader to the MBR. So then you need to use Boot-Repair or your Ubuntu live installer to restore grub.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)


 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

