---
title: "windows cannot be installed anymore thanks to ubuntu"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by hackernewtolinux on 2013-10-19
hi there guys. so i wanted to install ubuntu and got my hands on a windows 7 iso. when i burned it and put it in my disk it did not work. i booted via the dvd reader, and i got that
press any key to continue ... screen.
i tried pressing some keys and it showed me blank screen and booted into ubuntu.
so i booted up a live ubuntu CD and deleted all partitions and tried booting up like that. but i still get that screen and no use....
i thought the ISO was a defective one and downloaded another time. but both of the DVD's work in another laptop and the installation works just fine. can anyone help me with this?
thanks a lot!!

---

### Post by TheFu on 2013-10-19
Please run **boot-info** and post the link.  More details in my signature.

---

### Post by fantab on 2013-10-19
Windwos install disk will NOT boot if it doesnt see any NTFS formatted Partition. Or atleast some space must be unallocated. 

If you want to dual boot I suggest you install Windows first and to the first partition. This is NOT a hard rule with Windows 7 but it will be better to have windows partition first on the disk. 

Boot with Ubuntu DVD/USB and "Try ubuntu without installing'. Open Gparted and create NTFS partitions (since you say you've deleted partitions) as required. Then when installing Windows format them again as NTFS with windows installers partition utility.

Good Luck...

---

### Post by hackernewtolinux on 2013-10-19
ok, then i formatted everything in NTFS, but now even Mint and ubuntu do the same. but no use.

---

### Post by fantab on 2013-10-19
Ubuntu and Mint wont work with NTFS. They need to see either EXT4 or unallocated Space. I understand if its frustrating. Just relax.

IS your HDD in good health? If you can boot Ubuntu then use 'Disks" utility to check your HDD health. If NOT, then, I'm afraid but you'll have to remove your HDD put it in some other working Machine and test it.
Try [Gparted Live]("http://gparted.sourceforge.net/livecd.php"), if Ubuntu won't boot.

---

### Post by Bucky Ball on 2013-10-19
Boot Ubuntu Live CD, get to a desktop and open Gparted
Delete all partitions leaving the entire disk as free space
Install Windows on whatever sized partition it needs, leave the rest free space
Install Ubuntu to the free space

---

### Post by mahesh3 on 2013-10-19
As far as I know, windows require bootable partitions to proceed installation. The best way to install windows after linux based partitions and installation is by formatting that driver. That is what I can suggest for now.

---

### Post by hackernewtolinux on 2013-10-19
guys thanks for the help, it is true that the community helps. BTW i made my whole hard drive NTFS and tried windows. i try to press a key when prompted and it the screen comes twice. then it goes back to the bios selection menu(Select device to boot from(bios)). that dosent happen to linux or mint.  but when i burnt a DVD with kali-linux it is the same prblem with the windows DVD. i think the ubuntu bootloader or whatever took over the system and i did'nt delete it.

---

### Post by Mark Phelps on 2013-10-19
Sorry for the  bad news, but this sounds like a problem with the Windows install media. If the media has a defect, the installer app won't be able to read it properly and will fail -- forcing a reboot.

As to formatting in advance, while that is a good idea (especially if you don't want the burden of an extra Windows boot partition), you should make sure that you REFORMAT the NTFS partition in the Windows installer, not just install to that partition.

---

