---
title: "Recover formatted EFI Partition"
date: 2020-05-10
forum: New to Ubuntu
---

### Post by zi1mann on 2020-05-10
Dear all, 

today, when I wanted to format a flash drive through gparted, I instead formatted my EFI/Boot partition on my local disk (wasnt paying attention, did not switch from sda to sdb). I though that this problem would be easily fixed through creating a startup disk from another device and then just repair the system through the installation wizard on a live disk ubuntu - but this wont work. When "Trying Ubuntu", I get no option to repair my existing installation (just the usual install ubuntu and delete all data on the drive).

I also found boot-repair as an option, but the Recommended Repair option isn't available for me - the only thing I can do is create a Boot Info Summary, which can be found here: [http://paste.ubuntu.com/p/bgvChgrrMX/](http://paste.ubuntu.com/p/bgvChgrrMX/). When starting, boot-repair also informs me, that "/boot" was found. 

The bootflag is still set on the sda1 partition (which is also recognized as EFI System Partition), according to parted

Model: ATA SAMSUNG MZ7TY256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1305MB  768MB  ext4
 3      1305MB  256GB   255GB


Now I am completely lost on what to do next in order to recover my current installation, especially since I have no deeper understanding of Ubuntu and therefore I already had a hard time searching for help online. 


Any help would be kindly appreciated, 
Regards!

---

### Post by oldfred on 2020-05-10
If ESP is otherwise ok, you just need to reinstall grub, full reinstall, not a  `sudo update-grub`. 

Be sure to boot Ubuntu live installer in UEFI boot mode. And use Advanced mode for full grub reinstall.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by zi1mann on 2020-05-10
I am not sure whether I understand your suggestions.

 Do you refer to the advanced options in Boot-Repair? Any GRUB related tabs there are not available/grayed out and Boot-Repair was installed through the ppa option. The Boot-Info summary was pasted here: [http://paste.ubuntu.com/p/3g9kwRMScv/](http://paste.ubuntu.com/p/3g9kwRMScv/)

How can I make sure that the live installer is booted in UEFI? When starting, I just drop into Grub where I then choose to try ubuntu without installing - or is this done when actually creating the startup drive? 
 

I also tried walking through some of the "chroot"-Options for Grub reinstall (without any idea, whether this would actually fix my problem), but I can not mount my efi partition because there is no mount point: 
sudo mount /dev/sda1 /mnt/boot/efi 
mount: /mnt/boot/efi: mount point does not exist.

---

### Post by oldfred on 2020-05-10
I do not really know LVM, as that is more for advanced users.
If you have to have encryption, then you have to have LVM.

For Boot-Repair to work, it has to see your install, so you have to manually mount your LVM volumes and decrypt the install.

Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

Query to check if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

You get different screens whether BIOS or UEFI.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by zi1mann on 2020-05-11
Okay, EFI is fine. I managed to run boot-repair and it actually ran through with the result that I should be able to reboot normally now. Thanks for the links to the threads about mounting encrypted partitions, this helped me great time and I wasnt really aware of this problem (thinking about it now, I should've been aware). 

However, it indicated that an error occurred in the process, which can be found in the report: [http://paste.ubuntu.com/p/r4DhVzQnWV/](http://paste.ubuntu.com/p/r4DhVzQnWV/)
I figured it has something to do with my external flash drive on dev/sdbX I am running my live session from. 

Is it safe to reboot normally now? Thank you so far.

Update: It actually worked, thank you!

---

### Post by oldfred on 2020-05-11
It showed no error on the reinstall of grub.

The error is on sdb, and often live installers are not normally partitioned drives, they are hybrid DVD/flash drive configurations. And then do not have standard partitions. So error is normal.

---

