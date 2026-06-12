---
title: "Windows 8 dual boot loader on 2 places - /dev/sda1 and /dev/sda2"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by rtindru on 2012-12-25
I had Windows 7 & Ubuntu 12.04 installed on my Dell Inspiron 64b
I removed the Windows 7 partition & installed (clean) Windows 8

I repaired the GRUB Bootloader, using Boot-Repair 

Now I have 2 Windows 8 option at boottime, mounted at 
1. /dev/sda1 &
2. /dev/sda2

They seem to be separate instances & I wonder if this is normal.

Check out the bootinfo on the link below.

[http://paste.ubuntu.com/1464483/](http://paste.ubuntu.com/1464483/)

-------------------------------------------------------------------
menuentry "Windows 8 (loader) (on /dev/sda1)" --class windows --class os { 	insmod part_msdos 	insmod ntfs 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root B654A6CB54A68DA5 	drivemap -s (hd0) ${root} 	chainloader +1 } menuentry "Windows 8 (loader) (on /dev/sda2)" --class windows --class os { 	insmod part_msdos 	insmod ntfs 	set root='(hd0,msdos2)' 	search --no-floppy --fs-uuid --set=root 362440E02440A4A9 	drivemap -s (hd0) ${root} 	chainloader +1
 }

---

### Post by oldfred on 2012-12-26
Yes, because you ran Boot-Repair.It is as a backup. 

Windows 7 & 8 create a separate small (hidden) boot/repair partition and many users do not see it from Windows and then delete it as they do not know it is required and never see it in Windows. But it has two of the three essential boot files bootmgr & the BCD. So Boot-Repair copies those to the main install so it is always bootable. Then grub sees the boot files & creates a chain load entry to use that also.

You can use Grub-Customizer if you want to hide boot entries. Or manually copy only the entries you want to 40_custom and turn off the os-prober so grub does not search for new entries. You can turn it back on later if desired.

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

    
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by YannBuntu on 2012-12-26
Oldfred +1

I would avoid GRUB-Customizer and/or disabling os-prober, when possible. 
For only hiding 1 of these 2 entries, i would recommend to simply rename the /bootmgr file of sda1 into /bootmgr_old , then run 'sudo update-grub' from Ubuntu.

---

