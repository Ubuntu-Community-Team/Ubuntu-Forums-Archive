---
title: "Boot drive is not mapped and Ununtu is not installing"
date: 2020-01-30
forum: New to Ubuntu
---

### Post by Crazy01 on 2020-01-30
I have HP laptop and trying to install Ubuntu. I created a USB bootable which is working fine and able to start Ubuntu from USB but once trying to install on drive it’s always unable to mound bootable drive(Disk utility shows tow partition one is bootable which is failed to mount) and my installation never get completed. Seems it’s hand and when I try to restarted without USB, it’s not finding bootable disk.

---

### Post by oldfred on 2020-01-30
Windows 10?

Is fast start up off?
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Or is drive not AHCI, many default to RAID/Intel RST. But if using Windows you must first install AHCI drivers into Windows.

Or have you updated UEFI or SSD firmware?

---

### Post by Crazy01 on 2020-01-30
I format my laptop so no OS  at present. Disk which shows bootable is a backup partition which is failing to mound.

---

### Post by yancek on 2020-01-30
How old is the HP?  Was there an OS on it previously and if so, what?  Which installation type method are you using?  Are you saying you can boot the Ubuntu usb and see 2 partition on the hard drive on which you wish to install?  It isn't really clear if you are still in the process of attempting to install Ubuntu or if you have completed the install and are unable to boot the newly installed system, which is it?  Boot the Ubuntu installer with the Try Ubuntu option and from a terminal, run the following command and post the output here:

```
sudo parted -l
```

That is a lower case Letter L in the command.

---

### Post by Crazy01 on 2020-01-31
> **yancek said:**
> How old is the HP?  Was there an OS on it previously and if so, what?  Which installation type method are you using?  Are you saying you can boot the Ubuntu usb and see 2 partition on the hard drive on which you wish to install?  It isn't really clear if you are still in the process of attempting to install Ubuntu or if you have completed the install and are unable to boot the newly installed system, which is it?  Boot the Ubuntu installer with the Try Ubuntu option and from a terminal, run the following command and post the output here:

```
sudo parted -l
```

That is a lower case Letter L in the command.

 HP is four year old.
Previously Windows 10 was installed. But I erase everything in the first try of installation.
 I booted from USB and tried to install from the a Install Ubunto 19.10 icon which is on my Ubuntu desktop.
 I think, my installation never completed and always hung and never seen any screen which say completed

.  
 
 
  Sudo parted -l  
 Model: ATA TOSHIBA MQ01ABD1 (scsi)
 Disk /dev/sda: 1000GB
 Sector size (logical/physical): 512B/4096B
 Partition Table: gpt
 Disk Flags:  
 
 
 Number  Start   End     Size    File system  Name  Flags
  1      1049kB  538MB   537MB   ntfs               boot, esp
  2      538MB   1000GB  1000GB                     lvm

When I tried to install from Installer, i get this error also:

 The Attempt to mount file system with type vfat in SCSI1(0,0,), pratition #1(sda) at *boot*efi failed.
You may resume partitioning from partitioning menu.

 
Installer UI stuck with label:

Creating ext4 file system / in partition #1 of LVM VG vgubuntu, LV root

---

### Post by oldfred on 2020-01-31
You have used LVM which is a more advanced logical volume system over standard partitions. 
Did you also select encryption?

In HP's UEFI boot menu can you boot the hard drive entry?

With LVM you have to manually mount the LVM volumes & if encrypted, decrypt the volumes otherwise Boot-Repair cannot see your install.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Crazy01 on 2020-02-04
> **oldfred said:**
> You have used LVM which is a more advanced logical volume system over standard partitions. 
Did you also select encryption?

In HP's UEFI boot menu can you boot the hard drive entry?

With LVM you have to manually mount the LVM volumes & if encrypted, decrypt the volumes otherwise Boot-Repair cannot see your install.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I don't select encryption 
I formatted my Windows and can't install anything from Hard Disk. 
I can't see any PPA version option in USB install option.

---

### Post by Crazy01 on 2020-02-04
> **oldfred said:**
> You have used LVM which is a more advanced logical volume system over standard partitions. 
Did you also select encryption?

In HP's UEFI boot menu can you boot the hard drive entry?

With LVM you have to manually mount the LVM volumes & if encrypted, decrypt the volumes otherwise Boot-Repair cannot see your install.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I tried Boot-Repair and then again tried to install Ubuntu but ended up with same error.
Boot repair log is:
[http://paste.ubuntu.com/p/JD9ZQ3rKqD/](http://paste.ubuntu.com/p/JD9ZQ3rKqD/)

Now I do remember, One time I chosen encrypt option but that installation abruptly stopped.
I appreciate any help

---

### Post by Crazy01 on 2020-02-04
I checked my disk in Gparted and both partition shows a key icon. does this  mean it's encrypted?

---

### Post by oldfred on 2020-02-04
You are showing sda1 as the Windows NTFS boot partition with Windows boot files, but no Windows install.
And you show the ESP flag on the partition, but that can only be on the FAT32 partition that is the ESP.
So that is why you are getting errors.

Reformat sda1 as FAT32 with boot & esp flags.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Crazy01 on 2020-02-05
> **oldfred said:**
> You are showing sda1 as the Windows NTFS boot partition with Windows boot files, but no Windows install.
And you show the ESP flag on the partition, but that can only be on the FAT32 partition that is the ESP.
So that is why you are getting errors.

Reformat sda1 as FAT32 with boot & esp flags.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Thanks after format it's installed without any issue.
Thanks again!

---

