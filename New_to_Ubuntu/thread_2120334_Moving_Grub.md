---
title: "Moving Grub"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by benj23673 on 2013-02-26
So I have 3 hard drives in my current computer one has a partition of backtrack then is used to store files (sda), the other one is completely dedicated to windows (sdb) and the last is completely dedicated to ubuntu (sdc). Currently when I want to edit the grub menu, I have to go into backtrack to do it. I want to edit the grub menu from ubuntu instead, but it does not recognize the backtrack kernels?

---

### Post by oldfred on 2013-02-26
With 3 drives you have 3 MBRs, so you can have each system's boot loader in a different MBR. Best if on same drive as install, but does not have to be.

Quick install to MBR is just boot into system you want in the MBR and install grub to that MBR.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

    
But grub does remember where to reinstall on major updates. So in both systems you may need to change where it installs.

       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
If you unchoose every option then it will not reinstall to a MBR.

---

### Post by benj23673 on 2013-02-26
Ok, so I did all that but it would not let me probe -t the device? 
Hmm I need to read more into MBR's and Grub maybe.

---

