---
title: "XP will not boot from dual boot"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by nalkari2001 on 2008-11-06
:)I have recently loaded XP and Ubuntu 8.10 64 desktop on a dual boot single hard drive and they were working well and suddenly XP will not boot. When I startup the selection menu works fine and boots into Ubuntu with no problems, but when I select XP from the boot menu it displays "starting up .." and thats where it stays until I reboot the PC. I have checked the harddrive in Ubuntu with Fdisk -l and the HPFS/NTFS partition displays. I can access the windows drive from Ubuntu and the files are intact. I have also tried repairing he windows installation from the XP boot disk but to no avail. Any suggestionwould be appreciated, Thank in advancce.:confused::confused:

---

### Post by Bölvaður on 2008-11-06
I suggest using super grub disk.
It will find out every os on the computer, so if you are unable to run it from there, windows is not working.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by caljohnsmith on 2008-11-06
How about opening a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Also, with that "Starting up..." error when booting Windows, that can often be due to your Windows boot sector not having the correct file system parameters, and it can usually be fixed with "testdisk". To use testdisk, just do:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and see if you can boot Windows. Let me know how it goes. :)

---

### Post by nalkari2001 on 2008-11-07
:):):):):)
Thanks for the replies, I used testdisk and it worked perfectly. The output from fdisk -lu is as follows. 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd521d521

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   117194174    58597056    7  HPFS/NTFS
/dev/sda2       117194175   225391949    54098887+  83  Linux
/dev/sda3       225391950   234436544     4522297+   5  Extended
/dev/sda5       225392013   234436544     4522266   82  Linux swap / Solaris

Also thanks for the super grub disk suggestion had it downloaded onto a CD in case testdisk did not work.

This is my test PC to see if the 64 bit is better than the 32 and to get used to Ubuntu. I am presently building a new PC and intend dual boot it as well. Again thanks for both replies.:guitar:

---

### Post by caljohnsmith on 2008-11-07
Glad the testdisk procedure worked. Cheers and have fun. :)

---

